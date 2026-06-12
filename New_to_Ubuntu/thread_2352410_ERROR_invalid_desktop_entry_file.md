---
title: "ERROR: invalid desktop entry file"
date: 2017-02-12
forum: New to Ubuntu
---

### Post by jeferris on 2017-02-12
Hello
I'm attempting to use linux, and I've experimented with installing lubuntu.
I have supported windows - multiple flavours - and have a reasonable level of experience with operating systems.
But truthfully, I'm a new linux user.

A google search found some similar issues to mine, but none have given an answer that solved this error.
My error happens when I attempt to start the 'Samba' icon from the "System tools" listing in my lubuntu basic desktop LXpanel.

Basic Info:
hardware - all basic stuff, about 8 years old - Intel 64-bit quad-core with 4-gig Ram, 500-gig HDD
OS  - lubuntu from Feb 2017 v16.10 Desktop 64-bit
package - samba via Synaptic Package Manager with all required dependencies from 'Main' in Canada / USA = all as per default
issue - when select icon via - LXpanel 0.8.2 to "System tools" to icon "Samba" get error result as below

ERROR:
invalid desktop entry file: '/usr/share/applications/system-config-samba.desktop'

what I've done to try to fix:
via Synaptic Package Manager - checked Status = no Broken packages listed
via SPM - looked thru list of Installed. found and reinstalled = Samba and Samba-related packages
via Command Prompt - 'sudo apt-get update' && 'sudo apt-get -f install'

