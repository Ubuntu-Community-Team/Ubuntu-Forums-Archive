---
title: "Need Internet Explorer for Online Banking"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by mankoskidesu on 2008-07-14
I need to install internet explorer on my computer for online banking in China.  After I have installed IE, i need to install thier specific security program.  I have wine installed.  I tried to follow the steps at this site:

[http://www.howtoforge.org/how-to-install-internet-explorer-on-ubuntu8.04](http://www.howtoforge.org/how-to-install-internet-explorer-on-ubuntu8.04)

afterwards my terminal looks like this:



> howard@Napoleon:~$ sudo apt-get install wine cabextract binfmt-support
[sudo] password for howard: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wine is already the newest version.
cabextract is already the newest version.
binfmt-support is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
howard@Napoleon:~$ wget [http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz](http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz)
--23:40:05--  [http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz](http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz)
           => `ies4linux-latest.tar.gz.1'
Resolving [www.tatanka.com.br](www.tatanka.com.br)... 208.113.179.228
Connecting to [www.tatanka.com.br|208.113.179.228|:80](www.tatanka.com.br|208.113.179.228|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 332,341 (325K) [application/x-tar]

100%[====================================>] 332,341       57.06K/s    ETA 00:00

23:40:12 (56.97 KB/s) - `ies4linux-latest.tar.gz.1' saved [332341/332341]

howard@Napoleon:~$ tar xvfz ies4linux-latest.tar.gz
ies4linux-2.99.0.1/
ies4linux-2.99.0.1/LICENSE
ies4linux-2.99.0.1/ies4linux
ies4linux-2.99.0.1/README
ies4linux-2.99.0.1/winereg/
ies4linux-2.99.0.1/lang/
ies4linux-2.99.0.1/mac/
ies4linux-2.99.0.1/lib/
ies4linux-2.99.0.1/ui/
ies4linux-2.99.0.1/winereg/ie55.reg
ies4linux-2.99.0.1/winereg/ie6.reg
ies4linux-2.99.0.1/winereg/ie7.reg
ies4linux-2.99.0.1/winereg/.ie2.reg
ies4linux-2.99.0.1/winereg/.ie1.reg
ies4linux-2.99.0.1/winereg/ie5.reg
ies4linux-2.99.0.1/lang/esMX.sh
ies4linux-2.99.0.1/lang/slSI.sh
ies4linux-2.99.0.1/lang/svSE.sh
ies4linux-2.99.0.1/lang/ukUA.sh
ies4linux-2.99.0.1/lang/plPL.sh
ies4linux-2.99.0.1/lang/esES.sh
ies4linux-2.99.0.1/lang/skSK.sh
ies4linux-2.99.0.1/lang/trTR.sh
ies4linux-2.99.0.1/lang/huHU.sh
ies4linux-2.99.0.1/lang/fiFI.sh
ies4linux-2.99.0.1/lang/viVN.sh
ies4linux-2.99.0.1/lang/deDE.sh
ies4linux-2.99.0.1/lang/etEE.sh
ies4linux-2.99.0.1/lang/hrHR.sh
ies4linux-2.99.0.1/lang/itIT.sh
ies4linux-2.99.0.1/lang/siSI.sh
ies4linux-2.99.0.1/lang/zhTW.sh
ies4linux-2.99.0.1/lang/ptPT.sh
ies4linux-2.99.0.1/lang/roRO.sh
ies4linux-2.99.0.1/lang/ptBR.sh
ies4linux-2.99.0.1/lang/bgBG.sh
ies4linux-2.99.0.1/lang/lvLV.sh
ies4linux-2.99.0.1/lang/enUS.sh
ies4linux-2.99.0.1/lang/zhCN.sh
ies4linux-2.99.0.1/lang/frFR.sh
ies4linux-2.99.0.1/lang/msMY.sh
ies4linux-2.99.0.1/lang/nlNL.sh
ies4linux-2.99.0.1/lang/nbNO.sh
ies4linux-2.99.0.1/lang/ltLT.sh
ies4linux-2.99.0.1/lang/idID.sh
ies4linux-2.99.0.1/lang/jaJP.sh
ies4linux-2.99.0.1/lang/srYU.sh
ies4linux-2.99.0.1/lang/daDK.sh
ies4linux-2.99.0.1/lang/etET.sh
ies4linux-2.99.0.1/lang/esAR.sh
ies4linux-2.99.0.1/lang/csCZ.sh
ies4linux-2.99.0.1/lang/caES.sh
ies4linux-2.99.0.1/mac/functions-overwrite.sh
ies4linux-2.99.0.1/mac/whereiswine.sh
ies4linux-2.99.0.1/lib/xdg-desktop-menu
ies4linux-2.99.0.1/lib/help.sh
ies4linux-2.99.0.1/lib/files
ies4linux-2.99.0.1/lib/ies4linux.png
ies4linux-2.99.0.1/lib/functions.sh
ies4linux-2.99.0.1/lib/messages.txt
ies4linux-2.99.0.1/lib/install.sh
ies4linux-2.99.0.1/lib/xdg-desktop-icon
ies4linux-2.99.0.1/lib/uninstall.sh
ies4linux-2.99.0.1/lib/ies4linux.svg
ies4linux-2.99.0.1/ui/.svn/
ies4linux-2.99.0.1/ui/pygtk/
ies4linux-2.99.0.1/ui/kommander/
ies4linux-2.99.0.1/ui/.svn/format
ies4linux-2.99.0.1/ui/.svn/entries
ies4linux-2.99.0.1/ui/.svn/prop-base/
ies4linux-2.99.0.1/ui/.svn/tmp/
ies4linux-2.99.0.1/ui/.svn/text-base/
ies4linux-2.99.0.1/ui/.svn/props/
ies4linux-2.99.0.1/ui/.svn/tmp/prop-base/
ies4linux-2.99.0.1/ui/.svn/tmp/text-base/
ies4linux-2.99.0.1/ui/.svn/tmp/props/
ies4linux-2.99.0.1/ui/pygtk/python-gtk.sh
ies4linux-2.99.0.1/ui/pygtk/ies4linux-gtk.py
ies4linux-2.99.0.1/ui/kommander/advanced.kmdr
ies4linux-2.99.0.1/ui/kommander/kommander.sh
ies4linux-2.99.0.1/ui/kommander/logo.kmdr
ies4linux-2.99.0.1/ui/kommander/installation.kmdr
howard@Napoleon:~$ cd cd ies4linux-*
bash: cd: cd: No such file or directory
howard@Napoleon:~$ ./ies4linux



I really need IE so any help would be appreciated.  Also, I don't know the first thing about using Linux.  I mean nothing.  All I do is follow the instructions on sites that I google, but I cannot "think for myself".  Does anyone have any suggestions about how to learn the fundamentals of linux?

---

### Post by tuxxy on 2008-07-14
You could try virtualbox and run windows rather than IE.

---

### Post by philinux on 2008-07-14
Have you tried the user agent switcher addon for firefox to see if it can bypass the check.

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

---

### Post by sbassett on 2008-07-14
Also, it looks like you have 2 "cd"s in there, it should be

 cd ies4linux-*

give that a try.

---

### Post by bumanie on 2008-07-14
You could try ie4linux [http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page) Was also going to suggest the firefox add-on that replicates ie behaviour, but philinux beat me to it.

---

### Post by Valsodar on 2008-07-14
First of all you need to install wine (sudo apt-get install wine), then go to ies4linux website and download the tar archive, extract it, and in its directory ies4linux-xxxxxxx run the ies4linux. Install (you might need to re-run the application several times cuse it crashed on me during install about 10-15 times) and after done you can lunch ie by typing in terminal
/home/[you user name]/bin/ie6 or /home/[you user name]/bin/ie7 is you have installed ie7. Also i believe there should be desktop icons.

---

### Post by LowSky on 2008-07-14
User Agnet is the best idea I can think of. Most website only look for the verification file that the progrma gives you. But be wary it can cause some stability issues...
Follow these instructions, they are better

go to menu
System>Admin>Software Sources
you wan to enable all downloadable software, excluding source code, close the program and let it reload.

now open a terminal window and type ```
 sudo gedit /etc/apt/sources.list

``` at the bottom of that page type ```
 deb http://wine.budgetdedicated.com/apt hardy main
``` then save and close the window.

go back to the terminal and type the next three codes one code at a time
 ```
 
 wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

sudo apt-get update
 
sudo apt-get install wine cabextract
```

now your ready to download and install

```
 wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz

 tar zxvf ies4linux-latest.tar.gz

 cd ies4linux-*

 ./ies4linux

```

---

### Post by mankoskidesu on 2008-07-15
Ok, IE is now installed on my desktop.  Now I have to run the exe that my bank makes me download for security.  I probably need to run it from the came "c:\" drive that my IE is installed on, but when i look at my wine "c:\" drive, ie6 is not installed.  Can someone tell me how to run my exe so that it is set up to run on the ie6 that is now on my system?

---

### Post by hyper_ch on 2008-07-15
I don't think you can combine two "indipendant" programs just like that.

Try vbox/vmware or another bank ;)

---

### Post by el10t on 2008-07-15
> **philinux said:**
> Have you tried the user agent switcher addon for firefox to see if it can bypass the check.

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

I had the same problem with NatWest and throughly recommend this approach - it works fine and avoids having to install unnecessary browsers.  The simplest solutions are always the best!

---

### Post by pooyaplus on 2008-07-15
> **mankoskidesu said:**
> Ok, IE is now installed on my desktop.  Now I have to run the exe that my bank makes me download for security.  I probably need to run it from the came "c:\" drive that my IE is installed on, but when i look at my wine "c:\" drive, ie6 is not installed.  Can someone tell me how to run my exe so that it is set up to run on the ie6 that is now on my system?

Hi, just give it a try and see if that works. The installation wizard of that program will ask you the preferred location and the execution path. 

As it would be in windows, choose program file in c:\. and see if it works. 

If not, I do recommend using the virtualbox. It's really cool.

Good luck

---

