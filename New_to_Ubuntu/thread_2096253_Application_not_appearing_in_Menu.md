---
title: "Application not appearing in Menu"
date: 2012-12-19
forum: New to Ubuntu
---

### Post by hans12345 on 2012-12-19
In 12.04, I have a problem with applications not showing up in the application menu (the button on the left of the bottom panel).

I installed fslint and Kfind (the 'find files/folders' app) from the Ubuntu Software Center. fslint showed up in the application menu, but Kfind did not. When I check, both of them show up as installed (with the little green tick). So I assumed something was wrong with the installation, so I removed and re-installed Kfind. No change.

Before anyone suggests that Kfind does not work with Lubuntu, I should mention that it all works fine on my other Lubuntu PC.

2 questions:
- any idea why it does not show up in the application menu?
- how do I edit the application menu?

Thanks

---

### Post by pierceTN on 2012-12-19
> **hans12345 said:**
> In 12.04, I have a problem with applications not showing up in the application menu (the button on the left of the bottom panel).

I installed fslint and Kfind (the 'find files/folders' app) from the Ubuntu Software Center. fslint showed up in the application menu, but Kfind did not. When I check, both of them show up as installed (with the little green tick). So I assumed something was wrong with the installation, so I removed and re-installed Kfind. No change.

Before anyone suggests that Kfind does not work with Lubuntu, I should mention that it all works fine on my other Lubuntu PC.

2 questions:
- any idea why it does not show up in the application menu?
- how do I edit the application menu?

Thanks




Go to "Main Menu" editor (that is how you edit your menu) and add a new item. then name it and add the command (in you case "Kfind")


I have had programs do that before.

hope that helps

-Pierce

---

### Post by hans12345 on 2012-12-19
Thanks. That was fast! I'll try your idea now

---

### Post by hans12345 on 2012-12-19
Problem!

This is Lubuntu. How do I edit the Main Menu?

---

