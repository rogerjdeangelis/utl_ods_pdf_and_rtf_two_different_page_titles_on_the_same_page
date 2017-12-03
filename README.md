# utl_ods_pdf_and_rtf_two_different_page_titles_on_the_same_page
I need two reports with different titles on the same page. If you set 'startpage=no' then multiple procedures can appear on one page, however only one title will be honored. The solution for two titles is to use 'ods text'. You also want the pdf/rtf les to align so that they both span a portrait page.
    SAS Forum: Two reports with different "page" titles on the same page

    SAS forum Title: ODS PDF, Proc Report startpage=no                   1

    PROBLEM
    =======

    I need two reports with different "page" titles on the same page.
    If you set 'startpage=no' then multiple procedures can appear
    on one page, however only one title will be honored.
    The solution for two titles is to use 'ods text'. You also want the pdf/rtf
    les to align so that they both span a portrait page.

    INPUT
    =====
       Five records from

          sashelp.classfit(obs=5)
          sashelp.shoes   (obs=5)

    PROCESS (all the code)
    ======================

    title;
    footnote; * just in case clear titles;

    ods escapechar="^"; * supress default titles ie "The SAS System" ;
    options orientation=portrait;
    ods noptitle;
    ods pdf file='d:/pdf/test1.pdf' startpage=no;  * do not srart a new page;

    ods text='^S={just=center font_size=13pt } First Report';
    proc report data=sashelp.classfit(obs=5) style(report)={outputwidth=100pct};
    run;quit;

    ods text='^S={just=center font_size=13pt } Second Report';
    proc report data=sashelp.shoes(obs=5) style(report)={outputwidth=100pct};;
    run;quit;
    ods pdf close;


    OUTPUT  (note the common spread - both reports are on the same page)
    ======
                              First Report

       Obs     NAME       SEX      AGE      HEIGHT       WEIGHT

          1    Alfred      M        14       69.0         112.5
          2    Alice       F        13       56.5          84.0
          3    Barbara     F        13       65.3          98.0
          4    Carol       F        14       62.8         102.5
          5    Henry       M        14       63.5         102.5

                             Second Report

        Obs    REGION    PRODUCT         SUBSIDIARY      STORES

          1    Africa    Boot            Addis Ababa         12
          2    Africa    Men's Casual    Addis Ababa          4
          3    Africa    Men's Dress     Addis Ababa          7
          4    Africa    Sandal          Addis Ababa         10
          5    Africa    Slipper         Addis Ababa         14


    SAS forum
    https://goo.gl/H3HzJ6
    https://communities.sas.com/t5/ODS-and-Base-Reporting/ODS-PDF-Proc-Report-startpage-no/m-p/417989

    Cynthia SAS profile
    https://communities.sas.com/t5/user/viewprofilepage/user-id/13549

    *                _               _       _
     _ __ ___   __ _| | _____     __| | __ _| |_ __ _
    | '_ ` _ \ / _` | |/ / _ \   / _` |/ _` | __/ _` |
    | | | | | | (_| |   <  __/  | (_| | (_| | || (_| |
    |_| |_| |_|\__,_|_|\_\___|   \__,_|\__,_|\__\__,_|

    ;
      sashelp datasets

          classfit
          shoes

    *          _       _   _
     ___  ___ | |_   _| |_(_) ___  _ __  ___
    / __|/ _ \| | | | | __| |/ _ \| '_ \/ __|
    \__ \ (_) | | |_| | |_| | (_) | | | \__ \
    |___/\___/|_|\__,_|\__|_|\___/|_| |_|___/
               _  __
     _ __   __| |/ _|
    | '_ \ / _` | |_
    | |_) | (_| |  _|
    | .__/ \__,_|_|
    |_|
    ;

    title;
    footnote; * just in case clear titles;

    ods escapechar="^"; * supress default titles ie "The SAS System" ;
    options orientation=portrait;
    ods noptitle;
    ods pdf file='d:/pdf/utl_ods_pdf_and_rtf_two_different_titles_on_the_same_page.pdf' startpage=no;

    ods text='^S={just=center font_size=13pt } First Report';
    proc report data=sashelp.classfit(obs=5) style(report)={outputwidth=100pct};
    run;quit;

    ods text='^S={just=center font_size=13pt } Second Report';
    proc report data=sashelp.shoes(obs=5) style(report)={outputwidth=100pct};;
    run;quit;
    ods pdf close;

    *     _    __
     _ __| |_ / _|
    | '__| __| |_
    | |  | |_|  _|
    |_|   \__|_|

    ;

    title;
    footnote; * just in case clear titles;

    ods escapechar="^"; * supress default titles ie "The SAS System" ;
    options orientation=portrait;
    ods noptitle;
    ods rtf file='d:/rtf/utl_ods_pdf_and_rtf_two_different_titles_on_the_same_page.rtf'
      startpage=no style=minimal;  * do not srart a new page;

    ods text='^S={just=center font_size=13pt outputwidth=100pct} First Report';
    proc report data=sashelp.classfit(obs=5) style(report)={outputwidth=100pct};
    run;quit;

    ods text='^S={just=center font_size=13pt outputwidth=100pct} Second Report';
    proc report data=sashelp.shoes(obs=5) style(report)={outputwidth=100pct};;
    run;quit;
    ods rtf close;


