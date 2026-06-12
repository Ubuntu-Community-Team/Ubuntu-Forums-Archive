---
title: "Installing Ubuntu on a computer that does not have any OS"
date: 2014-05-07
forum: New to Ubuntu
---

### Post by charlie21 on 2014-05-07
I need to install Ubuntu on my old laptop. The hard drive died, and I do not want to purchase windows again. Is there any way to install Ubuntu on the computer with a CD/DVD?

Thanks

PS: I am new to Ubuntu

---

### Post by kc1di on 2014-05-07
Hi charlie21 and welcome to Ubuntu Forums,

Yes indeed it should install fine.   You said old Laptop.  Give us some specs. how old , processor , ram video card etc. And will try to steer you to the right flavor for your machine.  if it too old unity most likely would not run.  so you may need lubuntu or xubuntu.
[URL="https://help.ubuntu.com/community/BurningIsoHowto"]
this page [/URL]will help get you started with the dvd /cd.

---

### Post by Bashing-om on 2014-05-07
charlie21; Hi ! Welcome to the forum.
Tough thing to make any advisements if truly :
> 
The hard drive died

ubuntu is great, but it is not that great. However, let us check and see what can be done, - Maybe it is the operating system on the hard drive that is corrupt and the hardware is good.

This is ubuntu, and we work with linux tools, to that end let's get some tools to work with.
Down load the latest release .iso " for "my old laptop" Lubuntu might be the better choice. Lubuntu is designed to run on older hardware. If ya got the horse power you may consider trying the top-of-the-line ubuntu. 
Download the .iso file:
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)
Verify the .iso file integrity:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Burn the .iso file as an image - NOT as data:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

once the .iso is burned to disk, boot the install medium (term: liveDVD)
Now as soon as the bios screen clears, depress and hold the right shift key -> language screen. escape key to accept the default; ->
Boot option screen -> choose " check disk for defects"
Once the checks are complete you will be pronpeted to reboot. Do it.

Boot back into the now known good liveDVD, get a good strong cup of coffee ( or beverage of choice ), and let's see what is.
Let it boot on it own ->
The liveDVD takes a L O N G time to load, patience, the files must be copied into ram, and the image decompressed, and the operating system started, you will see the various stages as changes in the screen - most often a black screen, cursor perhaps in the top left corner, patience.
Boots to a screen with 2 options
a) try ubuntu
b) install ubuntu
We going for "try ubuntu" /// more long long time to load up -> desk top
At the desk top for Lubuntu in the lower left corner is the application menu, in this is "disk utility"; activate "disk utility" and in the "disk utility" is the tool "check SMART status" or such. Take the time to use the tool to do the full test of the hard drive.
It comes back "passes" great, we are in business !

Install ubuntu ! from the desk top icon.
Make sure you have the machine plugged into a working wired (modem) internet connection and it is
Easy and straight forward. The install wizard takes care of all - if you accept a default install -> "erase disk and install ubuntu"//
Whoa, wait, got any data on the hard disk ya want to salvage ? .. now would be a good time to save your data. ubuntu can do that !
Back to the desk top open the file manager (icon lower left of screen ), plug in a usb thumb drive, open up the thumb drive ( icon now on the desktop) and just drag and drop files from the file manager window to the thumb drive window. 
OK, data all saved, going to install ubuntu as the sole and only operating system, right ? -> back to the easy way.

Choose install -> "erase disk and install ubuntu" , I suggest you do NOT check the boxes for "install updates" or "install 3rd party software" - the install goes faster and less chance of problems. We will take care of the updates and 3rd party software after the install completes.
Answer the few simple questions as to the keyboard in use, location, and the user info - REMEMBER your password choice, critical, you can not live ubuntu life with out it ! -> and the install wizard gets with it and does it's magic. let her rip and the install wizard takes care of the install, Depending on internet speed, about 15 minutes.

You are prompted to remove the disk, and press the enter key to reboot the system.

Welcome to ubuntu. 

Complete the install at this time:
desktop -> key combo ctl+alt+t yields a terminal interface ( not at all a scary thing, could be your best friend), terminal commands are faster and universal across all distributions and releases.

execute terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ubuntu-restricted-extras 

```
Lots of new files are added - updating all the files on you system to what is current from that of the liveDVD, and as well "restricted-extra" installing the non-free software you may enjoy and/or require.

Guess what, you are done. Now take you time - enjoy - and learn a new operating system.

[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by whitesmith on 2014-05-07
A ! (bang) to **Bashing-om** for one of the best, most detailed answers I've seen in a while. To **charlie21**: Since you're new to Ubuntu you might profit from reading the references in my sig line, especially the first. Good luck to you!

---

