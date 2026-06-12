---
title: "Creating a launcher?"
date: 2008-03-30
forum: Programming Talk
---

### Post by Godofgrunts on 2008-03-30
Okay, I'm new to Ubuntu and programming in Ubuntu. I've been asked to write a program to download and run [Folding at Home]("http://folding.stanford.edu/"). I'm sure some of you have heard of it.

That was easy.

Now I've been asked to make the script create a desktop launcher, but I'm lost on how to do this...

Here is the code for the script if you need it.

> 
[COLOR="Blue"]#A quick installer for F@H
#Only tested in *buntu, DSL, Debian, and OCNix[/COLOR]

[COLOR="Blue"]#sudo apt-get update
#Updates[/COLOR]

cd /home/$USER/Desktop/
[COLOR="Blue"]#Redirects to the Desktop[/COLOR]

mkdir -p folding
[COLOR="Blue"]#Creates a folder called "folding" on the Desktop[/COLOR]

cd ./folding
[COLOR="Blue"]#Redirects to the newly created "folding" folder.[/COLOR]

wget [http://www.stanford.edu/group/pandegroup/folding/release/FAH6.02beta1-Linux.tgz](http://www.stanford.edu/group/pandegroup/folding/release/FAH6.02beta1-Linux.tgz)
[COLOR="Blue"]#Downloads the F@H client (64-bit linux version).[/COLOR]

tar -zxvf FAH6.02beta1-Linux.tgz
[COLOR="Blue"]#Unpacks the tar.[/COLOR]

chmod +u+x fah6 mpiexec
[COLOR="Blue"]#Allows for modification of the file and makes executable.[/COLOR]

./fah6 -smp
[COLOR="Blue"]#Runs the program.[/COLOR]

The name of the script is called
> FAH-64bit.sh

Somewhere in there I need it to automatically create a launcher and put it on the desktop...

Please help.

---

### Post by slavik on 2008-03-31
dump from gnome-terminal launcher :)

