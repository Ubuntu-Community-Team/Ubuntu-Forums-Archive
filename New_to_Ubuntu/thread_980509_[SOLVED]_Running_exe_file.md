---
title: "[SOLVED] Running exe file?"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by Miss Karen on 2008-11-12
My laptop came with Ubuntu Gutsy Gibbon (I think) already installed. I've had trials and tribulations aplenty trying to get it to play videos and dvds but now I have a new problem.

It won't open files with the .exe file extension, meaning I can't install anything outside Linux.

Help, please!:confused:

---

### Post by SuperSonic4 on 2008-11-12
WINE might work depending on the app.

Btw what is the app in question?

---

### Post by sharkster2007 on 2008-11-12
Is your machine dual-booting windows and Linux?

The common (.exe) type of file for Ubuntu Linux is .deb (.exe is for windows programs only, as far as I know)

Windows programs will not work on Linux, as Linux is a different type of operating system (Like Apple's OSX)

---

### Post by Miss Karen on 2008-11-12
I was wondering if there was some kind of codec or something that I had to download...

Any kind of app with an .exe extension! Games, software, anything!

---

### Post by Miss Karen on 2008-11-12
> **sharkster2007 said:**
> Is your machine dual-booting windows and Linux?

The common (.exe) type of file for Ubuntu Linux is .deb (.exe is for windows programs only, as far as I know)

Windows programs will not work on Linux, as Linux is a different type of operating system (Like Apple's OSX)



No, I'm only booting Linux.

Hmm. But I am trying to load Windows onto my laptop, and it won't work. I assumed that it was because it couldn't read the .exe file...

---

### Post by SuperSonic4 on 2008-11-12
Windows shouldn't be an .exe file. You will get a CD or a CD image off the internet as an ISO file. Said file should be burnt to CD and then install it off the CD

---

### Post by sharkster2007 on 2008-11-12
The "Wine" program mentioned above is a sort of "windows simulator" for Linux i have no knowledge of this other than this.

Windows programs (.exe), will not work on Linux (unless you have a "windows Simulator" or "Windows Emulator" installed on Linux)

Its like trying to run an XBOX360 game, on a Wii it just wouldn't work, as they are radically different Operating Systems (Like Apple's OSX, that can't run Windows programs either).

---

### Post by sirebral on 2008-11-12
WINe = Windows Emulator.

You can also attempt to use Virtual Box which is a Virtual Machine that allows you to install a Windows OS into your Linux distro and run the entire OS within.

I suggest WINe.  It is great!

---

### Post by Miss Karen on 2008-11-12
sharkster - sorry for being a numpty, but I don't understand what you mean :confused: I have the windows cd, but it won't install..

---

### Post by jimmy the saint on 2008-11-12
Youre problem is that you are trying to load a windows program onto a linux computer.  Its like trying to put gasoline into a diesel truck.  It just wont work.  Wine is buggy at best.  What is the program you want?  There is probably a good linux program available that will do what you want.

[http://www.linuxalt.com/](http://www.linuxalt.com/)

check out that page and see

---

### Post by sharkster2007 on 2008-11-12
Don't worry, I have only been using Ubuntu since end of October 2008, I have dual-boot with windows Xp.

If you mean you want to delete Linux and replace it with windows, Press DELETE or F18 When your machine starts up (Black & White screen) and make sure the boot from CD-ROM function is enabled in the BIOS (Blue & White Screen). Save and exit, restart with your windows CD still in CD/DVD drive it should as you if you want to boot from CD press enter.

Then you should be able to install windows, this will remove Ubuntu/Linux from your PC though, is this what you meant?

---

### Post by sirebral on 2008-11-12
I run a lot of programs on Wine.  It is buggy, but it is better then buggy at best.

If you are trying to load Windows on your Linux then you need a Virtual Machine.  Virtual Box is free, Win 4 Lin costs a little.

---

### Post by poebae on 2008-11-12
> **sirebral said:**
> WINe = Windows Emulator.
Funny that, because Wine stands for "Wine is not an emulator" :D

@Miss Karen, if you want to install Windows alongside Linux to use separately, you'll have to burn Windows to a CD. 

When you first turn on your computer you have to boot from it. It should say "Press any key to boot from the CD". If you don't get that option, you'll have to change your BIOS settings by pressing the Delete key as soon as your computer starts. From there, there'll be a menu where you can choose the order of boot devices, where you can put your CD-ROM higher in the list. It's a little intimidating at first, but it's not too complicated a process.

If you're looking to perform basic functions in Linux like watching videos/word processing etc, there'll be a Linux equivalent to the Windows software you're used to using.

Basically what you have to realise in order to use Linux is that software installation no longer involves double-clicking .exe files. Let us know which software you're trying to install, and we'll try to help you find a solution :)

---

### Post by snova on 2008-11-12
> **sirebral said:**
> WINe = Windows Emulator.

Correction: Wine Is Not an Emulator. And it isn't, by any means.

Wine is a program to run Windows programs from Linux. This would otherwise be impossible, for various technical reasons. Unfortunately, Wine does not always work. The best I can say is to give it a shot.

There is a database of programs known to work under Wine at: [http://appdb.winehq.org/](http://appdb.winehq.org/)

If your program is listed there, you may have better luck.

If Wine fails, there is a commercial variant called Crossover that may produce better results. I have not tried it.

---

### Post by sirebral on 2008-11-12
Sorry.  You guys are right.  I just think of it as an Emulator.

---

### Post by thiebaude on 2008-11-12
if your trying to install windows after ubuntu is installed, it wont work.Install windows first then install ubuntu.

---

### Post by sharkster2007 on 2008-11-12
> Funny that, because Wine stands for "Wine is not an emulator" 

Thats why I refered to it as a "Windows Simulator", Poebae is correct it is not an emulator, but a linux project set up to mimic windows programs to run on linux :-)

---

### Post by Miss Karen on 2008-11-12
> **sharkster2007 said:**
> Don't worry, I have only been using Ubuntu since end of October 2008, I have dual-boot with windows Xp.

If you mean you want to delete Linux and replace it with windows, Press DELETE or F18 When your machine starts up (Black & White screen) and make sure the boot from CD-ROM function is enabled in the BIOS (Blue & White Screen). Save and exit, restart with your windows CD still in CD/DVD drive it should as you if you want to boot from CD press enter.

Then you should be able to install windows, this will remove Ubuntu/Linux from your PC though, is this what you meant?


Yes, thankyou!


So after the first step (the BIOS bit) will that delete Linux then or will it still be on there until I install windows?

---

### Post by sharkster2007 on 2008-11-12
thiebaude is correct:

> if your trying to install windows after ubuntu is installed, it wont work.Install windows first then install ubuntu.

To dual boot Windows & Linux (Have the option to install and have the option to use both systems on the same machine) Windows has to be installed before Linux, then Linux is installed afterwards, this gives you a menu on booting up so you can select either Windows or Linux to load up everytime you start your machine.:-)

Both poebae and myself are correct then, your machine has to be able to boot up from CD as well as your Hard drive, then you should be able to start your machine up with the CD in still in the drive press enter when prompted then install windows. :-)