### Post by oldos2er on 2012-12-19
See [http://wiki.lxde.org/en/Main_Menu](http://wiki.lxde.org/en/Main_Menu)

---

### Post by pierceTN on 2012-12-19
> **oldos2er said:**
> See [http://wiki.lxde.org/en/Main_Menu](http://wiki.lxde.org/en/Main_Menu)


try this in terminal:


edit:

try this one: sudo apt-get install alacarte

---

### Post by hans12345 on 2012-12-19
I have been looking at this idea:

> **oldos2er said:**
> See [http://wiki.lxde.org/en/Main_Menu](http://wiki.lxde.org/en/Main_Menu)

I have cross checked with my Lubuntu PC that has Kfind visible on the desktop and in the applications menu.

BOTH have the same entry for kfind.desktop:

```

[Desktop Entry]
Exec=kfind %u
Icon=kfind
X-DocPath=kfind/index.html
Type=Application
Terminal=false
Name=Find Files/Folders
Name[af]=Soek Lêers/Gidse
Name[ar]=&#1573;&#1576;&#1581;&#1579; &#1593;&#1606; &#1605;&#1604;&#1601;&#1575;&#1578;/&#1605;&#1580;&#1604;&#1617;&#1583;&#1575;&#1578;
Name[as]=&#2472;&#2469;&#2495;&#2474;&#2468;&#2509;&#2544;/&#2474;&#2462;&#2509;&#2460;&#2495;&#2453;&#2494; &#2476;&#2495;&#2458;&#2494;&#2544;&#2453;
Name[ast]=Guetar ficheros/carpetes
Name[be]=&#1055;&#1086;&#1096;&#1091;&#1082; &#1092;&#1072;&#1081;&#1083;&#1072;&#1118; &#1110; &#1090;&#1101;&#1095;&#1072;&#1082;
Name[be@latin]=Pošuk faj&#322;a&#365; i kataloha&#365;
Name[bg]=&#1058;&#1098;&#1088;&#1089;&#1077;&#1085;&#1077; &#1085;&#1072; &#1092;&#1072;&#1081;&#1083;&#1086;&#1074;&#1077;
Name[bn]=&#2475;&#2494;&#2439;&#2482;/&#2475;&#2507;&#2482;&#2509;&#2465;&#2494;&#2480; &#2437;&#2472;&#2497;&#2488;&#2472;&#2509;&#2471;&#2494;&#2472;
Name[bn_IN]=&#2475;&#2494;&#2439;&#2482;/&#2475;&#2507;&#2482;&#2509;&#2465;&#2494;&#2480; &#2437;&#2472;&#2497;&#2488;&#2472;&#2509;&#2471;&#2494;&#2472;
Name[br]=Klask restroù/renkelloù
Name[bs]=Traženje datoteka i fascikli
Name[ca]=Cerca fitxers i carpetes
Name[ca@valencia]=Cerca fitxers i carpetes
Name[cs]=Najít soubory/složky
Name[csb]=Szëkba lopków/katalogów
Name[da]=Find filer/mapper
Name[de]=Dateien/Ordner suchen
Name[el]=&#913;&#957;&#945;&#950;&#942;&#964;&#951;&#963;&#951; &#945;&#961;&#967;&#949;&#943;&#969;&#957;/&#966;&#945;&#954;&#941;&#955;&#969;&#957;
Name[en_GB]=Find Files/Folders
Name[eo]=Trovi dosierojn/dosierujojn
Name[es]=Buscar archivos/carpetas
Name[et]=Failide/kataloogide otsimine
Name[eu]=Bilatu fitxategiak/karpetak
Name[fa]=&#1740;&#1575;&#1601;&#1578;&#1606; &#1662;&#1585;&#1608;&#1606;&#1583;&#1607;*&#1607;&#1575;/&#1662;&#1608;&#1588;&#1607;*&#1607;&#1575;
Name[fi]=Etsi tiedostoja ja kansioita
Name[fr]=Recherche de fichiers*/ dossiers
Name[fy]=Triemmen/mappen sykje
Name[ga]=Aimsigh Comhaid/Comhadlanna
Name[gl]=Buscar ficheiros/cartafoles
Name[gu]=&#2731;&#2750;&#2695;&#2738;&#2763;/&#2731;&#2763;&#2738;&#2765;&#2721;&#2736;&#2763; &#2742;&#2763;&#2727;&#2763;
Name[he]=&#1495;&#1497;&#1508;&#1493;&#1513; &#1511;&#1489;&#1510;&#1497;&#1501; &#1493;&#1514;&#1497;&#1511;&#1497;&#1493;&#1514;
Name[hi]=&#2347;&#2364;&#2366;&#2311;&#2354;&#2375;&#2306;/&#2347;&#2379;&#2354;&#2381;&#2337;&#2352; &#2338;&#2370;&#2306;&#2338;&#2375;&#2306;
Name[hne]=&#2347;&#2366;&#2311;&#2354; &#2350;&#2344; &#2354;/&#2347;&#2379;&#2354;&#2381;&#2337;&#2352; &#2350;&#2344; &#2354; &#2326;&#2379;&#2332;&#2357;
Name[hr]=Traži datoteke/mape
Name[hsb]=Dataje/zapiski namaka&#263;
Name[hu]=Fájlkeres&#337;
Name[ia]=Trova files/dossieres
Name[id]=Cari Berkas/Folder
Name[is]=Finna skrár/möppur
Name[it]=Trova file e cartelle
Name[ja]=&#12501;&#12449;&#12452;&#12523;/&#12501;&#12457;&#12523;&#12480;&#12434;&#26908;&#32034;
Name[ka]=&#4324;&#4304;&#4312;&#4314;&#4311;&#4304; &#4307;&#4304; &#4321;&#4304;&#4325;&#4304;&#4326;&#4304;&#4314;&#4307;&#4308;&#4311;&#4304; &#4331;&#4312;&#4308;&#4305;&#4304;
Name[kk]=&#1060;&#1072;&#1081;&#1083;&#1076;&#1099; &#1085;&#1077; &#1179;&#1072;&#1087;&#1096;&#1099;&#1179;&#1090;&#1099; &#1090;&#1072;&#1073;&#1091;
Name[km]=&#6042;&#6016;&#8203;&#6063;&#6016;&#6047;&#6070;&#6042;/&#6032;&#6031;
Name[kn]=&#3221;&#3233;&#3236;&#3223;&#3251;&#3240;&#3277;&#3240;&#3265;/&#3221;&#3233;&#3236;&#3221;&#3275;&#3254;&#3223;&#3251;&#3240;&#3277;&#3240;&#3265; &#3257;&#3265;&#3233;&#3265;&#3221;&#3265;
Name[ko]=&#54028;&#51068;/&#54260;&#45908; &#52286;&#44592;
Name[ku]=Pelan/peldankan Bibîne
Name[lt]=Rasti failus/aplankus
Name[lv]=Mekl&#275;t failus/mapes
Name[mai]=&#2347;&#2366;&#2311;&#2354;&#2360;&#2349;/&#2347;&#2379;&#2354;&#2381;&#2337;&#2352;&#2360;&#2349; &#2338;&#2370;&#2305;&#2338;&#2370;
Name[mk]=&#1055;&#1088;&#1086;&#1085;&#1072;&#1112;&#1076;&#1080; &#1076;&#1072;&#1090;&#1086;&#1090;&#1077;&#1082;&#1080;/&#1087;&#1072;&#1087;&#1082;&#1080;
Name[ml]=&#3376;&#3399;&#3350;&#3349;&#3379;&#3393;&#3330; &#3349;&#3394;&#3359;&#3349;&#3379;&#3393;&#3330; &#3364;&#3391;&#3376;&#3375;&#3393;&#3349;
Name[mr]=&#2347;&#2366;&#2311;&#2354;/&#2347;&#2379;&#2354;&#2381;&#2337;&#2352; &#2346;&#2361;&#2366;
Name[ms]=Cari Fail/Folder
Name[nb]=Finn filer/mapper
Name[nds]=Dateien un Ornern söken
Name[ne]=&#2347;&#2366;&#2311;&#2354;/&#2347;&#2379;&#2354;&#2381;&#2337;&#2352; &#2347;&#2375;&#2354;&#2366; &#2346;&#2366;&#2352;&#2381;&#2344;&#2369;&#2361;&#2379;&#2360;&#2381;
Name[nl]=Bestanden/mappen zoeken
Name[nn]=Finn filer/mapper
Name[or]=&#2859;&#2878;&#2823;&#2866;/&#2859;&#2891;&#2866;&#2849;&#2864; &#2838;&#2891;&#2844;&#2856;&#2893;&#2852;&#2881;
Name[pa]=&#2603;&#2622;&#2567;&#2610;/&#2603;&#2635;&#2610;&#2593;&#2608; &#2582;&#2635;&#2588;
Name[pl]=Wyszukiwanie plików/katalogów
Name[pt]=Procurar Ficheiros/Pastas
Name[pt_BR]=Procurar arquivos/pastas
Name[ro]=Caut&#259; fi&#537;iere/dosare
Name[ru]=&#1055;&#1086;&#1080;&#1089;&#1082; &#1092;&#1072;&#1081;&#1083;&#1086;&#1074; &#1080; &#1087;&#1072;&#1087;&#1086;&#1082;
Name[se]=Oza fiillaid dahje máhpaid
Name[si]=&#3484;&#3548;&#3505;&#3540;/&#3510;&#3524;&#3517;&#3540;&#3512;&#3530; &#3523;&#3548;&#3514;&#3505;&#3530;&#3505;
Name[sk]=Nájs&#357; súbory/prie&#269;inky
Name[sl]=Najdi datoteke in mape
Name[sr]=&#1058;&#1088;&#1072;&#1078;&#1077;&#1114;&#1077; &#1092;&#1072;&#1112;&#1083;&#1086;&#1074;&#1072; &#1080; &#1092;&#1072;&#1089;&#1094;&#1080;&#1082;&#1083;&#1080;
Name[sr@ijekavian]=&#1058;&#1088;&#1072;&#1078;&#1077;&#1114;&#1077; &#1092;&#1072;&#1112;&#1083;&#1086;&#1074;&#1072; &#1080; &#1092;&#1072;&#1089;&#1094;&#1080;&#1082;&#1083;&#1080;
Name[sr@ijekavianlatin]=Traženje fajlova i fascikli
Name[sr@latin]=Traženje fajlova i fascikli
Name[sv]=Hitta filer eller kataloger
Name[ta]=&#2965;&#3019;&#2986;&#3021;&#2986;&#3009;&#2965;&#2995;&#3021;/&#2949;&#2975;&#3016;&#2997;&#3009;&#2965;&#2995;&#3016;&#2965;&#3021; &#2965;&#2979;&#3021;&#2975;&#3009;&#2986;&#3007;&#2975;&#3007;
Name[te]=&#3110;&#3128;&#3149;&#3108;&#3149;&#3120;&#3134;&#3122;&#3137;/&#3115;&#3146;&#3122;&#3149;&#3105;&#3120;&#3149;&#3122;&#3112;&#3137; &#3125;&#3142;&#3108;&#3137;&#3093;&#3137;
Name[tg]=&#1206;&#1091;&#1089;&#1090;&#1091;&#1207;&#1263;&#1080; &#1092;&#1072;&#1081;&#1083;&#1203;&#1086;/&#1092;&#1077;&#1203;&#1088;&#1080;&#1089;&#1090;&#1203;&#1086;
Name[th]=&#3588;&#3657;&#3609;&#3627;&#3634;&#3649;&#3615;&#3657;&#3617;/&#3650;&#3615;&#3621;&#3648;&#3604;&#3629;&#3619;&#3660;
Name[tr]=Dosya / Dizin Bul
Name[ug]=&#1726;&#1734;&#1580;&#1580;&#1749;&#1578;/&#1602;&#1609;&#1587;&#1602;&#1735;&#1670; &#1574;&#1609;&#1586;&#1583;&#1749;
Name[uk]=&#1055;&#1086;&#1096;&#1091;&#1082; &#1092;&#1072;&#1081;&#1083;&#1110;&#1074; &#1090;&#1072; &#1090;&#1077;&#1082;
Name[uz]=Fayl/jildlarni qidirish
Name[uz@cyrillic]=&#1060;&#1072;&#1081;&#1083;/&#1078;&#1080;&#1083;&#1076;&#1083;&#1072;&#1088;&#1085;&#1080; &#1179;&#1080;&#1076;&#1080;&#1088;&#1080;&#1096;
Name[vi]=Tìm T&#7853;p tin/Th&#432; m&#7909;c
Name[wa]=Trover des fitchîs/ridants
Name[x-test]=xxFind Files/Foldersxx
Name[zh_CN]=&#26597;&#25214;&#25991;&#20214;/&#25991;&#20214;&#22841;
Name[zh_TW]=&#23563;&#25214;&#27284;&#26696;/&#36039;&#26009;&#22846;
X-KDE-StartupNotify=true
OnlyShowIn=KDE;
Categories=Qt;KDE;Core;

```

The problem must be elsewhere. 

Any ideas?

---

### Post by Dennis N on 2012-12-19
> **hans12345 said:**
> 

The problem must be elsewhere. 

Any ideas?

Comment out the line:

**OnlyShowIn=KDE;**

and resave the .desktop file(s).

Also change the categories: Maybe Use **Utility;** or **GTK;Utility;**

---

### Post by pierceTN on 2012-12-19
> **hans12345 said:**
> I have been looking at this idea:



I have cross checked with my Lubuntu PC that has Kfind visible on the desktop and in the applications menu.

BOTH have the same entry for kfind.desktop:

```

[Desktop Entry]
Exec=kfind %u
Icon=kfind
X-DocPath=kfind/index.html
Type=Application
Terminal=false
Name=Find Files/Folders
Name[af]=Soek Lêers/Gidse
Name[ar]=&#1573;&#1576;&#1581;&#1579; &#1593;&#1606; &#1605;&#1604;&#1601;&#1575;&#1578;/&#1605;&#1580;&#1604;&#1617;&#1583;&#1575;&#1578;
Name[as]=&#2472;&#2469;&#2495;&#2474;&#2468;&#2509;&#2544;/&#2474;&#2462;&#2509;&#2460;&#2495;&#2453;&#2494; &#2476;&#2495;&#2458;&#2494;&#2544;&#2453;
Name[ast]=Guetar ficheros/carpetes
Name[be]=&#1055;&#1086;&#1096;&#1091;&#1082; &#1092;&#1072;&#1081;&#1083;&#1072;&#1118; &#1110; &#1090;&#1101;&#1095;&#1072;&#1082;
Name[be@latin]=Pošuk faj&#322;a&#365; i kataloha&#365;
Name[bg]=&#1058;&#1098;&#1088;&#1089;&#1077;&#1085;&#1077; &#1085;&#1072; &#1092;&#1072;&#1081;&#1083;&#1086;&#1074;&#1077;
Name[bn]=&#2475;&#2494;&#2439;&#2482;/&#2475;&#2507;&#2482;&#2509;&#2465;&#2494;&#2480; &#2437;&#2472;&#2497;&#2488;&#2472;&#2509;&#2471;&#2494;&#2472;
Name[bn_IN]=&#2475;&#2494;&#2439;&#2482;/&#2475;&#2507;&#2482;&#2509;&#2465;&#2494;&#2480; &#2437;&#2472;&#2497;&#2488;&#2472;&#2509;&#2471;&#2494;&#2472;
Name[br]=Klask restroù/renkelloù
Name[bs]=Traženje datoteka i fascikli
Name[ca]=Cerca fitxers i carpetes
Name[ca@valencia]=Cerca fitxers i carpetes
Name[cs]=Najít soubory/složky
Name[csb]=Szëkba lopków/katalogów
Name[da]=Find filer/mapper
Name[de]=Dateien/Ordner suchen
Name[el]=&#913;&#957;&#945;&#950;&#942;&#964;&#951;&#963;&#951; &#945;&#961;&#967;&#949;&#943;&#969;&#957;/&#966;&#945;&#954;&#941;&#955;&#969;&#957;
Name[en_GB]=Find Files/Folders
Name[eo]=Trovi dosierojn/dosierujojn
Name[es]=Buscar archivos/carpetas
Name[et]=Failide/kataloogide otsimine
Name[eu]=Bilatu fitxategiak/karpetak
Name[fa]=&#1740;&#1575;&#1601;&#1578;&#1606; &#1662;&#1585;&#1608;&#1606;&#1583;&#1607;*&#1607;&#1575;/&#1662;&#1608;&#1588;&#1607;*&#1607;&#1575;
Name[fi]=Etsi tiedostoja ja kansioita
Name[fr]=Recherche de fichiers*/ dossiers
Name[fy]=Triemmen/mappen sykje
Name[ga]=Aimsigh Comhaid/Comhadlanna
Name[gl]=Buscar ficheiros/cartafoles
Name[gu]=&#2731;&#2750;&#2695;&#2738;&#2763;/&#2731;&#2763;&#2738;&#2765;&#2721;&#2736;&#2763; &#2742;&#2763;&#2727;&#2763;
Name[he]=&#1495;&#1497;&#1508;&#1493;&#1513; &#1511;&#1489;&#1510;&#1497;&#1501; &#1493;&#1514;&#1497;&#1511;&#1497;&#1493;&#1514;
Name[hi]=&#2347;&#2364;&#2366;&#2311;&#2354;&#2375;&#2306;/&#2347;&#2379;&#2354;&#2381;&#2337;&#2352; &#2338;&#2370;&#2306;&#2338;&#2375;&#2306;
Name[hne]=&#2347;&#2366;&#2311;&#2354; &#2350;&#2344; &#2354;/&#2347;&#2379;&#2354;&#2381;&#2337;&#2352; &#2350;&#2344; &#2354; &#2326;&#2379;&#2332;&#2357;
Name[hr]=Traži datoteke/mape
Name[hsb]=Dataje/zapiski namaka&#263;
Name[hu]=Fájlkeres&#337;
Name[ia]=Trova files/dossieres
Name[id]=Cari Berkas/Folder
Name[is]=Finna skrár/möppur
Name[it]=Trova file e cartelle
Name[ja]=&#12501;&#12449;&#12452;&#12523;/&#12501;&#12457;&#12523;&#12480;&#12434;&#26908;&#32034;
Name[ka]=&#4324;&#4304;&#4312;&#4314;&#4311;&#4304; &#4307;&#4304; &#4321;&#4304;&#4325;&#4304;&#4326;&#4304;&#4314;&#4307;&#4308;&#4311;&#4304; &#4331;&#4312;&#4308;&#4305;&#4304;
Name[kk]=&#1060;&#1072;&#1081;&#1083;&#1076;&#1099; &#1085;&#1077; &#1179;&#1072;&#1087;&#1096;&#1099;&#1179;&#1090;&#1099; &#1090;&#1072;&#1073;&#1091;
Name[km]=&#6042;&#6016;&#8203;&#6063;&#6016;&#6047;&#6070;&#6042;/&#6032;&#6031;
Name[kn]=&#3221;&#3233;&#3236;&#3223;&#3251;&#3240;&#3277;&#3240;&#3265;/&#3221;&#3233;&#3236;&#3221;&#3275;&#3254;&#3223;&#3251;&#3240;&#3277;&#3240;&#3265; &#3257;&#3265;&#3233;&#3265;&#3221;&#3265;
Name[ko]=&#54028;&#51068;/&#54260;&#45908; &#52286;&#44592;
Name[ku]=Pelan/peldankan Bibîne
Name[lt]=Rasti failus/aplankus
Name[lv]=Mekl&#275;t failus/mapes
Name[mai]=&#2347;&#2366;&#2311;&#2354;&#2360;&#2349;/&#2347;&#2379;&#2354;&#2381;&#2337;&#2352;&#2360;&#2349; &#2338;&#2370;&#2305;&#2338;&#2370;
Name[mk]=&#1055;&#1088;&#1086;&#1085;&#1072;&#1112;&#1076;&#1080; &#1076;&#1072;&#1090;&#1086;&#1090;&#1077;&#1082;&#1080;/&#1087;&#1072;&#1087;&#1082;&#1080;
Name[ml]=&#3376;&#3399;&#3350;&#3349;&#3379;&#3393;&#3330; &#3349;&#3394;&#3359;&#3349;&#3379;&#3393;&#3330; &#3364;&#3391;&#3376;&#3375;&#3393;&#3349;
Name[mr]=&#2347;&#2366;&#2311;&#2354;/&#2347;&#2379;&#2354;&#2381;&#2337;&#2352; &#2346;&#2361;&#2366;
Name[ms]=Cari Fail/Folder
Name[nb]=Finn filer/mapper
Name[nds]=Dateien un Ornern söken
Name[ne]=&#2347;&#2366;&#2311;&#2354;/&#2347;&#2379;&#2354;&#2381;&#2337;&#2352; &#2347;&#2375;&#2354;&#2366; &#2346;&#2366;&#2352;&#2381;&#2344;&#2369;&#2361;&#2379;&#2360;&#2381;
Name[nl]=Bestanden/mappen zoeken
Name[nn]=Finn filer/mapper
Name[or]=&#2859;&#2878;&#2823;&#2866;/&#2859;&#2891;&#2866;&#2849;&#2864; &#2838;&#2891;&#2844;&#2856;&#2893;&#2852;&#2881;
Name[pa]=&#2603;&#2622;&#2567;&#2610;/&#2603;&#2635;&#2610;&#2593;&#2608; &#2582;&#2635;&#2588;
Name[pl]=Wyszukiwanie plików/katalogów
Name[pt]=Procurar Ficheiros/Pastas
Name[pt_BR]=Procurar arquivos/pastas
Name[ro]=Caut&#259; fi&#537;iere/dosare
Name[ru]=&#1055;&#1086;&#1080;&#1089;&#1082; &#1092;&#1072;&#1081;&#1083;&#1086;&#1074; &#1080; &#1087;&#1072;&#1087;&#1086;&#1082;
Name[se]=Oza fiillaid dahje máhpaid
Name[si]=&#3484;&#3548;&#3505;&#3540;/&#3510;&#3524;&#3517;&#3540;&#3512;&#3530; &#3523;&#3548;&#3514;&#3505;&#3530;&#3505;
Name[sk]=Nájs&#357; súbory/prie&#269;inky
Name[sl]=Najdi datoteke in mape
Name[sr]=&#1058;&#1088;&#1072;&#1078;&#1077;&#1114;&#1077; &#1092;&#1072;&#1112;&#1083;&#1086;&#1074;&#1072; &#1080; &#1092;&#1072;&#1089;&#1094;&#1080;&#1082;&#1083;&#1080;
Name[sr@ijekavian]=&#1058;&#1088;&#1072;&#1078;&#1077;&#1114;&#1077; &#1092;&#1072;&#1112;&#1083;&#1086;&#1074;&#1072; &#1080; &#1092;&#1072;&#1089;&#1094;&#1080;&#1082;&#1083;&#1080;
Name[sr@ijekavianlatin]=Traženje fajlova i fascikli
Name[sr@latin]=Traženje fajlova i fascikli
Name[sv]=Hitta filer eller kataloger
Name[ta]=&#2965;&#3019;&#2986;&#3021;&#2986;&#3009;&#2965;&#2995;&#3021;/&#2949;&#2975;&#3016;&#2997;&#3009;&#2965;&#2995;&#3016;&#2965;&#3021; &#2965;&#2979;&#3021;&#2975;&#3009;&#2986;&#3007;&#2975;&#3007;
Name[te]=&#3110;&#3128;&#3149;&#3108;&#3149;&#3120;&#3134;&#3122;&#3137;/&#3115;&#3146;&#3122;&#3149;&#3105;&#3120;&#3149;&#3122;&#3112;&#3137; &#3125;&#3142;&#3108;&#3137;&#3093;&#3137;
Name[tg]=&#1206;&#1091;&#1089;&#1090;&#1091;&#1207;&#1263;&#1080; &#1092;&#1072;&#1081;&#1083;&#1203;&#1086;/&#1092;&#1077;&#1203;&#1088;&#1080;&#1089;&#1090;&#1203;&#1086;
Name[th]=&#3588;&#3657;&#3609;&#3627;&#3634;&#3649;&#3615;&#3657;&#3617;/&#3650;&#3615;&#3621;&#3648;&#3604;&#3629;&#3619;&#3660;
Name[tr]=Dosya / Dizin Bul
Name[ug]=&#1726;&#1734;&#1580;&#1580;&#1749;&#1578;/&#1602;&#1609;&#1587;&#1602;&#1735;&#1670; &#1574;&#1609;&#1586;&#1583;&#1749;
Name[uk]=&#1055;&#1086;&#1096;&#1091;&#1082; &#1092;&#1072;&#1081;&#1083;&#1110;&#1074; &#1090;&#1072; &#1090;&#1077;&#1082;
Name[uz]=Fayl/jildlarni qidirish
Name[uz@cyrillic]=&#1060;&#1072;&#1081;&#1083;/&#1078;&#1080;&#1083;&#1076;&#1083;&#1072;&#1088;&#1085;&#1080; &#1179;&#1080;&#1076;&#1080;&#1088;&#1080;&#1096;
Name[vi]=Tìm T&#7853;p tin/Th&#432; m&#7909;c
Name[wa]=Trover des fitchîs/ridants
Name[x-test]=xxFind Files/Foldersxx
Name[zh_CN]=&#26597;&#25214;&#25991;&#20214;/&#25991;&#20214;&#22841;
Name[zh_TW]=&#23563;&#25214;&#27284;&#26696;/&#36039;&#26009;&#22846;
X-KDE-StartupNotify=true
OnlyShowIn=KDE;
Categories=Qt;KDE;Core;

```

The problem must be elsewhere. 

Any ideas?

did you try installing alacarte (main menu)???

You could at least see if it will install: 
sudo apt-get install alacarte


-Pierce

---

### Post by hans12345 on 2012-12-24
> **pierceTN said:**
> did you try installing alacarte (main menu)???

You could at least see if it will install: 
sudo apt-get install alacarte


-Pierce

I did not install it yet. I use Lubuntu since I wanted a lightweight OS on this older PC, and Alacarte wanted to download 175 packages!

I was hoping someone could help me see the difference between my 2 Lubuntu PCs. On one PC, Kfind appears in both application menu and on the desktop (well, I probably added it later to the desktop), and on this PC, Kfind does not appear at all.

All very strange!

---

### Post by vasa1 on 2012-12-24
> **Dennis N said:**
> Comment out the line:

**OnlyShowIn=KDE;**

and resave the .desktop file(s).

Also change the categories: Maybe Use **Utility;** or **GTK;Utility;**

My money's on this ^^^. Except that I don't know how to comment out lines in a .desktop file. I usually back up the file and then delete lines I don't want. And, instead of changing categories, you could just add whatever you need.

---

