---
title: "renaming shortcuts on desktop problem"
date: 2012-03-17
forum: New to Ubuntu
---

### Post by markvond on 2012-03-17
A couple of hours ago I installed xubuntu on my sisters netbook.
This is my first time using anything other than windows and I'm having some troubles.

I installed Chromium and managed to get the icon on the desktop.
Now I want to rename it from "chromium webbrowser" to "internet".
this is what happens:

I rightclick on the icon and select rename.
This opens a pop-up thingy.
I change the name and press rename.
The pop-up disappears and the name remains unchanged.

---

### Post by mc4man on 2012-03-17
Don't have or ever used xubuntu but can answer generically - **Maybe**, see edit

A shortcut on the Desktop (desktop launcher) is a .desktop file, it has an actual file name , (whatever.desktop), & a display name

Generally you can't change the actual file name, nor do you want to, it doesn't matter in this case
You are free to change the display name to whatever you wish by editing a line in the file - Name=

So open a text editor or text file in a window so you can also see your desktop icon
Drag the icon over to the editor window & drop in to your editor window.
This will open the .desktop, find the Name= line & change it to Whatever you wish, in this case internet or maybe nicer,  Internet
(there is No space between Name= and the name you choose though the name Can contain spaces

screen shows Ex. - in this case a .desktop I made - the file name is aud-cd.desktop. The display name is Audacious Cd Player

Edit: - if launchers in Xubuntu don't look like what I've posted then copy the contents & post, will take a look, as mentioned never used xubuntu

---

### Post by markvond on 2012-03-17
Thanks for the quick reply.
Here is the code. 
It's aparently showing a different name in every language on earth.
I'm using Dutch[nl] so I should change those right?

```

[Desktop Entry]
Version=1.0
Name=chrome
Name[ast]=Restolador web Chromium
Name[bg]=&#1059;&#1077;&#1073; &#1095;&#1077;&#1090;&#1077;&#1094; Chromium
Name[bn]=&#2453;&#2509;&#2480;&#2507;&#2478;&#2495;&#2479;&#2492;&#2494;&#2478; &#2451;&#2479;&#2492;&#2503;&#2476; &#2476;&#2509;&#2480;&#2494;&#2441;&#2460;&#2494;&#2480;
Name[bs]=Chromium web preglednik
Name[ca]=Navegador web Chromium
Name[ca@valencia]=Navegador web Chromium
Name[da]=Chromium netbrowser
Name[de]=Chromium-Webbrowser
Name[en_AU]=Chromium Web Browser
Name[eo]=Kromiumo retfoliumilo
Name[es]=Navegador web Chromium
Name[et]=Chromiumi veebibrauser
Name[eu]=Chromium web-nabigatzailea
Name[fi]=Chromium-selain
Name[fr]=Navigateur Web Chromium
Name[gl]=Navegador web Chromium
Name[he]=&#1491;&#1508;&#1491;&#1508;&#1503; &#1492;&#1488;&#1497;&#1504;&#1496;&#1512;&#1504;&#1496; &#1499;&#1512;&#1493;&#1502;&#1497;&#1493;&#1501;
Name[hr]=Chromium web preglednik
Name[hu]=Chromium webböngész&#337;
Name[hy]=Chromium &#1400;&#1405;&#1407;&#1377;&#1397;&#1398; &#1382;&#1398;&#1398;&#1377;&#1408;&#1391;&#1387;&#1401;
Name[ia]=Navigator del web Chromium
Name[id]=Peramban Web Chromium
Name[it]=Browser web Chromium
Name[ja]=Chromium &#12454;&#12455;&#12502;&#12539;&#12502;&#12521;&#12454;&#12470;
Name[ka]=&#4309;&#4308;&#4305; &#4305;&#4320;&#4304;&#4323;&#4310;&#4308;&#4320;&#4312; Chromium
Name[ko]=Chromium &#50937; &#48652;&#46972;&#50864;&#51200;
Name[kw]=Peurel wias Chromium
Name[ms]=Pelayar Web Chromium
Name[nb]=Chromium nettleser
Name[nl]=Chromium webbrowser
Name[pt_BR]=Navegador de Internet Chromium
Name[ro]=Navigator Internet Chromium
Name[ru]=&#1042;&#1077;&#1073;-&#1073;&#1088;&#1072;&#1091;&#1079;&#1077;&#1088; Chromium
Name[sl]=Chromium spletni brskalnik
Name[sv]=Webbläsaren Chromium
Name[ug]=Chromium &#1578;&#1608;&#1585;&#1603;&#1734;&#1585;&#1711;&#1736;
Name[vi]=Trình duy&#7879;t Web Chromium
Name[zh_CN]=Chromium &#32593;&#39029;&#27983;&#35272;&#22120;
Name[zh_HK]=Chromium &#32178;&#38913;&#28687;&#35261;&#22120;
Name[zh_TW]=Chromium &#32178;&#38913;&#28687;&#35261;&#22120;
GenericName=Web Browser
GenericName[ar]=&#1605;&#1578;&#1589;&#1601;&#1581; &#1575;&#1604;&#1588;&#1576;&#1603;&#1577;
GenericName[ast]=Restolador web
GenericName[bg]=&#1059;&#1077;&#1073; &#1073;&#1088;&#1072;&#1091;&#1079;&#1098;&#1088;
GenericName[bn]=&#2451;&#2479;&#2492;&#2503;&#2476; &#2476;&#2509;&#2480;&#2494;&#2441;&#2460;&#2494;&#2480;
GenericName[bs]=Web preglednik
GenericName[ca]=Navegador web
GenericName[ca@valencia]=Navegador web
GenericName[cs]=WWW prohlíže&#269;
GenericName[da]=Browser
GenericName[de]=Web-Browser
GenericName[el]=&#928;&#949;&#961;&#953;&#951;&#947;&#951;&#964;&#942;&#962; &#953;&#963;&#964;&#959;&#973;
GenericName[en_AU]=Web Browser
GenericName[en_GB]=Web Browser
GenericName[eo]=Retfoliumilo
GenericName[es]=Navegador web
GenericName[et]=Veebibrauser
GenericName[eu]=Web-nabigatzailea
GenericName[fi]=WWW-selain
GenericName[fil]=Web Browser
GenericName[fr]=Navigateur Web
GenericName[gl]=Navegador web
GenericName[gu]=&#2741;&#2759;&#2732; &#2732;&#2765;&#2736;&#2750;&#2697;&#2717;&#2736;
GenericName[he]=&#1491;&#1508;&#1491;&#1508;&#1503; &#1488;&#1497;&#1504;&#1496;&#1512;&#1504;&#1496;
GenericName[hi]=&#2357;&#2375;&#2348; &#2348;&#2381;&#2352;&#2366;&#2313;&#2332;&#2364;&#2352;
GenericName[hr]=Web preglednik
GenericName[hu]=Webböngész&#337;
GenericName[hy]=&#1352;&#1405;&#1407;&#1377;&#1397;&#1398; &#1382;&#1398;&#1398;&#1377;&#1408;&#1391;&#1387;&#1401;
GenericName[ia]=Navigator del Web
GenericName[id]=Peramban Web
GenericName[it]=Browser web
GenericName[ja]=&#12454;&#12455;&#12502;&#12539;&#12502;&#12521;&#12454;&#12470;
GenericName[ka]=&#4309;&#4308;&#4305; &#4305;&#4320;&#4304;&#4323;&#4310;&#4308;&#4320;&#4312;
GenericName[kn]=&#3228;&#3262;&#3250; &#3253;&#3264;&#3221;&#3277;&#3255;&#3221;
GenericName[ko]=&#50937; &#48652;&#46972;&#50864;&#51200;
GenericName[kw]=Peurel wias
GenericName[lt]=Žiniatinklio naršykl&#279;
GenericName[lv]=T&#299;mek&#316;a p&#257;rl&#363;ks
GenericName[ml]=&#3381;&#3398;&#3372;&#3405; &#3372;&#3405;&#3376;&#3404;&#3384;&#3376;&#3405;*
GenericName[mr]=&#2357;&#2375;&#2348; &#2348;&#2381;&#2352;&#2366;&#2314;&#2332;&#2352;
GenericName[ms]=Pelayar Web
GenericName[nb]=Nettleser
GenericName[nl]=Webbrowser
GenericName[or]=&#2835;&#2893;&#2860;&#2887;&#2860; &#2860;&#2893;&#2864;&#2878;&#2825;&#2844;&#2864;
GenericName[pl]=Przegl&#261;darka WWW
GenericName[pt]=Navegador Web
GenericName[pt_BR]=Navegador web
GenericName[ro]=Navigator de Internet
GenericName[ru]=&#1042;&#1077;&#1073;-&#1073;&#1088;&#1072;&#1091;&#1079;&#1077;&#1088;
GenericName[sk]=WWW prehliada&#269;
GenericName[sl]=Spletni brskalnik
GenericName[sr]=&#1048;&#1085;&#1090;&#1077;&#1088;&#1085;&#1077;&#1090; &#1087;&#1088;&#1077;&#1075;&#1083;&#1077;&#1076;&#1085;&#1080;&#1082;
GenericName[sv]=Webbläsare
GenericName[ta]=&#2951;&#2979;&#3016;&#2991; &#2953;&#2994;&#3006;&#2997;&#3007;
GenericName[te]=&#3118;&#3129;&#3134;&#3108;&#3122; &#3077;&#3112;&#3149;&#3125;&#3143;&#3127;&#3135;
GenericName[th]=&#3648;&#3623;&#3655;&#3610;&#3648;&#3610;&#3619;&#3634;&#3623;&#3660;&#3648;&#3595;&#3629;&#3619;&#3660;
GenericName[tr]=Web Taray&#305;c&#305;
GenericName[ug]=&#1578;&#1608;&#1585;&#1603;&#1734;&#1585;&#1711;&#1736;
GenericName[uk]=&#1053;&#1072;&#1074;&#1110;&#1075;&#1072;&#1090;&#1086;&#1088; &#1058;&#1077;&#1085;&#1077;&#1090;
GenericName[vi]=B&#7897; duy&#7879;t Web
GenericName[zh_CN]=&#32593;&#39029;&#27983;&#35272;&#22120;
GenericName[zh_HK]=&#32178;&#38913;&#28687;&#35261;&#22120;
GenericName[zh_TW]=&#32178;&#38913;&#28687;&#35261;&#22120;
Comment=Access the Internet
Comment[ar]=&#1575;&#1604;&#1583;&#1582;&#1608;&#1604; &#1573;&#1604;&#1609; &#1575;&#1604;&#1573;&#1606;&#1578;&#1585;&#1606;&#1578;
Comment[ast]=Accesu a Internet
Comment[bg]=&#1044;&#1086;&#1089;&#1090;&#1098;&#1087; &#1076;&#1086; &#1080;&#1085;&#1090;&#1077;&#1088;&#1085;&#1077;&#1090;
Comment[bn]=&#2439;&#2472;&#2509;&#2463;&#2494;&#2480;&#2472;&#2503;&#2463;&#2503; &#2474;&#2509;&#2480;&#2476;&#2503;&#2486; &#2453;&#2480;&#2497;&#2472;
Comment[bs]=Pristup internetu
Comment[ca]=Accediu a Internet
Comment[ca@valencia]=Accediu a Internet
Comment[cs]=P&#345;ístup k internetu
Comment[da]=Få adgang til internettet
Comment[de]=Internetzugriff
Comment[el]=&#928;&#961;&#972;&#963;&#946;&#945;&#963;&#951; &#963;&#964;&#959; &#916;&#953;&#945;&#948;&#943;&#954;&#964;&#965;&#959;
Comment[en_AU]=Access the Internet
Comment[en_GB]=Access the Internet
Comment[eo]=Akiri interreton
Comment[es]=Acceda a Internet
Comment[et]=Pääs Internetti
Comment[eu]=Sartu Internetera
Comment[fi]=Käytä internetiä
Comment[fil]=I-access ang Internet
Comment[fr]=Accéder à Internet
Comment[gl]=Acceda a Internet
Comment[gu]=&#2695;&#2690;&#2719;&#2736;&#2728;&#2759;&#2719; &#2701;&#2709;&#2765;&#2744;&#2759;&#2744; &#2709;&#2736;&#2763;
Comment[he]=&#1490;&#1497;&#1513;&#1492; &#1500;&#1488;&#1497;&#1504;&#1496;&#1512;&#1504;&#1496;
Comment[hi]=&#2311;&#2306;&#2335;&#2352;&#2344;&#2375;&#2335; &#2340;&#2325; &#2346;&#2361;&#2369;&#2306;&#2330; &#2360;&#2381;&#2341;&#2366;&#2346;&#2367;&#2340; &#2325;&#2352;&#2375;&#2306;
Comment[hr]=Pristupite Internetu
Comment[hu]=Az internet elérése
Comment[hy]=&#1348;&#1400;&#1410;&#1407;&#1412; &#1392;&#1377;&#1396;&#1377;&#1409;&#1377;&#1398;&#1409;
Comment[ia]=Accede a le Interrete
Comment[id]=Akses Internet
Comment[it]=Accesso a Internet
Comment[ja]=&#12452;&#12531;&#12479;&#12540;&#12493;&#12483;&#12488;&#12395;&#12450;&#12463;&#12475;&#12473;
Comment[ka]=&#4312;&#4316;&#4322;&#4308;&#4320;&#4316;&#4308;&#4322;&#4328;&#4312; &#4328;&#4308;&#4321;&#4309;&#4314;&#4304;
Comment[kn]=&#3207;&#3202;&#3231;&#3248;&#3277;&#3240;&#3270;&#3231;&#3277; &#3205;&#3240;&#3277;&#3240;&#3265; &#3242;&#3277;&#3248;&#3253;&#3271;&#3254;&#3263;&#3256;&#3263;
Comment[ko]=&#51064;&#53552;&#45367;&#50640; &#50672;&#44208;&#54633;&#45768;&#45796;
Comment[kw]=Hedhes an Kesrosweyth
Comment[lt]=Interneto prieiga
Comment[lv]=Piek&#316;&#363;t internetam
Comment[ml]=&#3335;&#3368;&#3405;&#3377;&#3376;&#3405;**&#3368;&#3398;&#3377;&#3405;&#3377;&#3405; &#3334;&#3349;&#3405;*&#3384;&#3384;&#3405; &#3354;&#3398;&#3375;&#3405;&#3375;&#3393;&#3349;
Comment[mr]=&#2311;&#2306;&#2335;&#2352;&#2344;&#2375;&#2335;&#2350;&#2343;&#2381;&#2351;&#2375; &#2346;&#2381;&#2352;&#2357;&#2375;&#2358; &#2325;&#2352;&#2366;
Comment[ms]=Mengakses Internet
Comment[nb]=Bruk internett
Comment[nl]=Verbinding maken met internet
Comment[or]=&#2823;&#2851;&#2893;&#2847;&#2864;&#2893;&#2856;&#2887;&#2847;&#2893; &#2858;&#2893;&#2864;&#2860;&#2887;&#2870; &#2837;&#2864;&#2856;&#2893;&#2852;&#2881;
Comment[pl]=Skorzystaj z internetu
Comment[pt]=Aceder à Internet
Comment[pt_BR]=Acessar a internet
Comment[ro]=Accesa&#539;i Internetul
Comment[ru]=&#1044;&#1086;&#1089;&#1090;&#1091;&#1087; &#1074; &#1048;&#1085;&#1090;&#1077;&#1088;&#1085;&#1077;&#1090;
Comment[sk]=Prístup do siete Internet
Comment[sl]=Dostop do interneta
Comment[sr]=&#1055;&#1088;&#1080;&#1089;&#1090;&#1091;&#1087;&#1080;&#1090;&#1077; &#1048;&#1085;&#1090;&#1077;&#1088;&#1085;&#1077;&#1090;&#1091;
Comment[sv]=Surfa på Internet
Comment[ta]=&#2951;&#2979;&#3016;&#2991;&#2980;&#3021;&#2980;&#3016; &#2949;&#2979;&#3009;&#2965;&#3009;&#2980;&#2994;&#3021;
Comment[te]=&#3079;&#3074;&#3103;&#3120;&#3149;&#3112;&#3142;&#3103;&#3149;*&#3112;&#3137; &#3078;&#3093;&#3149;&#3128;&#3142;&#3128;&#3149; &#3098;&#3142;&#3119;&#3149;&#3119;&#3074;&#3105;&#3135;
Comment[th]=&#3648;&#3586;&#3657;&#3634;&#3606;&#3638;&#3591;&#3629;&#3636;&#3609;&#3648;&#3607;&#3629;&#3619;&#3660;&#3648;&#3609;&#3655;&#3605;
Comment[tr]=&#304;nternet'e eri&#351;in
Comment[ug]=&#1574;&#1609;&#1606;&#1578;&#1744;&#1585;&#1606;&#1744;&#1578; &#1586;&#1609;&#1610;&#1575;&#1585;&#1609;&#1578;&#1609;
Comment[uk]=&#1044;&#1086;&#1089;&#1090;&#1091;&#1087; &#1076;&#1086; &#1030;&#1085;&#1090;&#1077;&#1088;&#1085;&#1077;&#1090;&#1091;
Comment[vi]=Truy c&#7853;p Internet
Comment[zh_CN]=&#35775;&#38382;&#20114;&#32852;&#32593;
Comment[zh_HK]=&#36899;&#32218;&#21040;&#32178;&#38555;&#32178;&#36335;
Comment[zh_TW]=&#36899;&#32218;&#21040;&#32178;&#38555;&#32178;&#36335;
Exec=/usr/bin/chromium-browser %U
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=chromium-browser
Categories=Network;WebBrowser;
MimeType=text/html;text/xml;application/xhtml_xml;x-scheme-handler/http;x-scheme-handler/https;
StartupWMClass=Chromium-browser
StartupNotify=true
X-Ayatana-Desktop-Shortcuts=NewWindow;Incognito;TempProfile

[NewWindow Shortcut Group]
Name=Open a New Window
Name[ast]=Abrir una Ventana Nueva
Name[bg]=&#1054;&#1090;&#1074;&#1072;&#1088;&#1103;&#1085;&#1077; &#1085;&#1072; &#1053;&#1086;&#1074; &#1087;&#1088;&#1086;&#1079;&#1086;&#1088;&#1077;&#1094;
Name[bn]=&#2447;&#2453;&#2463;&#2495; &#2472;&#2468;&#2497;&#2472; &#2441;&#2439;&#2472;&#2509;&#2465;&#2507; &#2454;&#2497;&#2482;&#2497;&#2472;
Name[bs]=Otvori novi prozor
Name[ca]=Obre una finestra nova
Name[ca@valencia]=Obri una finestra nova
Name[da]=Åbn et nyt vindue
Name[de]=Ein neues Fenster öffnen
Name[en_AU]=Open a New Window
Name[eo]=Malfermi novan fenestron
Name[es]=Abrir una ventana nueva
Name[et]=Ava uus aken
Name[eu]=Ireki leiho berria
Name[fi]=Avaa uusi ikkuna
Name[fr]=Ouvrir une nouvelle fenêtre
Name[gl]=Abrir unha nova xanela
Name[he]=&#1508;&#1514;&#1497;&#1495;&#1514; &#1495;&#1500;&#1493;&#1503; &#1495;&#1491;&#1513;
Name[hy]=&#1330;&#1377;&#1409;&#1381;&#1388; &#1398;&#1400;&#1408; &#1402;&#1377;&#1407;&#1400;&#1410;&#1392;&#1377;&#1398;
Name[ia]=Aperi un nove fenestra
Name[it]=Apri una nuova finestra
Name[ja]=&#26032;&#12375;&#12356;&#12454;&#12451;&#12531;&#12489;&#12454;&#12434;&#38283;&#12367;
Name[ka]=&#4304;&#4334;&#4304;&#4314;&#4312; &#4324;&#4304;&#4316;&#4335;&#4320;&#4312;&#4321; &#4306;&#4304;&#4334;&#4321;&#4316;&#4304;
Name[kw]=Egery fenester noweth
Name[ms]=Buka Tetingkap Baru
Name[nb]=Åpne et nytt vindu
Name[nl]=Nieuw venster openen
Name[pt_BR]=Abre uma nova janela
Name[ro]=Deschide o fereastr&#259; nou&#259;
Name[ru]=&#1054;&#1090;&#1082;&#1088;&#1099;&#1090;&#1100; &#1085;&#1086;&#1074;&#1086;&#1077; &#1086;&#1082;&#1085;&#1086;
Name[sl]=Odpri novo okno
Name[sv]=Öppna ett nytt fönster
Name[ug]=&#1610;&#1744;&#1709;&#1609; &#1603;&#1734;&#1586;&#1606;&#1749;&#1603; &#1574;&#1575;&#1670;
Name[uk]=&#1042;&#1110;&#1076;&#1082;&#1088;&#1080;&#1090;&#1080; &#1085;&#1086;&#1074;&#1077; &#1074;&#1110;&#1082;&#1085;&#1086;
Name[vi]=M&#7903; c&#7917;a s&#7893; m&#7899;i
Name[zh_CN]=&#25171;&#24320;&#26032;&#31383;&#21475;
Name[zh_TW]=&#38283;&#21855;&#26032;&#35222;&#31383;
Exec=/usr/bin/chromium-browser
TargetEnvironment=Unity

[Incognito Shortcut Group]
Name=Open a New Window in incognito mode
Name[ast]=Abrir una ventana nueva en mou incógnitu
Name[bg]=&#1054;&#1090;&#1074;&#1072;&#1088;&#1103;&#1085;&#1077; &#1085;&#1072; &#1085;&#1086;&#1074; &#1087;&#1088;&#1086;&#1079;&#1086;&#1088;&#1077;&#1094; &#1074; &#1088;&#1077;&#1078;&#1080;&#1084; \"&#1080;&#1085;&#1082;&#1086;&#1075;&#1085;&#1080;&#1090;&#1086;\"
Name[bn]=&#2447;&#2453;&#2463;&#2495; &#2472;&#2468;&#2497;&#2472; &#2441;&#2439;&#2472;&#2509;&#2465;&#2507; &#2454;&#2497;&#2482;&#2497;&#2472; &#2439;&#2472;&#2453;&#2507;&#2455;&#2472;&#2495;&#2463;&#2507; &#2437;&#2476;&#2488;&#2509;&#2469;&#2494;&#2479;&#2492;
Name[bs]=Otvori novi prozor u privatnom modu
Name[ca]=Obre una finestra nova en mode d'incògnit
Name[ca@valencia]=Obri una finestra nova en mode d'incògnit
Name[de]=Ein neues Fenster im Inkognito-Modus öffnen
Name[en_AU]=Open a New Window in incognito mode
Name[eo]=Malfermi novan fenestron nekoni&#285;eble
Name[es]=Abrir una ventana nueva en modo incógnito
Name[et]=Ava uus aken tundmatus olekus
Name[eu]=Ireki leiho berria isileko moduan
Name[fi]=Avaa uusi ikkuna incognito-tilassa
Name[fr]=Ouvrir une nouvelle fenêtre en mode navigation privée
Name[gl]=Abrir unha nova xanela en modo de incógnito
Name[he]=&#1508;&#1514;&#1497;&#1495;&#1514; &#1495;&#1500;&#1493;&#1503; &#1495;&#1491;&#1513; &#1489;&#1502;&#1510;&#1489; &#1490;&#1500;&#1497;&#1513;&#1492; &#1489;&#1505;&#1514;&#1512;
Name[hy]=&#1330;&#1377;&#1409;&#1381;&#1388; &#1398;&#1400;&#1408; &#1402;&#1377;&#1407;&#1400;&#1410;&#1392;&#1377;&#1398; &#1390;&#1402;&#1407;&#1397;&#1377;&#1388; &#1377;&#1399;&#1389;&#1377;&#1407;&#1377;&#1391;&#1381;&#1408;&#1402;&#1400;&#1410;&#1396;
Name[ia]=Aperi un nove fenestra in modo incognite
Name[it]=Apri una nuova finestra in modalità incognito
Name[ja]=&#26032;&#12375;&#12356;&#12471;&#12540;&#12463;&#12524;&#12483;&#12488; &#12454;&#12451;&#12531;&#12489;&#12454;&#12434;&#38283;&#12367;
Name[ka]=&#4304;&#4334;&#4304;&#4314;&#4312; &#4324;&#4304;&#4316;&#4335;&#4320;&#4312;&#4321; &#4312;&#4316;&#4313;&#4317;&#4306;&#4316;&#4312;&#4322;&#4317;&#4307; &#4306;&#4304;&#4334;&#4321;&#4316;&#4304;
Name[kw]=Egry fenester noweth en modh privedh
Name[ms]=Buka Tetingkap Baru dalam mod menyamar
Name[nl]=Nieuw venster openen in incognito-modus
Name[pt_BR]=Abrir uma nova janela em modo anônimo
Name[ro]=Deschide o fereastr&#259; nou&#259; în mod incognito
Name[ru]=&#1054;&#1090;&#1082;&#1088;&#1099;&#1090;&#1100; &#1085;&#1086;&#1074;&#1086;&#1077; &#1086;&#1082;&#1085;&#1086; &#1074; &#1088;&#1077;&#1078;&#1080;&#1084;&#1077; &#1080;&#1085;&#1082;&#1086;&#1075;&#1085;&#1080;&#1090;&#1086;
Name[sl]=Odpri novo okno v na&#269;inu brez beleženja
Name[sv]=Öppna ett nytt inkognitofönster
Name[ug]=&#1610;&#1608;&#1588;&#1735;&#1585;&#1735;&#1606; &#1726;&#1575;&#1604;&#1749;&#1578;&#1578;&#1749; &#1610;&#1744;&#1709;&#1609; &#1603;&#1734;&#1586;&#1606;&#1749;&#1603; &#1574;&#1575;&#1670;
Name[uk]=&#1042;&#1110;&#1076;&#1082;&#1088;&#1080;&#1090;&#1080; &#1085;&#1086;&#1074;&#1077; &#1074;&#1110;&#1082;&#1085;&#1086; &#1091; &#1087;&#1088;&#1080;&#1074;&#1072;&#1090;&#1085;&#1086;&#1084;&#1091; &#1088;&#1077;&#1078;&#1080;&#1084;&#1110;
Name[vi]=M&#7903; c&#7917;a s&#7893; m&#7899;i trong ch&#7871; &#273;&#7897; &#7849;n danh
Name[zh_CN]=&#20197;&#38544;&#36523;&#27169;&#24335;&#25171;&#24320;&#26032;&#31383;&#21475;
Name[zh_TW]=&#20197;&#21311;&#21517;&#27169;&#24335;&#38283;&#21855;&#26032;&#35222;&#31383;
Exec=/usr/bin/chromium-browser --incognito
TargetEnvironment=Unity

[TempProfile Shortcut Group]
Name=Open a New Window with a temporary profile
Name[ast]=Abrir una ventana nueva con perfil temporal
Name[bg]=&#1054;&#1090;&#1074;&#1072;&#1088;&#1103;&#1085;&#1077; &#1085;&#1072; &#1053;&#1086;&#1074; &#1087;&#1088;&#1086;&#1079;&#1086;&#1088;&#1077;&#1094; &#1089; &#1074;&#1088;&#1077;&#1084;&#1077;&#1085;&#1077;&#1085; &#1087;&#1088;&#1086;&#1092;&#1080;&#1083;
Name[bn]=&#2488;&#2494;&#2478;&#2479;&#2492;&#2495;&#2453; &#2474;&#2509;&#2480;&#2507;&#2475;&#2494;&#2439;&#2482; &#2488;&#2489; &#2447;&#2453;&#2463;&#2495; &#2472;&#2468;&#2497;&#2472; &#2441;&#2439;&#2472;&#2509;&#2465;&#2507; &#2454;&#2497;&#2482;&#2497;&#2472;
Name[bs]=Otvori novi prozor pomo&#263;u privremenog profila
Name[ca]=Obre una finestra nova amb un perfil temporal
Name[ca@valencia]=Obri una finestra nova amb un perfil temporal
Name[de]=Ein neues Fenster mit einem temporären Profil öffnen
Name[en_AU]=Open a New Window with a temporary profile
Name[eo]=Malfermi novan fenestron portempe
Name[es]=Abrir una ventana nueva con perfil temporal
Name[et]=Ava uus aken ajutise profiiliga
Name[eu]=Ireki leiho berria behin-behineko profil batekin
Name[fi]=Avaa uusi ikkuna käyttäen väliaikaista profiilia
Name[fr]=Ouvrir une nouvelle fenêtre avec un profil temporaire
Name[gl]=Abrir unha nova xanela con perfil temporal
Name[he]=&#1508;&#1514;&#1497;&#1495;&#1514; &#1495;&#1500;&#1493;&#1503; &#1495;&#1491;&#1513; &#1506;&#1501; &#1508;&#1512;&#1493;&#1508;&#1497;&#1500; &#1494;&#1502;&#1504;&#1497;
Name[hy]=&#1330;&#1377;&#1409;&#1381;&#1388; &#1398;&#1400;&#1408; &#1402;&#1377;&#1407;&#1400;&#1410;&#1392;&#1377;&#1398; &#1386;&#1377;&#1396;&#1377;&#1398;&#1377;&#1391;&#1377;&#1406;&#1400;&#1408; &#1392;&#1377;&#1407;&#1391;&#1377;&#1379;&#1408;&#1400;&#1406;
Name[ia]=Aperi un nove fenestra con un profilo provisori
Name[it]=Apri una nuova finestra con un profilo temporaneo
Name[ja]=&#19968;&#26178;&#12503;&#12525;&#12501;&#12449;&#12452;&#12523;&#12391;&#26032;&#12375;&#12356;&#12454;&#12451;&#12531;&#12489;&#12454;&#12434;&#38283;&#12367;
Name[ka]=&#4304;&#4334;&#4304;&#4314;&#4312; &#4324;&#4304;&#4316;&#4335;&#4320;&#4312;&#4321; &#4306;&#4304;&#4334;&#4321;&#4316;&#4304; &#4307;&#4320;&#4317;&#4308;&#4305;&#4312;&#4311; &#4318;&#4320;&#4317;&#4324;&#4312;&#4314;&#4328;&#4312;
Name[kw]=Egery fenester noweth gen profil dres prys
Name[ms]=Buka Tetingkap Baru dengan profil sementara
Name[nb]=Åpne et nytt vindu med en midlertidig profil
Name[nl]=Nieuw venster openen met een tijdelijk profiel
Name[pt_BR]=Abrir uma nova janela com um perfil temporário
Name[ro]=Deschide o fereastr&#259; nou&#259; cu un profil temporar
Name[ru]=&#1054;&#1090;&#1082;&#1088;&#1099;&#1090;&#1100; &#1085;&#1086;&#1074;&#1086;&#1077; &#1086;&#1082;&#1085;&#1086; &#1089; &#1074;&#1088;&#1077;&#1084;&#1077;&#1085;&#1085;&#1099;&#1084; &#1087;&#1088;&#1086;&#1092;&#1080;&#1083;&#1077;&#1084;
Name[sl]=Odpri novo okno z za&#269;asnim profilom
Name[sv]=Öppna ett nytt fönster med temporär profil
Name[ug]=&#1739;&#1575;&#1602;&#1609;&#1578;&#1604;&#1609;&#1602; &#1587;&#1749;&#1662;&#1604;&#1609;&#1605;&#1749; &#1726;&#1734;&#1580;&#1580;&#1749;&#1578; &#1576;&#1609;&#1604;&#1749;&#1606; &#1610;&#1744;&#1709;&#1609; &#1603;&#1734;&#1586;&#1606;&#1749;&#1603; &#1574;&#1575;&#1670;
Name[vi]=M&#7903; c&#7917;a s&#7893; m&#7899;i v&#7899;i h&#7891; s&#417; t&#7841;m
Name[zh_CN]=&#20197;&#20020;&#26102;&#37197;&#32622;&#25991;&#20214;&#25171;&#24320;&#26032;&#31383;&#21475;
Name[zh_TW]=&#20197;&#26283;&#26178;&#24615;&#20491;&#20154;&#36523;&#20998;&#38283;&#21855;&#26032;&#35222;&#31383;
Exec=/usr/bin/chromium-browser --temp-profile
TargetEnvironment=Unity

```

It's aparently showing a different name in every language.

---

### Post by mc4man on 2012-03-17
Yeah - try changing the Dutch one to what you want. (it doesn't hurt anything so keep at till it gives you what you want

---

### Post by JKyleOKC on 2012-03-17
In my Xubuntu 10.04 desktop, when I right-click on the icon I get a pop-up menu that includes options to "edit launcher" and if I select that, I can directly modify the display name and the comment without having to locate and edit the file directly. I don't know if this is still available in the newer versions, though...

---

### Post by markvond on 2012-03-17
Well it worked, thanks for the help.

---