---

### Post by thiebaude on 2008-11-12
And also not all programs or games will run on Wine.

---

### Post by laffinet on 2008-11-12
Back to topic:

Miss Karen, can you please explain what you are trying to do:

1. run windows programs in Ubuntu
2. run windows alongside Ubuntu

Different solutions to both:

1. use wine or similar
2. set up a dual boot system or set up a virtual box within Ubuntu and install windows to that

If you do 2 you obviously then have the ability to run windows programs

From what I understand you tried so far is simply boot into Ubuntu and then tried to run a windows install CD. That won't work, you're trying to install an operating system within another operating system. Won't work like that, for that you'd go option 2 above.

---

### Post by sharkster2007 on 2008-11-12
If you wish to replace linux and your machine can already boot from cd (most can), place your windows CD in drive, leave it in the drive, restart your machine, press enter when prompted to boot from cd,follow on screen instructions, this installs Windows but will remove Linux.

---

### Post by lbarnes on 2008-11-12
are you unable to boot from the windows disc?

oops, you beat me to it lol

---

### Post by Miss Karen on 2008-11-12
> **sharkster2007 said:**
> If you wish to replace linux and your machine can already boot from cd (most can), place your windows CD in drive, leave it in the drive, restart your machine, press enter when prompted to boot from cd,follow on screen instructions, this installs Windows but will remove Linux.



Got it now!!! thankyou!!!!!

@ laffinet - I was originally trying to boot windows programs in linux with a view to installing windows, but not dual boot. But now I think I can make it work. thanks all!

---

