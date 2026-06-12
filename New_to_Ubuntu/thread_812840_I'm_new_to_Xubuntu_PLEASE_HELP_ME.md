---
title: "I'm new to Xubuntu PLEASE HELP ME"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by mac143_01 on 2008-05-30
I'm still downloading a Xubuntu ISO for a 32bit and a 64 bit Pc. I'm planning to use it as my OS.

Please help me and answer my questions step by step if possible thank you very much.

1. which is best: Ubuntu, Kubuntu, or Xubuntu?

2. what is the difference between the DVD and CD installers of Ubuntu that can be downloaded in the internet? the DVD is almost 3gig and CD is 700mb

3. can Xubuntu handle and can be installed in a PC with the following Specs: Core 2 Quad Processor, 8gig DDR2 Memory, 1gig Inno3d video card, 1 Terabyte Hard drive, and can Xubuntu open NTFS formats of hard drives?  

4. How can I Install the drivers for each hardware like the driver of the video card, motherboard, Nero, and for an HP 3in1 (printer, scanner, xerox)in Xubuntu?

5. How can I install and play games for windows in Xubuntu? like NBA2008, Need for Speed, Diablo II, Dungeon Siege, etc.

6. how to install wine and beryl on Xubuntu? please tell me the steps so that I will not get confused. 

7. if I am using Xubuntu as my OS, can I install programs or drivers by just clicking the SETUP.EXE?

8. how can i learn the basics and commands for Xubuntu? or just the simple steps for installation of a certain program please teach me the steps.. Coz Xubuntu is not taught in schools here in the Philippines, only Windows programs. 


I really appreciate the answers that you will post for my thread thank you very much to all of you and may GOD bless us all.

---

