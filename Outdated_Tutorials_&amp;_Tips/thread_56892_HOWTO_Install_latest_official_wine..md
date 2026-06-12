---
title: "HOWTO: Install latest official wine."
date: 2005-08-14
forum: Outdated Tutorials &amp; Tips
---

### Post by xodeus on 2005-08-14
Hi.
This guide is for all those folks that want to install Wine the easy way and Maintain for the newest version.
This is taken from [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb) WinwHQ's own guide.

At first add the Wine GPG key
```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```
Then it's time to add a source to your apt. It's done very easily by a single command

For Ubuntu Feisty (7.04):```

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list

```
For Ubuntu Edgy (6.10):```

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list -O /etc/apt/sources.list.d/winehq.list

```
For Ubuntu Dapper (6.06):```

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/dapper.list -O /etc/apt/sources.list.d/winehq.list

```
Then update your apt and install
```

sudo apt-get update
sudo apt-get install wine

```

**64-bit Users:**

Packages for the 64 bit version of Ubuntu Feisty (7.04) are now available, however for users of Debian and older Ubuntus the entries above are for i386 users only. Attempting to use these repositories with a different architecture (eg amd64), will result in 404 errors as APT will be looking for files not in the repository.

If you are using an older 64 bit distribution and would still like a working Wine package, there is a relatively easy hack that can be used to install the 32-bit package into the 64-bit distribution and have it function normally. See this page on the [Wine wiki]("http://wiki.winehq.org/UbuntuAMD64") for more details.

__________________________________________________________________________
If you want to use this version with Internet Explorer then use [Sidenet Wine Configuration Utility](http://sidenet.ddo.jp/winetips/config.html) 

For other applications you can use the guides at [Franks Corner](http://frankscorner.org/) 
___________________________________________________________________________

Update. I'm back here and have just edited it to be exactly the same as on the [WineHQ]("http://winehq.org/site/download-deb").

---

### Post by Arandomcow5 on 2005-08-14
FINNALLY A GUIDE THAT WORKS FOR ME!!!!

ive been trying for weeks to install wine with many failed attempts....
this guide seems to work (i say seems only because it allowed me to install AOE2, and its still installing. I dont know if it will run or not)

I feel really stupid now...that guide seems so simple

UPDATE: well...it completely downloaded age of empires....but now i have no clue where the exe file is....
but when it was downloaded, and it asked me if i wanted to play the game, i said "yes" and it gave me this huge error (i meen like 100-200 lines long or sumtin like that)
meh....ill try winetools

---

### Post by franziski on 2005-08-15
[QUOTE=xodeus]Hi.
You can continue using wine or installing winetools.
Winetools howto [/QUOTE]

Installing of winetools by using apt-get fails :(

```

root@ubuntu:~# apt-get install winetools
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso... Fatto
I seguenti pacchetti NUOVI (NEW) saranno installati:
  winetools
0 aggiornati, 1 installati, 0 da rimuovere e 0 non aggiornati.
È necessario prendere 382kB di archivi.
Dopo l'estrazione, verranno occupati 2758kB di spazio su disco.
ATTENZIONE: i seguenti pacchetti non possono essere autenticati!
  winetools
Install these packages without verification [y/N]? y
Err http://wine.sourceforge.net binary/ winetools 2.1.1-1
  404 Not Found
Impossibile ottenere http://wine.sourceforge.net/apt/binary/old/winetools_2.1.1-1_all.deb  404 Not Found
E: Impossibile prendere alcuni archivi, forse è meglio eseguire apt-get update o provare l'opzione --fix-missing

```

---

### Post by xodeus on 2005-08-15
[QUOTE=franziski]Installing of winetools by using apt-get fails :(

```

root@ubuntu:~# apt-get install winetools
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso... Fatto
I seguenti pacchetti NUOVI (NEW) saranno installati:
  winetools
0 aggiornati, 1 installati, 0 da rimuovere e 0 non aggiornati.
È necessario prendere 382kB di archivi.
Dopo l'estrazione, verranno occupati 2758kB di spazio su disco.
ATTENZIONE: i seguenti pacchetti non possono essere autenticati!
  winetools
Install these packages without verification [y/N]? y
Err http://wine.sourceforge.net binary/ winetools 2.1.1-1
  404 Not Found
Impossibile ottenere http://wine.sourceforge.net/apt/binary/old/winetools_2.1.1-1_all.deb  404 Not Found
E: Impossibile prendere alcuni archivi, forse è meglio eseguire apt-get update o provare l'opzione --fix-missing

```[/QUOTE]
 You didn't follow this guide here:
[http://www.ubuntuforums.org/showpost.php?p=149181&postcount=4](http://www.ubuntuforums.org/showpost.php?p=149181&postcount=4)

---

### Post by franziski on 2005-08-15
[QUOTE=xodeus]You didn't follow this guide here:
[http://www.ubuntuforums.org/showpost.php?p=149181&postcount=4](http://www.ubuntuforums.org/showpost.php?p=149181&postcount=4)[/QUOTE]

Installed but it doesn't work well (like previous version installed through apt
before adding wine repositories): click on "Base setup" but happens nothing and come back to menu; same happens with other menu entries.

---

### Post by AndyAWS on 2005-08-15
I don't think winetools works very well with the latest wine snapshot.

I used sidenet for my wine configuration.
[http://sidenet.ddo.jp/winetips/config.html](http://sidenet.ddo.jp/winetips/config.html)

Sidestep worked great for me, but all I use wine for is IE (when some idiot-site requires it), and for MS Freecell.

---

### Post by Mr. Electric Wizard on 2005-08-15
Dang, I just wish I could get MS Word to install...

---

### Post by Verlager on 2005-08-19
I sure couldn't get it to work. I followed the instructions at [http://www.ubuntuforums.org/showpost.php?p=149181&postcount=4](http://www.ubuntuforums.org/showpost.php?p=149181&postcount=4)

rmack@ubuntu:~/temp/winetools$ sudo sh install.sh
Installing WineTools to /usr/local/winetools...
Installing translations...
install.sh: line 22: msgfmt: command not found
Installed translations for de_DE@euro to /usr/local/share/locale/de_DE@euro/LC_MESSAGES/wt2.mo
install.sh: line 22: msgfmt: command not found
Installed translations for es to /usr/local/share/locale/es/LC_MESSAGES/wt2.mo
Start WineTools as *normal* user with "wt2". Don't use as root!
rmack@ubuntu:~/temp/winetools$

NOTHING ! Just error messages...

Now to try wt2:

rmack@ubuntu:~/temp/winetools$ wt2
found gettext in path
Browser is /usr/bin/firefox.
no suitable Wine directory found...
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Wine 0
wine is executed as wine
Parameters are --noexit
Wine is not configured yet!
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Calls to wine are executed as wine.
Config is /home/rmack/.wine/winetools.log.
CDROM is .
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
rmack@ubuntu:~/temp/winetools$

NOTHING! Just more error messages!

---

### Post by Mishura on 2005-08-19
You need the GTK1.2 libraries, which are not default in Ubuntu's install.. lemme see here..

Ah yes.  The package names are:

```
libgtk1.2
libgtk1.2-dev
libgtk1.2-common
```

Should work now.  **I think**.

---

### Post by bogyit on 2005-08-19
Hi :)

I've a problem! :shock: I've been using wine's old version, but yesterday I made the upgrade and Internet Explorer now fails to open, or better it doesn't do anything at all.. so I removed Wine and reinstalled (reading this topic and the one related to WineTools) and all went fine.. BUT  ](*,) when I try to download Internet Explorer from Microsoft site I get a funny message:> *Setup was unable to download the required components. Please make sure you are connected to the Internet, or try to run Setup again later.*[img]http://img369.imageshack.us/img369/2922/iecrap5ia.png[/img]

And I'm receiving this message since yesterday, is anybody experiencing the same problem? Any ideas or workaround solution?

Thanks in advance :)

[size=1]note: this is my first post here, I hope is the right place[/size]

---

### Post by blure007 on 2005-08-19
[QUOTE=bogyit]Hi :)

I've a problem! :shock: I've been using wine's old version, but yesterday I made the upgrade and Internet Explorer now fails to open, or better it doesn't do anything at all.. so I removed Wine and reinstalled (reading this topic and the one related to WineTools) and all went fine.. BUT  ](*,) when I try to download Internet Explorer from Microsoft site I get a funny message:[img]http://img369.imageshack.us/img369/2922/iecrap5ia.png[/img]

And I'm receiving this message since yesterday, is anybody experiencing the same problem? Any ideas or workaround solution?

Thanks in advance :)

