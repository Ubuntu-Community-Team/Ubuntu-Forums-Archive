---
title: "How to run a Windows software that require .NET Framework 4 on Ubuntu?"
date: 2013-08-04
forum: New to Ubuntu
---

### Post by Annas_Taqueria_at_MIT on 2013-08-04
Greetings!

I am aware that this post is an extremely long shot, but I just had to try something and start somewhere, so here we go:

Working in the Food Service Industry as a Multi-Unit Restaurant General Manager and Food Safety Specialist in the Boston Area, I make use of an electronic data logging thermometer called Saf-T-Log, manufactured by Thermoworks (thermoworks.com). This particular device requires requires a Windows software supplied by Thermoworks in order for data collected and stored in the unit to be downloaded to a computer, as well as for creating and maintaining lists of the items that are routinely temped using the Saf-T-Log thermometer.

I now need to make this Windows software run in a Linux computer (Ubuntu 12.04 running on a Intel® Celeron(R) CPU 847 @ 1.10GHz × 2 64-bit). My first attempt was to use Wine 1.6 to try and make the software install and run, but all my attempts were unsuccessful thus far.

The Thermoworks installer program, before installing the Saf-T-Log software, attempts to install the Microsoft .NET Framework 4 and an update for it, and that's when Wine returns the following error message:

___

*Component Microsoft .NET Framework 4 (x86 and x64) and Update for .NET Framework 4 (KB2468871) has failed to install with the following error message:*
*"A failuree occurred attempting to install the .NET Framework 4."*

*The following components failed to install:*
*- Microsoft .NET Framework 4 (x86 and x64) and Update for .NET Framework 4 (KB2468871)*

*See the setup log file located at 'C:\users\user\Temp\VSDacf7.tmp\install.log' for more information.*
___


On the other hand, when I try to install .NET Framework 4.0 myself, the installer returns an error message saying that .NET Framework 4 or higher is already installed.

I know it is more a Wine problem than an Ubuntu problem, but I have also posted the same issue on the WineHQ forum, so I just posting it over here also in order to improve my chances of someone that can help seeing the post.

Thank you much!

Caesar Grubel

---

### Post by sandyd on 2013-08-04
Have you tried the instructions at [http://appdb.winehq.org/objectManager.php?sClass=version&iId=17886](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17886) ?

---

### Post by Mark Phelps on 2013-08-04
If you look at the linked page, while .Net 4 should work OK, the newer version does not -- it's rated garbage.  So, it could be the .NET updates that are the problem:  [http://appdb.winehq.org/objectManager.php?sClass=application&iId=2586]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=2586")

---