### Post by Kevbert on 2008-05-30
Answers:
1) Xubuntu is a cut down OS, but is fastest, good for low spec PCs.  Kubuntu or Ubuntu are better.
2) With the CDs you'll still need to download a lot of software.  Very little  for DVDs.  Updates will still be downloaded for both.
3) I'm not sure, but it looks like Ubuntu or Kubuntu are a better choice as your equipment spec is quite good.
4) Most hardware is detected during install.  If you can, you want to have it powered up and an active Ethernet connection running so that any additional drivers can be download from the web.
5) Again don't know about Xubuntu, but with Ubuntu you can use Wine or various other Windows 'emulator' programs.  In this case it's very much try it and see.
6) Pass.  Better to use Compiz fusion which comes with Ubuntu 8.04.
7) No.
8) Have a look at the community documents: Xubuntu [http://www.xubuntu.org/help]("http://www.xubuntu.org/help")
Kubuntu 
[http://www.kubuntu.org/index.php]("http://www.kubuntu.org/index.php")
Ubuntu
[https://help.ubuntu.com/]("https://help.ubuntu.com/")
Best of luck and welcome.

---

### Post by eriqjaffe on 2008-05-30
> **mac143_01 said:**
> 1. which is best: Ubuntu, Kubuntu, or Xubuntu?It's really just a matter of preference.  Once you have one installed, you can install the others as well by entering:

```
sudo apt-get install ubuntu-desktop
sudo apt-get install kubuntu-desktop
```

In the terminal - those are separate commands, each one will install the components necessary to run Ubuntu and Kubuntu - all 3 can co-exist without issue, you just have to choose which session you want to launch from the login screen.

Be aware that when you enter "sudo" to preface a command, you are asking Ubuntu to run a program as root (similar - although far less intrusive - to Vista's User Account Control).  When you enter your password, you will not get any visual feedback that you are entering a password.  This is by design so that anybody peeking over your shoulder can't guess the root password by counting the characters on the screen.

> **mac143_01 said:**
> 2. what is the difference between the DVD and CD installers of Ubuntu that can be downloaded in the internet? the DVD is almost 3gig and CD is 700mbIIRC, the DVD has all of the software repositories on it.  If you have a fast internet connection, it's really not necessary.

> **mac143_01 said:**
> 3. can Xubuntu handle and can be installed in a PC with the following Specs: Core 2 Quad Processor, 8gig DDR2 Memory, 1gig Inno3d video card, 1 Terabyte Hard drive, and can Xubuntu open NTFS formats of hard drives?Oh, mercy yes.  I've run Xubuntu on a 366mhz Pentium II with 128mb of RAM. 

> **mac143_01 said:**
> 4. How can I Install the drivers for each hardware like the driver of the video card, motherboard, Nero, and for an HP 3in1 (printer, scanner, xerox)in Xubuntu?Drivers are, in most cases, already part of the Linux kernel - there should be very little extra driver installation necessary.  If all of your hardware works when you run the LiveCD, then it should all work when you install to the hard drive just the same.

> **mac143_01 said:**
> 5. How can I install and play games for windows in Xubuntu? like NBA2008, Need for Speed, Diablo II, Dungeon Siege, etc.WINE, but it doesn't work for every game/application.  [http://appdb.winehq.org/](http://appdb.winehq.org/) for information on specific games.


> **mac143_01 said:**
> 6. how to install wine and beryl on Xubuntu? please tell me the steps so that I will not get confused.Beryl is deprecated, and has been replaced with compiz-fusion.  I don't use it, so I'm not sure how to install it, though.  To install Wine:

```
sudo apt-get install wine
```

...or install it from Synaptic Package Manager, if you prefer a GUI. 

> **mac143_01 said:**
> 7. if I am using Xubuntu as my OS, can I install programs or drivers by just clicking the SETUP.EXE?There are no SETUP.EXEs in Ubuntu, those are Windows executables.  That being said, if you want/need to run a Windows program through wine:

```
wine /path/to/the/file/setup.exe
```

...will launch the installer, or whatever executable you tell it to.  Again, WINE isn't 100%, some things just won't work.  Also, see my comment above about drivers.


> **mac143_01 said:**
> 8. how can i learn the basics and commands for Xubuntu? or just the simple steps for installation of a certain program please teach me the steps.. Coz Xubuntu is not taught in schools here in the Philippines, only Windows programs.[https://help.ubuntu.com/community/Beginners/Guide](https://help.ubuntu.com/community/Beginners/Guide) is a good place to start, and these forums are an incredibly useful resource.

---

### Post by Game_boy on 2008-05-30
1. If you're new and have the sort of PC you describe, then Ubuntu. The others require a little more experience.

2. Both come with enough for a good desktop, but the DVD has more stuff on it while the CD may require you to download more applications after you install it. The CD does come with everything you would expect, though: word processor, spreadsheet, media player, instant messenger, drawing application, etc.

3. Of course. 


4. 
video card - done automatically on install

motherboard - done automatically on install

Nero - You don't need that. There are plenty of better, free applications on the CD/DVD that do that already

HP 3in1 (printer, scanner, xerox) - Go to the Printing appliaction in the menu and it should automatically install the driver

5. Most of those games only work in Windows. Try something like Wine, which allows you to play a lot of Windows games on Ubuntu.

6. It already comes with something better than beryl called compiz. This is done automatically when you install Ubuntu (don;t know about Xubuntu). As for wine, you go to "Add/Remove Programs" and search for and click on Wine.

7. No. But as I've said, most drivers are already installed and most programs can be done as with Wine by going to Add/Remove Programs.

8. It's pretty much like Windows, but easier to use. There are very few "weird" things to learn. To install programs is much easier than Windows - you just go to Add/Remove Programs and choose the ones you want.

7.

---

### Post by fluteflute on 2008-05-30
Compiz Fusion (what used to be Beryl) is installed by default.

---

### Post by arpanaut on 2008-05-30
Might want to start doing some reading: [http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

!. matter of personal preference

2. Cd basic installer & default programs, DVD has has much of the "repositories" on disc, If you have fast/unlimited internet no need for DVD

3.Those specs are sufficient for Xubuntu, any of the *buntu's for that matter

4. Most drivers are prety automated, burning saftware installed by default, don't know about multifunction priners, but HP support is prety solid.

5. Don't game... Wine works for some, 

6.Wine how to's all over, beryl has merged with Compiz, installed by default... 

7.Nope, do some reading in link above

8.  Don't teach it around here either, heh... do some research all that info is around, thats what this place if for.

Howdy, and Welcome 
ENJOY!

---

### Post by jpryor68 on 2008-05-30
> 1. which is best: Ubuntu, Kubuntu, or Xubuntu?

Xubuntu :=)

OK, it depends. If you're not used to the three desktops (gnome, kde, xfce) then try them out and see what feels best. You can use any of the ISOs to start with. Install Xubuntu, and try it out. After a while, install the ubuntu-desktop to get the gnome desktop. You should see an option when logging in whether to log into a Xfce desktop or a Gnome one. Similarly, you can install kubuntu-desktop to get the kde desktop.

> 2. what is the difference between the DVD and CD installers of Ubuntu that can be downloaded in the internet? the DVD is almost 3gig and CD is 700mb

The only difference is how much software is available on the installation media, and how much you'll need to download. If you've got good bandwidth, then just use the Xubuntu CD you've already downloaded, and you can install further software later.

> 3. can Xubuntu handle and can be installed in a PC with the following Specs: Core 2 Quad Processor, 8gig DDR2 Memory, 1gig Inno3d video card, 1 Terabyte Hard drive, and can Xubuntu open NTFS formats of hard drives?

Can open ntfs yes. Your system is more than powerful enough to run any of the Ubuntu distributions. Don't know details about that video card.

> 7. if I am using Xubuntu as my OS, can I install programs or drivers by just clicking the SETUP.EXE?

No, Linux doesn't have any BLAHBLAH.EXE files. You'll need to do some reading to figure out what's what. There's plenty of information available on the web, but it's also going to be confusing at first trying to organize and digest what you find. I recommend finding some useful-looking Intro to Linux or Intro to Ubuntu book in your bookstore. You may find it easier to start out with Ubuntu than with Xubuntu, because the books you find will be much more likely to talk about menus, programs, etc. that are installed by default in Ubuntu but not Xubuntu.

You've got a lot of learning ahead of you, but I hope you'll enjoy it and find it fun, rather than a deterrent. Good luck.

---