google search result:
[http://askubuntu.com/questions/118749/package-system-is-broken-how-to-fix-it](http://askubuntu.com/questions/118749/package-system-is-broken-how-to-fix-it)
[https://ubuntuforums.org/showthread.php?t=1305656](https://ubuntuforums.org/showthread.php?t=1305656)
[http://unix.stackexchange.com/questions/66555/why-are-my-application-desktop-files-not-showing-up-in-linux-application-menu](http://unix.stackexchange.com/questions/66555/why-are-my-application-desktop-files-not-showing-up-in-linux-application-menu)

All no effect, no change.

I can find no info about what the actual error is. Nor can I find the file as listed in the error, even remembering to make all system / hidden files visible.

Any suggestions?

---

### Post by &amp;KyT$0P# on 2017-02-12
> **jeferris said:**
> ERROR:
invalid desktop entry file: '/usr/share/applications/system-config-samba.desktop'
Can you please post the full contents of that file?

> Nor can I find the file as listed in the error, even remembering to make all system / hidden files visible.
So, to answer my question, please open a Terminal and post the output from running these commands -
```
ls -la /usr/share/applications/system-config-samba.desktop
cat /usr/share/applications/system-config-samba.desktop
```

---

### Post by jeferris on 2017-02-13
as requested, and thanks for the clear instructions....

```
jeferris@Clear-Rampage:~$ ls -la /usr/share/applications/system-config-samba.desktop
-rw-r--r-- 1 root root 5815 Jan 26  2014 /usr/share/applications/system-config-samba.desktop
```
```
jeferris@Clear-Rampage:~$ cat /usr/share/applications/system-config-samba.desktop
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Samba
Name[ar]=&#1587;&#1575;&#1605;&#1576;&#1575;
Name[as]=Samba
Name[bg]=Samba
Name[bn]=&#2488;&#2494;&#2478;&#2509;&#2476;&#2494;
Name[bn_IN]=Samba
Name[bs]=Samba
Name[ca]=Samba
Name[cs]=Samba
Name[cy]=Samba
Name[da]=Samba
Name[de]=Samba
Name[el]=Samba
Name[en_GB]=Samba
Name[es]=Samba
Name[et]=Samba
Name[fi]=Samba
Name[fr]=Samba
Name[gu]=&#2744;&#2750;&#2734;&#2765;&#2732;&#2750;
Name[he]=&#1505;&#1502;&#1489;&#1492;
Name[hi]=&#2360;&#2366;&#2306;&#2348;&#2366;
Name[hr]=Samba
Name[hu]=Samba
Name[id]=Samba
Name[is]=Samba
Name[it]=Samba
Name[ja]=Samba
Name[kn]=&#3256;&#3262;&#3202;&#3244;&#3262;
Name[ko]=Samba
Name[lv]=Samba
Name[mk]=&#1057;&#1072;&#1084;&#1073;&#1072;
Name[ml]=&#3384;&#3390;&#3374;&#3405;&#3370;&#3390;
Name[mr]=Samba
Name[ms]=Samba
Name[nb]=Samba
Name[nl]=Samba
Name[or]=&#2870;&#2878;&#2862;&#2893;&#2860;&#2878;
Name[pa]=&#2616;&#2622;&#2562;&#2604;&#2622;
Name[pl]=Samba
Name[pt]=Samba
Name[pt_BR]=Samba
Name[ro]=Samba
Name[ru]=Samba
Name[si]=&#3523;&#3512;&#3530;&#3510;&#3535;
Name[sk]=Samba
Name[sl]=Samba
Name[sr]=&#1057;&#1072;&#1084;&#1073;&#1072;
Name[sr@latin]=Samba
Name[sv]=Samba
Name[ta]=&#2970;&#2990;&#3021;&#2986;&#3006;
Name[te]=&#3128;&#3134;&#3074;&#3116;
Name[tr]=Samba
Name[uk]=Samba
Name[vi]=Samba
Name[zh_CN]=Samba
Name[zh_TW]=Samba
Comment=Create, modify, and delete samba shares
Comment[ar]=&#1573;&#1606;&#1588;&#1575;&#1569;&#1548; &#1578;&#1593;&#1583;&#1617;&#1610;&#1604; &#1608;&#1581;&#1584;&#1601; &#1605;&#1580;&#1604;&#1583;&#1575;&#1578; &#1587;&#1575;&#1605;&#1576;&#1575; &#1575;&#1604;&#1605;&#1615;&#1588;&#1578;&#1585;&#1603;&#1577;
Comment[as]=samba &#2437;&#2434;&#2486;&#2544; &#2488;&#2499;&#2487;&#2509;&#2463;&#2495;, &#2488;&#2494;&#2482;-&#2488;&#2482;&#2472;&#2495; &#2453;&#2544;&#2453; &#2476;&#2494; &#2438;&#2433;&#2468;&#2433;&#2468;&#2544;&#2494; &#2470;&#2495;&#2527;&#2453;&#2439; 
Comment[bg]=&#1057;&#1098;&#1079;&#1076;&#1072;&#1074;&#1072;&#1085;&#1077;, &#1088;&#1077;&#1076;&#1072;&#1082;&#1090;&#1080;&#1088;&#1072;&#1085;&#1077; &#1080; &#1087;&#1088;&#1077;&#1084;&#1072;&#1093;&#1074;&#1072;&#1085;&#1077; &#1085;&#1072; samba &#1089;&#1087;&#1086;&#1076;&#1077;&#1083;&#1077;&#1085;&#1080; &#1088;&#1077;&#1089;&#1091;&#1088;&#1089;&#1080;
Comment[bn]=&#2488;&#2494;&#2478;&#2509;&#2476;&#2494;&#2480; &#2486;&#2503;&#2527;&#2494;&#2480; &#2468;&#2504;&#2480;&#2495; &#2453;&#2480;&#2497;&#2472;, &#2474;&#2480;&#2495;&#2476;&#2480;&#2509;&#2468;&#2472; &#2453;&#2480;&#2497;&#2472; &#2447;&#2476;&#2434; &#2478;&#2497;&#2459;&#2503; &#2475;&#2503;&#2482;&#2497;&#2472;
Comment[bn_IN]=Samba &#2486;&#2503;&#2527;&#2494;&#2480; &#2472;&#2495;&#2480;&#2509;&#2478;&#2494;&#2467;, &#2474;&#2480;&#2495;&#2476;&#2480;&#2509;&#2468;&#2472; &#2447;&#2476;&#2434; &#2437;&#2474;&#2488;&#2494;&#2480;&#2467; &#2474;&#2470;&#2509;&#2471;&#2468;&#2495;
Comment[bs]=Izrada, izmjena ili brisanje Samba dijeljenih mapa
Comment[ca]=Crea, modifica, i esborra compartits samba
Comment[cs]=Vytvo&#345;it, upravit nebo smazat sdílení samba
Comment[cy]=Creu, addasu, a dileu rhaniadau samba
Comment[da]=Opret, ændr og fjern samba-delinger
Comment[de]=Samba Shares anlegen, ändern und löschen
Comment[el]=&#916;&#951;&#956;&#953;&#959;&#965;&#961;&#947;&#943;&#945;,  &#956;&#949;&#964;&#945;&#964;&#961;&#959;&#960;&#942;,  &#954;&#945;&#953; &#948;&#953;&#945;&#947;&#961;&#945;&#966;&#942; &#954;&#959;&#953;&#957;&#974;&#957; &#960;&#972;&#961;&#969;&#957; samba
Comment[en_GB]=Create, modify, and delete samba shares
Comment[es]=Crear, modificar y borrar recursos compartidos samba
Comment[et]=Loo, muuda ja kustuta samba jagamisi
Comment[fi]=Luo, muokkaa ja poista samba-jakoja
Comment[fr]=Créer, modifier et supprimer les partages samba
Comment[gu]=&#2744;&#2750;&#2734;&#2765;&#2732;&#2750; &#2742;&#2759;&#2736;&#2763; &#2732;&#2728;&#2750;&#2741;&#2763;, &#2744;&#2753;&#2727;&#2750;&#2736;&#2763; &#2693;&#2728;&#2759; &#2709;&#2750;&#2722;&#2752; &#2728;&#2750;&#2690;&#2710;&#2763;
Comment[he]=&#1510;&#1493;&#1512;, &#1513;&#1504;&#1492;, &#1493;&#1502;&#1495;&#1511; &#1513;&#1497;&#1514;&#1493;&#1508;&#1497; &#1505;&#1502;&#1489;&#1492;
Comment[hi]=&#2360;&#2366;&#2306;&#2348;&#2366; &#2360;&#2366;&#2333;&#2366; &#2348;&#2344;&#2366;&#2319;&#2305;, &#2360;&#2306;&#2358;&#2379;&#2343;&#2367;&#2340;, &#2324;&#2352; &#2357;&#2367;&#2354;&#2379;&#2346;&#2367;&#2340; &#2325;&#2352;&#2375;&#2306;
Comment[hr]=Izrada, izmjena ili brisanje Samba dijeljenih mapa
Comment[hu]=Megosztások létrehozása, módosítása, törlése
Comment[id]=Buat, modifikasi, dan hapus samba shares
Comment[is]=Búa til, breyta eða eyða samba netdrifum
Comment[it]=Creare, modificare e rimuovere condivisioni di samba
Comment[ja]=samba &#20849;&#26377;&#12398;&#20316;&#25104;&#12289;&#22793;&#26356;&#21450;&#12403;&#21066;&#38500;
Comment[kn]=&#3256;&#3262;&#3202;&#3244;&#3262; &#3257;&#3202;&#3226;&#3263;&#3221;&#3270;&#3223;&#3251;&#3240;&#3277;&#3240;&#3265; &#3256;&#3267;&#3255;&#3277;&#3231;&#3263;&#3256;&#3265;, &#3244;&#3238;&#3250;&#3262;&#3247;&#3263;&#3256;&#3265; &#3257;&#3262;&#3223;&#3265; &#3205;&#3251;&#3263;&#3256;&#3265;
Comment[ko]=samba &#44277;&#50976;&#47484; &#49373;&#49457;, &#49688;&#51221;&#54616;&#44256; &#49325;&#51228;&#54616;&#44592;
Comment[lv]=Izveidot, modific&#275;t un dz&#275;st Samba koplietojumus
Comment[mk]=&#1050;&#1088;&#1077;&#1080;&#1088;&#1072;&#1112;, &#1091;&#1088;&#1077;&#1076;&#1080; &#1080; &#1086;&#1090;&#1089;&#1090;&#1088;&#1072;&#1085;&#1080; &#1089;&#1072;&#1084;&#1073;&#1072; &#1076;&#1077;&#1083;&#1077;&#1114;&#1072;
Comment[ml]=samba &#3383;&#3398;&#3375;&#3377;&#3393;&#3349;&#3379;&#3405;* &#3337;&#3363;&#3405;&#3359;&#3390;&#3349;&#3405;&#3349;&#3393;&#3381;&#3390;&#3368;&#3393;&#3330; &#3374;&#3390;&#3377;&#3405;&#3377;&#3330; &#3381;&#3376;&#3393;&#3364;&#3405;&#3364;&#3393;&#3381;&#3390;&#3368;&#3393;&#3330; &#3368;&#3392;&#3349;&#3405;&#3349;&#3330; &#3354;&#3398;&#3375;&#3405;&#3375;&#3393;&#3381;&#3390;&#3368;&#3393;&#3330; &#3384;&#3385;&#3390;&#3375;&#3391;&#3349;&#3405;&#3349;&#3393;&#3368;&#3405;&#3368;&#3393;
Comment[mr]=samba &#2349;&#2366;&#2327; &#2344;&#2367;&#2352;&#2381;&#2350;&#2366;&#2339;, &#2348;&#2342;&#2354;, &#2310;&#2339;&#2367; &#2344;&#2359;&#2381;&#2335; &#2325;&#2352;&#2366;
Comment[ms]=Cipta, ubahsuai, dan padam pengkongsian samba
Comment[nb]=Opprett, endre og slett samba-ressurser
Comment[nl]=Aanmaken, wijzigen en verwijderen van Samba gedeelde bronnen
Comment[or]=&#2870;&#2878;&#2862;&#2893;&#2860;&#2878; &#2864; &#2872;&#2873;&#2861;&#2878;&#2839; &#2862;&#2878;&#2856;&#2841;&#2893;&#2837;&#2881; &#2872;&#2893;&#2864;&#2881;&#2871;&#2893;&#2847;&#2879; &#2837;&#2864;, &#2864;&#2882;&#2858;&#2878;&#2856;&#2893;&#2852;&#2864; &#2837;&#2864;, &#2831;&#2860;&#2818; &#2821;&#2858;&#2872;&#2878;&#2864;&#2851; &#2837;&#2864;
Comment[pa]=&#2616;&#2622;&#2562;&#2604;&#2622; &#2614;&#2631;&#2565;&#2608; &#2604;&#2595;&#2622;&#2579;, &#2616;&#2635;&#2599;&#2635; &#2565;&#2596;&#2631; &#2617;&#2591;&#2622;&#2579;
Comment[pl]=Tworzenie, modyfikowanie i usuwanie udzia&#322;ów Samby
Comment[pt]=Criar, modificar e apagar partilhas samba
Comment[pt_BR]=Criar, modificar e apagar compartilhamentos do samba
Comment[ro]=Creeaz&#259;, modific&#259; &#351;i &#351;terge partaj&#259;ri samba
Comment[ru]=&#1057;&#1086;&#1079;&#1076;&#1072;&#1085;&#1080;&#1077;, &#1080;&#1079;&#1084;&#1077;&#1085;&#1077;&#1085;&#1080;&#1077; &#1080; &#1091;&#1076;&#1072;&#1083;&#1077;&#1085;&#1080;&#1077; &#1088;&#1077;&#1089;&#1091;&#1088;&#1089;&#1086;&#1074; samba
Comment[si]=&#3523;&#3512;&#3530;&#3510;&#3535; &#3524;&#3520;&#3540;&#3517;&#3530; &#3523;&#3535;&#3503;&#3505;&#3530;&#3505;, &#3523;&#3458;&#3521;&#3549;&#3504;&#3505;&#3514; &#3482;&#3515;&#3505;&#3530;&#3505; &#3505;&#3536;&#3501;&#3524;&#3548;&#3501;&#3530; &#3512;&#3482;&#3535;&#3503;&#3512;&#3505;&#3530;&#3505;
Comment[sk]=Vytvori&#357;, upravi&#357; alebo odstráni&#357; samba zdie&#318;ania
Comment[sl]=Izdela, spremeni in izbri&#353;e skupne diske SMB
Comment[sr]=&#1053;&#1072;&#1087;&#1088;&#1072;&#1074;&#1080;, &#1080;&#1079;&#1084;&#1077;&#1085;&#1080;, &#1080; &#1086;&#1073;&#1088;&#1080;&#1096;&#1080; &#1057;&#1072;&#1084;&#1073;&#1072; &#1076;&#1077;&#1113;&#1077;&#1085;&#1077; &#1088;&#1077;&#1089;&#1091;&#1088;&#1089;&#1077;
Comment[sr@latin]=Napravi, izmeni, i obri&#353;i Samba deljene resurse
Comment[sv]=Skapa, ändra och ta bort sambautdelningar
Comment[ta]=&#2970;&#2990;&#3021;&#2986;&#3006; &#2986;&#2965;&#3007;&#2992;&#3021;&#2997;&#3009;&#2965;&#2995;&#3016; &#2953;&#2992;&#3009;&#2997;&#3006;&#2965;&#3021;&#2965;&#2997;&#3009;&#2990;&#3021;, &#2980;&#3007;&#2992;&#3009;&#2980;&#3021;&#2980;&#2997;&#3009;&#2990;&#3021;, &#2949;&#2996;&#3007;&#2965;&#3021;&#2965;&#2997;&#3009;&#2990;&#3021;
Comment[te]=&#3128;&#3134;&#3074;&#3116;&#3134; &#3117;&#3134;&#3095;&#3134;&#3122;&#3112;&#3137; &#3128;&#3139;&#3127;&#3149;&#3103;&#3135;&#3074;&#3098;&#3137;, &#3118;&#3134;&#3120;&#3149;&#3098;&#3137;, &#3118;&#3120;&#3135;&#3119;&#3138; &#3108;&#3146;&#3122;&#3095;&#3135;&#3074;&#3098;&#3137;
Comment[tr]=Samba payla&#351;&#305;mlar&#305;n&#305; olu&#351;turur, de&#287;i&#351;tirir ve siler
Comment[uk]=&#1057;&#1090;&#1074;&#1086;&#1088;&#1077;&#1085;&#1085;&#1103;, &#1079;&#1084;&#1110;&#1085;&#1072; &#1095;&#1080; &#1074;&#1080;&#1076;&#1072;&#1083;&#1077;&#1085;&#1085;&#1103; &#1088;&#1077;&#1089;&#1091;&#1088;&#1089;&#1110;&#1074; Samba
Comment[vi]=T&#7841;o, hi&#7879;u ch&#7881;nh, và xóa Chia s&#7867; Samba
Comment[zh_CN]=&#21019;&#24314;&#12289;&#20462;&#25913;&#21644;&#21024;&#38500; samba &#20849;&#20139;
Comment[zh_TW]=&#24314;&#31435;&#12289;&#20462;&#25913;&#33287;&#21034;&#38500; Samba &#20849;&#20139;
Categories=System;Settings;
Icon=system-config-samba
Exec=gksu system-config-samba
Type=Application
StartupNotify=true
Terminal=false
jeferris@Clear-Rampage:~$
```

---

### Post by &amp;KyT$0P# on 2017-02-13
Can you try removing the [FONT=Courier New]Version=[/FONT] and [FONT=Courier New]Encoding=[/FONT] lines?

Lubuntu uses Leafpad as the main text editor, right?  Use this Terminal command to edit the file -
```
sudo -H leafpad /usr/share/applications/system-config-samba.desktop
```

---

### Post by jeferris on 2017-02-14
Completed edit = remove Version= and Encoding= lines. No change to performance of Samba icon.

---

### Post by Perfect Storm on 2017-02-14
What if you make a new entry instead.

---

### Post by deadflowr on 2017-02-14
Perhaps the desktop-file-validate command may shed some light
```
desktop-file-validate /path/to/desktop/file
```

---

### Post by daffodils on 2017-03-19
It might be different for you but I have this problem because gksu is not installed by default.  You can check with ```
which gksu
``` If that command doesn't return anything then the line "Exec=gksu system-config-samba" is your problem.

I don't know what to do about it though. I tried using pkexec instead but get "permission denied".  Installing gksu is probably an option but it looks like it was removed deliberately years ago? Everything I see about it is old.

in the meantime I'm just using a terminal to ```
sudo -H system-config-samba
```

---

### Post by Cka3o4nik on 2017-08-16
I solved the same problem in Linux Mint 18 by running Exec value in terminal, which told me I have to install lxsession-logout, 'cause it wasn't installed on my system

---

### Post by Oby on 2017-09-12
I faced the exact same issue as described in the first post, and solved it by simply installing gksu and creating a blank config file:
```
sudo apt install gksu
sudo touch /etc/libuser.conf
```

---

### Post by Gireesh_Sadasivan on 2018-02-02
> **Oby said:**
> I faced the exact same issue as described in the first post, and solved it by simply installing gksu and creating a blank config file:
```
sudo apt install gksu
sudo touch /etc/libuser.conf
```


The above steps worked well for me. Samba UI came up. Lubuntu 17.10

---

### Post by chrzk on 2018-04-17
Thanks @Oby

That is all I needed to do.
From my point of view, I would like your reply to be upvoted to the top.

NB I initially missed the touch, and when I started System Tools-Samba, I was promted for my password, which I entered, but the screen just flickered, and nothing was shown.
 Another post suggested using command line
**gksu system-config-samba**
which returned
*SystemError: could not open configuration file `/etc/libuser.conf': No such file or directory*
being the reason for the touch you rightly instructed.

Further information; prior to the installing gksu, I had only used Synaptic Package Manager to install Samba + System-Config-Samba (with dependancies)

---