```

slavik@slavik-desktop:~/Desktop$ cat gnome-terminal.desktop 
[Desktop Entry]
Encoding=UTF-8
Name=Terminal
Name[am]=&#4720;&#4653;&#4634;&#4755;&#4621;
Name[ar]=&#1591;&#1585;&#1601;&#1610;&#1577;
Name[as]=&#2463;&#2494;&#2544;&#2509;&#2478;&#2495;&#2472;&#2494;&#2482;
Name[az]=Terminal
Name[be]=&#1058;&#1101;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;
Name[be@latin]=Termina&#322;
Name[bg]=&#1058;&#1077;&#1088;&#1084;&#1080;&#1085;&#1072;&#1083;
Name[bn]=&#2463;&#2494;&#2480;&#2509;&#2478;&#2495;&#2472;&#2494;&#2482;
Name[bn_IN]=&#2463;&#2494;&#2480;&#2509;&#2478;&#2495;&#2472;&#2494;&#2482;
Name[bs]=Terminal
Name[ca]=Terminal
Name[cs]=Terminál
Name[cy]=Terfynell
Name[da]=Terminal
Name[de]=Terminal
Name[dz]=&#3914;&#3938;&#3851;&#3928;&#3954;&#3851;&#3923;&#3953;&#3939;&#3851;&#3853;
Name[el]=&#932;&#949;&#961;&#956;&#945;&#964;&#953;&#954;&#972;
Name[en_CA]=Terminal
Name[en_GB]=Terminal
Name[es]=Terminal
Name[et]=Terminal
Name[eu]=Terminala
Name[fa]=&#1662;&#1575;&#1740;&#1575;&#1606;&#1607;
Name[fi]=Pääte
Name[fr]=Terminal
Name[fur]=Terminâl
Name[ga]=Teirminéal
Name[gl]=Terminal
Name[gu]=&#2719;&#2736;&#2765;&#2734;&#2751;&#2728;&#2738;
Name[he]=&#1502;&#1505;&#1493;&#1507;
Name[hi]=&#2335;&#2352;&#2381;&#2350;&#2367;&#2344;&#2354;
Name[hr]=Terminal
Name[hu]=Terminál
Name[hy]=&#1359;&#1381;&#1408;&#1396;&#1387;&#1398;&#1377;&#1388;
Name[id]=Terminal
Name[it]=Terminale
Name[ja]=&#31471;&#26411;
Name[ka]=&#4322;&#4308;&#4320;&#4315;&#4312;&#4316;&#4304;&#4314;&#4312;
Name[ko]=&#53552;&#48120;&#45328;
Name[ku]=Termînal
Name[lt]=Terminalas
Name[lv]=Termin&#257;lis
Name[mg]=Terminal
Name[mk]=&#1058;&#1077;&#1088;&#1084;&#1080;&#1085;&#1072;&#1083;
Name[ml]=&#3359;&#3398;&#3376;&#3405;*&#3374;&#3391;&#3368;&#3378;&#3405;*
Name[mn]=&#1058;&#1077;&#1088;&#1084;&#1080;&#1085;&#1072;&#1083;
Name[mr]=&#2335;&#2352;&#2381;&#2350;&#2367;&#2344;&#2354;
Name[ms]=Terminal
Name[nb]=Terminal
Name[ne]=&#2335;&#2352;&#2381;&#2350;&#2367;&#2344;&#2354;
Name[nl]=Terminalvenster
Name[nn]=Terminal
Name[oc]=Terminal
Name[or]=&#2847;&#2864;&#2893;&#2862;&#2879;&#2856;&#2878;&#2866;
Name[pa]=&#2591;&#2608;&#2606;&#2624;&#2600;&#2610;
Name[pl]=Terminal
Name[pt]=Consola
Name[pt_BR]=Terminal
Name[ro]=Terminal
Name[ru]=&#1058;&#1077;&#1088;&#1084;&#1080;&#1085;&#1072;&#1083;
Name[si]=&#3461;&#3484;&#3530;*&#3515;&#3514;
Name[sk]=Terminál
Name[sl]=Terminal
Name[sq]=Terminali
Name[sr]=&#1058;&#1077;&#1088;&#1084;&#1080;&#1085;&#1072;&#1083;
Name[sr@Latn]=Terminal
Name[sv]=Terminal
Name[ta]=&#2990;&#3009;&#2985;&#3016;&#2991;&#2990;&#3021;
Name[th]=&#3648;&#3607;&#3629;&#3619;&#3660;&#3617;&#3636;&#3609;&#3633;&#3621;
Name[tr]=Uçbirim
Name[uk]=&#1058;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;
Name[vi]=Thi&#7871;t b&#7883; cu&#7889;i
Name[wa]=Terminå
Name[xh]=i-Terminal
Name[zh_CN]=&#32456;&#31471;
Name[zh_HK]=&#32066;&#31471;&#27231;
Name[zh_TW]=&#32066;&#31471;&#27231;
Comment=Use the command line
Comment[ar]=&#1575;&#1587;&#1578;&#1593;&#1605;&#1604; &#1587;&#1591;&#1585;&#1575;&#1604;&#1571;&#1608;&#1575;&#1605;&#1585;
Comment[as]=&#2438;&#2470;&#2503;&#2486; &#2482;&#2494;&#2439;&#2472; &#2476;&#2509;&#2479;&#2476;&#2489;&#2494;&#2544; &#2453;&#2544;&#2497;&#2472;
Comment[be]=&#1059;&#1078;&#1099;&#1094;&#1100; &#1079;&#1072;&#1075;&#1072;&#1076;&#1085;&#1099; &#1088;&#1072;&#1076;&#1086;&#1082;
Comment[be@latin]=U&#382;yj zahadny radok
Comment[bg]=&#1048;&#1079;&#1087;&#1086;&#1083;&#1079;&#1074;&#1072;&#1085;&#1077; &#1085;&#1072; &#1082;&#1086;&#1084;&#1072;&#1085;&#1076;&#1077;&#1085; &#1088;&#1077;&#1076;
Comment[bn]=&#2453;&#2478;&#2494;&#2472;&#2509;&#2465; &#2482;&#2494;&#2439;&#2472; &#2476;&#2509;&#2479;&#2476;&#2489;&#2494;&#2480; &#2453;&#2480;&#2497;&#2472;
Comment[bn_IN]=&#2453;&#2478;&#2494;&#2472;&#2509;&#2465; &#2482;&#2494;&#2439;&#2472; &#2476;&#2509;&#2479;&#2476;&#2489;&#2494;&#2480; &#2453;&#2480;&#2497;&#2472;
Comment[ca]=Obriu la línia d'ordres
Comment[cs]=Pou&#382;ívat p&#345;íkazový &#345;ádek
Comment[cy]=Defnyddio'r llinell orchymyn
Comment[da]=Brug kommandolinjen
Comment[de]=Befehlszeile verwenden
Comment[dz]=&#3926;&#3904;&#3964;&#3921;&#3851;&#3939;&#3928;&#3851;&#3939;&#3906;&#3851;&#3939;&#3962;&#3923;&#3851;&#3936;&#3920;&#3926;&#3853;
Comment[el]=&#935;&#961;&#942;&#963;&#951; &#947;&#961;&#945;&#956;&#956;&#942;&#962; &#949;&#957;&#964;&#959;&#955;&#974;&#957;
Comment[en_CA]=Use the command line
Comment[en_GB]=Use the command line
Comment[es]=Use la línea de comandos
Comment[et]=Käsurea kasutamine
Comment[eu]=Erabili komando-lerroa
Comment[fa]=&#1575;&#1587;&#1578;&#1601;&#1575;&#1583;&#1607; &#1575;&#1586; &#1587;&#1591;&#1585; &#1601;&#1585;&#1605;&#1575;&#1606;
Comment[fi]=Käytä komentoriviä
Comment[fr]=Utiliser la ligne de commande
Comment[fur]=Dopre la rie di comant
Comment[ga]=Bain úsáid as líne na n-orduithe
Comment[gl]=Usar a liña de comandos
Comment[gu]=&#2694;&#2726;&#2759;&#2742; &#2741;&#2750;&#2709;&#2765;&#2735; &#2741;&#2750;&#2730;&#2736;&#2763;
Comment[he]=&#1492;&#1513;&#1514;&#1502;&#1513; &#1489;&#1513;&#1493;&#1512;&#1514; &#1492;&#1508;&#1511;&#1493;&#1491;&#1492;
Comment[hi]=&#2325;&#2350;&#2366;&#2306;&#2337; &#2354;&#2366;&#2311;&#2344; &#2325;&#2366; &#2346;&#2381;&#2352;&#2351;&#2379;&#2327; &#2325;&#2352;&#2375;&#2306;
Comment[hu]=Parancssor használata
Comment[id]=Pergunakan perintah baris
Comment[it]=Usa la riga di comando
Comment[ja]=&#12467;&#12510;&#12531;&#12489;&#12539;&#12521;&#12452;&#12531;&#31471;&#26411;&#12391;&#12377;
Comment[ka]=&#4305;&#4320;&#4310;&#4304;&#4316;&#4308;&#4305;&#4312;&#4321; &#4334;&#4304;&#4310;&#4312;&#4321; &#4306;&#4304;&#4315;&#4317;&#4327;&#4308;&#4316;&#4308;&#4305;&#4304;
Comment[ko]=&#47749;&#47161; &#54665;&#51012; &#49324;&#50857;&#54633;&#45768;&#45796;
Comment[ku]=Rêzika fermanan bikar bîne
Comment[lt]=Naudoti komand&#371; eilut&#281;
Comment[lv]=Izmantot komandrindu
Comment[mg]=Hampiasa ny lazam-baiko
Comment[mk]=&#1050;&#1086;&#1088;&#1080;&#1089;&#1090;&#1080; &#1112;&#1072; &#1082;&#1086;&#1084;&#1072;&#1085;&#1076;&#1085;&#1072;&#1090;&#1072; &#1083;&#1080;&#1085;&#1080;&#1112;&#1072;
Comment[ml]=&#3349;&#3374;&#3390;&#3368;&#3405;*&#3361;&#3405; &#3378;&#3400;&#3368;&#3405;* &#3337;&#3370;&#3375;&#3403;&#3351;&#3391;&#3349;&#3405;&#3349;&#3393;&#3349;
Comment[mn]=&#1058;&#1091;&#1096;&#1072;&#1072;&#1083;&#1099;&#1085; &#1084;&#1257;&#1088; &#1093;&#1101;&#1088;&#1101;&#1075;&#1083;&#1101;
Comment[mr]=&#2310;&#2342;&#2375;&#2358; &#2346;&#2306;&#2325;&#2381;&#2340;&#2368; &#2357;&#2366;&#2346;&#2352;&#2366;
Comment[nb]=Bruk kommandolinjen
Comment[ne]=&#2310;&#2342;&#2375;&#2358; &#2352;&#2375;&#2326;&#2366; &#2346;&#2381;&#2352;&#2351;&#2379;&#2327; &#2327;&#2352;&#2381;&#2344;&#2369;&#2361;&#2379;&#2360;&#2381;
Comment[nl]=Gebruik de opdrachtregel
Comment[nn]=Bruk kommandolinja
Comment[oc]=Utilizar la linha de comandas
Comment[pa]=&#2581;&#2606;&#2622;&#2562;&#2593; &#2610;&#2622;&#2567;&#2600; &#2613;&#2608;&#2596;&#2635;&#2562;
Comment[pl]=Wiersz polece&#324;
Comment[pt]=Utilizar a linha de comando
Comment[pt_BR]=Use a linha de comando
Comment[ro]=Folose&#351;te linia de comand&#259;
Comment[ru]=&#1048;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1100; &#1082;&#1086;&#1084;&#1072;&#1085;&#1076;&#1085;&#1091;&#1102; &#1089;&#1090;&#1088;&#1086;&#1082;&#1091;
Comment[sk]=Pou&#382;i&#357; príkazový riadok
Comment[sl]=Uporabi ukazno vrstico
Comment[sq]=Përdor rreshtin e komandës
Comment[sr]=&#1050;&#1086;&#1088;&#1080;&#1089;&#1090;&#1080;&#1090;&#1077; &#1083;&#1080;&#1085;&#1080;&#1112;&#1091; &#1085;&#1072;&#1088;&#1077;&#1076;&#1073;&#1080;
Comment[sr@Latn]=Koristite liniju naredbi
Comment[sv]=Använd kommandoraden
Comment[ta]=&#2965;&#2975;&#3021;&#2975;&#2995;&#3016; &#2997;&#2992;&#3007;&#2991;&#3016; &#2986;&#2991;&#2985;&#3021;&#2986;&#2975;&#3009;&#2980;&#3021;&#2980;&#3009;
Comment[th]=&#3626;&#3633;&#3656;&#3591;&#3585;&#3634;&#3619;&#3604;&#3657;&#3623;&#3618;&#3610;&#3619;&#3619;&#3607;&#3633;&#3604;&#3588;&#3635;&#3626;&#3633;&#3656;&#3591;
Comment[tr]=Komut sat&#305;r&#305;n&#305; kullan
Comment[uk]=&#1050;&#1086;&#1084;&#1072;&#1085;&#1076;&#1085;&#1080;&#1081; &#1088;&#1103;&#1076;&#1086;&#1082;
Comment[vi]=Dùng dòng l&#7879;nh
Comment[wa]=Eployî l'*roye di comande
Comment[zh_CN]=&#20351;&#29992;&#21629;&#20196;&#34892;
Comment[zh_HK]=&#20351;&#29992;&#21629;&#20196;&#21015;
Comment[zh_TW]=&#20351;&#29992;&#21629;&#20196;&#21015;
TryExec=gnome-terminal
Exec=gnome-terminal
Icon=gnome-terminal
Type=Application
X-GNOME-DocPath=gnome-terminal/index.html
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-terminal
X-GNOME-Bugzilla-Component=BugBuddyBugs
X-GNOME-Bugzilla-Version=2.22.0
Categories=GNOME;GTK;Utility;TerminalEmulator;
StartupNotify=true
X-Ubuntu-Gettext-Domain=gnome-terminal

```

---

### Post by Godofgrunts on 2008-03-31
Woah... um... Yeah I'm not sure what that code does or how to implament that into my code...

---

### Post by Lord Illidan on 2008-03-31
Most of that file is just internationalization - gnome-terminal in various languages. I suggest you read the [spec]("http://standards.freedesktop.org/desktop-entry-spec/latest/"). A .desktop file is really just a text file.

---

### Post by mssever on 2008-03-31
> **Godofgrunts said:**
> ```
 cd /home/$USER/Desktop/
```
That's not guaranteed to work on all systems for two reasons: First, the user's home dir can be anywhere. Root's is at /root, for example, and there's nothing stopping somebody from having user joe with the homedir /home/quux. So assuming it's under /home is a mistake. Instead of /home/$USER, do $HOME, which will work every time.

Second, if $USER (or $HOME once you switch) ever contains spaces or certain other characters, your script will break. Surround it in double quotes to guard against that: ```
cd "$HOME/Desktop"
```

---

### Post by Godofgrunts on 2008-04-25
Thanks a lot! I didn't think about that.

---

