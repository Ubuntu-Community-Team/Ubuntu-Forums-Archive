---
title: "Help with lexmark Z640 printer please."
date: 2008-10-05
forum: New to Ubuntu
---

### Post by bwallum on 2008-10-05
Hello

I've tried to install a printer driver for a Lexmark Z640 printer. I have followed the instructions on openprinting.org, loaded libstdc++5 and alien as advised. I have also downloaded CJLZ600LE-CUPS-1.0-1.TAR.gz, the printer driver.

I have been following this set of code (I won't post it in code quotes because it does not work for me):-

1 $ mkdir lexmark 
2 $ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark 
3 $ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz 
4 $ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz 
5 $ tar -xvzf install.tar.gz 
6 $ alien -t z600cups-1.0-1.i386.rpm 
7 $ alien -t z600llpddk-2.0-1.i386.rpm 
8 $ sudo tar xvzf z600llpddk-2.0.tgz -C / 
9 $ sudo tar xvzf z600cups-1.0.tgz -C / 
10 $ sudo ldconfig 
11 $ cd /usr/share/cups/model 
12 $ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz

I can make the directory and move the file to it. Everything below line 3 fails.

Can you help me install the printer driver please? Note that I am running Intrepid Alpha 6

---

### Post by eternalnewbee on 2008-10-07
Hi bwallum.
I read somewhere in the forums that Lexmark is sort of anti Linux.
I can't really help you out, because I'm not technical whatsoever, but my advice is to search the forums carefully, because I think there are some workarounds...
Good luck.

---

### Post by Temposs on 2008-10-10
hi bwallum, I've made a deb package for installing the z600 drivers. You can try it out :-)

After you install the deb package, just go to the Printers settings and set up the printer with the newly found driver.

[http://temposs.googlepages.com/liblexz600core0.deb](http://temposs.googlepages.com/liblexz600core0.deb)

---

### Post by phidia on 2008-10-10
Temposs, If the package you made works-you get feedback that it does you should consider making an edit to the [Ubuntu printer wiki]("https://help.ubuntu.com/community/Printers") and maybe having a sticky somewhere (hardware?) there are frequent questions here about that lexmark model.

---

### Post by Bosnod on 2008-10-10
The deb package works. I got the printer going within a couple of minutes. Nice one Temposs.

---

### Post by bwallum on 2008-10-11
> **Temposs said:**
> hi bwallum, I've made a deb package for installing the z600 drivers. You can try it out :-)

After you install the deb package, just go to the Printers settings and set up the printer with the newly found driver.

[http://temposs.googlepages.com/liblexz600core0.deb](http://temposs.googlepages.com/liblexz600core0.deb)

Thanks Temposs! I'm a few hundred miles away from the target machine at the moment (trying to get to grips with vinagre over a WAN) so can't test it personally just yet. Thanks for all your effort! I'll get back eventually I'm sure.

---

### Post by bwallum on 2008-10-11
Andrew, at the risk of sounding cheeky could you do one for a 64bit architecture?
Regards, Bob

---

### Post by bepcapo on 2008-10-16
Your package works fine  many thanks

---

### Post by Satal Keto on 2008-11-12
Im the same as bwallum, I was wondering whether it would be possible for a x64 version to be made or maybe someone can point me in the right direction for making it myself (although I have to admit Im still pretty new to Linux)

Thanks for any help in advance
Satal

---

### Post by thorekk on 2008-11-17
I tried this package in Intrepid but, it didn't work. 
There is no ```
/etc/init.d/cupsys
``` in Intrepid, but it's called only ```
/etc/init.d/cups
``` So when postinstall script tries to restart cupsys it fails. I tried to install this package two-times before I noticed the cupsys --> cups change. Next boot my fstab was cleared off with only one usbfs row in it, and the automatic backup of fstab was the same. 
So I had to write a new fstab manually. 
I tried to deinstall the package but it didn't suceeded because of the failing of the script, until I made a symlink cupsys to cups.

---

### Post by Micy on 2008-11-29
Temposs - **[SIZE="6"]THANK YOU!![/SIZE]!**

Your solution is excellent!!!!

---

### Post by Temposs on 2008-12-01
> **thorekk said:**
> I tried this package in Intrepid but, it didn't work. 
There is no ```
/etc/init.d/cupsys
``` in Intrepid, but it's called only ```
/etc/init.d/cups
``` So when postinstall script tries to restart cupsys it fails. I tried to install this package two-times before I noticed the cupsys --> cups change. Next boot my fstab was cleared off with only one usbfs row in it, and the automatic backup of fstab was the same. 
So I had to write a new fstab manually. 
I tried to deinstall the package but it didn't suceeded because of the failing of the script, until I made a symlink cupsys to cups.

What I've done now is to edit the Lexmark Printer wiki in Ubuntu Documentation and place the Z600 package on it, for your convenience:

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters)

As per the issue quoted above, I've also tested and added a package for Ubuntu 8.10 Intrepid Ibex. It seems to install properly, but I don't have a printer to test it on. Tell me how it works for you guys.

Oh yeah, I've also fixed both of these packages to be (hopefully) architecture independent, although I don't have a 64-bit machine to test these on. I don't think there's anything that relies on 64-bit packages, though, so it should work.

Feedback by comments and email is welcomed :)

---

### Post by bwallum on 2008-12-01
Thanks for this piece of work Temposs! I'm away from the target machine at present but will get back to you when I have tried it.

mmmmmhhhhhhh!

---

### Post by neekbreeker on 2009-11-13
[SIZE=4]please  help temposs or anybody i downloaded your great help that you have kindly donated for z640 printer but as i know nothing about nothing concerning linux i stuck in to how to install deb.
colin
[/SIZE]

---

### Post by Temposs on 2009-11-13
Just download the file to your desktop and double click it. Then click Install on the window that appears.

---

### Post by neekbreeker on 2009-11-14
[SIZE=3]thanks for your quick respond temposs 
sorry to be a pain but do not see any install .clicked left and right but no install 
theres an extract 
.written on the top is file:///root/desktop/libexz600core0.deb-ark
witten in the box is three items 

control.tar gz rw-r--r--    0/0
data .tar.gz rw rr 0
devbian -binary rw r r 0

 i realy havant a clue what i am doing or how to make this file work i have tryd using the comand line for stuff but stay in root as i do not no how to change diretories
[/SIZE]

---

### Post by Temposs on 2009-11-14
Download it again. You renamed the file to have a "-ark" on it...this is not part of the original file name. It should only have .deb at the end.

You are using Ubuntu, right?

---

### Post by neekbreeker on 2009-11-15
[SIZE=4]thanks again for help temposs [SIZE=3]
in the properties of your download it says liblex600core0.deb 
location  /root/desktop 
size 
mod 11/13/09
accessed 11/13/09  i think it opend with ark when i clicked on it not arguing downloading again 
system not sure what it is the os year is 2007
thanks  again colin

[/SIZE][/SIZE]

---

### Post by neekbreeker on 2009-11-15
hello tempos still the same thing i am afraid no difference from second download 
now says libexz600core0(2).d -ark
ime guessing that the 2 stands for second download as i have not wipped the first one from the desk top 
regards colin

---

### Post by Temposs on 2009-11-15
I think you are not using Ubuntu, since you are logged in as root. Ubuntu generally doesn't allow logging in as root.

Note that my package is only made to work with Ubuntu. So, it will NOT work on your computer right now.

I suggest that you install the newest version of Ubuntu on your system: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

If you are going to install Ubuntu, do not post on this thread for help with that. To get help installing, you can start a new thread on the Absolute Beginner's section here:
[http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326)

---

### Post by neekbreeker on 2009-11-16
thanks for all your  help temposs 
regards colin

---

### Post by neekbreeker on 2009-11-19
calling on cars harrrrrrrh i found another solution for lexmark z640  printer  so thought i share 
i am sure that temposs fix is an aderquate fix ,but you might like to try this first defo works and is certaintly less tech than sir temposs 
hear it is then 2 steps first get lexmark drivers form synaptics  step 2 install your printer from scratch usesing configur your computer when it says your driver cant be found is this the right one follow the screen which will give you an option to find go to lexmark and pick the z6000 .you are done

[U]notes

[/U]when downloading lexmark drivers  leave first box emty tick second one 
when installing printer make sure only first box has tick in it 

coments 

i do not know if this soultion will let you print form the net but i just got a letter printed from it 
best of luck regards 
colin
ps wares the spell checker

---

### Post by vvfil64 on 2011-03-10
Great Thanks for Temposs!
My Lexmark Z640 printing under Ubuntu 10.04! But many people says: "Buy new printer for Ubuntu..."
And in OpenPrinting this model is not in list yet!
Thanks from Moscow!

&#1054;&#1075;&#1088;&#1086;&#1084;&#1085;&#1086;&#1077; &#1089;&#1087;&#1072;&#1089;&#1080;&#1073;&#1086; Temposs-&#1091;!
&#1052;&#1086;&#1081; Lexmark Z640 &#1087;&#1077;&#1095;&#1072;&#1090;&#1072;&#1077;&#1090; &#1087;&#1086;&#1076; Ubuntu 10.04! &#1061;&#1086;&#1090;&#1103; &#1084;&#1085;&#1086;&#1075;&#1080;&#1077; &#1087;&#1080;&#1096;&#1091;&#1090;: "&#1054;&#1090;&#1087;&#1088;&#1072;&#1074;&#1083;&#1103;&#1081;&#1089;&#1103; &#1079;&#1072; &#1085;&#1086;&#1074;&#1099;&#1084; &#1087;&#1088;&#1080;&#1085;&#1090;&#1077;&#1088;&#1086;&#1084; &#1076;&#1083;&#1103; Ubuntu..."
&#1048; &#1074; OpenPrinting &#1101;&#1090;&#1086;&#1081; &#1084;&#1086;&#1076;&#1077;&#1083;&#1080; &#1085;&#1077;&#1090; &#1074;&#1089;&#1077; &#1077;&#1097;&#1077; &#1074; &#1089;&#1087;&#1080;&#1089;&#1082;&#1077;!
&#1057;&#1087;&#1072;&#1089;&#1080;&#1073;&#1086; &#1080;&#1079; &#1052;&#1086;&#1089;&#1082;&#1074;&#1099;!

---

