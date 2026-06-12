---
title: "Dash Home"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by arno48 on 2012-08-01
Hello,
How can I get LibreOffice Writer icon appear in Dash Home?
thanks

---

### Post by raja.genupula on 2012-08-01
I think you want to add it Unity bar . press your super key and type there as  LibreOffice Writer . then it will give you the  LibreOffice Writer . click it . Now thats available in unity panel . then give a right click at  LibreOffice Writer  and select lock to launcher . Then it will be fixed to panel .

---

### Post by Vaphell on 2012-08-01
i dont get what you mean
you type lib - LO apps are shown, Writer among them
writer - LOWriter is shown
apps lens -> Office - LOWriter is shown
[https://lh6.googleusercontent.com/-rqAAoHny_pE/Tl6izfiet8I/AAAAAAAAF64/k3OknyrHtMQ/s400/ubuntu11.10-applications-lens.png](https://lh6.googleusercontent.com/-rqAAoHny_pE/Tl6izfiet8I/AAAAAAAAF64/k3OknyrHtMQ/s400/ubuntu11.10-applications-lens.png)

if you want the icon persist in the launcher bar, you simply launch the app and right click the icon, pin to launcher bar.

---

### Post by arno48 on 2012-08-01
[COLOR=#000000][FONT=Verdana][SIZE=2]*I want to have the LibreOffice Writer  in the Launcher when I am working with it.*[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana][SIZE=2]*I tried to drag the icon to the Launcher, but the icon does not stay.*[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana][SIZE=2]*On the contrary LibreOffice Calc appears in the launcher.  *[/SIZE][/FONT][/COLOR] 
 


 [COLOR=#000000][FONT=Verdana][SIZE=2]*Thanks.*[/SIZE][/FONT][/COLOR]

---

### Post by raja.genupula on 2012-08-01
> **arno48 said:**
> [COLOR=#000000][FONT=Verdana][SIZE=2]*I want to have the LibreOffice Writer  in the Launcher when I am working with it.*[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana][SIZE=2]*I tried to drag the icon to the Launcher, but the icon does not stay.*[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana][SIZE=2]*On the contrary LibreOffice Calc appears in the launcher.  *[/SIZE][/FONT][/COLOR] 
 


 [COLOR=#000000][FONT=Verdana][SIZE=2]*Thanks.*[/SIZE][/FONT][/COLOR]

have you tried post #2 .

---

### Post by arno48 on 2012-08-01
> **raja.genupula said:**
> have you tried post #2 .

  	 	 	 	 	 	   [COLOR=#000000][FONT=Verdana][SIZE=2]*Yes I tried:*[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana][SIZE=2]*I press super key and type LibreOffice Writer, then I click it and LOwriter opens and I can work but the icon does not appear in the Launcher *[/SIZE][/FONT][/COLOR]

---

### Post by raja.genupula on 2012-08-02
press **ctrl+alt+f1** and login there . then  type as ```
unity --reset-icons 
```. then 
```
sudo restart lightdm 
``` . try again . all the best.

---

### Post by arno48 on 2012-08-03
> **raja.genupula said:**
> press **ctrl+alt+f1** and login there . then  type as ```
unity --reset-icons 
```. then 
```
sudo restart lightdm 
``` . try again . all the best.


Thank you

---

### Post by arno48 on 2012-08-03
Hello,
 How can I select  LibreOffice Writer's  Quick List when LibreOffice Writer is running?
 Thanks

---

### Post by MG&amp;TL on 2012-08-03
Just the same as you would normally do, just right-click on the Writer icon. 

Hope that helped.

---

### Post by arno48 on 2012-08-03
> **MG&TL said:**
> Just the same as you would normally do, just right-click on the Writer icon. 

Hope that helped.
Thanks but Writer icon does not appear in the Launcher, even when Writer is open.
I tried to drag the icon from Dash to the Launcher,  but it does not stay in the Launcher.
If I right-click on the Writer icon in Dash, Writer opens without showing Quick List.

---

### Post by MG&amp;TL on 2012-08-03
> **arno48 said:**
> Thanks but Writer icon does not appear in the Launcher, even when Writer is open.
I tried to drag the icon from Dash to the Launcher,  but it does not stay in the Launcher.
If I right-click on the Writer icon in Dash, Writer opens without showing Quick List.

Then we've got a different issue. You can't access quicklists from Dash by design.

When you say 'doesn't stay in the launcher'-what do you mean? Does it refuse to go into the launcher at all, stay for a while and then disappear, show a blank space?

---

### Post by arno48 on 2012-08-03
> **MG&TL said:**
> Then we've got a different issue. You can't access quicklists from Dash by design.

When you say 'doesn't stay in the launcher'-what do you mean? Does it refuse to go into the launcher at all, stay for a while and then disappear, show a blank space?


  	 	 	 	 	 	   I can drag it into the Launcher, but as soon as I lift my finger from the left-click, the icon disappears  from the Launcher.
 Thanks for your interest

---

### Post by MG&amp;TL on 2012-08-03
Right. I'm assuming that something is wrong with LibreOffice's .desktop files (the files unity uses to show applications).

Can you post the output of:

```
cat /usr/share/applications/libreoffice-writer.desktop
```

...thanks.

---

### Post by wildmanne39 on 2012-08-03
Please do not post duplicates, it dilutes community effort. Threads merged

---

### Post by arno48 on 2012-08-03
> **MG&TL said:**
> Right. I'm assuming that something is wrong with LibreOffice's .desktop files (the files unity uses to show applications).

Can you post the output of:

```

```...thanks.
The answer is:

-bash: No such file or directory

By the way,  could you please learn me how to paste 
cat /usr/share/applications/libreoffice-writer.desktop
on the PROMPT and how to copy and to paste the output

Thanks

---

### Post by MG&amp;TL on 2012-08-03
> **arno48 said:**
> The answer is:

-bash: No such file or directory

By the way,  could you please learn me how to paste 
cat /usr/share/applications/libreoffice-writer.desktop
on the PROMPT and how to copy and to paste the output

Thanks

It sounds like you've made a mistake somewhere. Never fear though, I shall show you a magic trick: how to copy/paste from the command-line.

Paste:

1.Make sure focus is given to the prompt (i.e. can you type in it)
2.Press Ctrl-Shift-V.

Copy:

1.Make sure the prompt is focused and you have selected something with your mouse.
2.Press Ctrl-Shift-C to copy the selection onto the clipboard.

Hope that helps a bit.

---

### Post by arno48 on 2012-08-03
> **MG&TL said:**
> It sounds like you've made a mistake somewhere. Never fear though, I shall show you a magic trick: how to copy/paste from the command-line.

Paste:

1.Make sure focus is given to the prompt (i.e. can you type in it)
2.Press Ctrl-Shift-V.

Copy:

1.Make sure the prompt is focused and you have selected something with your mouse.
2.Press Ctrl-Shift-C to copy the selection onto the clipboard.

Hope that helps a bit.


matteo@matteo-desktop:~$ cat /usr/share/applications/libreoffice-writer.desktop
[Desktop Entry]
Version=1.0
Terminal=false
Icon=libreoffice-writer
Type=Application
Categories=Office;
Exec=libreoffice --writer %U
MimeType=application/vnd.oasis.opendocument.text;application/vnd.oasis.opendocument.text-flat-xml;application/vnd.oasis.opendocument.text-template;application/vnd.oasis.opendocument.text-web;application/vnd.oasis.opendocument.text-master;a

The output goes on several additional rows. Have I to paste them?
Thanks a lot for your time.

---

### Post by wildmanne39 on 2012-08-03
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by MG&amp;TL on 2012-08-03
> **arno48 said:**
> matteo@matteo-desktop:~$ cat /usr/share/applications/libreoffice-writer.desktop
[Desktop Entry]
Version=1.0
Terminal=false
Icon=libreoffice-writer
Type=Application
Categories=Office;
Exec=libreoffice --writer %U
MimeType=application/vnd.oasis.opendocument.text;application/vnd.oasis.opendocument.text-flat-xml;application/vnd.oasis.opendocument.text-template;application/vnd.oasis.opendocument.text-web;application/vnd.oasis.opendocument.text-master;a

The output goes on several additional rows. Have I to paste them?
Thanks a lot for your time.

Okay, maybe it might be better in future for you to attach the file if it's that big. Anyway, in the morning, I'll go on my desktop (this one doesn't have unity) and attach a file for you to re-copy in case the LO one got corrupted somehow.

---

### Post by MG&amp;TL on 2012-08-04
As promised: try copying this to a new file called libreoffice-writer.desktop, then copy that to  /usr/share/applications/ 

```
[Desktop Entry]
Version=1.0
Terminal=false
Icon=libreoffice-writer
Type=Application
Categories=Office;
Exec=libreoffice --writer %U
MimeType=application/vnd.oasis.opendocument.text;application/vnd.oasis.opendocument.text-flat-xml;application/vnd.oasis.opendocument.text-template;application/vnd.oasis.opendocument.text-web;application/vnd.oasis.opendocument.text-master;application/vnd.sun.xml.writer;application/vnd.sun.xml.writer.template;application/vnd.sun.xml.writer.global;application/msword;application/vnd.ms-word;application/x-doc;application/x-hwp;application/rtf;text/rtf;application/vnd.wordperfect;application/wordperfect;application/vnd.lotus-wordpro;application/vnd.openxmlformats-officedocument.wordprocessingml.document;application/vnd.ms-word.document.macroenabled.12;application/vnd.openxmlformats-officedocument.wordprocessingml.template;application/vnd.ms-word.template.macroenabled.12;
Name=LibreOffice Writer
GenericName=Word Processor
GenericName[en]=Word Processor
GenericName[af]=Woordverwerker
GenericName[ar]=&#1605;&#1593;&#1575;&#1604;&#1580; &#1575;&#1604;&#1605;&#1587;&#1578;&#1606;&#1583;&#1575;&#1578;
GenericName[as]=Word &#2474;&#2509;&#2544;&#2458;&#2503;&#2459;&#2544;
GenericName[ast]=Procesador de testos
GenericName[be]=&#1058;&#1101;&#1082;&#1089;&#1090;&#1072;&#1074;&#1099; &#1087;&#1088;&#1072;&#1094;&#1101;&#1089;&#1072;&#1088;
GenericName[bg]=&#1058;&#1077;&#1082;&#1089;&#1090;&#1086;&#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1082;&#1072;
GenericName[bn]=&#2451;&#2479;&#2492;&#2494;&#2480;&#2509;&#2465; &#2474;&#2509;&#2480;&#2488;&#2503;&#2488;&#2480;
GenericName[br]=Kewerier testenn
GenericName[bs]=Program za obradu teksta
GenericName[ca]=Processador de textos
GenericName[ca_XV]=Processador de textos
GenericName[cs]=Textový procesor
GenericName[cy]=Prosesydd Geiriau
GenericName[da]=Tekstbehandling
GenericName[de]=Textverarbeitung
GenericName[dz]=Word Processor
GenericName[el]=&#917;&#960;&#949;&#958;&#949;&#961;&#947;&#945;&#963;&#964;&#942;&#962; Word
GenericName[en_GB]=Word Processor
GenericName[en_ZA]=Word Processor
GenericName[eo]=Verkilo
GenericName[es]=Procesador de texto
GenericName[et]=Tekstitöötlus
GenericName[eu]=Testu prozesatzailea
GenericName[fa]=&#1608;&#1575;&#1688;&#1607;*&#1662;&#1585;&#1583;&#1575;&#1586;
GenericName[fi]=Tekstinkäsittely
GenericName[fr]=Traitement de texte
GenericName[ga]=Próiseálaí Focal
GenericName[gl]=Procesador de textos
GenericName[gu]=&#2741;&#2736;&#2765;&#2721; &#2730;&#2765;&#2736;&#2763;&#2744;&#2759;&#2744;&#2736;
GenericName[he]=&#1502;&#1506;&#1489;&#1491; &#1514;&#1502;&#1500;&#1497;&#1500;&#1497;&#1501;
GenericName[hi]=&#2357;&#2352;&#2381;&#2337; &#2346;&#2381;&#2352;&#2379;&#2360;&#2375;&#2360;&#2352;
GenericName[hr]=Program za obradu teksta
GenericName[hu]=Szövegszerkeszt&#337;
GenericName[id]=Pengolah Kata
GenericName[is]=Ritvinnsluforrit
GenericName[it]=Elaboratore di testo
GenericName[ja]=&#12527;&#12540;&#12489;&#12503;&#12525;&#12475;&#12483;&#12469;
GenericName[ka]=Word Processor
GenericName[km]=&#6016;&#6040;&#6098;&#6040;&#6044;&#6071;&#6034;&#6072;&#8203;&#6044;&#6070;&#6041;&#8203;&#6050;&#6031;&#6098;&#6032;&#6036;&#6033;
GenericName[ko]=&#50892;&#46300; &#54532;&#47196;&#49464;&#49436;
GenericName[ku]=Kiryarê Peyvan
GenericName[lt]=Tekst&#371; rengykl&#279;
GenericName[lv]=Tekstapstr&#257;des programma
GenericName[mk]=&#1054;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1082;&#1072; &#1085;&#1072; &#1090;&#1077;&#1082;&#1089;&#1090;
GenericName[ml]=&#3381;&#3399;&#3376;&#3405;*&#3361;&#3405; &#3370;&#3405;&#3376;&#3402;&#3384;&#3384;&#3405;&#3384;&#3376;&#3405;*
GenericName[mn]=&#1042;&#1086;&#1088;&#1076; &#1073;&#1086;&#1083;&#1086;&#1074;&#1089;&#1088;&#1091;&#1091;&#1083;&#1072;&#1075;&#1095;
GenericName[mr]=&#2357;&#2352;&#2381;&#2337; &#2346;&#2381;&#2352;&#2379;&#2360;&#2375;&#2360;&#2352;
GenericName[nb]=Skriveprogram
GenericName[ne]=&#2357;&#2352;&#2381;&#2337; &#2346;&#2381;&#2352;&#2379;&#2360;&#2375;&#2360;&#2352;
GenericName[nl]=Tekstverwerker
GenericName[nn]=Teksthandsamar
GenericName[nr]=Word Processor
GenericName[nso]=Sebopi sa mantšu
GenericName[oc]=Tractament de tèxte
GenericName[om]=Hujeessaa Jecha
GenericName[or]=&#2870;&#2860;&#2893;&#2854; &#2872;&#2846;&#2893;&#2842;&#2878;&#2867;&#2837;
GenericName[pa_IN]=&#2613;&#2608;&#2593; &#2602;&#2608;&#2635;&#2616;&#2632;&#2616;&#2608;
GenericName[pl]=Word Processor
GenericName[pt]=Processador de texto
GenericName[pt_BR]=Editor de texto
GenericName[qtz]=Qgym&#8214;Word Processor
GenericName[ro]=Procesor de text
GenericName[ru]=&#1058;&#1077;&#1082;&#1089;&#1090;&#1086;&#1074;&#1099;&#1081; &#1087;&#1088;&#1086;&#1094;&#1077;&#1089;&#1089;&#1086;&#1088;
GenericName[rw]=Musesenguramagambo
GenericName[si]=&#3517;&#3538;&#3508;&#3538; &#3523;&#3482;&#3523;&#3505;&#3514;
GenericName[sk]=Textový procesor
GenericName[sl]=Urejevalnik besedila
GenericName[sr]=&#1059;&#1088;&#1077;&#1106;&#1080;&#1074;&#1072;&#1095; &#1090;&#1077;&#1082;&#1089;&#1090;&#1072;
GenericName[ss]=Word Processor
GenericName[st]=Word Processor
GenericName[sv]=Ordbehandlare
GenericName[ta]=&#2970;&#3018;&#2993;&#3021;&#2970;&#3014;&#2991;&#2994;&#3007;
GenericName[te]=&#3125;&#3120;&#3149;&#3105;&#3149; &#3114;&#3149;&#3120;&#3134;&#3128;&#3142;&#3128;&#3120;&#3149;
GenericName[tg]=Word Processor
GenericName[th]=Word Processor
GenericName[tn]=Word Processor
GenericName[tr]=Kelime &#304;&#351;lemci
GenericName[ts]=Word Processor
GenericName[ug]=&#1610;&#1744;&#1586;&#1609;&#1602; &#1576;&#1609;&#1585; &#1578;&#1749;&#1585;&#1749;&#1662; &#1602;&#1609;&#1604;&#1609;&#1588;
GenericName[uk]=&#1058;&#1077;&#1082;&#1089;&#1090;&#1086;&#1074;&#1080;&#1081; &#1087;&#1088;&#1086;&#1094;&#1077;&#1089;&#1086;&#1088;
GenericName[uz]=Matn protsessori
GenericName[ve]=Word Processor
GenericName[vi]=X&#7917; lý t&#7915;
GenericName[xh]=Word Processor
GenericName[zh_CN]=&#23383;&#22788;&#29702;&#22120;
GenericName[zh_TW]=&#25991;&#26360;&#34389;&#29702;&#22120;
GenericName[zu]=Word Processor
Comment=Create and edit text and graphics in letters, reports, documents and Web pages by using Writer.
Comment[en]=Create and edit text and graphics in letters, reports, documents and Web pages by using Writer.
Comment[af]=Skep en redigeer teks en grafika in briewe, verslae, dokumente en webbladsye met Writer.
Comment[ar]=&#1573;&#1606;&#1588;&#1575;&#1569; &#1575;&#1604;&#1606;&#1589;&#1608;&#1589; &#1608;&#1575;&#1604;&#1585;&#1587;&#1608;&#1605;&#1575;&#1578; &#1601;&#1610; &#1575;&#1604;&#1582;&#1591;&#1575;&#1576;&#1575;&#1578;&#1548; &#1608;&#1575;&#1604;&#1578;&#1602;&#1575;&#1585;&#1610;&#1585;&#1548; &#1608;&#1575;&#1604;&#1605;&#1587;&#1578;&#1606;&#1583;&#1575;&#1578; &#1608;&#1589;&#1601;&#1581;&#1575;&#1578; &#1608;&#1610;&#1576; &#1608;&#1578;&#1581;&#1585;&#1610;&#1585;&#1607;&#1575; &#1576;&#1575;&#1587;&#1578;&#1582;&#1583;&#1575;&#1605; Writer.
Comment[as]=Writer &#2476;&#2509;&#2479;&#2545;&#2489;&#2494;&#2544; &#2453;&#2544;&#2495; &#2458;&#2495;&#2464;&#2495;, &#2488;&#2434;&#2476;&#2494;&#2470;, &#2470;&#2488;&#2509;&#2468;&#2494;&#2476;&#2503;&#2460; &#2438;&#2544;&#2497; &#2474;&#2499;&#2487;&#2509;&#2464;&#2494;&#2476;&#2507;&#2544;&#2468; &#2469;&#2453;&#2494; &#2482;&#2495;&#2454;&#2472;&#2496; &#2438;&#2544;&#2497; &#2455;&#2509;&#2544;&#2494;&#2475;&#2495;&#2453;&#2509;&#2488; &#2488;&#2499;&#2487;&#2509;&#2463;&#2495; &#2438;&#2544;&#2497; &#2488;&#2478;&#2509;&#2474;&#2494;&#2470;&#2472;&#2494; &#2453;&#2544;&#2453;&#2404;
Comment[ast]=Crear y editar testos y gráficos de cartes, informes, documentos y páxines Web usando Writer.
Comment[be]=&#1057;&#1090;&#1074;&#1072;&#1088;&#1072;&#1081;&#1094;&#1077; &#1110; &#1088;&#1101;&#1076;&#1072;&#1075;&#1091;&#1081;&#1094;&#1077; &#1090;&#1101;&#1082;&#1089;&#1090; &#1110; &#1075;&#1088;&#1072;&#1092;&#1110;&#1082;&#1091; &#1118; &#1083;&#1110;&#1089;&#1090;&#1072;&#1093;, &#1089;&#1087;&#1088;&#1072;&#1074;&#1072;&#1079;&#1076;&#1072;&#1095;&#1072;&#1093;, &#1076;&#1072;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1072;&#1093; &#1110; &#1089;&#1090;&#1072;&#1088;&#1086;&#1085;&#1082;&#1072;&#1093; &#1057;&#1077;&#1094;&#1110;&#1074;&#1072; &#1079; &#1076;&#1072;&#1087;&#1072;&#1084;&#1086;&#1075;&#1072;&#1102; Writer-&#1072;.
Comment[bg]=&#1057; Writer &#1084;&#1086;&#1078;&#1077;&#1090;&#1077; &#1076;&#1072; &#1089;&#1098;&#1079;&#1076;&#1072;&#1074;&#1072;&#1090;&#1077; &#1080; &#1088;&#1077;&#1076;&#1072;&#1082;&#1090;&#1080;&#1088;&#1072;&#1090;&#1077; &#1090;&#1077;&#1082;&#1089;&#1090; &#1080; &#1075;&#1088;&#1072;&#1092;&#1080;&#1082;&#1080; &#1074; &#1087;&#1080;&#1089;&#1084;&#1072;, &#1086;&#1090;&#1095;&#1077;&#1090;&#1080;, &#1076;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1080; &#1080; &#1091;&#1077;&#1073;&#1089;&#1090;&#1088;&#1072;&#1085;&#1080;&#1094;&#1080;.
Comment[bn]=&#2480;&#2494;&#2439;&#2463;&#2494;&#2480; &#2476;&#2509;&#2479;&#2476;&#2489;&#2494;&#2480; &#2453;&#2480;&#2503; &#2458;&#2495;&#2464;&#2495;&#2474;&#2468;&#2509;&#2480;, &#2480;&#2495;&#2474;&#2507;&#2480;&#2509;&#2463;, &#2472;&#2469;&#2495; &#2447;&#2476;&#2434; &#2451;&#2479;&#2492;&#2503;&#2476;&#2474;&#2503;&#2460;&#2503;&#2480; &#2482;&#2503;&#2454;&#2494; &#2451; &#2459;&#2476;&#2495; &#2468;&#2504;&#2480;&#2495; &#2447;&#2476;&#2434; &#2488;&#2478;&#2509;&#2474;&#2494;&#2470;&#2472;&#2494; &#2453;&#2480;&#2497;&#2472;&#2404;
Comment[br]=Writer - Krouiñ hag embann testennoù ha skeudennoù evit lizhiri, danevelloù, teulioù ha pajennoù Web.
Comment[bs]=Kreiranje i ure&#273;ivanje teksta i grafike u pismima, izvještajima, dokumentima i Web stranicama koriste&#263;i Writer.
Comment[ca]=Creeu i editeu textos i gràfics en cartes, informes, documents i pàgines web amb el Writer.
Comment[ca_XV]=Creeu i editeu textos i gràfics en cartes, informes, documents i pàgines web amb el Writer.
Comment[cs]=Writer umož&#328;uje vytvá&#345;et a upravovat text a grafiku v dopisech, sestavách, dokumentech a webových stránkách.
Comment[cy]=Creu a golygu testun a graffigau mewn llythyron, adroddiadau, dogfennau a thudalennau Gwe gyda Writer.
Comment[da]=LibreOffice-tekstdokument
Comment[de]=Erstellen und bearbeiten von Text und Grafiken in Briefen, Reports, Dokumenten und Web-Seiten - Writer macht's möglich.
Comment[dz]=&#3938;&#4009;&#3964;&#3928;&#3851;&#3936;&#3926;&#4018;&#3954;&#3851;&#3924;&#3851;&#3939;&#3906;&#3851;&#3939;&#3962;&#3923;&#3851;&#3936;&#3920;&#3926;&#3851;&#3920;&#3964;&#3906;&#3851;&#3939;&#3942;&#3851; &#3933;&#3962;&#3926;&#3851;&#3924;&#3962;&#3911;&#3954;&#3851;&#3921;&#3908;&#3851; &#3937;&#3954;&#3906;&#3851;&#3910;&#3936;&#3954;&#3851;&#3938;&#3954;&#3906;&#3942;&#3851; &#3942;&#3993;&#3923;&#3851;&#3934;&#3956;&#3936;&#3954;&#3851;&#3938;&#3954;&#3906;&#3942;&#3851; &#3937;&#3954;&#3851;&#3906;&#3956;&#3936;&#3954;&#3851;&#3938;&#3954;&#3906;&#3942;&#3851;&#3930;&#3956;&#3851;&#3923;&#3908;&#3851;&#3939;&#3956;&#3851; &#3930;&#3954;&#3906;&#3851;&#3937;&#3954;&#3906;&#3851;&#3921;&#3908;&#3851;&#3930;&#3921;&#3851;&#3938;&#3954;&#3942;&#3851;&#3930;&#3956;&#3851;&#3926;&#3935;&#3964;&#3851;&#3923;&#3954;&#3851;&#3921;&#3908;&#3851;&#3934;&#3956;&#3923;&#3851;&#3921;&#3906;&#3851;&#3938;&#3984;&#4017;&#3926;&#3851;&#3923;&#3954;&#3853;
Comment[el]=&#916;&#951;&#956;&#953;&#959;&#965;&#961;&#947;&#943;&#945; &#954;&#945;&#953; &#949;&#960;&#949;&#958;&#949;&#961;&#947;&#945;&#963;&#943;&#945; &#954;&#949;&#953;&#956;&#941;&#957;&#959;&#965; &#954;&#945;&#953; &#947;&#961;&#945;&#966;&#953;&#954;&#974;&#957; &#963;&#949; &#949;&#960;&#953;&#963;&#964;&#959;&#955;&#941;&#962;, &#945;&#957;&#945;&#966;&#959;&#961;&#941;&#962;, &#941;&#947;&#947;&#961;&#945;&#966;&#945; &#954;&#945;&#953; &#953;&#963;&#964;&#959;&#963;&#949;&#955;&#943;&#948;&#949;&#962; &#956;&#949; &#964;&#951; &#967;&#961;&#942;&#963;&#951; &#964;&#959;&#965; Writer.
Comment[en_GB]=Create and edit text and graphics in letters, reports, documents and Web pages using Writer.
Comment[en_ZA]=Create and edit text and graphics in letters, reports, documents and Web pages by using Writer.
Comment[eo]=Krei kaj redakti tekston kaj grafika&#309;ojn en leteroj, raportoj, dokumentoj kaj TTT-pa&#285;oj per Verkilo.
Comment[es]=Cree y edite texto y gráficos en cartas, informes, documentos y páginas Web con Writer.
Comment[et]=Writer võimaldab luua ja redigeerida kirjade, aruannete, dokumentide ning veebilehtede teksti ja pilte.
Comment[eu]=Testua eta grafikoak sortu eta editatu gutunetan, txostenetan, dokumentuetan eta web orrietan Writer erabiliz.
Comment[fa]=&#1576;&#1575; &#1575;&#1587;&#1578;&#1601;&#1575;&#1583;&#1607; &#1575;&#1586; &#1705;&#1575;&#1578;&#1576;&#1548; &#1605;&#1578;&#1606; &#1608; &#1711;&#1585;&#1575;&#1601;&#1740;&#1705; &#1606;&#1575;&#1605;&#1607;*&#1607;&#1575;&#1548; &#1711;&#1586;&#1575;&#1585;&#1588;*&#1607;&#1575;&#1548; &#1606;&#1608;&#1588;&#1578;&#1575;&#1585;&#1607;&#1575; &#1608; &#1589;&#1601;&#1581;&#1575;&#1578; &#1608;&#1576; &#1585;&#1575; &#1575;&#1740;&#1580;&#1575;&#1583; &#1740;&#1575; &#1608;&#1740;&#1585;&#1575;&#1740;&#1588; &#1705;&#1606;&#1740;&#1583;.
Comment[fi]=Luo ja muokkaa tekstiä ja grafiikkaa kirjeisiin, raportteihin, tekstiasiakirjoihin ja internet-sivuihin Writer-ohjelmalla.
Comment[fr]=Writer - Création et édition de textes et d'images pour courriers, rapports, documents et pages Web.
Comment[ga]=Cruthaigh téacs agus grafaicí i litreacha, tuairiscí, cáipéisí, agus leathanaigh Ghréasáin le Writer.
Comment[gl]=Crear e editar texto ou imaxes en cartas, informes, documentos e páxinas web usando Writer.
Comment[gu]=&#2738;&#2710;&#2750;&#2723; &#2726;&#2765;&#2726;&#2750;&#2736;&#2750; &#2730;&#2724;&#2765;&#2736;&#2763;, &#2693;&#2745;&#2759;&#2741;&#2750;&#2738;&#2763;, &#2726;&#2744;&#2765;&#2724;&#2750;&#2741;&#2759;&#2716;&#2763; &#2693;&#2728;&#2759; &#2741;&#2759;&#2732; &#2730;&#2750;&#2728;&#2750;&#2707;&#2734;&#2750;&#2690; &#2738;&#2710;&#2750;&#2723; &#2693;&#2728;&#2759; &#2714;&#2751;&#2724;&#2765;&#2736;&#2763; &#2732;&#2728;&#2750;&#2741;&#2763; &#2693;&#2728;&#2759; &#2744;&#2753;&#2712;&#2750;&#2736;&#2763;.
Comment[he]=&#1497;&#1510;&#1497;&#1512;&#1492; &#1493;&#1506;&#1512;&#1497;&#1499;&#1492; &#1513;&#1500; &#1496;&#1511;&#1505;&#1496; &#1493;&#1490;&#1512;&#1508;&#1497;&#1511;&#1492; &#1489;&#1502;&#1499;&#1514;&#1489;&#1497;&#1501;, &#1491;&#1493;&#1495;&#1493;&#1514;, &#1502;&#1505;&#1502;&#1499;&#1497;&#1501; &#1493;&#1491;&#1508;&#1497; &#1488;&#1497;&#1504;&#1496;&#1512;&#1504;&#1496; &#1489;&#1488;&#1502;&#1510;&#1506;&#1493;&#1514; Writer.
Comment[hi]=&#2354;&#2375;&#2326;&#2325; &#2325;&#2375; &#2346;&#2381;&#2352;&#2351;&#2379;&#2327; &#2360;&#2375; &#2346;&#2340;&#2381;&#2352;, &#2352;&#2367;&#2346;&#2379;&#2352;&#2381;&#2335;, &#2342;&#2360;&#2381;&#2340;&#2366;&#2357;&#2375;&#2332;&#2364; &#2350;&#2375;&#2306; &#2346;&#2366;&#2336; &#2324;&#2352; &#2310;&#2352;&#2375;&#2326; &#2348;&#2344;&#2366;&#2340;&#2366; &#2361;&#2376; &#2324;&#2352; &#2360;&#2306;&#2346;&#2366;&#2342;&#2367;&#2340; &#2325;&#2352;&#2340;&#2366; &#2361;&#2376;.
Comment[hr]=Stvorite i uredite tekst i slike u pisma, izvješ&#263;ima, dokumentima i web stranicama.
Comment[hu]=Levelek, jelentések, dokumentumok és weboldalak szövegének és grafikájának létrehozása és szerkesztése a Writer használatával.
Comment[id]=Mengolah teks dan gambar pada surat, laporan, dokumen, dan halaman Web menggunakan Writer.
Comment[is]=Búa til og breyta texta og myndefni í bréfum, skýrslum, skjölum og vefsíðum með því að nota Writer.
Comment[it]=Usando Writer, potete creare e modificare il testo e le immagini di lettere, rapporti, documenti e pagine Web.
Comment[ja]=Writer &#12434;&#20351;&#29992;&#12375;&#12390;&#12289;&#12524;&#12479;&#12540;&#12289;&#12524;&#12509;&#12540;&#12488;&#12289;&#12489;&#12461;&#12517;&#12513;&#12531;&#12488;&#12362;&#12424;&#12403; Web &#12506;&#12540;&#12472;&#12398;&#12486;&#12461;&#12473;&#12488;&#12362;&#12424;&#12403;&#22259;&#12434;&#20316;&#25104;&#12362;&#12424;&#12403;&#32232;&#38598;&#12375;&#12414;&#12377;&#12290;
Comment[ka]=&#4325;&#4315;&#4316;&#4312;&#4321; &#4307;&#4304; &#4304;&#4321;&#4332;&#4317;&#4320;&#4308;&#4305;&#4321; &#4307;&#4317;&#4313;&#4323;&#4315;&#4308;&#4316;&#4322;&#4308;&#4305;&#4321;&#4304; &#4307;&#4304; &#4307;&#4312;&#4304;&#4306;&#4320;&#4304;&#4315;&#4308;&#4305;&#4321; &#4332;&#4308;&#4320;&#4312;&#4314;&#4308;&#4305;&#4328;&#4312;, &#4315;&#4317;&#4334;&#4321;&#4308;&#4316;&#4308;&#4305;&#4308;&#4305;&#4328;&#4312;, &#4307;&#4317;&#4313;&#4323;&#4315;&#4308;&#4316;&#4322;&#4308;&#4305;&#4328;&#4312; &#4307;&#4304; &#4309;&#4308;&#4305;-&#4306;&#4309;&#4308;&#4320;&#4307;&#4308;&#4305;&#4328;&#4312; Writer-&#4312;&#4321; &#4315;&#4308;&#4328;&#4309;&#4308;&#4317;&#4305;&#4312;&#4311;.
Comment[km]=&#6036;&#6020;&#6098;&#6016;&#6078;&#6031; &#6035;&#6071;&#6020;&#8203;&#6016;&#6082;&#8203;&#6047;&#6040;&#6098;&#6042;&#6077;&#6043;&#8203;&#6050;&#6031;&#6098;&#6032;&#6036;&#6033; &#6035;&#6071;&#6020;&#8203;&#6016;&#6098;&#6042;&#6070;&#6048;&#6098;&#6044;&#6071;&#6016;&#8203;&#6016;&#6098;&#6035;&#6075;&#6020;&#8203;&#6047;&#6086;&#6036;&#6075;&#6031;&#6098;&#6042; &#6042;&#6036;&#6070;&#6041;&#6016;&#6070;&#6042;&#6030;&#6093; &#6063;&#6016;&#6047;&#6070;&#6042; &#6035;&#6071;&#6020;&#8203;&#6033;&#6086;&#6038;&#6096;&#6042;&#8203;&#6036;&#6030;&#6098;&#6031;&#6070;&#6025;&#8203;&#6026;&#6084;&#6041;&#8203;&#6036;&#6098;&#6042;&#6078; Writer &#6100;
Comment[ko]=Writer&#47484; &#49324;&#50857;&#54616;&#50668; &#54200;&#51648;, &#48372;&#44256;&#49436;, &#47928;&#49436; &#48143; &#50937; &#54168;&#51060;&#51648;&#50640;&#49436; &#53581;&#49828;&#53944;&#50752; &#44536;&#47548;&#51012; &#47564;&#46308;&#44256; &#54200;&#51665;&#54624; &#49688; &#51080;&#49845;&#45768;&#45796;.
Comment[ku]=Nivîs û grafîkên di name, rapor, belge û rûpelên torê de bî Writerê çêbike û sererast bike.
Comment[lt]=Tekst&#371; rengykle galima kurti laiškus, ataskaitas, kitus dokumentus ir tinklalapius, &#303;terpti &#303; juos paveikslus.
Comment[lv]=Veidot un redi&#291;&#275;t tekstu un grafisku v&#275;stul&#275;s, atskait&#275;s, dokumentos un t&#299;mek&#316;a lap&#257;s, lietojot Writer.
Comment[mk]=&#1050;&#1088;&#1077;&#1080;&#1088;&#1072;&#1112;&#1090;&#1077; &#1080; &#1091;&#1088;&#1077;&#1076;&#1091;&#1074;&#1072;&#1112;&#1090;&#1077; &#1090;&#1077;&#1082;&#1089;&#1090; &#1080; &#1075;&#1088;&#1072;&#1092;&#1080;&#1082;&#1072; &#1074;&#1086; &#1087;&#1080;&#1089;&#1084;&#1072;, &#1080;&#1079;&#1074;&#1077;&#1096;&#1090;&#1072;&#1080;, &#1076;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1080; &#1080; &#1074;&#1077;&#1073;-&#1089;&#1090;&#1088;&#1072;&#1085;&#1080;&#1094;&#1080; &#1089;&#1086; &#1082;&#1086;&#1088;&#1080;&#1089;&#1090;&#1077;&#1114;&#1077; &#1085;&#1072; Writer.
Comment[ml]=&#3377;&#3400;&#3377;&#3405;&#3377;&#3376;&#3405; &#3337;&#3370;&#3375;&#3403;&#3351;&#3391;&#3354;&#3405;&#3354;&#3405;  &#3349;&#3364;&#3405;&#3364;&#3393;&#3349;&#3379;&#3391;&#3378;&#3398;&#3375;&#3393;&#3330; &#3377;&#3391;&#3370;&#3405;&#3370;&#3403;&#3376;&#3405;&#3359;&#3405;&#3359;&#3393;&#3349;&#3379;&#3391;&#3378;&#3398;&#3375;&#3393;&#3330; &#3361;&#3403;&#3349;&#3405;&#3349;&#3393;&#3374;&#3398;&#3368;&#3405;&#3377;&#3391;&#3378;&#3398;&#3375;&#3393;&#3330; &#3381;&#3398;&#3372;&#3405; &#3370;&#3399;&#3356;&#3391;&#3378;&#3398;&#3375;&#3393;&#3330;  &#3359;&#3398;&#3349;&#3405;&#3384;&#3405;&#3377;&#3405;&#3377;&#3393;&#3330; &#3351;&#3405;&#3376;&#3390;&#3371;&#3391;&#3349;&#3405;&#3384;&#3393;&#3330; &#3384;&#3395;&#3383;&#3405;&#3359;&#3391;&#3349;&#3405;&#3349;&#3393;&#3349;&#3375;&#3393;&#3330; &#3342;&#3361;&#3391;&#3377;&#3405;&#3377;&#3393; &#3354;&#3398;&#3375;&#3405;&#3375;&#3393;&#3349;&#3375;&#3393;&#3330; &#3354;&#3398;&#3375;&#3405;&#3375;&#3393;&#3349;.
Comment[mn]=Writer &#1072;&#1096;&#1080;&#1075;&#1083;&#1072;&#1085; &#1079;&#1072;&#1093;&#1080;&#1072;, &#1090;&#1072;&#1081;&#1083;&#1072;&#1085;, &#1073;&#1072;&#1088;&#1080;&#1084;&#1090; &#1076;&#1072;&#1093;&#1100; &#1073;&#1080;&#1095;&#1074;&#1101;&#1088; &#1073;&#1072; &#1075;&#1088;&#1072;&#1092;&#1080;&#1082; &#1199;&#1199;&#1089;&#1075;&#1101;&#1093; &#1073;&#1086;&#1083;&#1086;&#1085; &#1079;&#1072;&#1089;&#1074;&#1072;&#1088;&#1083;&#1072;&#1093;.
Comment[mr]=Writer &#2330;&#2366; &#2357;&#2366;&#2346;&#2352;&#2370;&#2344; &#2346;&#2340;&#2381;&#2352;&#2306;, &#2309;&#2361;&#2357;&#2366;&#2354;, &#2342;&#2360;&#2381;&#2340;&#2320;&#2357;&#2332; &#2357; &#2357;&#2375;&#2348; &#2346;&#2366;&#2344; &#2309;&#2306;&#2340;&#2352;&#2381;&#2327;&#2340; &#2346;&#2366;&#2336;&#2381;&#2351; &#2357; &#2330;&#2367;&#2340;&#2381;&#2352;&#2354;&#2375;&#2326; &#2348;&#2344;&#2357;&#2366; &#2357; &#2360;&#2306;&#2346;&#2366;&#2342;&#2368;&#2340; &#2325;&#2352;&#2366;.
Comment[nb]=Opprett og rediger tekst og bilder i brev, rapporter, dokumenter og nettsider ved å bruke Writer.
Comment[ne]=&#2354;&#2375;&#2326;&#2325;&#2325;&#2379; &#2346;&#2381;&#2352;&#2351;&#2379;&#2327;&#2342;&#2381;&#2357;&#2366;&#2352;&#2366; &#2330;&#2367;&#2336;&#2381;&#2336;&#2368;&#2361;&#2352;&#2370;, &#2346;&#2381;&#2352;&#2340;&#2367;&#2357;&#2375;&#2342;&#2344;&#2361;&#2352;&#2370;, &#2325;&#2366;&#2327;&#2332;&#2366;&#2340;&#2361;&#2352;&#2370; &#2352; &#2357;&#2375;&#2348; &#2346;&#2371;&#2359;&#2381;&#2336;&#2361;&#2352;&#2370;&#2350;&#2366; &#2346;&#2366;&#2336; &#2340;&#2341;&#2366; &#2327;&#2381;&#2352;&#2366;&#2347;&#2367;&#2325;&#2381;&#2360; &#2360;&#2367;&#2352;&#2381;&#2332;&#2344;&#2366; &#2340;&#2341;&#2366; &#2360;&#2350;&#2381;&#2346;&#2366;&#2342;&#2344; &#2327;&#2352;&#2381;&#2344;&#2369;&#2361;&#2379;&#2360;&#2381; &#2404;
Comment[nl]=Met Writer kunt u tekst en afbeeldingen in brieven, rapporten, documenten en webpagina's maken en bewerken.
Comment[nn]=Med Writer kan du laga og redigera tekst og bilete i brev, rapportar, dokument og nettsider.
Comment[nr]=Enza nokuhlela itheksti neentjengiso eziseencwadini, emibikweni, emitlolweni nemakhasini weWebh ngokusebenzisa i-Writer.
Comment[nso]=Hlama le go lokiša sengwalwa le dikrafiki mangwalong, dipegong, ditokumenteng le matlakaleng a wepe ka go diriša Writer.
Comment[oc]=Writer - Creacion e edicion de tèxtes e d'imatges per corrièrs, rapòrts, documents e paginas Web.
Comment[om]=Bareessaa fayyadamuun xalayaalee, gabasota, galmeewwanii fi fuulota saphaphuu irratti barruu fi saxxatoo uumi, gulaali.
Comment[or]=&#2864;&#2878;&#2823;&#2847;&#2864; &#2825;&#2858;&#2911;&#2891;&#2839; &#2837;&#2864;&#2879; &#2858;&#2852;&#2893;&#2864;&#2839;&#2881;&#2849;&#2879;&#2837;&#2864;&#2887;, &#2864;&#2879;&#2858;&#2891;&#2864;&#2893;&#2847;&#2864;&#2887;,&#2854;&#2866;&#2879;&#2866;&#2839;&#2881;&#2849;&#2879;&#2837;&#2864;&#2887; &#2831;&#2860;&#2818; &#2825;&#2831;&#2860;&#2893; &#2858;&#2883;&#2871;&#2893;&#2848;&#2878;&#2839;&#2881;&#2849;&#2879;&#2837;&#2864;&#2887; &#2847;&#2887;&#2837;&#2893;&#2872;&#2847; &#2831;&#2860;&#2818; &#2866;&#2887;&#2838;&#2878;&#2842;&#2879;&#2852;&#2893;&#2864;&#2839;&#2881;&#2849;&#2879;&#2837;&#2881; &#2872;&#2883;&#2871;&#2893;&#2847;&#2879; &#2831;&#2860;&#2818; &#2872;&#2862;&#2893;&#2858;&#2878;&#2854;&#2856; &#2837;&#2864;&#2856;&#2893;&#2852;&#2881;&#2404;
Comment[pa_IN]=&#2608;&#2622;&#2567;&#2591;&#2608; &#2600;&#2622;&#2610; &#2602;&#2673;&#2596;&#2608;&#2622;&#2562;, &#2608;&#2623;&#2602;&#2635;&#2608;&#2591;&#2622;&#2562;, &#2593;&#2636;&#2581;&#2626;&#2606;&#2632;&#2562;&#2591;&#2622;&#2562; &#2565;&#2596;&#2631; &#2613;&#2632;&#2673;&#2604; &#2616;&#2603;&#2620;&#2623;&#2566;&#2562; &#2613;&#2623;&#2673;&#2586; &#2591;&#2632;&#2581;&#2616;&#2591; &#2565;&#2596;&#2631; &#2586;&#2623;&#2673;&#2596;&#2608; &#2604;&#2595;&#2622;&#2575; &#2565;&#2596;&#2631; &#2616;&#2635;&#2599;&#2631; &#2588;&#2622; &#2616;&#2581;&#2598;&#2631; &#2617;&#2600;&#2404;
Comment[pl]=Twórz i edytuj listy, raporty, dokumenty i strony www wykorzystuj&#261;c program Writer.
Comment[pt]=Criar e editar texto e objetos gráficos em cartas, relatórios, documentos e páginas web através do Writer.
Comment[pt_BR]=Crie e edite textos e figuras em cartas, relatórios, documentos e páginas da Web por meio do Writer.
Comment[qtz]=seqx&#8214;Create and edit text and graphics in letters, reports, documents and Web pages by using Writer.
Comment[ro]=Crea&#539;i &#537;i edita&#539;i text &#537;i grafic&#259; în scrisori, rapoarte, documente &#537;i pagini web folosind Writer.
Comment[ru]=&#1057;&#1086;&#1079;&#1076;&#1072;&#1085;&#1080;&#1077; &#1080; &#1088;&#1077;&#1076;&#1072;&#1082;&#1090;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085;&#1080;&#1077; &#1090;&#1077;&#1082;&#1089;&#1090;&#1072; &#1080; &#1088;&#1080;&#1089;&#1091;&#1085;&#1082;&#1086;&#1074; &#1074; &#1087;&#1080;&#1089;&#1100;&#1084;&#1072;&#1093;, &#1086;&#1090;&#1095;&#1105;&#1090;&#1072;&#1093;, &#1076;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1072;&#1093; &#1080;&#1083;&#1080; &#1074;&#1077;&#1073;-&#1089;&#1090;&#1088;&#1072;&#1085;&#1080;&#1094;&#1072;&#1093;.
Comment[rw]=Kurema no guhindura umwandiko n'ibishushanyo mu mabaruwa, raporo, inyandiko na paji Rubuga ukoresheje Writer.
Comment[si]=Writer &#3511;&#3535;&#3520;&#3538;&#3501;&#3535; &#3482;&#3515;&#3512;&#3538;&#3505;&#3530; &#3517;&#3538;&#3508;&#3538; &#3520;&#3517; &#3508;&#3545;&#3525; &#3523;&#3524; &#3488;&#3538;&#3501;&#3530;*&#3515;&#3482;, &#3520;&#3535;&#3515;&#3530;&#3501;&#3535;, &#3517;&#3538;&#3508;&#3538; &#3523;&#3524; &#3520;&#3538;&#3514;&#3540;&#3499;&#3540; &#3508;&#3538;&#3495;&#3540; &#3523;&#3535;&#3503;&#3505;&#3530;&#3505; &#3523;&#3524; &#3520;&#3545;&#3505;&#3523;&#3530; &#3482;&#3515;&#3505;&#3530;&#3505;.
Comment[sk]=Vytvárajte a upravujte textové a grafické listy, správy, dokumenty a webové stránky s použitím Writer.
Comment[sl]=S programom Writer ustvarjajte in urejajte besedilo in slike v pismih, poro&#269;ilih, dokumentih in spletnih straneh.
Comment[sr]=&#1055;&#1080;&#1096;&#1080;&#1090;&#1077; &#1080; &#1091;&#1088;&#1077;&#1106;&#1091;&#1112;&#1090;&#1077; &#1090;&#1077;&#1082;&#1089;&#1090; &#1080; &#1075;&#1088;&#1072;&#1092;&#1080;&#1082;&#1091; &#1091; &#1087;&#1080;&#1089;&#1084;&#1080;&#1084;&#1072;, &#1080;&#1079;&#1074;&#1077;&#1096;&#1090;&#1072;&#1112;&#1080;&#1084;&#1072; &#1080; &#1074;&#1077;&#1073; &#1089;&#1090;&#1088;&#1072;&#1085;&#1080;&#1094;&#1072;&#1084;&#1072; &#1091; &#1055;&#1080;&#1089;&#1094;&#1091;.
Comment[ss]=Yakha u-edithe umbhalo nemagrafiki etincwadzini, umbiko, wemadokhumenti nemapheji eWebhu ngekusebentisa Writer.
Comment[st]=Bopa le ho lokisa mongolo le ditshwantsho mangolong, ditlalehong, ditokomaneng le maqepheng a Wepe ka ho sebedisa Writer.
Comment[sv]=Skapa och redigera text och grafik i brev, rapporter, dokument och webbsidor med hjälp av Writer.
Comment[ta]=&#2965;&#2975;&#3007;&#2980;&#2969;&#3021;&#2965;&#2995;&#3021;, &#2949;&#2993;&#3007;&#2965;&#3021;&#2965;&#3016;&#2965;&#2995;&#3021;, &#2950;&#2997;&#2979;&#2969;&#3021;&#2965;&#2995;&#3021;, &#2997;&#2994;&#3016;&#2986;&#3021;&#2986;&#2965;&#3021;&#2965;&#2969;&#3021;&#2965;&#2995;&#3021; &#2950;&#2965;&#3007;&#2991;&#2997;&#2993;&#3021;&#2993;&#3007;&#2985;&#3021; &#2953;&#2992;&#3016;, &#2986;&#2975;&#2969;&#3021;&#2965;&#2995;&#3021; &#2951;&#2997;&#2993;&#3021;&#2993;&#3016; &#2953;&#2992;&#3009;&#2997;&#3006;&#2965;&#3021;&#2965;&#2997;&#3009;&#2990;&#3021; &#2980;&#3018;&#2965;&#3009;&#2965;&#3021;&#2965;&#2997;&#3009;&#2990;&#3021; &#2992;&#3016;&#2975;&#3021;&#2975;&#2992;&#3016;&#2986;&#3021; &#2986;&#2991;&#2985;&#3021;&#2986;&#2975;&#3009;&#2980;&#3021;&#2980;&#3009;&#2965;.
Comment[te]=&#3114;&#3108;&#3149;&#3120;&#3118;&#3137; &#3118;&#3120;&#3135;&#3119;&#3137; &#3122;&#3143;&#3094; &#3119;&#3146;&#3093;&#3149;&#3093; &#3098;&#3135;&#3108;&#3149;&#3120;&#3120;&#3138;&#3114;&#3118;&#3137;&#3122;&#3137;,&#3112;&#3135;&#3125;&#3143;&#3110;&#3112;&#3122;&#3137;,&#3114;&#3108;&#3149;&#3120;&#3118;&#3137;&#3122;&#3137; &#3118;&#3120;&#3135;&#3119;&#3137; &#3125;&#3149;&#3120;&#3134;&#3119;&#3137; &#3119;&#3074;&#3108;&#3149;&#3120;&#3118;&#3137;&#3112;&#3137; &#3081;&#3114;&#3119;&#3147;&#3095;&#3135;&#3074;&#3098;&#3135;&#3112; &#3125;&#3142;&#3116;&#3149;  &#3114;&#3137;&#3103;&#3122;&#3137;&#3112;&#3137; &#3112;&#3135;&#3120;&#3149;&#3118;&#3135;&#3074;&#3098;&#3135; &#3128;&#3120;&#3135;&#3098;&#3143;&#3119;&#3137;&#3118;&#3137;. 
Comment[tg]=&#1041;&#1086; &#1105;&#1088;&#1080;&#1080; Writer &#1084;&#1072;&#1090;&#1085; &#1074;&#1072; &#1090;&#1072;&#1089;&#1074;&#1080;&#1088; &#1089;&#1086;&#1093;&#1090;&#1072;&#1085;, &#1086;&#1085;&#1203;&#1086;&#1088;&#1086; &#1080;&#1089;&#1083;&#1086;&#1203; &#1082;&#1072;&#1088;&#1076;&#1072;&#1085; &#1084;&#1091;&#1084;&#1082;&#1080;&#1085; &#1072;&#1089;&#1090;.
Comment[th]=&#3626;&#3619;&#3657;&#3634;&#3591;&#3649;&#3621;&#3632;&#3649;&#3585;&#3657;&#3652;&#3586;&#3586;&#3657;&#3629;&#3588;&#3623;&#3634;&#3617;&#3649;&#3621;&#3632;&#3585;&#3619;&#3634;&#3615;&#3636;&#3585;&#3626;&#3660;&#3651;&#3609;&#3592;&#3604;&#3627;&#3617;&#3634;&#3618; &#3619;&#3634;&#3618;&#3591;&#3634;&#3609; &#3648;&#3629;&#3585;&#3626;&#3634;&#3619; &#3649;&#3621;&#3632;&#3627;&#3609;&#3657;&#3634;&#3648;&#3623;&#3655;&#3610;&#3650;&#3604;&#3618;&#3585;&#3634;&#3619;&#3651;&#3594;&#3657; Writer
Comment[tn]=Create and edit text and graphics in letters, reports, documents and Web pages by using Writer.
Comment[tr]=Writer kullanarak mektuplardaki metin ve grafikleri, rapor, belge ve Web sayfalar&#305; olu&#351;turabilir ve düzenleyebilirsiniz.
Comment[ts]=Cinca ni ku lulamisa marito ni vudirowi eka mapapila, swiviko, tidokumente ni tipheji ta Web hi ku tirhisa Writer.
Comment[ug]=Writer &#1574;&#1609;&#1588;&#1604;&#1609;&#1578;&#1609;&#1662; &#1582;&#1749;&#1578;-&#1670;&#1749;&#1603;&#1548; &#1583;&#1608;&#1603;&#1604;&#1575;&#1578; &#1580;&#1749;&#1583;&#1739;&#1609;&#1604;&#1609;&#1548; &#1662;&#1736;&#1578;&#1736;&#1603; &#1739;&#1749; &#1578;&#1608;&#1585; &#1576;&#1749;&#1578;&#1578;&#1609;&#1603;&#1609; &#1578;&#1744;&#1603;&#1587;&#1578; &#1739;&#1749; &#1711;&#1585;&#1575;&#1601;&#1609;&#1603;&#1604;&#1575;&#1585;&#1606;&#1609; &#1602;&#1735;&#1585;&#1735;&#1662; &#1578;&#1749;&#1726;&#1585;&#1609;&#1585;&#1604;&#1609;&#1711;&#1609;&#1604;&#1609; &#1576;&#1608;&#1604;&#1609;&#1583;&#1735;.
Comment[uk]=&#1057;&#1090;&#1074;&#1086;&#1088;&#1077;&#1085;&#1085;&#1103; &#1090;&#1072; &#1088;&#1077;&#1076;&#1072;&#1075;&#1091;&#1074;&#1072;&#1085;&#1085;&#1103; &#1090;&#1077;&#1082;&#1089;&#1090;&#1091; &#1090;&#1072; &#1075;&#1088;&#1072;&#1092;&#1110;&#1082;&#1080; &#1091; &#1083;&#1080;&#1089;&#1090;&#1072;&#1093;, &#1079;&#1074;&#1110;&#1090;&#1072;&#1093;, &#1076;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1072;&#1093; &#1090;&#1072; &#1074;&#1077;&#1073;-&#1089;&#1090;&#1086;&#1088;&#1110;&#1085;&#1082;&#1072;&#1093;.
Comment[uz]=Writer yordamida hisobotlar, matn hujjatlari, veb sahifalar yaratish va tahrirlash.
Comment[ve]=Vhumbani ni dovhe ni lulamise &#7741;i&#7749;walwa na dzigirafiki kha ma&#7749;walo, mivhigo, ma&#7749;walo na masia&#7793;ari a Web nga u shumisa Writer.
Comment[vi]=T&#7841;o và s&#7917;a v&#259;n b&#7843;n và &#273;&#7891; h&#7885;a trong lá th&#432;, báo cáo, tài li&#7879;u và trang Web b&#7857;ng Writer.
Comment[xh]=Dala uze uhlele isiqendu nezazobe zegrafu ezileteni, iingxelo, amaxwebhu namakhasi Othungelwano ngokusebenzisa i-Writer.
Comment[zh_CN]=&#20351;&#29992; Writer &#21019;&#24314;&#24182;&#32534;&#36753;&#20449;&#20989;&#12289;&#25253;&#34920;&#12289;&#25991;&#26723;&#21644;&#32593;&#39029;&#20013;&#30340;&#25991;&#26412;&#21644;&#22270;&#24418;&#12290;
Comment[zh_TW]=&#20351;&#29992; Writer &#21487;&#20197;&#22312;&#20449;&#20214;&#12289;&#22577;&#21578;&#12289;&#25991;&#20214;&#21644;&#32178;&#38913;&#20013;&#24314;&#31435;&#33287;&#32232;&#36655;&#25991;&#23383;&#21644;&#22294;&#24418;&#12290;
Comment[zu]=Yenza futhi ulungise umbhalo nemidwebo esezinhlamvini zamagama, emibikweni, emafayelini nasemakhasini eWebhu ngokusebenzisa i-Writer.
InitialPreference=5
X-Ayatana-Desktop-Shortcuts=New
[New Shortcut Group]
Name=New Document
Name[en]=New Document
Name[ast]=Documentu nuevu
Name[ca]=Document nou
Name[da]=Nyt dokument
Name[de]=Neues Dokument
Name[es]=Documento nuevo
Name[el]=&#925;&#941;&#959; &#941;&#947;&#947;&#961;&#945;&#966;&#959;
Name[fi]=Uusi tekstiasiakirja
Name[fr]=Nouveau document
Name[gl]=Novo documento
Name[he]=&#1502;&#1505;&#1502;&#1498; &#1495;&#1491;&#1513;
Name[hr]=Novi dokument
Name[hu]=Új dokumentum
Name[it]=Nuovo documento
Name[is]=Nýtt textaskjal
Name[ja]=&#26032;&#35215;&#25991;&#26360;&#12434;&#20316;&#25104;
Name[ku]=Belgeya nû
Name[nl]=Nieuw Document
Name[pt_BR]=Novo documento
Name[ro]=Document nou
Name[ru]=&#1053;&#1086;&#1074;&#1099;&#1081; &#1076;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;
Name[sl]=Nov dokument
Name[te]=&#3093;&#3146;&#3108;&#3149;&#3108; &#3114;&#3108;&#3149;&#3120;&#3074;
Name[vi]=Tài li&#7879;u m&#7899;i
Name[zh_CN]=&#26032;&#24314;&#25991;&#26723;
Name[zh_TW]=&#26032;&#22686;&#25991;&#20214;
Exec=libreoffice --writer %U
TargetEnvironment=Unity

```You'll need to start a root nautilus window. Press Alt-F2 and type:

```
gksu nautilus
```and then navigate to File System -> usr -> share -> applications

and drag and drop it in, most likely replacing the old LO one. 

I hope this fixes it, but it's a long shot. You might be best off making a [bug report ]("https://bugs.launchpad.net/unity/+filebug")against Unity.

---

### Post by arno48 on 2012-08-04
> **wildmanne39 said:**
> Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.
OK Thanks.
Is the POST #22 a correct one?

---

### Post by arno48 on 2012-08-04
> **MG&TL said:**
> As promised: try copying this to a new file called libreoffice-writer.desktop, then copy that to  /usr/share/applications/ 

```
[Desktop Entry]
Version=1.0
Terminal=false
Icon=libreoffice-writer
Type=Application
Categories=Office;
Exec=libreoffice --writer %U
MimeType=application/vnd.oasis.opendocument.text;application/vnd.oasis.opendocument.text-flat-xml;application/vnd.oasis.opendocument.text-template;application/vnd.oasis.opendocument.text-web;application/vnd.oasis.opendocument.text-master;application/vnd.sun.xml.writer;application/vnd.sun.xml.writer.template;application/vnd.sun.xml.writer.global;application/msword;application/vnd.ms-word;application/x-doc;application/x-hwp;application/rtf;text/rtf;application/vnd.wordperfect;application/wordperfect;application/vnd.lotus-wordpro;application/vnd.openxmlformats-officedocument.wordprocessingml.document;application/vnd.ms-word.document.macroenabled.12;application/vnd.openxmlformats-officedocument.wordprocessingml.template;application/vnd.ms-word.template.macroenabled.12;
Name=LibreOffice Writer
GenericName=Word Processor
GenericName[en]=Word Processor
GenericName[af]=Woordverwerker
GenericName[ar]=&#1605;&#1593;&#1575;&#1604;&#1580; &#1575;&#1604;&#1605;&#1587;&#1578;&#1606;&#1583;&#1575;&#1578;
GenericName[as]=Word &#2474;&#2509;&#2544;&#2458;&#2503;&#2459;&#2544;
GenericName[ast]=Procesador de testos
GenericName[be]=&#1058;&#1101;&#1082;&#1089;&#1090;&#1072;&#1074;&#1099; &#1087;&#1088;&#1072;&#1094;&#1101;&#1089;&#1072;&#1088;
GenericName[bg]=&#1058;&#1077;&#1082;&#1089;&#1090;&#1086;&#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1082;&#1072;
GenericName[bn]=&#2451;&#2479;&#2492;&#2494;&#2480;&#2509;&#2465; &#2474;&#2509;&#2480;&#2488;&#2503;&#2488;&#2480;
GenericName[br]=Kewerier testenn
GenericName[bs]=Program za obradu teksta
GenericName[ca]=Processador de textos
GenericName[ca_XV]=Processador de textos
GenericName[cs]=Textový procesor
GenericName[cy]=Prosesydd Geiriau
GenericName[da]=Tekstbehandling
GenericName[de]=Textverarbeitung
GenericName[dz]=Word Processor
GenericName[el]=&#917;&#960;&#949;&#958;&#949;&#961;&#947;&#945;&#963;&#964;&#942;&#962; Word
GenericName[en_GB]=Word Processor
GenericName[en_ZA]=Word Processor
GenericName[eo]=Verkilo
GenericName[es]=Procesador de texto
GenericName[et]=Tekstitöötlus
GenericName[eu]=Testu prozesatzailea
GenericName[fa]=&#1608;&#1575;&#1688;&#1607;*&#1662;&#1585;&#1583;&#1575;&#1586;
GenericName[fi]=Tekstinkäsittely
GenericName[fr]=Traitement de texte
GenericName[ga]=Próiseálaí Focal
GenericName[gl]=Procesador de textos
GenericName[gu]=&#2741;&#2736;&#2765;&#2721; &#2730;&#2765;&#2736;&#2763;&#2744;&#2759;&#2744;&#2736;
GenericName[he]=&#1502;&#1506;&#1489;&#1491; &#1514;&#1502;&#1500;&#1497;&#1500;&#1497;&#1501;
GenericName[hi]=&#2357;&#2352;&#2381;&#2337; &#2346;&#2381;&#2352;&#2379;&#2360;&#2375;&#2360;&#2352;
GenericName[hr]=Program za obradu teksta
GenericName[hu]=Szövegszerkeszt&#337;
GenericName[id]=Pengolah Kata
GenericName[is]=Ritvinnsluforrit
GenericName[it]=Elaboratore di testo
GenericName[ja]=&#12527;&#12540;&#12489;&#12503;&#12525;&#12475;&#12483;&#12469;
GenericName[ka]=Word Processor
GenericName[km]=&#6016;&#6040;&#6098;&#6040;&#6044;&#6071;&#6034;&#6072;&#8203;&#6044;&#6070;&#6041;&#8203;&#6050;&#6031;&#6098;&#6032;&#6036;&#6033;
GenericName[ko]=&#50892;&#46300; &#54532;&#47196;&#49464;&#49436;
GenericName[ku]=Kiryarê Peyvan
GenericName[lt]=Tekst&#371; rengykl&#279;
GenericName[lv]=Tekstapstr&#257;des programma
GenericName[mk]=&#1054;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1082;&#1072; &#1085;&#1072; &#1090;&#1077;&#1082;&#1089;&#1090;
GenericName[ml]=&#3381;&#3399;&#3376;&#3405;*&#3361;&#3405; &#3370;&#3405;&#3376;&#3402;&#3384;&#3384;&#3405;&#3384;&#3376;&#3405;*
GenericName[mn]=&#1042;&#1086;&#1088;&#1076; &#1073;&#1086;&#1083;&#1086;&#1074;&#1089;&#1088;&#1091;&#1091;&#1083;&#1072;&#1075;&#1095;
GenericName[mr]=&#2357;&#2352;&#2381;&#2337; &#2346;&#2381;&#2352;&#2379;&#2360;&#2375;&#2360;&#2352;
GenericName[nb]=Skriveprogram
GenericName[ne]=&#2357;&#2352;&#2381;&#2337; &#2346;&#2381;&#2352;&#2379;&#2360;&#2375;&#2360;&#2352;
GenericName[nl]=Tekstverwerker
GenericName[nn]=Teksthandsamar
GenericName[nr]=Word Processor
GenericName[nso]=Sebopi sa mant&#353;u
GenericName[oc]=Tractament de tèxte
GenericName[om]=Hujeessaa Jecha
GenericName[or]=&#2870;&#2860;&#2893;&#2854; &#2872;&#2846;&#2893;&#2842;&#2878;&#2867;&#2837;
GenericName[pa_IN]=&#2613;&#2608;&#2593; &#2602;&#2608;&#2635;&#2616;&#2632;&#2616;&#2608;
GenericName[pl]=Word Processor
GenericName[pt]=Processador de texto
GenericName[pt_BR]=Editor de texto
GenericName[qtz]=Qgym&#8214;Word Processor
GenericName[ro]=Procesor de text
GenericName[ru]=&#1058;&#1077;&#1082;&#1089;&#1090;&#1086;&#1074;&#1099;&#1081; &#1087;&#1088;&#1086;&#1094;&#1077;&#1089;&#1089;&#1086;&#1088;
GenericName[rw]=Musesenguramagambo
GenericName[si]=&#3517;&#3538;&#3508;&#3538; &#3523;&#3482;&#3523;&#3505;&#3514;
GenericName[sk]=Textový procesor
GenericName[sl]=Urejevalnik besedila
GenericName[sr]=&#1059;&#1088;&#1077;&#1106;&#1080;&#1074;&#1072;&#1095; &#1090;&#1077;&#1082;&#1089;&#1090;&#1072;
GenericName[ss]=Word Processor
GenericName[st]=Word Processor
GenericName[sv]=Ordbehandlare
GenericName[ta]=&#2970;&#3018;&#2993;&#3021;&#2970;&#3014;&#2991;&#2994;&#3007;
GenericName[te]=&#3125;&#3120;&#3149;&#3105;&#3149; &#3114;&#3149;&#3120;&#3134;&#3128;&#3142;&#3128;&#3120;&#3149;
GenericName[tg]=Word Processor
GenericName[th]=Word Processor
GenericName[tn]=Word Processor
GenericName[tr]=Kelime &#304;&#351;lemci
GenericName[ts]=Word Processor
GenericName[ug]=&#1610;&#1744;&#1586;&#1609;&#1602; &#1576;&#1609;&#1585; &#1578;&#1749;&#1585;&#1749;&#1662; &#1602;&#1609;&#1604;&#1609;&#1588;
GenericName[uk]=&#1058;&#1077;&#1082;&#1089;&#1090;&#1086;&#1074;&#1080;&#1081; &#1087;&#1088;&#1086;&#1094;&#1077;&#1089;&#1086;&#1088;
GenericName[uz]=Matn protsessori
GenericName[ve]=Word Processor
GenericName[vi]=X&#7917; lý t&#7915;
GenericName[xh]=Word Processor
GenericName[zh_CN]=&#23383;&#22788;&#29702;&#22120;
GenericName[zh_TW]=&#25991;&#26360;&#34389;&#29702;&#22120;
GenericName[zu]=Word Processor
Comment=Create and edit text and graphics in letters, reports, documents and Web pages by using Writer.
Comment[en]=Create and edit text and graphics in letters, reports, documents and Web pages by using Writer.
Comment[af]=Skep en redigeer teks en grafika in briewe, verslae, dokumente en webbladsye met Writer.
Comment[ar]=&#1573;&#1606;&#1588;&#1575;&#1569; &#1575;&#1604;&#1606;&#1589;&#1608;&#1589; &#1608;&#1575;&#1604;&#1585;&#1587;&#1608;&#1605;&#1575;&#1578; &#1601;&#1610; &#1575;&#1604;&#1582;&#1591;&#1575;&#1576;&#1575;&#1578;&#1548; &#1608;&#1575;&#1604;&#1578;&#1602;&#1575;&#1585;&#1610;&#1585;&#1548; &#1608;&#1575;&#1604;&#1605;&#1587;&#1578;&#1606;&#1583;&#1575;&#1578; &#1608;&#1589;&#1601;&#1581;&#1575;&#1578; &#1608;&#1610;&#1576; &#1608;&#1578;&#1581;&#1585;&#1610;&#1585;&#1607;&#1575; &#1576;&#1575;&#1587;&#1578;&#1582;&#1583;&#1575;&#1605; Writer.
Comment[as]=Writer &#2476;&#2509;&#2479;&#2545;&#2489;&#2494;&#2544; &#2453;&#2544;&#2495; &#2458;&#2495;&#2464;&#2495;, &#2488;&#2434;&#2476;&#2494;&#2470;, &#2470;&#2488;&#2509;&#2468;&#2494;&#2476;&#2503;&#2460; &#2438;&#2544;&#2497; &#2474;&#2499;&#2487;&#2509;&#2464;&#2494;&#2476;&#2507;&#2544;&#2468; &#2469;&#2453;&#2494; &#2482;&#2495;&#2454;&#2472;&#2496; &#2438;&#2544;&#2497; &#2455;&#2509;&#2544;&#2494;&#2475;&#2495;&#2453;&#2509;&#2488; &#2488;&#2499;&#2487;&#2509;&#2463;&#2495; &#2438;&#2544;&#2497; &#2488;&#2478;&#2509;&#2474;&#2494;&#2470;&#2472;&#2494; &#2453;&#2544;&#2453;&#2404;
Comment[ast]=Crear y editar testos y gráficos de cartes, informes, documentos y páxines Web usando Writer.
Comment[be]=&#1057;&#1090;&#1074;&#1072;&#1088;&#1072;&#1081;&#1094;&#1077; &#1110; &#1088;&#1101;&#1076;&#1072;&#1075;&#1091;&#1081;&#1094;&#1077; &#1090;&#1101;&#1082;&#1089;&#1090; &#1110; &#1075;&#1088;&#1072;&#1092;&#1110;&#1082;&#1091; &#1118; &#1083;&#1110;&#1089;&#1090;&#1072;&#1093;, &#1089;&#1087;&#1088;&#1072;&#1074;&#1072;&#1079;&#1076;&#1072;&#1095;&#1072;&#1093;, &#1076;&#1072;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1072;&#1093; &#1110; &#1089;&#1090;&#1072;&#1088;&#1086;&#1085;&#1082;&#1072;&#1093; &#1057;&#1077;&#1094;&#1110;&#1074;&#1072; &#1079; &#1076;&#1072;&#1087;&#1072;&#1084;&#1086;&#1075;&#1072;&#1102; Writer-&#1072;.
Comment[bg]=&#1057; Writer &#1084;&#1086;&#1078;&#1077;&#1090;&#1077; &#1076;&#1072; &#1089;&#1098;&#1079;&#1076;&#1072;&#1074;&#1072;&#1090;&#1077; &#1080; &#1088;&#1077;&#1076;&#1072;&#1082;&#1090;&#1080;&#1088;&#1072;&#1090;&#1077; &#1090;&#1077;&#1082;&#1089;&#1090; &#1080; &#1075;&#1088;&#1072;&#1092;&#1080;&#1082;&#1080; &#1074; &#1087;&#1080;&#1089;&#1084;&#1072;, &#1086;&#1090;&#1095;&#1077;&#1090;&#1080;, &#1076;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1080; &#1080; &#1091;&#1077;&#1073;&#1089;&#1090;&#1088;&#1072;&#1085;&#1080;&#1094;&#1080;.
Comment[bn]=&#2480;&#2494;&#2439;&#2463;&#2494;&#2480; &#2476;&#2509;&#2479;&#2476;&#2489;&#2494;&#2480; &#2453;&#2480;&#2503; &#2458;&#2495;&#2464;&#2495;&#2474;&#2468;&#2509;&#2480;, &#2480;&#2495;&#2474;&#2507;&#2480;&#2509;&#2463;, &#2472;&#2469;&#2495; &#2447;&#2476;&#2434; &#2451;&#2479;&#2492;&#2503;&#2476;&#2474;&#2503;&#2460;&#2503;&#2480; &#2482;&#2503;&#2454;&#2494; &#2451; &#2459;&#2476;&#2495; &#2468;&#2504;&#2480;&#2495; &#2447;&#2476;&#2434; &#2488;&#2478;&#2509;&#2474;&#2494;&#2470;&#2472;&#2494; &#2453;&#2480;&#2497;&#2472;&#2404;
Comment[br]=Writer - Krouiñ hag embann testennoù ha skeudennoù evit lizhiri, danevelloù, teulioù ha pajennoù Web.
Comment[bs]=Kreiranje i ure&#273;ivanje teksta i grafike u pismima, izvje&#353;tajima, dokumentima i Web stranicama koriste&#263;i Writer.
Comment[ca]=Creeu i editeu textos i gràfics en cartes, informes, documents i pàgines web amb el Writer.
Comment[ca_XV]=Creeu i editeu textos i gràfics en cartes, informes, documents i pàgines web amb el Writer.
Comment[cs]=Writer umo&#382;&#328;uje vytvá&#345;et a upravovat text a grafiku v dopisech, sestavách, dokumentech a webových stránkách.
Comment[cy]=Creu a golygu testun a graffigau mewn llythyron, adroddiadau, dogfennau a thudalennau Gwe gyda Writer.
Comment[da]=LibreOffice-tekstdokument
Comment[de]=Erstellen und bearbeiten von Text und Grafiken in Briefen, Reports, Dokumenten und Web-Seiten - Writer macht's möglich.
Comment[dz]=&#3938;&#4009;&#3964;&#3928;&#3851;&#3936;&#3926;&#4018;&#3954;&#3851;&#3924;&#3851;&#3939;&#3906;&#3851;&#3939;&#3962;&#3923;&#3851;&#3936;&#3920;&#3926;&#3851;&#3920;&#3964;&#3906;&#3851;&#3939;&#3942;&#3851; &#3933;&#3962;&#3926;&#3851;&#3924;&#3962;&#3911;&#3954;&#3851;&#3921;&#3908;&#3851; &#3937;&#3954;&#3906;&#3851;&#3910;&#3936;&#3954;&#3851;&#3938;&#3954;&#3906;&#3942;&#3851; &#3942;&#3993;&#3923;&#3851;&#3934;&#3956;&#3936;&#3954;&#3851;&#3938;&#3954;&#3906;&#3942;&#3851; &#3937;&#3954;&#3851;&#3906;&#3956;&#3936;&#3954;&#3851;&#3938;&#3954;&#3906;&#3942;&#3851;&#3930;&#3956;&#3851;&#3923;&#3908;&#3851;&#3939;&#3956;&#3851; &#3930;&#3954;&#3906;&#3851;&#3937;&#3954;&#3906;&#3851;&#3921;&#3908;&#3851;&#3930;&#3921;&#3851;&#3938;&#3954;&#3942;&#3851;&#3930;&#3956;&#3851;&#3926;&#3935;&#3964;&#3851;&#3923;&#3954;&#3851;&#3921;&#3908;&#3851;&#3934;&#3956;&#3923;&#3851;&#3921;&#3906;&#3851;&#3938;&#3984;&#4017;&#3926;&#3851;&#3923;&#3954;&#3853;
Comment[el]=&#916;&#951;&#956;&#953;&#959;&#965;&#961;&#947;&#943;&#945; &#954;&#945;&#953; &#949;&#960;&#949;&#958;&#949;&#961;&#947;&#945;&#963;&#943;&#945; &#954;&#949;&#953;&#956;&#941;&#957;&#959;&#965; &#954;&#945;&#953; &#947;&#961;&#945;&#966;&#953;&#954;&#974;&#957; &#963;&#949; &#949;&#960;&#953;&#963;&#964;&#959;&#955;&#941;&#962;, &#945;&#957;&#945;&#966;&#959;&#961;&#941;&#962;, &#941;&#947;&#947;&#961;&#945;&#966;&#945; &#954;&#945;&#953; &#953;&#963;&#964;&#959;&#963;&#949;&#955;&#943;&#948;&#949;&#962; &#956;&#949; &#964;&#951; &#967;&#961;&#942;&#963;&#951; &#964;&#959;&#965; Writer.
Comment[en_GB]=Create and edit text and graphics in letters, reports, documents and Web pages using Writer.
Comment[en_ZA]=Create and edit text and graphics in letters, reports, documents and Web pages by using Writer.
Comment[eo]=Krei kaj redakti tekston kaj grafika&#309;ojn en leteroj, raportoj, dokumentoj kaj TTT-pa&#285;oj per Verkilo.
Comment[es]=Cree y edite texto y gráficos en cartas, informes, documentos y páginas Web con Writer.
Comment[et]=Writer võimaldab luua ja redigeerida kirjade, aruannete, dokumentide ning veebilehtede teksti ja pilte.
Comment[eu]=Testua eta grafikoak sortu eta editatu gutunetan, txostenetan, dokumentuetan eta web orrietan Writer erabiliz.
Comment[fa]=&#1576;&#1575; &#1575;&#1587;&#1578;&#1601;&#1575;&#1583;&#1607; &#1575;&#1586; &#1705;&#1575;&#1578;&#1576;&#1548; &#1605;&#1578;&#1606; &#1608; &#1711;&#1585;&#1575;&#1601;&#1740;&#1705; &#1606;&#1575;&#1605;&#1607;*&#1607;&#1575;&#1548; &#1711;&#1586;&#1575;&#1585;&#1588;*&#1607;&#1575;&#1548; &#1606;&#1608;&#1588;&#1578;&#1575;&#1585;&#1607;&#1575; &#1608; &#1589;&#1601;&#1581;&#1575;&#1578; &#1608;&#1576; &#1585;&#1575; &#1575;&#1740;&#1580;&#1575;&#1583; &#1740;&#1575; &#1608;&#1740;&#1585;&#1575;&#1740;&#1588; &#1705;&#1606;&#1740;&#1583;.
Comment[fi]=Luo ja muokkaa tekstiä ja grafiikkaa kirjeisiin, raportteihin, tekstiasiakirjoihin ja internet-sivuihin Writer-ohjelmalla.
Comment[fr]=Writer - Création et édition de textes et d'images pour courriers, rapports, documents et pages Web.
Comment[ga]=Cruthaigh téacs agus grafaicí i litreacha, tuairiscí, cáipéisí, agus leathanaigh Ghréasáin le Writer.
Comment[gl]=Crear e editar texto ou imaxes en cartas, informes, documentos e páxinas web usando Writer.
Comment[gu]=&#2738;&#2710;&#2750;&#2723; &#2726;&#2765;&#2726;&#2750;&#2736;&#2750; &#2730;&#2724;&#2765;&#2736;&#2763;, &#2693;&#2745;&#2759;&#2741;&#2750;&#2738;&#2763;, &#2726;&#2744;&#2765;&#2724;&#2750;&#2741;&#2759;&#2716;&#2763; &#2693;&#2728;&#2759; &#2741;&#2759;&#2732; &#2730;&#2750;&#2728;&#2750;&#2707;&#2734;&#2750;&#2690; &#2738;&#2710;&#2750;&#2723; &#2693;&#2728;&#2759; &#2714;&#2751;&#2724;&#2765;&#2736;&#2763; &#2732;&#2728;&#2750;&#2741;&#2763; &#2693;&#2728;&#2759; &#2744;&#2753;&#2712;&#2750;&#2736;&#2763;.
Comment[he]=&#1497;&#1510;&#1497;&#1512;&#1492; &#1493;&#1506;&#1512;&#1497;&#1499;&#1492; &#1513;&#1500; &#1496;&#1511;&#1505;&#1496; &#1493;&#1490;&#1512;&#1508;&#1497;&#1511;&#1492; &#1489;&#1502;&#1499;&#1514;&#1489;&#1497;&#1501;, &#1491;&#1493;&#1495;&#1493;&#1514;, &#1502;&#1505;&#1502;&#1499;&#1497;&#1501; &#1493;&#1491;&#1508;&#1497; &#1488;&#1497;&#1504;&#1496;&#1512;&#1504;&#1496; &#1489;&#1488;&#1502;&#1510;&#1506;&#1493;&#1514; Writer.
Comment[hi]=&#2354;&#2375;&#2326;&#2325; &#2325;&#2375; &#2346;&#2381;&#2352;&#2351;&#2379;&#2327; &#2360;&#2375; &#2346;&#2340;&#2381;&#2352;, &#2352;&#2367;&#2346;&#2379;&#2352;&#2381;&#2335;, &#2342;&#2360;&#2381;&#2340;&#2366;&#2357;&#2375;&#2332;&#2364; &#2350;&#2375;&#2306; &#2346;&#2366;&#2336; &#2324;&#2352; &#2310;&#2352;&#2375;&#2326; &#2348;&#2344;&#2366;&#2340;&#2366; &#2361;&#2376; &#2324;&#2352; &#2360;&#2306;&#2346;&#2366;&#2342;&#2367;&#2340; &#2325;&#2352;&#2340;&#2366; &#2361;&#2376;.
Comment[hr]=Stvorite i uredite tekst i slike u pisma, izvje&#353;&#263;ima, dokumentima i web stranicama.
Comment[hu]=Levelek, jelentések, dokumentumok és weboldalak szövegének és grafikájának létrehozása és szerkesztése a Writer használatával.
Comment[id]=Mengolah teks dan gambar pada surat, laporan, dokumen, dan halaman Web menggunakan Writer.
Comment[is]=Búa til og breyta texta og myndefni í bréfum, skýrslum, skjölum og vefsíðum með því að nota Writer.
Comment[it]=Usando Writer, potete creare e modificare il testo e le immagini di lettere, rapporti, documenti e pagine Web.
Comment[ja]=Writer &#12434;&#20351;&#29992;&#12375;&#12390;&#12289;&#12524;&#12479;&#12540;&#12289;&#12524;&#12509;&#12540;&#12488;&#12289;&#12489;&#12461;&#12517;&#12513;&#12531;&#12488;&#12362;&#12424;&#12403; Web &#12506;&#12540;&#12472;&#12398;&#12486;&#12461;&#12473;&#12488;&#12362;&#12424;&#12403;&#22259;&#12434;&#20316;&#25104;&#12362;&#12424;&#12403;&#32232;&#38598;&#12375;&#12414;&#12377;&#12290;
Comment[ka]=&#4325;&#4315;&#4316;&#4312;&#4321; &#4307;&#4304; &#4304;&#4321;&#4332;&#4317;&#4320;&#4308;&#4305;&#4321; &#4307;&#4317;&#4313;&#4323;&#4315;&#4308;&#4316;&#4322;&#4308;&#4305;&#4321;&#4304; &#4307;&#4304; &#4307;&#4312;&#4304;&#4306;&#4320;&#4304;&#4315;&#4308;&#4305;&#4321; &#4332;&#4308;&#4320;&#4312;&#4314;&#4308;&#4305;&#4328;&#4312;, &#4315;&#4317;&#4334;&#4321;&#4308;&#4316;&#4308;&#4305;&#4308;&#4305;&#4328;&#4312;, &#4307;&#4317;&#4313;&#4323;&#4315;&#4308;&#4316;&#4322;&#4308;&#4305;&#4328;&#4312; &#4307;&#4304; &#4309;&#4308;&#4305;-&#4306;&#4309;&#4308;&#4320;&#4307;&#4308;&#4305;&#4328;&#4312; Writer-&#4312;&#4321; &#4315;&#4308;&#4328;&#4309;&#4308;&#4317;&#4305;&#4312;&#4311;.
Comment[km]=&#6036;&#6020;&#6098;&#6016;&#6078;&#6031; &#6035;&#6071;&#6020;&#8203;&#6016;&#6082;&#8203;&#6047;&#6040;&#6098;&#6042;&#6077;&#6043;&#8203;&#6050;&#6031;&#6098;&#6032;&#6036;&#6033; &#6035;&#6071;&#6020;&#8203;&#6016;&#6098;&#6042;&#6070;&#6048;&#6098;&#6044;&#6071;&#6016;&#8203;&#6016;&#6098;&#6035;&#6075;&#6020;&#8203;&#6047;&#6086;&#6036;&#6075;&#6031;&#6098;&#6042; &#6042;&#6036;&#6070;&#6041;&#6016;&#6070;&#6042;&#6030;&#6093; &#6063;&#6016;&#6047;&#6070;&#6042; &#6035;&#6071;&#6020;&#8203;&#6033;&#6086;&#6038;&#6096;&#6042;&#8203;&#6036;&#6030;&#6098;&#6031;&#6070;&#6025;&#8203;&#6026;&#6084;&#6041;&#8203;&#6036;&#6098;&#6042;&#6078; Writer &#6100;
Comment[ko]=Writer&#47484; &#49324;&#50857;&#54616;&#50668; &#54200;&#51648;, &#48372;&#44256;&#49436;, &#47928;&#49436; &#48143; &#50937; &#54168;&#51060;&#51648;&#50640;&#49436; &#53581;&#49828;&#53944;&#50752; &#44536;&#47548;&#51012; &#47564;&#46308;&#44256; &#54200;&#51665;&#54624; &#49688; &#51080;&#49845;&#45768;&#45796;.
Comment[ku]=Nivîs û grafîkên di name, rapor, belge û rûpelên torê de bî Writerê çêbike û sererast bike.
Comment[lt]=Tekst&#371; rengykle galima kurti lai&#353;kus, ataskaitas, kitus dokumentus ir tinklalapius, &#303;terpti &#303; juos paveikslus.
Comment[lv]=Veidot un redi&#291;&#275;t tekstu un grafisku v&#275;stul&#275;s, atskait&#275;s, dokumentos un t&#299;mek&#316;a lap&#257;s, lietojot Writer.
Comment[mk]=&#1050;&#1088;&#1077;&#1080;&#1088;&#1072;&#1112;&#1090;&#1077; &#1080; &#1091;&#1088;&#1077;&#1076;&#1091;&#1074;&#1072;&#1112;&#1090;&#1077; &#1090;&#1077;&#1082;&#1089;&#1090; &#1080; &#1075;&#1088;&#1072;&#1092;&#1080;&#1082;&#1072; &#1074;&#1086; &#1087;&#1080;&#1089;&#1084;&#1072;, &#1080;&#1079;&#1074;&#1077;&#1096;&#1090;&#1072;&#1080;, &#1076;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1080; &#1080; &#1074;&#1077;&#1073;-&#1089;&#1090;&#1088;&#1072;&#1085;&#1080;&#1094;&#1080; &#1089;&#1086; &#1082;&#1086;&#1088;&#1080;&#1089;&#1090;&#1077;&#1114;&#1077; &#1085;&#1072; Writer.
Comment[ml]=&#3377;&#3400;&#3377;&#3405;&#3377;&#3376;&#3405; &#3337;&#3370;&#3375;&#3403;&#3351;&#3391;&#3354;&#3405;&#3354;&#3405;  &#3349;&#3364;&#3405;&#3364;&#3393;&#3349;&#3379;&#3391;&#3378;&#3398;&#3375;&#3393;&#3330; &#3377;&#3391;&#3370;&#3405;&#3370;&#3403;&#3376;&#3405;&#3359;&#3405;&#3359;&#3393;&#3349;&#3379;&#3391;&#3378;&#3398;&#3375;&#3393;&#3330; &#3361;&#3403;&#3349;&#3405;&#3349;&#3393;&#3374;&#3398;&#3368;&#3405;&#3377;&#3391;&#3378;&#3398;&#3375;&#3393;&#3330; &#3381;&#3398;&#3372;&#3405; &#3370;&#3399;&#3356;&#3391;&#3378;&#3398;&#3375;&#3393;&#3330;  &#3359;&#3398;&#3349;&#3405;&#3384;&#3405;&#3377;&#3405;&#3377;&#3393;&#3330; &#3351;&#3405;&#3376;&#3390;&#3371;&#3391;&#3349;&#3405;&#3384;&#3393;&#3330; &#3384;&#3395;&#3383;&#3405;&#3359;&#3391;&#3349;&#3405;&#3349;&#3393;&#3349;&#3375;&#3393;&#3330; &#3342;&#3361;&#3391;&#3377;&#3405;&#3377;&#3393; &#3354;&#3398;&#3375;&#3405;&#3375;&#3393;&#3349;&#3375;&#3393;&#3330; &#3354;&#3398;&#3375;&#3405;&#3375;&#3393;&#3349;.
Comment[mn]=Writer &#1072;&#1096;&#1080;&#1075;&#1083;&#1072;&#1085; &#1079;&#1072;&#1093;&#1080;&#1072;, &#1090;&#1072;&#1081;&#1083;&#1072;&#1085;, &#1073;&#1072;&#1088;&#1080;&#1084;&#1090; &#1076;&#1072;&#1093;&#1100; &#1073;&#1080;&#1095;&#1074;&#1101;&#1088; &#1073;&#1072; &#1075;&#1088;&#1072;&#1092;&#1080;&#1082; &#1199;&#1199;&#1089;&#1075;&#1101;&#1093; &#1073;&#1086;&#1083;&#1086;&#1085; &#1079;&#1072;&#1089;&#1074;&#1072;&#1088;&#1083;&#1072;&#1093;.
Comment[mr]=Writer &#2330;&#2366; &#2357;&#2366;&#2346;&#2352;&#2370;&#2344; &#2346;&#2340;&#2381;&#2352;&#2306;, &#2309;&#2361;&#2357;&#2366;&#2354;, &#2342;&#2360;&#2381;&#2340;&#2320;&#2357;&#2332; &#2357; &#2357;&#2375;&#2348; &#2346;&#2366;&#2344; &#2309;&#2306;&#2340;&#2352;&#2381;&#2327;&#2340; &#2346;&#2366;&#2336;&#2381;&#2351; &#2357; &#2330;&#2367;&#2340;&#2381;&#2352;&#2354;&#2375;&#2326; &#2348;&#2344;&#2357;&#2366; &#2357; &#2360;&#2306;&#2346;&#2366;&#2342;&#2368;&#2340; &#2325;&#2352;&#2366;.
Comment[nb]=Opprett og rediger tekst og bilder i brev, rapporter, dokumenter og nettsider ved å bruke Writer.
Comment[ne]=&#2354;&#2375;&#2326;&#2325;&#2325;&#2379; &#2346;&#2381;&#2352;&#2351;&#2379;&#2327;&#2342;&#2381;&#2357;&#2366;&#2352;&#2366; &#2330;&#2367;&#2336;&#2381;&#2336;&#2368;&#2361;&#2352;&#2370;, &#2346;&#2381;&#2352;&#2340;&#2367;&#2357;&#2375;&#2342;&#2344;&#2361;&#2352;&#2370;, &#2325;&#2366;&#2327;&#2332;&#2366;&#2340;&#2361;&#2352;&#2370; &#2352; &#2357;&#2375;&#2348; &#2346;&#2371;&#2359;&#2381;&#2336;&#2361;&#2352;&#2370;&#2350;&#2366; &#2346;&#2366;&#2336; &#2340;&#2341;&#2366; &#2327;&#2381;&#2352;&#2366;&#2347;&#2367;&#2325;&#2381;&#2360; &#2360;&#2367;&#2352;&#2381;&#2332;&#2344;&#2366; &#2340;&#2341;&#2366; &#2360;&#2350;&#2381;&#2346;&#2366;&#2342;&#2344; &#2327;&#2352;&#2381;&#2344;&#2369;&#2361;&#2379;&#2360;&#2381; &#2404;
Comment[nl]=Met Writer kunt u tekst en afbeeldingen in brieven, rapporten, documenten en webpagina's maken en bewerken.
Comment[nn]=Med Writer kan du laga og redigera tekst og bilete i brev, rapportar, dokument og nettsider.
Comment[nr]=Enza nokuhlela itheksti neentjengiso eziseencwadini, emibikweni, emitlolweni nemakhasini weWebh ngokusebenzisa i-Writer.
Comment[nso]=Hlama le go loki&#353;a sengwalwa le dikrafiki mangwalong, dipegong, ditokumenteng le matlakaleng a wepe ka go diri&#353;a Writer.
Comment[oc]=Writer - Creacion e edicion de tèxtes e d'imatges per corrièrs, rapòrts, documents e paginas Web.
Comment[om]=Bareessaa fayyadamuun xalayaalee, gabasota, galmeewwanii fi fuulota saphaphuu irratti barruu fi saxxatoo uumi, gulaali.
Comment[or]=&#2864;&#2878;&#2823;&#2847;&#2864; &#2825;&#2858;&#2911;&#2891;&#2839; &#2837;&#2864;&#2879; &#2858;&#2852;&#2893;&#2864;&#2839;&#2881;&#2849;&#2879;&#2837;&#2864;&#2887;, &#2864;&#2879;&#2858;&#2891;&#2864;&#2893;&#2847;&#2864;&#2887;,&#2854;&#2866;&#2879;&#2866;&#2839;&#2881;&#2849;&#2879;&#2837;&#2864;&#2887; &#2831;&#2860;&#2818; &#2825;&#2831;&#2860;&#2893; &#2858;&#2883;&#2871;&#2893;&#2848;&#2878;&#2839;&#2881;&#2849;&#2879;&#2837;&#2864;&#2887; &#2847;&#2887;&#2837;&#2893;&#2872;&#2847; &#2831;&#2860;&#2818; &#2866;&#2887;&#2838;&#2878;&#2842;&#2879;&#2852;&#2893;&#2864;&#2839;&#2881;&#2849;&#2879;&#2837;&#2881; &#2872;&#2883;&#2871;&#2893;&#2847;&#2879; &#2831;&#2860;&#2818; &#2872;&#2862;&#2893;&#2858;&#2878;&#2854;&#2856; &#2837;&#2864;&#2856;&#2893;&#2852;&#2881;&#2404;
Comment[pa_IN]=&#2608;&#2622;&#2567;&#2591;&#2608; &#2600;&#2622;&#2610; &#2602;&#2673;&#2596;&#2608;&#2622;&#2562;, &#2608;&#2623;&#2602;&#2635;&#2608;&#2591;&#2622;&#2562;, &#2593;&#2636;&#2581;&#2626;&#2606;&#2632;&#2562;&#2591;&#2622;&#2562; &#2565;&#2596;&#2631; &#2613;&#2632;&#2673;&#2604; &#2616;&#2603;&#2620;&#2623;&#2566;&#2562; &#2613;&#2623;&#2673;&#2586; &#2591;&#2632;&#2581;&#2616;&#2591; &#2565;&#2596;&#2631; &#2586;&#2623;&#2673;&#2596;&#2608; &#2604;&#2595;&#2622;&#2575; &#2565;&#2596;&#2631; &#2616;&#2635;&#2599;&#2631; &#2588;&#2622; &#2616;&#2581;&#2598;&#2631; &#2617;&#2600;&#2404;
Comment[pl]=Twórz i edytuj listy, raporty, dokumenty i strony www wykorzystuj&#261;c program Writer.
Comment[pt]=Criar e editar texto e objetos gráficos em cartas, relatórios, documentos e páginas web através do Writer.
Comment[pt_BR]=Crie e edite textos e figuras em cartas, relatórios, documentos e páginas da Web por meio do Writer.
Comment[qtz]=seqx&#8214;Create and edit text and graphics in letters, reports, documents and Web pages by using Writer.
Comment[ro]=Crea&#539;i &#537;i edita&#539;i text &#537;i grafic&#259; în scrisori, rapoarte, documente &#537;i pagini web folosind Writer.
Comment[ru]=&#1057;&#1086;&#1079;&#1076;&#1072;&#1085;&#1080;&#1077; &#1080; &#1088;&#1077;&#1076;&#1072;&#1082;&#1090;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085;&#1080;&#1077; &#1090;&#1077;&#1082;&#1089;&#1090;&#1072; &#1080; &#1088;&#1080;&#1089;&#1091;&#1085;&#1082;&#1086;&#1074; &#1074; &#1087;&#1080;&#1089;&#1100;&#1084;&#1072;&#1093;, &#1086;&#1090;&#1095;&#1105;&#1090;&#1072;&#1093;, &#1076;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1072;&#1093; &#1080;&#1083;&#1080; &#1074;&#1077;&#1073;-&#1089;&#1090;&#1088;&#1072;&#1085;&#1080;&#1094;&#1072;&#1093;.
Comment[rw]=Kurema no guhindura umwandiko n'ibishushanyo mu mabaruwa, raporo, inyandiko na paji Rubuga ukoresheje Writer.
Comment[si]=Writer &#3511;&#3535;&#3520;&#3538;&#3501;&#3535; &#3482;&#3515;&#3512;&#3538;&#3505;&#3530; &#3517;&#3538;&#3508;&#3538; &#3520;&#3517; &#3508;&#3545;&#3525; &#3523;&#3524; &#3488;&#3538;&#3501;&#3530;*&#3515;&#3482;, &#3520;&#3535;&#3515;&#3530;&#3501;&#3535;, &#3517;&#3538;&#3508;&#3538; &#3523;&#3524; &#3520;&#3538;&#3514;&#3540;&#3499;&#3540; &#3508;&#3538;&#3495;&#3540; &#3523;&#3535;&#3503;&#3505;&#3530;&#3505; &#3523;&#3524; &#3520;&#3545;&#3505;&#3523;&#3530; &#3482;&#3515;&#3505;&#3530;&#3505;.
Comment[sk]=Vytvárajte a upravujte textové a grafické listy, správy, dokumenty a webové stránky s pou&#382;itím Writer.
Comment[sl]=S programom Writer ustvarjajte in urejajte besedilo in slike v pismih, poro&#269;ilih, dokumentih in spletnih straneh.
Comment[sr]=&#1055;&#1080;&#1096;&#1080;&#1090;&#1077; &#1080; &#1091;&#1088;&#1077;&#1106;&#1091;&#1112;&#1090;&#1077; &#1090;&#1077;&#1082;&#1089;&#1090; &#1080; &#1075;&#1088;&#1072;&#1092;&#1080;&#1082;&#1091; &#1091; &#1087;&#1080;&#1089;&#1084;&#1080;&#1084;&#1072;, &#1080;&#1079;&#1074;&#1077;&#1096;&#1090;&#1072;&#1112;&#1080;&#1084;&#1072; &#1080; &#1074;&#1077;&#1073; &#1089;&#1090;&#1088;&#1072;&#1085;&#1080;&#1094;&#1072;&#1084;&#1072; &#1091; &#1055;&#1080;&#1089;&#1094;&#1091;.
Comment[ss]=Yakha u-edithe umbhalo nemagrafiki etincwadzini, umbiko, wemadokhumenti nemapheji eWebhu ngekusebentisa Writer.
Comment[st]=Bopa le ho lokisa mongolo le ditshwantsho mangolong, ditlalehong, ditokomaneng le maqepheng a Wepe ka ho sebedisa Writer.
Comment[sv]=Skapa och redigera text och grafik i brev, rapporter, dokument och webbsidor med hjälp av Writer.
Comment[ta]=&#2965;&#2975;&#3007;&#2980;&#2969;&#3021;&#2965;&#2995;&#3021;, &#2949;&#2993;&#3007;&#2965;&#3021;&#2965;&#3016;&#2965;&#2995;&#3021;, &#2950;&#2997;&#2979;&#2969;&#3021;&#2965;&#2995;&#3021;, &#2997;&#2994;&#3016;&#2986;&#3021;&#2986;&#2965;&#3021;&#2965;&#2969;&#3021;&#2965;&#2995;&#3021; &#2950;&#2965;&#3007;&#2991;&#2997;&#2993;&#3021;&#2993;&#3007;&#2985;&#3021; &#2953;&#2992;&#3016;, &#2986;&#2975;&#2969;&#3021;&#2965;&#2995;&#3021; &#2951;&#2997;&#2993;&#3021;&#2993;&#3016; &#2953;&#2992;&#3009;&#2997;&#3006;&#2965;&#3021;&#2965;&#2997;&#3009;&#2990;&#3021; &#2980;&#3018;&#2965;&#3009;&#2965;&#3021;&#2965;&#2997;&#3009;&#2990;&#3021; &#2992;&#3016;&#2975;&#3021;&#2975;&#2992;&#3016;&#2986;&#3021; &#2986;&#2991;&#2985;&#3021;&#2986;&#2975;&#3009;&#2980;&#3021;&#2980;&#3009;&#2965;.
Comment[te]=&#3114;&#3108;&#3149;&#3120;&#3118;&#3137; &#3118;&#3120;&#3135;&#3119;&#3137; &#3122;&#3143;&#3094; &#3119;&#3146;&#3093;&#3149;&#3093; &#3098;&#3135;&#3108;&#3149;&#3120;&#3120;&#3138;&#3114;&#3118;&#3137;&#3122;&#3137;,&#3112;&#3135;&#3125;&#3143;&#3110;&#3112;&#3122;&#3137;,&#3114;&#3108;&#3149;&#3120;&#3118;&#3137;&#3122;&#3137; &#3118;&#3120;&#3135;&#3119;&#3137; &#3125;&#3149;&#3120;&#3134;&#3119;&#3137; &#3119;&#3074;&#3108;&#3149;&#3120;&#3118;&#3137;&#3112;&#3137; &#3081;&#3114;&#3119;&#3147;&#3095;&#3135;&#3074;&#3098;&#3135;&#3112; &#3125;&#3142;&#3116;&#3149;  &#3114;&#3137;&#3103;&#3122;&#3137;&#3112;&#3137; &#3112;&#3135;&#3120;&#3149;&#3118;&#3135;&#3074;&#3098;&#3135; &#3128;&#3120;&#3135;&#3098;&#3143;&#3119;&#3137;&#3118;&#3137;. 
Comment[tg]=&#1041;&#1086; &#1105;&#1088;&#1080;&#1080; Writer &#1084;&#1072;&#1090;&#1085; &#1074;&#1072; &#1090;&#1072;&#1089;&#1074;&#1080;&#1088; &#1089;&#1086;&#1093;&#1090;&#1072;&#1085;, &#1086;&#1085;&#1203;&#1086;&#1088;&#1086; &#1080;&#1089;&#1083;&#1086;&#1203; &#1082;&#1072;&#1088;&#1076;&#1072;&#1085; &#1084;&#1091;&#1084;&#1082;&#1080;&#1085; &#1072;&#1089;&#1090;.
Comment[th]=&#3626;&#3619;&#3657;&#3634;&#3591;&#3649;&#3621;&#3632;&#3649;&#3585;&#3657;&#3652;&#3586;&#3586;&#3657;&#3629;&#3588;&#3623;&#3634;&#3617;&#3649;&#3621;&#3632;&#3585;&#3619;&#3634;&#3615;&#3636;&#3585;&#3626;&#3660;&#3651;&#3609;&#3592;&#3604;&#3627;&#3617;&#3634;&#3618; &#3619;&#3634;&#3618;&#3591;&#3634;&#3609; &#3648;&#3629;&#3585;&#3626;&#3634;&#3619; &#3649;&#3621;&#3632;&#3627;&#3609;&#3657;&#3634;&#3648;&#3623;&#3655;&#3610;&#3650;&#3604;&#3618;&#3585;&#3634;&#3619;&#3651;&#3594;&#3657; Writer
Comment[tn]=Create and edit text and graphics in letters, reports, documents and Web pages by using Writer.
Comment[tr]=Writer kullanarak mektuplardaki metin ve grafikleri, rapor, belge ve Web sayfalar&#305; olu&#351;turabilir ve düzenleyebilirsiniz.
Comment[ts]=Cinca ni ku lulamisa marito ni vudirowi eka mapapila, swiviko, tidokumente ni tipheji ta Web hi ku tirhisa Writer.
Comment[ug]=Writer &#1574;&#1609;&#1588;&#1604;&#1609;&#1578;&#1609;&#1662; &#1582;&#1749;&#1578;-&#1670;&#1749;&#1603;&#1548; &#1583;&#1608;&#1603;&#1604;&#1575;&#1578; &#1580;&#1749;&#1583;&#1739;&#1609;&#1604;&#1609;&#1548; &#1662;&#1736;&#1578;&#1736;&#1603; &#1739;&#1749; &#1578;&#1608;&#1585; &#1576;&#1749;&#1578;&#1578;&#1609;&#1603;&#1609; &#1578;&#1744;&#1603;&#1587;&#1578; &#1739;&#1749; &#1711;&#1585;&#1575;&#1601;&#1609;&#1603;&#1604;&#1575;&#1585;&#1606;&#1609; &#1602;&#1735;&#1585;&#1735;&#1662; &#1578;&#1749;&#1726;&#1585;&#1609;&#1585;&#1604;&#1609;&#1711;&#1609;&#1604;&#1609; &#1576;&#1608;&#1604;&#1609;&#1583;&#1735;.
Comment[uk]=&#1057;&#1090;&#1074;&#1086;&#1088;&#1077;&#1085;&#1085;&#1103; &#1090;&#1072; &#1088;&#1077;&#1076;&#1072;&#1075;&#1091;&#1074;&#1072;&#1085;&#1085;&#1103; &#1090;&#1077;&#1082;&#1089;&#1090;&#1091; &#1090;&#1072; &#1075;&#1088;&#1072;&#1092;&#1110;&#1082;&#1080; &#1091; &#1083;&#1080;&#1089;&#1090;&#1072;&#1093;, &#1079;&#1074;&#1110;&#1090;&#1072;&#1093;, &#1076;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1072;&#1093; &#1090;&#1072; &#1074;&#1077;&#1073;-&#1089;&#1090;&#1086;&#1088;&#1110;&#1085;&#1082;&#1072;&#1093;.
Comment[uz]=Writer yordamida hisobotlar, matn hujjatlari, veb sahifalar yaratish va tahrirlash.
Comment[ve]=Vhumbani ni dovhe ni lulamise &#7741;i&#7749;walwa na dzigirafiki kha ma&#7749;walo, mivhigo, ma&#7749;walo na masia&#7793;ari a Web nga u shumisa Writer.
Comment[vi]=T&#7841;o và s&#7917;a v&#259;n b&#7843;n và &#273;&#7891; h&#7885;a trong lá th&#432;, báo cáo, tài li&#7879;u và trang Web b&#7857;ng Writer.
Comment[xh]=Dala uze uhlele isiqendu nezazobe zegrafu ezileteni, iingxelo, amaxwebhu namakhasi Othungelwano ngokusebenzisa i-Writer.
Comment[zh_CN]=&#20351;&#29992; Writer &#21019;&#24314;&#24182;&#32534;&#36753;&#20449;&#20989;&#12289;&#25253;&#34920;&#12289;&#25991;&#26723;&#21644;&#32593;&#39029;&#20013;&#30340;&#25991;&#26412;&#21644;&#22270;&#24418;&#12290;
Comment[zh_TW]=&#20351;&#29992; Writer &#21487;&#20197;&#22312;&#20449;&#20214;&#12289;&#22577;&#21578;&#12289;&#25991;&#20214;&#21644;&#32178;&#38913;&#20013;&#24314;&#31435;&#33287;&#32232;&#36655;&#25991;&#23383;&#21644;&#22294;&#24418;&#12290;
Comment[zu]=Yenza futhi ulungise umbhalo nemidwebo esezinhlamvini zamagama, emibikweni, emafayelini nasemakhasini eWebhu ngokusebenzisa i-Writer.
InitialPreference=5
X-Ayatana-Desktop-Shortcuts=New
[New Shortcut Group]
Name=New Document
Name[en]=New Document
Name[ast]=Documentu nuevu
Name[ca]=Document nou
Name[da]=Nyt dokument
Name[de]=Neues Dokument
Name[es]=Documento nuevo
Name[el]=&#925;&#941;&#959; &#941;&#947;&#947;&#961;&#945;&#966;&#959;
Name[fi]=Uusi tekstiasiakirja
Name[fr]=Nouveau document
Name[gl]=Novo documento
Name[he]=&#1502;&#1505;&#1502;&#1498; &#1495;&#1491;&#1513;
Name[hr]=Novi dokument
Name[hu]=Új dokumentum
Name[it]=Nuovo documento
Name[is]=Nýtt textaskjal
Name[ja]=&#26032;&#35215;&#25991;&#26360;&#12434;&#20316;&#25104;
Name[ku]=Belgeya nû
Name[nl]=Nieuw Document
Name[pt_BR]=Novo documento
Name[ro]=Document nou
Name[ru]=&#1053;&#1086;&#1074;&#1099;&#1081; &#1076;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;
Name[sl]=Nov dokument
Name[te]=&#3093;&#3146;&#3108;&#3149;&#3108; &#3114;&#3108;&#3149;&#3120;&#3074;
Name[vi]=Tài li&#7879;u m&#7899;i
Name[zh_CN]=&#26032;&#24314;&#25991;&#26723;
Name[zh_TW]=&#26032;&#22686;&#25991;&#20214;
Exec=libreoffice --writer %U
TargetEnvironment=Unity

```You'll need to start a root nautilus window. Press Alt-F2 and type:

```
gksu nautilus
```and then navigate to File System -> usr -> share -> applications

and drag and drop it in, most likely replacing the old LO one. 

I hope this fixes it, but it's a long shot. You might be best off making a [bug report ]("https://bugs.launchpad.net/unity/+filebug")against Unity.

Thanks.  Pls consider that I have no experience with terminal.
If  you think I have a LibreOffice bug, could I download  LO  again?

---

### Post by arno48 on 2012-08-04
[COLOR=#000000][FONT=Verdana][SIZE=2]*The situation has changed.*[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana][SIZE=2]*Now the LibreOffice Writer's icon is steady in the Launcher (I locked it).*[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana][SIZE=2]*The strange thing is that when I am working some Writer files the little triangle appears beside the icon, and I can return to the Writer files from a different application just clicking on the icon.*[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana][SIZE=2]*On the contrary, when I am working different Writer files no triangle appears beside the icon and clicking on the icon does not work.*[/SIZE][/FONT][/COLOR]
 


 


 [COLOR=#000000][FONT=Verdana][SIZE=2]*Couldn't I have caused such a problem by checking a menu command erroneously? *[/SIZE][/FONT][/COLOR]

---

### Post by MG&amp;TL on 2012-08-04
> **arno48 said:**
> [COLOR=#000000][FONT=Verdana][SIZE=2]*The situation has changed.*[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana][SIZE=2]*Now the LibreOffice Writer's icon is steady in the Launcher (I locked it).*[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana][SIZE=2]*The strange thing is that when I am working some Writer files the little triangle appears beside the icon, and I can return to the Writer files from a different application just clicking on the icon.*[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana][SIZE=2]*On the contrary, when I am working different Writer files no triangle appears beside the icon and clicking on the icon does not work.*[/SIZE][/FONT][/COLOR]
 


 


 [COLOR=#000000][FONT=Verdana][SIZE=2]*Couldn't I have caused such a problem by checking a menu command erroneously? *[/SIZE][/FONT][/COLOR]

No...but if it helps, there's various ways to switch windows. Super-W is one, as is Alt-Tab.

Sorry, but I've no idea why it's doing that.

---

### Post by arno48 on 2012-08-04
> **MG&TL said:**
> No...but if it helps, there's various ways to switch windows. Super-W is one, as is Alt-Tab.

Sorry, but I've no idea why it's doing that.

Thanks, I took note of the other ways.
Actually it is a strange behavior. Also considering that all LO Calc files work correctly, at least so far.
What do you think about to download LO Writer again?

---

### Post by MG&amp;TL on 2012-08-04
> **arno48 said:**
> Thanks, I took note of the other ways.
Actually it is a strange behavior. Also considering that all LO Calc files work correctly, at least so far.
What do you think about to download LO Writer again?

You could try.

```
sudo apt-get purge libreoffice-writer
sudo apt-get install libreoffice-writer
```

---

### Post by arno48 on 2012-08-04
> **MG&TL said:**
> You could try.

```
sudo apt-get purge libreoffice-writer
sudo apt-get install libreoffice-writer
```
Could I download LOWriter from LibreOffice site?
As you see I am awfully afraid of terminal?

---

### Post by MG&amp;TL on 2012-08-04
> **arno48 said:**
> Could I download LOWriter from LibreOffice site?
As you see I am awfully afraid of terminal?


You could. But it would be far easier to use Ubuntu's system. 

My apologies, you can use graphical tools if you prefer. Open the software centre, remove Writer, then install it again, log out and see the change (if any).

---

### Post by arno48 on 2012-08-04
> **MG&TL said:**
> You could. But it would be far easier to use Ubuntu's system. 

My apologies, you can use graphical tools if you prefer. Open the software centre, remove Writer, then install it again, log out and see the change (if any).
 
I did. Through Software Centre I removed and Installed Again Writer. Shut down.
The Writer icon is steady in the Launcher, but now no Writer file shows the triangle and therefore the icon does not recall it when different applications are running.
I can use the other ways you suggested.

Thank you for your assistance, it has been a real pleasure to have met a kind person like you are.

---

### Post by MG&amp;TL on 2012-08-04
> **arno48 said:**
> I did. Through Software Centre I removed and Installed Again Writer. Shut down.
The Writer icon is steady in the Launcher, but now no Writer file shows the triangle and therefore the icon does not recall it when different applications are running.
I can use the other ways you suggested.

Thank you for your assistance, it has been a real pleasure to have met a kind person like you are.

The terminal method will remove configuration files as well as the program, that might do it. You never know. 

This is the good thing about open-source software, someone will likely fix it if we can track down why.

Not a problem, I try my best. :)

---

### Post by arno48 on 2012-08-04
> **MG&TL said:**
> The terminal method will remove configuration files as well as the program, that might do it. You never know. 

This is the good thing about open-source software, someone will likely fix it if we can track down why.

Not a problem, I try my best. :)
OK.
You say I have to use terminal
I say I don't want to use commands I don't know.
The solution is that I have to learn terminal commands.
This is what I want to do in the next days, then I shall be able to execute the command lines you suggested in previous post.
I'll keep you informed about the results.
Thank you a lot.

---

### Post by MG&amp;TL on 2012-08-04
> **arno48 said:**
> OK.
You say I have to use terminal
I say I don't want to use commands I don't know.
The solution is that I have to learn terminal commands.
This is what I want to do in the next days, then I shall be able to execute the command lines you suggested in previous post.
I'll keep you informed about the results.
Thank you a lot.

I'm not saying you have to use the terminal. It's just something to try. I have absolutely no idea what's going on (my LO works fine)...so I'm just going through things it might be.

The only reason I'm giving commands is that they're guaranteed to work (or you have a very serious problem), and they cut out a layer of other things to go wrong. Also, for nerds like me, it's easier than saying 'click that button, then flick that switch, type this in the box, search for that...'. 

If you're worried about me giving malicious commands (and that's sensible), I can explain each part.

If you wanted an alternative to those commands, you can install an alternative (more technical) software manager called *synaptic package manager* from the software centre. From there, search for LibreOffice, then mark the *libreoffice-writer* package for 'complete removal', then apply the changes, then search for it again and mark for installation. **Be very careful with synaptic. Unlike the software centre, it BITES. **It does warn you, but it will bite.

---

### Post by arno48 on 2012-08-05
> **MG&TL said:**
> I'm not saying you have to use the terminal. It's just something to try. I have absolutely no idea what's going on (my LO works fine)...so I'm just going through things it might be.

The only reason I'm giving commands is that they're guaranteed to work (or you have a very serious problem), and they cut out a layer of other things to go wrong. Also, for nerds like me, it's easier than saying 'click that button, then flick that switch, type this in the box, search for that...'. 

If you're worried about me giving malicious commands (and that's sensible), I can explain each part.

If you wanted an alternative to those commands, you can install an alternative (more technical) software manager called *synaptic package manager* from the software centre. From there, search for LibreOffice, then mark the *libreoffice-writer* package for 'complete removal', then apply the changes, then search for it again and mark for installation. **Be very careful with synaptic. Unlike the software centre, it BITES. **It does warn you, but it will bite.
  	 	 	 	 	 	   [COLOR=#000000][FONT=Verdana][SIZE=2][I]
[/I][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][SIZE=2]*Good Sunday,*[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana][SIZE=2]*Never thought about malicious people browsing in order to destroy my PC.*[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana][SIZE=2]*But I do not enjoy doing things I do not understand. *[/SIZE][/FONT][/COLOR] 
 [COLOR=#000000][FONT=Verdana][SIZE=2]*I am sure that it is the same for you.*[/SIZE][/FONT][/COLOR]
 


 [COLOR=#000000][FONT=Verdana][SIZE=2]*Through Terminal I removed Writer*[/SIZE][/FONT][/COLOR]
 ```
[COLOR=#000000]*[FONT=Verdana][SIZE=2]sudo apt-get purge libreoffice-writer[/SIZE][/FONT]*[/COLOR]
```[COLOR=#000000][/COLOR]  [COLOR=#000000][FONT=Verdana][SIZE=2]*then installed it again.*[/SIZE][/FONT][/COLOR]  [COLOR=#000000][FONT=Verdana][SIZE=2][I]Now I have two Writer icons in the Launcher, the new one working well (with triangles and able to recall open files), 
the old one able to open Writer with Untitled  files (but neither showing triangles nor recalling open files).[/I][/SIZE][/FONT][/COLOR]  [COLOR=#000000][FONT=Verdana][SIZE=2]*Not. Update. Also the new icon stopped showing triangles.*[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana][SIZE=2]*Luckily your trick to show all open files (Super+W) is very useful.*[/SIZE][/FONT][/COLOR]

---

### Post by MG&amp;TL on 2012-08-05
> Good Sunday,
Never thought about malicious people browsing in order to destroy my PC.
But I do not enjoy doing things I do not understand. 
I am sure that it is the same for you.

You too. :) It's not something that happens on this forum (at least, I haven't seen any, and this forum is fairly well-policed with experienced members.) but it is worth checking what a command should do before running it. In this case, a quick google for 'apt-get purge' brought up this page: [https://help.ubuntu.com/community/AptGet/Howto/]("https://help.ubuntu.com/community/AptGet/Howto/") which explains that it complete removes a package.

You are quite right, and you should always check commands, or at least give them a google.  

> Through Terminal I removed Writer
Code:
sudo apt-get purge libreoffice-writer
then installed it again. Now I have two Writer icons in the Launcher, the new one working well (with triangles and able to recall open files), 
the old one able to open Writer with Untitled files (but neither showing triangles nor recalling open files). Not. Update. Also the new icon stopped showing triangles. Luckily your trick to show all open files (Super+W) is very useful.


Feel like a nerd yet? You should...:D

Quick question-have you logged out and/or rebooted since then? Unity sometimes needs a logout to rebuild its application cache. 

That's the only thing I can think of, sorry. Other than that you could:

-get very good at Alt-Tab or Super-W. This might be the easiest way, but I can see it being irritating.

-try Unity2D, see if it works for you. It doesn't look as pretty, but if it works for you, it might be worthwhile. Click the Ubuntu logo next to your name on the login screen, and select "Ubuntu 2D". Then login as normal.

-try a different desktop environment altogether. You've got a huge         variety of choices in Ubuntu, but the ones I recommend are KDE (intensive but very pretty, Kubuntu comes with this by default), Xfce (more lightweight, menu-driven. Xubuntu comes with this by default), and LXDE (very lightweight, Lubuntu comes with this by default). 

-use an alternative word processor. Not exactly desirable, but if you prefer to use Word or OpenOffice.org, or any other one, I don't see it having the same problem.

-survive for now, report a bug at the link I gave, and it should get fixed. The Ubuntu bug-reporting system dictates that you'll get e-mail updates on your bug's progress through triage (assessing the importance of the bug-obviously, developers want to look at bugs that stop a program from running before new features or interface redesigns.) and bugfix. (a developer fixes the bug in the 'raw' software, publishes an update for supported Ubuntu systems, and puts it in by default for the next release). 

Hope this helps you come to a decision, I'm sorry I can't tell you why it's doing this.

---

### Post by arno48 on 2012-08-05
> **MG&TL said:**
> 
Quick question-have you logged out and/or rebooted since then? 
                                  [COLOR=#000000][FONT=Verdana][SIZE=2]*Yes. You're quite right. *[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana][SIZE=2]*I had forgotten to log out.*[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana][SIZE=2]*Now icon seems to work.*[/SIZE][/FONT][/COLOR]  [COLOR=#000000][FONT=Verdana][SIZE=2]*By the way, *[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana][SIZE=2]*by Ctrl+Alt+T     I opened Terminal*[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana][SIZE=2]*by  Ctrl- Alt-F1    I opened PROMPT*[/SIZE][/FONT][/COLOR]  [COLOR=#000000][FONT=Verdana][SIZE=2]*are Terminal and PROMPT the same thing?*[/SIZE][/FONT][/COLOR]

---

### Post by MG&amp;TL on 2012-08-05
> **arno48 said:**
> [COLOR=#000000][FONT=Verdana][SIZE=2]*Yes. You're quite right. *[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana][SIZE=2]*I had forgotten to log out.*[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana][SIZE=2]*Now icon seems to work.*[/SIZE][/FONT][/COLOR]  [COLOR=#000000][FONT=Verdana][SIZE=2]*By the way, *[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana][SIZE=2]*by Ctrl+Alt+T     I opened Terminal*[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana][SIZE=2]*by  Ctrl- Alt-F1    I opened PROMPT*[/SIZE][/FONT][/COLOR]  [COLOR=#000000][FONT=Verdana][SIZE=2]*are Terminal and PROMPT the same thing?*[/SIZE][/FONT][/COLOR]

Great! Don't know what happened to create that problem...glad you got it sorted.


The *terminals* (Ctrl-Alt-[F1-F6]) are not the same as* gnome-terminal *(whose shortcut is Ctrl-Alt-T), which is a terminal emulator. Terminal emulators were invented so you didn't have to switch out of your graphical environment to run a command. Hope that answers your question.

The prompt on the other hand is just the default indication of an idle terminal. By default on Ubuntu, it looks a little like this:

```
user@computer-name:/path/to/current/directory$
```

---

### Post by arno48 on 2012-08-06
> **MG&TL said:**
> 


The *terminals* (Ctrl-Alt-[F1-F6]) are not the same as* gnome-terminal *(whose shortcut is Ctrl-Alt-T), which is a terminal emulator. Terminal emulators were invented so you didn't have to switch out of your graphical environment to run a command. Hope that answers your question.

The prompt on the other hand is just the default indication of an idle terminal.
                                  
[COLOR=#000000][FONT=Verdana][SIZE=2]*Due to my poor English I am not quite sure to have understood.*[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana][SIZE=2]*Is the following correct?*[/SIZE][/FONT][/COLOR]
 
[LIST=1]
[*][COLOR=#000000][FONT=Verdana][SIZE=2]*CTRL-Alt-T     is the shortcut to Ubuntu terminal;*[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Verdana][SIZE=2]*CTRL-Alt-F1     is the shortcut to a terminal external to Ubuntu, in fact login and     password are requested.*[/SIZE][/FONT][/COLOR]
[/LIST]
  > 
    
By default on Ubuntu, it looks a little like this:

```
user@computer-name:/path/to/current/directory$
```It looks like a Etruscan Language.
Have a nice week.

---

### Post by MG&amp;TL on 2012-08-06
> **arno48 said:**
> [COLOR=#000000][FONT=Verdana][SIZE=2]*Due to my poor English I am not quite sure to have understood.*[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana][SIZE=2]*Is the following correct?*[/SIZE][/FONT][/COLOR]
 
[LIST=1]
[*][COLOR=#000000][FONT=Verdana][SIZE=2]*CTRL-Alt-T     is the shortcut to Ubuntu terminal;*[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Verdana][SIZE=2]*CTRL-Alt-F1     is the shortcut to a terminal external to Ubuntu, in fact login and     password are requested.*[/SIZE][/FONT][/COLOR]
[/LIST]
  It looks like a Etruscan Language.
Have a nice week.

Not especially. I'm not really sure what your native language is (your English is very good, btw), but there are many localised forums on here that you may get more specific help if you're struggling to understand my explanation. Does this thread: [http://ubuntuforums.org/showthread.php?t=602991](http://ubuntuforums.org/showthread.php?t=602991) help at all?

:lol: yup, it does a bit. You too.

---

### Post by arno48 on 2012-08-06
> **MG&TL said:**
> Not especially. I'm not really sure what your native language is (your English is very good, btw), but there are many localised forums on here that you may get more specific help if you're struggling to understand my explanation. Does this thread: [http://ubuntuforums.org/showthread.php?t=602991](http://ubuntuforums.org/showthread.php?t=602991) help at all?

:lol: yup, it does a bit. You too.

Yes, it helps. Thanks for all.
My wife wants me to the seaside for a few weeks and I have no internet connession there.
Have nice days you too.

---

