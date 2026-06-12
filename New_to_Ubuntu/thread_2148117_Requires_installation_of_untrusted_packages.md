---
title: "Requires installation of untrusted packages"
date: 2013-05-24
forum: New to Ubuntu
---

### Post by johnny907 on 2013-05-24
I cannot install anything new in ubuntu 10.10, even previously installed packages that I removed I cannot get install back.  Every time I go to software center and try to install something new I get the following:  
[I]

[B]Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.[/B]




Any help would be very much appreciated.[/I]

---

### Post by claracc on 2013-05-24
> **johnny907 said:**
> I cannot install anything new in ubuntu 10.10, even previously installed packages that I removed I cannot get install back.  Every time I go to software center and try to install something new I get the following:  
[I]

[B]Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.[/B]




Any help would be very much appreciated.[/I]



You obtained the same error some months ago: [http://ubuntuforums.org/showthread.php?t=2125428](http://ubuntuforums.org/showthread.php?t=2125428), and you were advised that ubuntu 10.10 has reached its end of life support, so the errors encountered is the normal behaviour.

You have to upgrade to a supported release: 12.04, 12.10, 13.04

---

### Post by claracc on 2013-05-25
More information, if you want to continue using outdated 10.10 (which I don't recommend) you can see instructions given in this link: [http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release](http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release)

But be aware that you are not going to receive any update and that your system will be on risk.

---

### Post by johnny907 on 2013-05-25
thank you for your replies, i have tried to install 13.04 recently but every time i try, my screen goes black after the first step (purple screen asking for language preferences)

---

### Post by claracc on 2013-05-25
Here you have a link : [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
to know if your hardware is compatible with the new ubuntu release.

Also you can see: [https://help.ubuntu.com/13.04/installation-guide/](https://help.ubuntu.com/13.04/installation-guide/)

You can try with 12.04 LTS, as it is a long time support, it will receive security updates till 2017.

---

### Post by johnny907 on 2013-05-25
I tried 12.04 with the same result, get to purple setup screen, then nothing but black screen. Even tried installing Elementary Luna beta 2, with same results.  My hardware seems to all checkout just fine to run aforementioned OS's.  It's a cheap secondary PC, but it can easily handle new Ubuntu or Ubuntu based releases.

Acer Aspire 5336-2524


[LIST]
[*=left][COLOR=#768696][FONT=inherit]Processor[/FONT][/COLOR][COLOR=#39434D][FONT=inherit]Intel Celeron 900 / 2.2 GHz[/FONT][/COLOR]
[*=left][COLOR=#768696][FONT=inherit]Memory[/FONT][/COLOR][COLOR=#39434D][FONT=inherit]3.0 GB / 4.0 GB (max)[/FONT][/COLOR]
[*=left][COLOR=#768696][FONT=inherit]Hard Drive[/FONT][/COLOR][COLOR=#39434D][FONT=inherit]250.0 GB - Serial ATA-150 - 5400.0 rpm[/FONT][/COLOR]
[*=left][COLOR=#768696][FONT=inherit]Operating System[/FONT][/COLOR][COLOR=#39434D][FONT=inherit]Microsoft Windows 7 Home Premium 64-bit Edition[/FONT][/COLOR]
[*=left][COLOR=#768696][FONT=inherit]Display Type[/FONT][/COLOR][COLOR=#39434D][FONT=inherit]15.6 in TFT active matrix[/FONT][/COLOR]
[*=left][COLOR=#768696][FONT=inherit]Max Resolution[/FONT][/COLOR][COLOR=#39434D][FONT=inherit]1366 x 768 ( HD )[/FONT][/COLOR]
[*=left][COLOR=#768696][FONT=inherit]Graphics Processor[/FONT][/COLOR][COLOR=#39434D][FONT=inherit]Intel GMA 4500M Dynamic Video Memory Technology 5.0[/FONT][/COLOR]
[*=left][COLOR=#768696][FONT=inherit]Optical Drive[/FONT][/COLOR][COLOR=#39434D][FONT=inherit]DVD±RW (±R DL) / DVD-RAM - Integrated[/FONT][/COLOR]
[/LIST]

---

### Post by Baldrick_NZ on 2013-05-26
can you run a LiveUSB of either 12.04 or 13.04 ok on the puter in question?

---

### Post by claracc on 2013-05-26
I have found this thread: [http://ubuntuforums.org/showthread.php?t=2127862](http://ubuntuforums.org/showthread.php?t=2127862) about using nomodeset in order to proceed for ubuntu installation.

You can try the instructions provided by grahammechanical:

1) at the first purple screen press Enter
2) at the next screen press Enter to select English as the default language or select another language
3) at the Try Ubuntu - Install Ubuntu screen press F6
4) scroll down the menu that appears and select nomodeset and press Enter
5) press Esc to get back to the Try - Install screen and make your select and press Enter

---

### Post by johnny907 on 2013-05-26
Thank you very much, it was the nomodset issue, but now I am having another one.  During the 13.04 installation setup everything is fine except I cannot connect to wifi.  The wifi on/off button in network setup cannot be switched to 'on', and the top menu wifi icon says 'wifi is disabled by hardware switch'.  I went ahead and installed 13.04 without internet connection because wifi is all I can access at the moment.

---

### Post by johnny907 on 2013-05-26
Never mind, wifi problem, I accidentally had checked "acpi=off" and it affected the wifi.  Re-doing installation and wifi working perfectly now.

---

### Post by claracc on 2013-05-26
So, at last I understand you have ubuntu 13.04 installed and running. 

Glad you got fixed your problem.

Please, if the problem is fixed, mark the thread as solved: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by johnny907 on 2013-05-26
Well its installed, but not running very well.  It runs extremely slow, cpu output is fine, but every action has huge lag.  Also, my screen resolution is stuck at 1024x768 and no option to go higher even though it's capable of doing so.

---