[size=1]note: this is my first post here, I hope is the right place[/size][/QUOTE]


I had to download the full install of IE
[How to download IE6 Full Install](http://www.updatexp.com/download-ie6.html)

---

### Post by Deusiah on 2005-08-20
I'm having exactly the same problem since the upgrade, still not found out how to fix it. The downloading the whole thing didn't work for me, still had the same problem.

---

### Post by zixxer on 2005-08-20
i can get it to install left and right...but i am having a problem with desktop icons. or lack of. 
i installed wine the other day on this same system then today i did a clean install and when i installed wine the same way i did last time and try to install picasa it will not make any desktop icons....which it used to. how do i make wine automatically make a linking desktop icon?

---

### Post by dbrine on 2005-08-20
I am getting the IE6SP1 error also. Fresh install on my part but still get error, HELP



here is what I received (also followed directions)

Microsoft Internet Explorer.*
regedit: Can't export. Registry key 'HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall' does not exist!
Success

grep: /home/dave/.wine/installed.reg: No such file or directory
grep: /home/dave/.wine/installed.reg: No such file or directory
rm: cannot remove `/home/dave/.wine/installed.reg': No such file or directory
software installation verified by /home/dave/.wine/winetools.log
dependency Microsoft
Choice is Base setup
Choice is Internet Explorer 6.0 SP1 English with checked=F
dcom98.exe
regedit: Can't export. Registry key 'HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall' does not exist!
Success

grep: /home/dave/.wine/installed.reg: No such file or directory
grep: /home/dave/.wine/installed.reg: No such file or directory
rm: cannot remove `/home/dave/.wine/installed.reg': No such file or directory
software installation verified by /home/dave/.wine/winetools.log
dcom98.exe = installed at 20.08.2005 20:41:58
dcom98.exe = installed at 20.08.2005 20:44:30
dependency dcom98.exe fulfilled
using english setup...
Microsoft Internet Explorer.*
regedit: Can't export. Registry key 'HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall' does not exist!
Success

grep: /home/dave/.wine/installed.reg: No such file or directory
grep: /home/dave/.wine/installed.reg: No such file or directory
rm: cannot remove `/home/dave/.wine/installed.reg': No such file or directory
software installation verified by /home/dave/.wine/winetools.log
491768
WINEDLLOVERRIDES="" wine ./ie6setup.exe
waiting for wineservers to exit...
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000
fixme:advpack:TranslateInfString ("C:\\windows\\temp\\IXP000.TMP\\IESetup.inf" "Options.WIN" "Options.WIN" "InstallDir" 0x10253f8 260 0x7b98f830 (nil)): stub
fixme:advpack:NeedReboot (0x00000000): stub
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:advpack:RunSetupCommand ((nil), "C:\\windows\\temp\\IXP000.TMP\\IESetup.inf", "ActiveX", "C:\\windows\\temp\\IXP000.TMP", (null), (nil), 0x0000000d, (nil)): stub
fixme:advpack:RunSetupCommand ((nil), "C:\\windows\\temp\\IXP000.TMP\\IESetup.inf", "IE4Setup.Failure", "C:\\windows\\temp\\IXP000.TMP", (null), (nil), 0x0000000d, (nil)): stub
fixme:advpack:RunSetupCommand ((nil), "C:\\windows\\temp\\IXP000.TMP\\IESetup.inf", "ActiveX.Failure", "C:\\windows\\temp\\IXP000.TMP", (null), (nil), 0x0000000d, (nil)): stub
fixme:advpack:ExecuteCab ((nil) 0x7b98f9e8 (nil)): stub
all wineservers endet after 10 seconds...
Failed: 0
check installation by path or registry value...
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
Microsoft Internet Explorer.*
regedit: Can't export. Registry key 'HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall' does not exist!
Success

grep: /home/dave/.wine/installed.reg: No such file or directory
grep: /home/dave/.wine/installed.reg: No such file or directory
rm: cannot remove `/home/dave/.wine/installed.reg': No such file or directory
software installation verified by /home/dave/.wine/winetools.log
Failed: 1
Failed: 1
mv: cannot stat `/home/dave/.wine/drive_c/windows/system/regsvr32.exe': No such file or directory
du: cannot access `/home/dave/winetools/sys/Windows Update Setup Files': No such file or directory
du: cannot access `/home/dave/.wine/c/windows/Windows Update Setup Files': No such file or directory
Downloaded IE6-Files=0
Winetools  IE6-Files=0
Choice is Internet Explorer 6.0 SP1 English with checked=F
dcom98.exe
regedit: Can't export. Registry key 'HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall' does not exist!
Success

grep: /home/dave/.wine/installed.reg: No such file or directory
grep: /home/dave/.wine/installed.reg: No such file or directory
rm: cannot remove `/home/dave/.wine/installed.reg': No such file or directory
software installation verified by /home/dave/.wine/winetools.log
dcom98.exe = installed at 20.08.2005 20:41:58
dcom98.exe = installed at 20.08.2005 20:44:30
dependency dcom98.exe fulfilled
using english setup...
Microsoft Internet Explorer.*
regedit: Can't export. Registry key 'HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall' does not exist!
Success

grep: /home/dave/.wine/installed.reg: No such file or directory
grep: /home/dave/.wine/installed.reg: No such file or directory
rm: cannot remove `/home/dave/.wine/installed.reg': No such file or directory
software installation verified by /home/dave/.wine/winetools.log
491768
WINEDLLOVERRIDES="" wine ./ie6setup.exe
waiting for wineservers to exit...
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000
fixme:advpack:TranslateInfString ("C:\\windows\\temp\\IXP000.TMP\\IESetup.inf" "Options.WIN" "Options.WIN" "InstallDir" 0x10253f8 260 0x7b98f830 (nil)): stub
fixme:advpack:NeedReboot (0x00000000): stub
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:advpack:RunSetupCommand ((nil), "C:\\windows\\temp\\IXP000.TMP\\IESetup.inf", "ActiveX", "C:\\windows\\temp\\IXP000.TMP", (null), (nil), 0x0000000d, (nil)): stub
fixme:winhelp:MACRO_JumpContext ("C:\windows\temp\IXP000.TMP\iesetup.hlp", "main", 125)semi-stub
fixme:advpack:RunSetupCommand ((nil), "C:\\windows\\temp\\IXP000.TMP\\IESetup.inf", "IE4Setup.Failure", "C:\\windows\\temp\\IXP000.TMP", (null), (nil), 0x0000000d, (nil)): stub
fixme:advpack:RunSetupCommand ((nil), "C:\\windows\\temp\\IXP000.TMP\\IESetup.inf", "ActiveX.Failure", "C:\\windows\\temp\\IXP000.TMP", (null), (nil), 0x0000000d, (nil)): stub
fixme:advpack:ExecuteCab ((nil) 0x7b98f9e8 (nil)): stub
all wineservers endet after 16 seconds...
Failed: 0
check installation by path or registry value...
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
Microsoft Internet Explorer.*
regedit: Can't export. Registry key 'HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall' does not exist!
Success

grep: /home/dave/.wine/installed.reg: No such file or directory
grep: /home/dave/.wine/installed.reg: No such file or directory
rm: cannot remove `/home/dave/.wine/installed.reg': No such file or directory
software installation verified by /home/dave/.wine/winetools.log
Failed: 1
Failed: 1
mv: cannot stat `/home/dave/.wine/drive_c/windows/system/regsvr32.exe': No such file or directory
du: cannot access `/home/dave/winetools/sys/Windows Update Setup Files': No such file or directory
du: cannot access `/home/dave/.wine/c/windows/Windows Update Setup Files': No such file or directory
Downloaded IE6-Files=0
Winetools  IE6-Files=0

---

### Post by zixxer on 2005-08-21
wine works as it should for me, i can launch the program if i manually enter the windows dir tree and then invoke wine to execute the .exe i want. i cannot get any of my own launchers to work right. im still working this out, the icon it created for me for picasa the first time it worked actually was good. it had the picasa logo and actually ran the program. i just need to figure out how to get it back

---

### Post by mstlyevil on 2005-08-25
[QUOTE=bogyit]Hi :)

I've a problem! :shock: I've been using wine's old version, but yesterday I made the upgrade and Internet Explorer now fails to open, or better it doesn't do anything at all.. so I removed Wine and reinstalled (reading this topic and the one related to WineTools) and all went fine.. BUT  ](*,) when I try to download Internet Explorer from Microsoft site I get a funny message:[img]http://img369.imageshack.us/img369/2922/iecrap5ia.png[/img]

And I'm receiving this message since yesterday, is anybody experiencing the same problem? Any ideas or workaround solution?

I am having the same problem.

---

### Post by A-star on 2005-08-26
I have downloaded the files and made a zip file for it so you guys can download it.
Can anyone provide me with some place where I can put it?

---

### Post by xodeus on 2005-08-26
[QUOTE=A-star]I have downloaded the files and made a zip file for it so you guys can download it.
Can anyone provide me with some place where I can put it?[/QUOTE]
 send it to my xodeus at gmail dot com

---

### Post by [Cyanide] on 2005-08-29
[QUOTE=bogyit]Hi :)

I've a problem! :shock: I've been using wine's old version, but yesterday I made the upgrade and Internet Explorer now fails to open, or better it doesn't do anything at all.. so I removed Wine and reinstalled (reading this topic and the one related to WineTools) and all went fine.. BUT  ](*,) when I try to download Internet Explorer from Microsoft site I get a funny message:[img]http://img369.imageshack.us/img369/2922/iecrap5ia.png[/img]

And I'm receiving this message since yesterday, is anybody experiencing the same problem? Any ideas or workaround solution?

Thanks in advance :)

[size=1]note: this is my first post here, I hope is the right place[/size][/QUOTE]

I'm having the same problem.

---

### Post by xodeus on 2005-08-29
[QUOTE='[Cyanide]']I'm having the same problem.[/QUOTE]
 You can get the full IE6 by downloading it from
temp.xodeus.dk/ie6setup.tar.bz2

---

### Post by [Cyanide] on 2005-08-29
[QUOTE=xodeus]You can get the full IE6 by downloading it from
temp.xodeus.dk/ie6setup.tar.bz2[/QUOTE]

Still doesn't work, it tells me "The files on your computer are not the right files for my operating system" then it proceeds to try & re-download it from the Internet, which of course it fails.

---

### Post by oofnik on 2005-08-29
[QUOTE=bogyit][img]http://img369.imageshack.us/img369/2922/iecrap5ia.png[/img][/QUOTE]
Same error. Seems like something has been broken.. oh no. I tried with sidenet and winetools, I tried fresh installing wine packages, I even tried.. *gasp* rebooting, and it didn't change. ](*,)

---

### Post by A-star on 2005-08-30
[QUOTE='[Cyanide]']Still doesn't work, it tells me "The files on your computer are not the right files for my operating system" then it proceeds to try & re-download it from the Internet, which of course it fails.[/QUOTE]
 well the version that is in the package is for Windows 2000/XP, I'll try to make another pack somewhere today and send it back to xodeus and see what that gives.

---

### Post by xodeus on 2005-08-30
[QUOTE=A-star]well the version that is in the package is for Windows 2000/XP, I'll try to make another pack somewhere today and send it back to xodeus and see what that gives.[/QUOTE]
 Still ready to recieve :D

---

### Post by xodeus on 2005-08-30
Hi again.
Just for your information.
I've used the sidenet configuration for the latest version of Internet Explorer and it works fine here.
So just choose the Internet Explorer installation only from sidenet menu and it will install. :D

---

### Post by xodeus on 2005-08-30
Post #1 updated.
winetools removed.
sidenet added.
Fransk Corner added.

---

### Post by A-star on 2005-08-31
[QUOTE=xodeus]Still ready to recieve :D[/QUOTE]
 I will do it in the weekend, then I will have access to a windows pc where I can do it.

---

### Post by Goober on 2005-09-01
Hi,

I am trying to install this, and it works fine, which makes me very happy, but I am stuck on the last part.  

Here is what I see:

> Install these packages without verification [y/N]? y
Get:1 [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ wine 0.0.20050725-winehq-1 [14.9MB]
1% [1 wine 180224/14.9MB 1%]



Whatever it is that is trying to install is doing so very, very slowly, like bites at a time, which is odd since I have High-speed. Is the server down? Or do I need to get my verification thingie first?

---

### Post by Goober on 2005-09-01
Ok, ignore the above.

I got Wine installed using Synaptic (however its spelt).  Now, I know it works, but how do I used it?  If I insert a CD in my CD Drive which is a Game to install, how do I install it?

Also, where would that game go if I installed it correctly?  And, most importantly, how would I play it? (The last might be obvious once I figure out how to install it)

Thanks, 

Goober.

---

### Post by xodeus on 2005-09-02
[QUOTE=Goober]Ok, ignore the above.

I got Wine installed using Synaptic (however its spelt).  Now, I know it works, but how do I used it?  If I insert a CD in my CD Drive which is a Game to install, how do I install it?

Also, where would that game go if I installed it correctly?  And, most importantly, how would I play it? (The last might be obvious once I figure out how to install it)

Thanks, 

Goober.[/QUOTE]
 Try to google "the name of the game linux" or "the name of the game wine" or the name of the game linux installer".
Maybe you can find the game at Fransk Corner. Find it in the #1 post.

---

### Post by Cad-Monkey on 2005-09-02
Hey all,

I have been having the darndest time installing wine...

I am stuck at putting in the repositories of all things. I enter the repo lines into the sources.list file, and then run:

sudo apt-get update

I keep getting this:

Malformed line 40 in source list /etc/apt/sources.list (dist)

Does anyone know what this means, and what I have done wrong? I don't get this error if I delete the wine repo lines.

Here is a quick profile of my machine

Apple Powerbook G4, 867 Mhz,
Nvidia Geforce 4 (which, by the way, does not seem to be giving me any 3d hardware acceleration for anything...)
Ubuntu 5.0.4 Hoary Hedgehog
640 MB DDR SDRAM

Somebody please help. I have been tried a great many different tutorials and howtos... so far nothing has worked.

-----------------Cad-Monkey

---

### Post by xodeus on 2005-09-03
[QUOTE=Cad-Monkey]Hey all,

I have been having the darndest time installing wine...

I am stuck at putting in the repositories of all things. I enter the repo lines into the sources.list file, and then run:

sudo apt-get update

I keep getting this:

Malformed line 40 in source list /etc/apt/sources.list (dist)

Does anyone know what this means, and what I have done wrong? I don't get this error if I delete the wine repo lines.

Here is a quick profile of my machine

Apple Powerbook G4, 867 Mhz,
Nvidia Geforce 4 (which, by the way, does not seem to be giving me any 3d hardware acceleration for anything...)
Ubuntu 5.0.4 Hoary Hedgehog
640 MB DDR SDRAM

Somebody please help. I have been tried a great many different tutorials and howtos... so far nothing has worked.

-----------------Cad-Monkey[/QUOTE]
 Yes I do.
There is something wrong with your sources.list file at line 40.
An error can be a missing "#" for quoting some repos or for a note, or maybe a space to much.
You could maybe try to attach it here as text then I could look at it. :D

---

### Post by nax on 2005-09-08
Why installing IE on linux?
 All gecko and mozilla based browsers are far superior than ie.
I really don't see the use of installing it on linux! 
It is so nice not having to use microsoft's slow, ugly and easy infected programs when you use a linux like ubuntu or any other linux distribution. (specially ubuntu)

If I was a linux browser developer ( or wine's) I would feel so offended and useless if someone asked me that question.

I use wine to get to work new commercial or not programs which are not yet ready to be used in a high quality system like linux, great and useful progs. like google earth for instance.

Have you tried Konkeror, mozilla, firefox or the gnome browser? even Opera? no matter which is better than ie.

if you miss ie go back to windows and don't waste your time or the browser developers brains and time.

some programs and some people are just not ready to Linux...
unbelievable!!! ](*,)

---

### Post by Hobbsee on 2005-09-09
[QUOTE=nax]Why installing IE on linux?
 All gecko and mozilla based browsers are far superior than ie.
I really don't see the use of installing it on linux! 
It is so nice not having to use microsoft's slow, ugly and easy infected programs when you use a linux like ubuntu or any other linux distribution. (specially ubuntu)

If I was a linux browser developer ( or wine's) I would feel so offended and useless if someone asked me that question.

I use wine to get to work new commercial or not programs which are not yet ready to be used in a high quality system like linux, great and useful progs. like google earth for instance.

Have you tried Konkeror, mozilla, firefox or the gnome browser? even Opera? no matter which is better than ie.

if you miss ie go back to windows and don't waste your time or the browser developers brains and time.

some programs and some people are just not ready to Linux...
unbelievable!!! ](*,)[/QUOTE]
 You're right - Firefox, opera, and other gecko browsers are far superior to IE.

It's useful for webpage writers to check how their webpages look in IE, as it's (unfortuantely) the most used browser...

---

### Post by xodeus on 2005-09-09
[QUOTE=Hobbsee]You're right - Firefox, opera, and other gecko browsers are far superior to IE.

It's useful for webpage writers to check how their webpages look in IE, as it's (unfortuantely) the most used browser...[/QUOTE]
 i do only need IE for homebanking.
My bank does not support other browsers.

---

### Post by Deusiah on 2005-09-09
[QUOTE=nax]Why installing IE on linux?
 All gecko and mozilla based browsers are far superior than ie.
I really don't see the use of installing it on linux! 
It is so nice not having to use microsoft's slow, ugly and easy infected programs when you use a linux like ubuntu or any other linux distribution. (specially ubuntu)

If I was a linux browser developer ( or wine's) I would feel so offended and useless if someone asked me that question.

I use wine to get to work new commercial or not programs which are not yet ready to be used in a high quality system like linux, great and useful progs. like google earth for instance.

Have you tried Konkeror, mozilla, firefox or the gnome browser? even Opera? no matter which is better than ie.

if you miss ie go back to windows and don't waste your time or the browser developers brains and time.

some programs and some people are just not ready to Linux...
unbelievable!!! ](*,)[/QUOTE]

Are you incapable of considering that people installing IE are not doing so to use it? Surely you do realise that many programs depend upon the installtion of IE such as "All of MP3" browser which is useless to me without IE. I dislike IE as much as the next Linux guy but if someone want's to use IE on their system that's up to them, Linux is afterall about having the choice to do what you want. I use IE on Linux for two reasons, one as I already mentioned many programs depend on it and two, I check my  websites for cross-browser compatibility in it.

In a perfect world IE would not exist and all browsers would be standards complient but in reality we are stuck with IE for a long time to come and there's no point in calling people stupid because they use it, you'd help us more if you expained to those who use it the reasons why they should not in a professional none degrading mannor.

---

### Post by xodeus on 2005-09-09
For all those who have problems installing IE normally, try again with the updated Sidenet:
[http://sidenet.ddo.jp/winetips/config.html](http://sidenet.ddo.jp/winetips/config.html)

---

### Post by nEXzEr on 2005-09-11
erm "sudo apt-get install wine" doesn't work, it keeps saying that the package doesn't exist (and yes I've added apt-get links)

---

### Post by Deusiah on 2005-09-11
Thank you ever so much Xodeus!

That link you supplied installed IE flawlessly, finally I can download music again!

---

### Post by tbasten on 2005-09-11
[QUOTE=bogyit]Hi :)

I've a problem! :shock: I've been using wine's old version, but yesterday I made the upgrade and Internet Explorer now fails to open, or better it doesn't do anything at all.. so I removed Wine and reinstalled (reading this topic and the one related to WineTools) and all went fine.. BUT  ](*,) when I try to download Internet Explorer from Microsoft site I get a funny message:[img]http://img369.imageshack.us/img369/2922/iecrap5ia.png[/img]

And I'm receiving this message since yesterday, is anybody experiencing the same problem? Any ideas or workaround solution?

Thanks in advance :)

[size=1]note: this is my first post here, I hope is the right place[/size][/QUOTE]


LOL. Just a quick question. Why are u trying to use IE? For etax? :S i really dont like the fact that the taxation office doesnt release a firefox version etax which would be lovely for use working tax payers.

Cheers

dYnA

---

### Post by xodeus on 2005-09-12
[QUOTE=nEXzEr]erm "sudo apt-get install wine" doesn't work, it keeps saying that the package doesn't exist (and yes I've added apt-get links)[/QUOTE]
 did you do the 
```

sudo apt-get update

```
then
```

sudo apt-get install wine
```

---

### Post by blair on 2005-09-19
I suggest you verify you added the repository lines correctly. I had apt errors and realized I did not include spaces where required. 

From the original post: 

 # Wine Official Package Mirror
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

Note that there is a space before 'binary' and a space before /source

After I put the spaces in where they belonged, I did a repository refresh in Synaptic and the wine packages showed right up.

---

### Post by bmarilena on 2005-10-05
[QUOTE=xodeus]Hi.
This guide is for all those folks that want to install Wine the easy way and Maintain for the newest version.
This is taken from [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb) WinwHQ's own guide.
First add Wine Repo to your sources.list file
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
sudo gedit /etc/apt/sources.list &

```
and add the repo at the end of the file
Then update your apt and install
```

sudo apt-get update
sudo apt-get install wine

```
__________________________________________________________________________
If you want to use this version with Internet Explorer then use [Sidenet Wine Configuration Utility](http://sidenet.ddo.jp/winetips/config.html) 
For other applications you can use the guides at [Franks Corner](http://frankscorner.org/) 
___________________________________________________________________________
Update. I can't really test stuff here anymore as I've changed fully to amd64 and can't manage to chroot to test. So please, if you have any tested additions to this post, post it as "UPDATE #1" as reference to update post 1 and I will do so.[/QUOTE]


Hi 
I tried, but after  # sudo apt-get update
I got this message:
E: Malformed line 21 in source list /etc/apt/sources.list (dist)
I mention that the line is exactly the one I introduced myself (deb-src [http://wine.sourceforge.net/apt/binary/](http://wine.sourceforge.net/apt/binary/) ).
what should I do next?

Thanks a lot for help

Marilena

---

### Post by Heretushi on 2005-10-08
[QUOTE=bmarilena]Hi 
I tried, but after  # sudo apt-get update
I got this message:
E: Malformed line 21 in source list /etc/apt/sources.list (dist)
I mention that the line is exactly the one I introduced myself (deb-src [http://wine.sourceforge.net/apt/binary/](http://wine.sourceforge.net/apt/binary/) ).
what should I do next?

Thanks a lot for help

Marilena[/QUOTE]
You need a space between "apt/" and "/binary/".
```
deb-src http://wine.sourceforge.net/apt/ binary/
```

---

### Post by Carus on 2005-10-11
hey after getting wine with apt-get i get this when i try to run it

```

carus@linuxcomp:~$ wine
wine: creating configuration directory '/home/carus/.wine'...
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.5: cannot open shared object file: No such file or directory
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"C:\\windows\\rundll32.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\rundll32.exe" failed, status c0000135
wine: wineprefixcreate failed while creating '/home/carus/.wine'.
carus@linuxcomp:~$ sudo wine
wine: creating configuration directory '/home/carus/.wine'...
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.5: cannot open shared object file: No such file or directory
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"C:\\windows\\rundll32.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\rundll32.exe" failed, status c0000135
wine: wineprefixcreate failed while creating '/home/carus/.wine'.

```

but when i try to go to the folder /home/carus/.wine to perhaps put the .dll's in them, it doesnt exist!?! what do i do?

---

### Post by jamesstansell on 2005-10-12
[QUOTE=Carus]hey after getting wine with apt-get i get this when i try to run it

```

carus@linuxcomp:~$ wine
wine: creating configuration directory '/home/carus/.wine'...
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.5: cannot open shared object file: No such file or directory
...
```

but when i try to go to the folder /home/carus/.wine to perhaps put the .dll's in them, it doesnt exist!?! what do i do?[/QUOTE]
It looks like you might have a problem with libstdc++.so.5, apparently missing.  I would search the forums for that for a possible answer.

---

### Post by Carus on 2005-10-12
im terribly sorry, i found this topic by searching for wine problems, but apparetly im in the wrong ubuntu version forum

---

### Post by t_ras on 2005-10-12
using 5.04 on AMD64
I tryed working by orders,
but I dont seem to have a wine package to choose, and when choosing to install winetools it says that wine is not installable :(...
any ideas?

---

### Post by sickdude on 2005-10-12
Setting up wine configuration ...
Removing old iebatch.txt ...
Enabling batch install ...
Setting up Internet Explorer 6 ...
Checking if ie6setup needs to be started again ...
Checking if ie6setup needs to be started again ...
Checking if ie6setup needs to be started again ...
Checking if ie6setup needs to be started again ...
Checking if ie6setup needs to be started again ...
ERROR: ie6setup respawned too many times.
Setup aborted.
sickdude@megatron:~/winetools/wine-config-sidenet$


damned im getting this wierd ass error dont know what to do about that

any ideas anybody?

---

### Post by Mozzer on 2005-10-18
I've installed Wine and then tried to get Cossacks: European Wars to work. I know Frank's Corner doesn't have it listed but I thought I'd give it a go.

```
root@ubuntu:/home/mozzer # wine /media/cdrom0/CSetup.exe
```

So far so good, the normal setup window appears and the progress bar starts filling up. Alas, at some point it goes wrong. The setup window disappears and terminal tells me

```
wine client error:9: write: Bad address
```

Is there any way of getting it working or will it only work if they program it right?

---

### Post by Omnios on 2005-10-18
Ill vouch for the [COLOR="Red"]Sidenet Wine Configuration Utility [/COLOR]  I played around with with wine and wintools a long time ago with failures. Ith sigent basicly downloaded it it found wine set up my fake windows and installed IE etc. Not shure if the cd works yet though. One work of advise if you want the mentioned extras download them and use the #3 installation. I also droped a copy off the dlls in system and system 32 just in case wich eleviated a error message. 

 I still can't get shoutcast to work though. The window lauches but nothing happenes.

---

### Post by Omnios on 2005-10-18
Is it safe to install media player 9 not shure if its bugged thats probably why I cant lauch shoutcast?

---

### Post by Omnios on 2005-10-18
My desktop .ink s dont seem to work, any suggestions?

---

### Post by Omnios on 2005-10-19
Im having a problem with dcom98 I could not install a game I had before so though it may have something to do with dcom errors are as follows.

> tom@main:~/C:/wine-config-sidenet$ WINEDLLOVERRIDES="ole32=n" wine dcom98.exe
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
fixme:setupapi:SETUPX_CreateStandardLDDs LDID_SRCPATH: what exactly do we have to do here ?
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_REGSRCPATH
err:module:load_builtin_dll loaded .so for L"compobj.dll" but got L"ole32.dll" instead - probably 16-bit dll
err:ver:GetFileVersionInfoW Cannot access NE resource in L"C:\\windows\\temp\\IXP001.TMP\\compobj.dll"
err:ver:GetFileVersionInfoW Cannot access NE resource in L"C:\\windows\\temp\\IXP001.TMP\\ole2.dll"
err:ver:GetFileVersionInfoW Cannot access NE resource in L"C:\\windows\\temp\\IXP001.TMP\\storage.dll"
fixme:setupapi:do_file_copyW Notify that target version is greater..
err:setupapi:SetupDefaultQueueCallbackA copy error 0 "C:\\windows\\temp\\IXP001.TMP\\stdole2.tlb" -> "c:\\windows\\system\\stdole2.tlb"
fixme:setupapi:do_file_copyW Notify that target version is greater..
err:setupapi:SetupDefaultQueueCallbackA copy error 0 "C:\\windows\\temp\\IXP001.TMP\\olepro32.dll" -> "c:\\windows\\system\\olepro32.dll"
fixme:setupapi:do_file_copyW Notify that target version is greater..
err:setupapi:SetupDefaultQueueCallbackA copy error 0 "C:\\windows\\temp\\IXP001.TMP\\asycfilt.dll" -> "c:\\windows\\system\\asycfilt.dll"
err:setupapi:SetupDefaultQueueCallbackA copy error 5 "C:\\windows\\temp\\IXP001.TMP\\install.exe" -> "c:\\windows\\system\\dcom98\\oldole\\uninstall.exe"
err:setupapi:SetupDefaultQueueCallbackA copy error 5 "C:\\windows\\temp\\IXP001.TMP\\dcom98.inf" -> "c:\\windows\\system\\dcom98\\oldole\\dcom98.inf"
err:setupapi:SetupDefaultQueueCallbackA copy error 5 "C:\\windows\\temp\\IXP001.TMP\\eula98.txt" -> "c:\\windows\\system\\dcom98\\license.txt"
err:setupapi:SetupDefaultQueueCallbackA copy error 5 "C:\\windows\\temp\\IXP001.TMP\\relnt98.txt" -> "c:\\windows\\system\\dcom98\\relnotes.txt"
err:ver:GetFileVersionInfoW Cannot access NE resource in L"C:\\windows\\temp\\IXP001.TMP\\compobj.dll"
fixme:setupapi:vcpUICallbackProc16 (0xf740, 0705, 0000, 00000000, 7fdb5a94) - semi-stub
fixme:setupapi:vcpUICallbackProc16 (0xf740, 070f, 0000, 00000000, 7fdb5a94) - semi-stub
fixme:setupapi:vcpUICallbackProc16 (0xf740, 0710, 0000, 00000000, 7fdb5a94) - semi-stub
fixme:setupapi:vcpUICallbackProc16 (0xf740, 070b, 0000, 00000000, 7fdb5a94) - semi-stub
fixme:setupapi:vcpUICallbackProc16 (0xf740, 070c, 0000, 00000000, 7fdb5a94) - semi-stub
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_CFGAUTO
fixme:rpc:RPCRT4_DllRegisterServer (): stub


 Also I was having problems installing yahoo messenger so figure this is a dcom problem, also does wine have any owner ship in fake windows I chmod 777 my fake C: to see if that was the reason it could not install though this was after it would not install yahoo and the game I tryed installing.

---

### Post by rmrf on 2005-10-21
[QUOTE=Omnios]Is it safe to install media player 9 not shure if its bugged thats probably why I cant lauch shoutcast?[/QUOTE]

use streamtuner

```
sudo apt-get install streamtuner
```

You will have a multitude of streams in there, and can even do searches. It will launch whatever media player you have set as default afaik.

---

### Post by OttoDestruct on 2005-10-21
[QUOTE=Goober]Ok, ignore the above.

I got Wine installed using Synaptic (however its spelt).  Now, I know it works, but how do I used it?  If I insert a CD in my CD Drive which is a Game to install, how do I install it?

Also, where would that game go if I installed it correctly?  And, most importantly, how would I play it? (The last might be obvious once I figure out how to install it)

Thanks, 

Goober.[/QUOTE]

Browse to the directory and do
wine [setupname].exe

Once its setup go to your home folder and
cd .wine

Look around for something called "fake windows" or similar, and go to the part of the file tree you installed the game to.
wine [gameexe].exe

---

### Post by eraos on 2005-10-21
I installed wine using apt-get, and this is what I get when I try to use it:

```
nick@dhcp-373-75:/mnt/Common$ wine Metronome.exe
wine: creating configuration directory '/home/nick/.wine'...
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.5: cannot open shared object file: No such file or directory
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"C:\\windows\\rundll32.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\rundll32.exe" failed, status c0000135
wine: wineprefixcreate failed while creating '/home/nick/.wine'.

```

can someone help me?

I'm on 5.10, if that makes a difference.

---

### Post by aloicious on 2005-10-22
I had that problem eraos, fixed by installing libstdc++5 via apt (or synaptic).

---

### Post by justhere on 2005-10-22
i was installing wine and got to winetools set up on the dcom98 install i get these errors thanks for any help.

Choice is Create a fake Windows drive with checked=F
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.5: cannot open shared object file: No such file or directory
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"C:\\windows\\rundll32.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\rundll32.exe" failed, status c0000135
waiting for wineservers to exit...
all wineservers endet after 2 seconds...
Drive C: is /home/tim/.wine/drive_c, links will be made for c fake_windows
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
err:wineboot:ProcessRunKeys RegOpenKey failed on Software\Microsoft\Windows\CurrentVersion (2)
detecting Wine version... done.
Drive C: is /home/tim/.wine/drive_c
Wine 0
wine is executed as wine
Parameters are
Choice is DCOM98 with checked=F
dcom98.exe
regedit: Can't export. Registry key 'HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall' does not exist!
Success

grep: /home/tim/.wine/installed.reg: No such file or directory
grep: /home/tim/.wine/installed.reg: No such file or directory
rm: cannot remove `/home/tim/.wine/installed.reg': No such file or directory
software installation verified by /home/tim/.wine/winetools.log
1229056
WINEDLLOVERRIDES="ole32=n" wine ./dcom98.exe
err:module:load_builtin_dll failed to load .so lib for builtin L"GDI32.dll": libstdc++.so.5: cannot open shared object file: No such file or directory
err:module:import_dll Loading library GDI32.dll (which is needed by L"F:\\sys\\dcom98.exe") failed (error c000007a).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.5: cannot open shared object file: No such file or directory
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system\\user32.dll") failed (error c000007a).
err:module:import_dll Library USER32.dll (which is needed by L"F:\\sys\\dcom98.exe") not found
err:module:import_dll Loading library user32.dll (which is needed by L"c:\\windows\\system\\comctl32.dll") failed (error c000007b).
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.5: cannot open shared object file: No such file or directory
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system\\comctl32.dll") failed (error c000007a).
err:module:import_dll Library COMCTL32.dll (which is needed by L"F:\\sys\\dcom98.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"F:\\sys\\dcom98.exe" failed, status c0000135
waiting for wineservers to exit...
all wineservers endet after 2 seconds...
Failed: 1
check installation by return value...
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
err:wineboot:ProcessRunKeys RegOpenKey failed on Software\Microsoft\Windows\CurrentVersion (2)
Failed: 1
Choice is Show installed Software
testsw
regedit: Can't export. Registry key 'HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall' does not exist!
Success

grep: /home/tim/.wine/installed.reg: No such file or directory
grep: /home/tim/.wine/installed.reg: No such file or directory
rm: cannot remove `/home/tim/.wine/installed.reg': No such file or directory
software installation verified by /home/tim/.wine/winetools.log
tim@ubuntu:~$
tim@ubuntu:~$
tim@ubuntu:~$
tim@ubuntu:~$

---

### Post by eraos on 2005-10-22
[QUOTE=aloicious]I had that problem eraos, fixed by installing libstdc++5 via apt (or synaptic).[/QUOTE]

ah, alright

i had tried looking for libstdc++ and forgot the 5 :razz:


Edit: Yup, that did it. Thanks.

---

### Post by Nebulus on 2005-10-23
[QUOTE=jamesstansell]It looks like you might have a problem with libstdc++.so.5, apparently missing. [/QUOTE]

Seems like Wine is looking for libstdc++.so.5 but the newest (and propable installed) version is libstdc++.so.6

---

### Post by Flame0001 on 2005-10-30
Whenever I try to install WINE using 'sudo apt-get install wine', I get this:
```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?

```

---

### Post by inacoma on 2005-11-02
[QUOTE=Flame0001]Whenever I try to install WINE using 'sudo apt-get install wine', I get this:
```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?

```[/QUOTE]

you probably have another instance of synaptic or another package manager open.

k

---

### Post by Flame0001 on 2005-11-02
[QUOTE=inacoma]you probably have another instance of synaptic or another package manager open.

k[/QUOTE]

Oh, what a stupid mistake >_<

Thanks.

---

### Post by eternal on 2005-11-03
i downloaded all the files by invoking "c:\download\ie6setup.exe /c:"ie6wzd.exe /d:1 /s:""#E" " on my XP box, and that downloaded everything that setup would need.  then i burned that along with vb and vc++ runtimes, and a few other goodies to a cd, and tossed it into the ubuntu box. i tried installing by typing "wine /media/cdrom0/IE6SetupFiles/ie6setup.exe", and i get the same error still...!

this is what returns:
-----------------------
fixme:advapi:CheckTokenMembership ((nil) 0x7fdde558 0x7fb2fd9c) stub!
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000
fixme:advpack:TranslateInfString ("C:\\windows\\temp\\IXP000.TMP\\IESetup.inf" "Options.NTx86" "Options.NTx86" "InstallDir" 0x10253f8 260 0x7fb1f83c (nil)): stub
fixme:advpack:NeedReboot (0x00000000): stub
fixme:advpack:IsNTAdmin (0x00000000, (nil)): stub
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:advpack:RunSetupCommand ((nil), "C:\\windows\\temp\\IXP000.TMP\\IESetup.inf", "ActiveX", "C:\\windows\\temp\\IXP000.TMP", (null), (nil), 0x0000000d, (nil)): stub
fixme:advpack:RunSetupCommand ((nil), "C:\\windows\\temp\\IXP000.TMP\\IESetup.inf", "IE4Setup.Failure", "C:\\windows\\temp\\IXP000.TMP", (null), (nil), 0x0000000d, (nil)): stub
fixme:advpack:RunSetupCommand ((nil), "C:\\windows\\temp\\IXP000.TMP\\IESetup.inf", "ActiveX.Failure", "C:\\windows\\temp\\IXP000.TMP", (null), (nil), 0x0000000d, (nil)): stub
fixme:advpack:ExecuteCab ((nil) 0x7fb1f9f4 (nil)): stub
------------------------------

now, i must add 1 other thing that i have changed in ~/.wine/config...  
the part that goes:
;IE4,5,6 Installer
[AppDefaults\\grpconv.exe\\Version]
"Windows" = "nt40"

i have tried it as that, and also with "Windows" = "win98"
and this is what returns:
-----------------
fixme:advapi:CheckTokenMembership ((nil) 0x7fdde558 0x7fb2fd9c) stub!
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000
fixme:advpack:TranslateInfString ("C:\\windows\\temp\\IXP000.TMP\\IESetup.inf" "Options.NTx86" "Options.NTx86" "InstallDir" 0x10253f8 260 0x7fb1f83c (nil)): stub
fixme:advpack:NeedReboot (0x00000000): stub
fixme:advpack:IsNTAdmin (0x00000000, (nil)): stub
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:advpack:RunSetupCommand ((nil), "C:\\windows\\temp\\IXP000.TMP\\IESetup.inf", "ActiveX", "C:\\windows\\temp\\IXP000.TMP", (null), (nil), 0x0000000d, (nil)): stub
fixme:advpack:RunSetupCommand ((nil), "C:\\windows\\temp\\IXP000.TMP\\IESetup.inf", "IE4Setup.Failure", "C:\\windows\\temp\\IXP000.TMP", (null), (nil), 0x0000000d, (nil)): stub
fixme:advpack:RunSetupCommand ((nil), "C:\\windows\\temp\\IXP000.TMP\\IESetup.inf", "ActiveX.Failure", "C:\\windows\\temp\\IXP000.TMP", (null), (nil), 0x0000000d, (nil)): stub
fixme:advpack:ExecuteCab ((nil) 0x7fb1f9f4 (nil)): stub
--------------------
the error that pops up says to close all applications and try again.

ubuntu5.10 all packages current.  wine0.9

as a side...  in 5 years, i have never seen ANYTHING run under wine; on freebsd, slackware, redhat, and now ubuntu.  is wine BS?

---

### Post by mattc on 2005-11-16
OK, I don't know if this is my network connection, or what.  I've followed every step I could find to get Wine installed, to no avail.

After using your HOWTO - this is my output, which is the same I get no matter how I set up my repositories.

mattc@ubuntu:~$ sudo apt-get update
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release.gpg
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Release.gpg
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Get:4 [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release [110B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [3386B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Get:6 [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Release [112B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [14B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources [1062B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources [232kB]
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Sources
Get:10 [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages [1094B]
Get:11 [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Sources [719B]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources [1454B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources [915kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/multiverse Packages
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources [3886B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Fetched 1159kB in 48s (23.9kB/s)
Reading package lists... Done
mattc@ubuntu:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate
mattc@ubuntu:~$
Anyone got any ideas?

---

### Post by Leshiy on 2005-11-16
I have tried to install wine and it find all that pakages but when i try and run install this error comes up 

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libstdc++6 but it is not installable
E: Broken packages
 I have libstdc++5 installed and 5.3.3 installed with gcc and such crap via manager ... is there that v6 lib i can download?

---

### Post by Mr. Electric Wizard on 2005-12-14
Check this out guys...

---

### Post by bogyit on 2005-12-18
[QUOTE=tbasten]LOL. Just a quick question. Why are u trying to use IE? For etax? :S i really dont like the fact that the taxation office doesnt release a firefox version etax which would be lovely for use working tax payers.

Cheers

dYnA[/QUOTE]

Sorry for the late answer. Just because the website of my university doesn't work with Gecko & Opera but only with Internet Explorer 5.* But things are going to change: I'm working to improve design and code in order to have more accessibility and usability ;)

---

### Post by jharbert on 2006-08-19
A note to anyone who is still having trouble downloading the required libraries for Internet Explorer (getting the "unable to download the required components" error.  Are you running dansguardian.  Either change the blocked extensions file for dansguardian or temporarily disable it.  I had the same problem and after disabling dansguardian it worked fine.

---

### Post by sirius0 on 2007-03-24
Oh dear! I am a begginer and I can't install wine.

This is what I get.

:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: **libstdc++6** but it is not installable
E: Broken packages

(My Bold)
I have followed the instructions completely but I don't know where to find **libstdc++6**. Is **libstdc++6** what i require? Otherwise what have I done?

---

### Post by YokoZar on 2007-03-24
Could a moderator please close and lock this thread?  It is way, way, *way* out of date.  The latest version of Wine still hosted at sourceforge is older than Ubuntu Breezy!

> **sirius0 said:**
> Oh dear! I am a begginer and I can't install wine.

This is what I get.

:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: **libstdc++6** but it is not installable
E: Broken packages

(My Bold)
I have followed the instructions completely but I don't know where to find **libstdc++6**. Is **libstdc++6** what i require? Otherwise what have I done?Follow the instructions here:

[http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

---

### Post by sirius0 on 2007-03-27
Thanks!
I will go there after I put 6.06 on.
I had been using 5.10
Chris

---

### Post by goodtimetribe on 2007-05-09
This didn't work for me. I already had Wine 0.9.22, and it says no new updates available. It's like I'm stuck with that version.

---

### Post by goodtimetribe on 2007-05-09
Here's how I fixed this:

I downloaded the latest package from their archive list at [WineHQ's Package Archive List](http://wine.budgetdedicated.com/archive/index.html).

I then made that my working directory in terminal and issued this command

```
sudo dpkg -i wine_0.9.36~winehq0~ubuntu~6.10-1_i386.deb
```

---

### Post by Arghesis on 2007-05-20
Hy, 

I installed Wine and I want to install 3Ds Max 7 to see how it behaves. Yesterday the setup started but told me I need to install IE. So I checked the internet for that. Finally, I installed IE6, with IEs 4 Linux.

My problem is this :
when I type $ wine "/media/3ds max 7/setup.exe" it sais : 

err:module:import_dll Library ole32.dll (which is needed by L"D:\\Bin\\demo32.exe") not found
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system32\\oleaut32.dll") not found
err:module:import_dll Library OLEAUT32.dll (which is needed by L"D:\\Bin\\demo32.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"D:\\Bin\\demo32.exe" failed, status c0000135

My guess is that it must have something with some DLL's ... 
I searched for ole32.dll and it's in /usr/lib/wine/ole32.dll.so

I'm pretty much stuck ... if you could please help me
Oh, and btw, I have the latest version of wine 0.0.37

---

### Post by xodeus on 2007-05-21
I've just updated the guide to be the latest version...

---

### Post by Omnios on 2007-07-11
Found this script on Google and would give it a 5 star rating.
[winetricks]("http://www.kegel.com/wine/winetricks")
right click and save link as winetricks
make it executable and cd ... sh winetricks
this will echo a list of stuff it can isntall. 
the win installer and dcom98  work,

sh winetricks corefonts
sh winetricks msi2
 sh winetricks dcom98

---

