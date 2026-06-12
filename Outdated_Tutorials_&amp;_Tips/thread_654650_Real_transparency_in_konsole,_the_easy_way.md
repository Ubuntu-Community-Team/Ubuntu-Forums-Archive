---
title: "Real transparency in konsole, the easy way"
date: 2007-12-31
forum: Outdated Tutorials &amp; Tips
---

### Post by ffi on 2007-12-31
It is very simple to get real transparency in the konsole under Kubuntu:
1. make sure you have a compositing window manager running, like compiz or beryl. There are many excellent guides for setting them up already.
2. Use the  switch  --real-transparency to start konsole

save the following as /usr/share/applications/kde/konsole.desktop

```
[Desktop Entry]
Encoding=UTF-8
Type=Application
Exec=konsole --real-transparency
Icon=konsole
DocPath=konsole/index.html
Terminal=false
X-KDE-StartupNotify=true

Name=Konsole
Name[ar]=&#1591;&#1585;&#1601;&#1610;&#1577; &#1575;&#1604;&#1578;&#1581;&#1603;&#1605;
Name[az]=Konsol
Name[be]=&#1050;&#1072;&#1085;&#1089;&#1086;&#1083;&#1100;
Name[bg]=&#1050;&#1086;&#1085;&#1079;&#1086;&#1083;&#1072;
Name[bn]=&#2453;&#2472;&#2488;&#2507;&#2482;
Name[bs]=Konzola
Name[ca]=Consola
Name[csb]=Kònsola
Name[el]=&#922;&#959;&#957;&#963;&#972;&#955;&#945;
Name[eo]=Konzolo
Name[et]=Konsool
Name[eu]=Kontsola
Name[he]=&#1502;&#1505;&#1493;&#1507;
Name[hi]=&#2325;&#2306;&#2360;&#2379;&#2354;
Name[hr]=Konzola
Name[is]=Skjáhermir
Name[ko]=KDE&#50857; &#53080;&#49556;
Name[lo]=&#3716;&#3757;&#3737;&#3778;&#3722;&#3749; - K
Name[mk]=&#1050;&#1086;&#1085;&#1079;&#1086;&#1083;&#1072;
Name[mn]=&#1050;&#1086;&#1085;&#1089;&#1086;&#1083;
Name[nb]=Konsoll
Name[ne]=&#2325;&#2344;&#2381;&#2360;&#2379;&#2354;
Name[nn]=Konsoll
Name[pa]=&#2581;&#2672;&#2600;&#2616;&#2635;&#2610;
Name[pl]=Konsola
Name[ro]=Consol&#259;
Name[ru]=&#1050;&#1086;&#1085;&#1089;&#1086;&#1083;&#1100;
Name[se]=Konsolla
Name[sk]=Konzola
Name[sl]=Konzola
Name[ta]=&#2965;&#3006;&#2985;&#3021;&#2970;&#3019;&#2994;&#3021;
Name[te]=&#3093;&#3134;&#3112;&#3149;&#3128;&#3147;&#3122;&#3149;
Name[tg]=&#1050;&#1086;&#1085;&#1089;&#1086;&#1083;
Name[th]=&#3588;&#3629;&#3609;&#3650;&#3595;&#3621; K
Name[zu]=Ikhonsoli

GenericName=Terminal Program
GenericName[af]=Terminaal Program
GenericName[ar]=&#1576;&#1585;&#1606;&#1575;&#1605;&#1580; &#1605;&#1591;&#1585;&#1575;&#1601;
GenericName[az]=Terminal Proqram&#305;
GenericName[be]=&#1058;&#1101;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;
GenericName[bg]=&#1058;&#1077;&#1088;&#1084;&#1080;&#1085;&#1072;&#1083;&#1085;&#1072; &#1087;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;&#1072;
GenericName[bn]=&#2463;&#2494;&#2480;&#2509;&#2478;&#2495;&#2472;&#2494;&#2482; &#2474;&#2509;&#2480;&#2507;&#2455;&#2509;&#2480;&#2494;&#2478;
GenericName[br]=Goulev termenell
GenericName[bs]=Terminalni program
GenericName[ca]=Programa de terminal
GenericName[cs]=Terminálový program
GenericName[csb]=Programa terminala
GenericName[cy]=Rhaglen Terfynell
GenericName[da]=Terminalprogram
GenericName[de]=Terminalprogramm
GenericName[el]=&#928;&#961;&#972;&#947;&#961;&#945;&#956;&#956;&#945; &#964;&#949;&#961;&#956;&#945;&#964;&#953;&#954;&#959;&#973;
GenericName[eo]=Terminalimita&#309;o
GenericName[es]=Programa de terminal
GenericName[et]=Terminaliemulaator
GenericName[eu]=Terminal programa
GenericName[fa]=&#1576;&#1585;&#1606;&#1575;&#1605;&#1728; &#1662;&#1575;&#1740;&#1575;&#1606;&#1607;
GenericName[fi]=Komentoikkunaohjelma
GenericName[fr]=Terminal
GenericName[fy]=Terminalprogramma
GenericName[ga]=Clár Teirminéil
GenericName[gl]=Programa de Terminal
GenericName[he]=&#1514;&#1493;&#1499;&#1504;&#1497;&#1514; &#1502;&#1505;&#1493;&#1507;
GenericName[hi]=&#2335;&#2352;&#2381;&#2350;&#2367;&#2344;&#2354; &#2346;&#2381;&#2352;&#2379;&#2327;&#2381;&#2352;&#2366;&#2350;
GenericName[hr]=Terminalski program
GenericName[hu]=Parancsértelmez&#337;
GenericName[id]=Program Terminal
GenericName[is]=Skjáhermir
GenericName[it]=Programma terminale
GenericName[ja]=&#12479;&#12540;&#12511;&#12490;&#12523;&#12503;&#12525;&#12464;&#12521;&#12512;
GenericName[kk]=&#1058;&#1077;&#1088;&#1084;&#1080;&#1085;&#1072;&#1083; &#1073;&#1072;&#1171;&#1076;&#1072;&#1088;&#1083;&#1072;&#1084;&#1072;&#1089;&#1099;
GenericName[km]=&#6016;&#6040;&#6098;&#6040;&#6044;&#6071;&#6034;&#6072;&#8203;&#6047;&#6098;&#6032;&#6070;&#6035;&#6072;&#6041;
GenericName[lo]=&#3757;&#3761;&#3738;&#3742;&#3749;&#3764;&#3713;&#3776;&#3716;&#3776;&#3722;&#3764;&#3737; &#3776;&#3735;&#3765;&#3745;&#3765;&#3737;&#3757;&#3737;
GenericName[lt]=Terminalo programa
GenericName[lv]=Termin&#257;la Programma
GenericName[mk]=&#1058;&#1077;&#1088;&#1084;&#1080;&#1085;&#1072;&#1083;&#1089;&#1082;&#1072; &#1087;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;&#1072;
GenericName[mn]=&#1058;&#1077;&#1088;&#1084;&#1080;&#1085;&#1072;&#1083;-&#1055;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;
GenericName[ms]=Program Terminal
GenericName[mt]=Programm ta' terminal
GenericName[nb]=Terminalprogram
GenericName[nds]=Terminal-Programm
GenericName[ne]=&#2335;&#2352;&#2381;&#2350;&#2367;&#2344;&#2354; &#2325;&#2366;&#2352;&#2381;&#2351;&#2325;&#2381;&#2352;&#2350;
GenericName[nl]=Terminalprogramma
GenericName[nn]=Terminalprogram
GenericName[nso]=Lenaneo la Terminal
GenericName[pa]=&#2591;&#2608;&#2606;&#2624;&#2600;&#2610; &#2602;&#2608;&#2635;&#2583;&#2608;&#2622;&#2606;
GenericName[pl]=Program terminala
GenericName[pt]=Programa de Terminal
GenericName[pt_BR]=Terminal
GenericName[ro]=Program terminal
GenericName[ru]=&#1058;&#1077;&#1088;&#1084;&#1080;&#1085;&#1072;&#1083;
GenericName[rw]=Porogaramu Umukiriya
GenericName[se]=Terminálaprográmma
GenericName[sk]=Terminál
GenericName[sl]=Terminalski program
GenericName[sr]=&#1058;&#1077;&#1088;&#1084;&#1080;&#1085;&#1072;&#1083;&#1089;&#1082;&#1080; &#1087;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;
GenericName[sr@Latn]=Terminalski program
GenericName[ss]=Luhlelo lwesikhungo
GenericName[sv]=Terminalprogram
GenericName[ta]=&#2965;&#2975;&#3016;&#2970;&#3007; &#2984;&#3007;&#2992;&#2994;&#3007;
GenericName[te]=&#3103;&#3142;&#3120;&#3149;&#3118;&#3135;&#3112;&#3122;&#3149; &#3093;&#3134;&#3120;&#3149;&#3119;&#3093;&#3149;&#3120;&#3118;&#3074;
GenericName[tg]=&#1041;&#1072;&#1088;&#1085;&#1086;&#1084;&#1072;&#1080; &#1087;&#1086;&#1105;&#1085;&#1072;
GenericName[th]=&#3650;&#3611;&#3619;&#3649;&#3585;&#3619;&#3617;&#3648;&#3607;&#3629;&#3619;&#3660;&#3617;&#3636;&#3609;&#3633;&#3621;
GenericName[tr]=Terminal Program&#305;
GenericName[tt]=Terminal Yaz&#305;l&#305;m&#305;
GenericName[uk]=&#1055;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;&#1072; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;&#1091;
GenericName[uz]=&#1058;&#1077;&#1088;&#1084;&#1080;&#1085;&#1072;&#1083; &#1076;&#1072;&#1089;&#1090;&#1091;&#1088;&#1080;
GenericName[ven]=Mbekanyamushumo ya Mafhedziselo
GenericName[vi]=Trình &#273;&#7847;u cu&#7889;i
GenericName[wa]=Programe di terminå
GenericName[xh]=Inkqubo Yesixhobo sangaphandle sekhompyutha
GenericName[zh_CN]=&#32456;&#31471;&#31243;&#24207;
GenericName[zh_TW]=&#32066;&#31471;&#27231;&#31243;&#24335;
GenericName[zu]=Uhlelo lwemisebenzi lwangaohandle
X-DCOP-ServiceType=Multi
X-KDE-AuthorizeAction=shell_access
Categories=Qt;KDE;System;TerminalEmulator;
```

3. Select a transparent scheme from the settings menu in Konsole


And voila, a transparent konsole. You might also have to update other shortcuts to konsole on the desktop or in the taskbar.

And a happy new year 8-)

---

### Post by bhavi on 2008-03-24
Nice trick mate.... :)

---

