---
title: "How To Install Adnroid SDK in Ubuntu Linux?"
date: 2012-08-25
forum: New to Ubuntu
---

### Post by rez182 on 2012-08-25
Ubuntu: 12.04 LTS

How can i install the linux version of Android SDK from the official developer site in my Ubuntu 12.04 LTS?

Im downloading the "android-sdk_r20.0.3-linux.tgz" file but i have no clue how to install such files.

Usually when i download softwares etc from the website like TeamViewer or Skype, the download automatically starts with Ubuntu Software Centre, but alot of the files dont start that way. They apparently have to be installed manually i guess. Can you guys help me learn how to install such files? thanks alot...


EDIT - This is the installation guide provided in the website. I cant seem to use the apt-get codes in the terminal to install the related programs...In other words, i could not do a thing other than download the Android SDK. PLEASE HELP...

>     **Getting started on Linux**

  Your download package is a .tgz.   Unpack it to a safe location on your machine. By default, the SDK files are unpacked into a directory named android-sdk-linux_x86.
  Make a note of the name and location of the SDK directory on your system&#8212;you will need to refer to the SDK directory later, when setting up the ADT plugin and when using the SDK tools from the command line.
  Now continue with the installation guide by clicking the **Next** link on the right.
   **Troubleshooting Ubuntu**

  
[LIST]
[*]If you need help installing and configuring Java on your     development machine, you might find these resources helpful:
[LIST]
[*][https://help.ubuntu.com/community/Java ]("https://help.ubuntu.com/community/Java")
[*][https://help.ubuntu.com/community/JavaInstallation]("https://help.ubuntu.com/community/Java")
[/LIST]
 
[*]Here are the steps to install Java and Eclipse, prior to installing   the Android SDK and ADT Plugin.
[LIST=1]
[*]If you are running a 64-bit distribution on your development       machine, you need to install the ia32-libs package using       apt-get::       apt-get install ia32-libs
[*]Next, install Java: apt-get install sun-java6-jdk
[*]The Ubuntu package manager does not currently offer an Eclipse 3.6       version for download, so we recommend that you download Eclipse from       eclipse.org ([http://www.eclipse.org/       downloads/]("http://www.eclipse.org/downloads/")). A Java or RCP version of Eclipse is recommended.
[*]Follow the steps given in previous sections to install the SDK       and the ADT plugin.
[/LIST]
   
[/LIST]
  


**PLEASE DUMB IT DOWN SO NOOBS LIKE ME CAN USE THE ANDROID SDK IN UBUNTU LINUX. THANKS...**

---

### Post by user333 on 2012-08-25
Don't worry, it's not that complicated ;)

First, decompress that tgz by right clicking on it and selecting 'Extract Here'. That is all that file really is; just another type of 'zip'. I think it should all be compiled and ready to go. Go into the 'tools' directory, and try to run the 'android' program. Just see if it runs. Ignore the stuff about needing sun (or oracle) java. I don't have it installed, and I have the sdk manager running as I write this.

Let me know if you are able to launch the manager. If you can, install the correct package for the version of android you want. Make sure to get the same version as your phone or tablet if you have one, otherwise just go with the latest (4.1). Then we can start on Eclipse.

I apologize if I stated the obvious, but I tried to follow your instructions very literally :D

---

