---
title: "VIA S3 Savage graphics card"
date: 2013-10-22
forum: New to Ubuntu
---

### Post by Michael_Kearney on 2013-10-22
I play with Ubuntu every few years but thats about it... I've been working with this computer for a few days now and can't get much done even with a lot of research. I've managed to connect to the internet and my USB printer but that's it.

Running Xubuntu 10.10 (Issues installing anything 11.04 or later)
I've been having a lot of issues getting packages to download, I've only been able to manually. Even some of those don't work.

I've tried logging on as root, i've changed my user account to administrator and put in the root group.

I can't edit the sources.list file ,  "Can't open file to write" is what I get when I try to save.
In terminal, I try to open it and get "error opening terminal: unknown"

Same thing happens with resolv.conf and printcap.

This is what I get when I try "sudo apt-get update && sudo apt-get upgrade"

```
<XT938:~$ sudo apt-get update && sudo apt-get upgrade                        
Ign http://us.archive.ubuntu.com maverick Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en       
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Ign http://us.archive.ubuntu.com maverick-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com maverick Release                    
Ign http://security.ubuntu.com maverick-security Release.gpg         
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://extras.ubuntu.com maverick Release.gpg                    
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en    
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US 
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com maverick-updates Release            
Ign http://us.archive.ubuntu.com maverick/main Sources               
Ign http://us.archive.ubuntu.com maverick/restricted Sources
Ign http://security.ubuntu.com maverick-security Release             
Ign http://extras.ubuntu.com maverick Release                        
Ign http://us.archive.ubuntu.com maverick/universe Sources
Ign http://us.archive.ubuntu.com maverick/multiverse Sources
Ign http://us.archive.ubuntu.com maverick/main i386 Packages
Ign http://us.archive.ubuntu.com maverick/restricted i386 Packages
Ign http://us.archive.ubuntu.com maverick/universe i386 Packages     
Ign http://us.archive.ubuntu.com maverick/multiverse i386 Packages   
Ign http://us.archive.ubuntu.com maverick-updates/main Sources       
Ign http://us.archive.ubuntu.com maverick-updates/restricted Sources 
Ign http://us.archive.ubuntu.com maverick-updates/universe Sources   
Ign http://us.archive.ubuntu.com maverick-updates/multiverse Sources 
Ign http://security.ubuntu.com maverick-security/main Sources/DiffIndex
Ign http://us.archive.ubuntu.com maverick-updates/main i386 Packages 
Ign http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages
Ign http://us.archive.ubuntu.com maverick-updates/universe i386 Packages
Ign http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Ign http://us.archive.ubuntu.com maverick/main Sources
Ign http://us.archive.ubuntu.com maverick/restricted Sources
Ign http://extras.ubuntu.com maverick/main Sources
Ign http://us.archive.ubuntu.com maverick/universe Sources
Ign http://us.archive.ubuntu.com maverick/multiverse Sources
Ign http://us.archive.ubuntu.com maverick/main i386 Packages
Ign http://us.archive.ubuntu.com maverick/restricted i386 Packages
Ign http://us.archive.ubuntu.com maverick/universe i386 Packages     
Ign http://us.archive.ubuntu.com maverick/multiverse i386 Packages   
Ign http://us.archive.ubuntu.com maverick-updates/main Sources       
Ign http://us.archive.ubuntu.com maverick-updates/restricted Sources 
Ign http://us.archive.ubuntu.com maverick-updates/universe Sources   
Ign http://us.archive.ubuntu.com maverick-updates/multiverse Sources 
Ign http://security.ubuntu.com maverick-security/restricted Sources/DiffIndex
Ign http://security.ubuntu.com maverick-security/universe Sources/DiffIndex
Ign http://security.ubuntu.com maverick-security/multiverse Sources/DiffIndex
Ign http://security.ubuntu.com maverick-security/main i386 Packages/DiffIndex
Ign http://security.ubuntu.com maverick-security/restricted i386 Packages/DiffIndex
Ign http://security.ubuntu.com maverick-security/universe i386 Packages/DiffIndex
Ign http://security.ubuntu.com maverick-security/multiverse i386 Packages/DiffIndex
Ign http://extras.ubuntu.com maverick/main i386 Packages
Ign http://us.archive.ubuntu.com maverick-updates/main i386 Packages
Ign http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages
Ign http://us.archive.ubuntu.com maverick-updates/universe i386 Packages
Ign http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Err http://us.archive.ubuntu.com maverick/main Sources               
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com maverick/restricted Sources         
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com maverick/universe Sources           
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com maverick/multiverse Sources         
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com maverick/main i386 Packages         
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com maverick/restricted i386 Packages   
  404  Not Found [IP: 91.189.91.14 80]
Ign http://security.ubuntu.com maverick-security/main Sources        
Ign http://security.ubuntu.com maverick-security/restricted Sources  
Err http://us.archive.ubuntu.com maverick/universe i386 Packages     
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com maverick/multiverse i386 Packages   
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com maverick-updates/main Sources       
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com maverick-updates/restricted Sources 
  404  Not Found [IP: 91.189.91.14 80]
Ign http://extras.ubuntu.com maverick/main Sources                   
Err http://us.archive.ubuntu.com maverick-updates/universe Sources   
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com maverick-updates/multiverse Sources
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com maverick-updates/main i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com maverick-updates/universe i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Ign http://security.ubuntu.com maverick-security/universe Sources    
Ign http://security.ubuntu.com maverick-security/multiverse Sources
Ign http://security.ubuntu.com maverick-security/main i386 Packages
Ign http://security.ubuntu.com maverick-security/restricted i386 Packages
Ign http://security.ubuntu.com maverick-security/universe i386 Packages
Ign http://extras.ubuntu.com maverick/main i386 Packages
Ign http://security.ubuntu.com maverick-security/multiverse i386 Packages
Ign http://security.ubuntu.com maverick-security/main Sources
Err http://extras.ubuntu.com maverick/main Sources
  404  Not Found
Ign http://security.ubuntu.com maverick-security/restricted Sources
Ign http://security.ubuntu.com maverick-security/universe Sources
Ign http://security.ubuntu.com maverick-security/multiverse Sources
Ign http://security.ubuntu.com maverick-security/main i386 Packages
Ign http://security.ubuntu.com maverick-security/restricted i386 Packages
Err http://extras.ubuntu.com maverick/main i386 Packages
  404  Not Found
Ign http://security.ubuntu.com maverick-security/universe i386 Packages
Ign http://security.ubuntu.com maverick-security/multiverse i386 Packages
Err http://security.ubuntu.com maverick-security/main Sources
  404  Not Found [IP: 91.189.92.181 80]
Err http://security.ubuntu.com maverick-security/restricted Sources
  404  Not Found [IP: 91.189.92.181 80]
Err http://security.ubuntu.com maverick-security/universe Sources
  404  Not Found [IP: 91.189.92.181 80]
Err http://security.ubuntu.com maverick-security/multiverse Sources
  404  Not Found [IP: 91.189.92.181 80]
Err http://security.ubuntu.com maverick-security/main i386 Packages
  404  Not Found [IP: 91.189.92.181 80]
Err http://security.ubuntu.com maverick-security/restricted i386 Packages
  404  Not Found [IP: 91.189.92.181 80]
Err http://security.ubuntu.com maverick-security/universe i386 Packages
  404  Not Found [IP: 91.189.92.181 80]
Err http://security.ubuntu.com maverick-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.181 80]
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz  404  Not Found [IP: 91.189.92.181 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz  404  Not Found [IP: 91.189.92.181 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz  404  Not Found [IP: 91.189.92.181 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.92.181 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.181 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.181 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.181 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.181 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
michael@michael-P5285A-ABA-XT938:~$ sudo nano /etc/printcap
Error opening terminal: unknown.
michael@michael-P5285A-ABA-XT938:~$ whoami
michael
michael@michael-P5285A-ABA-XT938:~$ whoami
michael
michael@michael-P5285A-ABA-XT938:~$ sudo nano /etc/apt/sources.list
Error opening terminal: unknown.
michael@michael-P5285A-ABA-XT938:~$ sudo nano /etc/resolv.conf
Error opening terminal: unknown.
michael@michael-P5285A-ABA-XT938:~$   

```

If you need more info, which I'm sure I left out, let me know.

---

### Post by Impavidus on 2013-10-22
10.10 is unsupported, therefore the repositories are no longer there. You could try the server for old releases, search the forum on how to do this. You'll have to modify sources.list manually. You can edit the file with **gksu gedit <filename>**. Don't try logging in as root.

Can you give some details about your hardware? With some work, it may be possible to install a recent version of Ubuntu or one of it's lighter flavours after all.

Edit: I see you have a problem with **sudo nano /etc/apt/sources.list**, which should work.

---

### Post by Michael_Kearney on 2013-10-22
I have an HP Pavilion xt938, 512 MB RAM, 1.3GHz Athlon processor. onboard graphics, 32MB memory.

I'd love to install a new version but the issues I have are that the desktop installers have issues displaying correctly, the screen is jacked. I don't know if the onboard graphics can handle it or what. I've tried two monitors and two VGA cables.

I've tried the alternate install as well and it gets stuck in the beginning with the language selection. I'm having trouble remembering what exactly happens so I'll run through it again. And I've been doing installs from USB via PLoP boot manager.

I'll look for the old repositories as well.

---

### Post by fantab on 2013-10-22
You must use Lubuntu on that machine. 
[http://lubuntu.net/](http://lubuntu.net/)

---

### Post by Michael_Kearney on 2013-10-22
Should I be able to install 13.10? I've tried lubuntu as well.... I have graphics issues with the desktop installer, with the alternate installer it is stuck at the language select screen. With either install, I have never been able to select a language, but with the desktop installer it counts down and proceeds on its own, and then the desktop loads and is not displaying right. 

Alternate install just sits on the language select screen, unresponsive. Is it possible my keyboard isn't working for the install? It's a wireless logitech keyboard but it works fine in BIOS and PLoP.

---

### Post by fantab on 2013-10-22
What graphics card do you have on that machine?

Have you tried the [NOMODESET]("http://ubuntuforums.org/showthread.php?t=1613132") option?

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

---

### Post by Michael_Kearney on 2013-10-22
Onboard graphics, VIA S3 Savage for, UMA up to 32mb.

According to the motherboard specs, it has an AGP slot, but it looks like the socket was removed, or never installed...

Will look into the nomodeset option.

---

### Post by Michael_Kearney on 2013-10-22
I'm upgrading to 11.04 as we speak.... (xubuntu) I mounted the iso from flash drive and am upgrading that way... was goin alright but now says 
> Could not calculate the upgrade
An unresolvable probem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages


I'm unable to select the language, and other options to get to nomodeset for the desktop cd, i think my wireless keyboard isnt recognized at that stage. I'm trying to get my hands on a wired ps2 keyboard now.

---

### Post by mörgæs on 2013-10-22
Upgrading is risky. Upgrading through unsupported versions like 11.04 and 11.10 is even more. 

I would suggest beginning with the 13.10 [mini.iso]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall"). Please post again when that works and then we can take a look at the desktop environment.

Besides... if you can get another graphics card it will make a big difference. Do you have a PCI or PCI-E slot?

---

### Post by Michael_Kearney on 2013-10-22
> **mörgæs said:**
> Upgrading is risky. Upgrading through unsupported versions like 11.04 and 11.10 is even more. 

I would suggest beginning with the 13.10 [mini.iso]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall"). Please post again when that works and then we can take a look at the desktop environment.

Besides... if you can get another graphics card it will make a big difference. Do you have a PCI or PCI-E slot?

Well... I do have some PCI slots but I don't know that I care enough to spend money on a pci video card. I will look into the minimal install if I can't get it to work this time with the 13.10 I have. I have a PS/2 keyboard hooked up now, and am able to use that since the wireless one wasn't working on the language select screen.

If I do manage to get a supported release installed I think that would most likely fix my issues. I'll see how it goes from here.

---

### Post by Petro Dawg on 2013-10-22
Lately, if I can't get Ubuntu to run to well on an old machine, I've had pretty good success with [Puppy]("http://puppylinux.org/main/Download%20Latest%20Release.htm").  The latest versions look good and are reasonably easy to use.  If Lubuntu is giving you fits, you might look into Slacko (latest build) or Precise Puppy (which is a LTS version and supposed to be compatible with Ubuntu packages).

---

### Post by Michael_Kearney on 2013-10-22
Thanks. I'll keep it in mind

Lubuntu 13.10 mini is installing now.... going well but I got an error installing GRUB.

> Unable to Install GRUB in /dev/sda
Executing 'grub-install /dev/sda' failed
This is a fatal error

I guess I'll push onward

---

### Post by Petro Dawg on 2013-10-22
If the only program that failed during installation was Grub, you might be able to recover it by running a live session of Lubuntu and running boot repair.

See the following link for instructions.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Michael_Kearney on 2013-10-22
Well it finsihed and it did not load the desktop. I'm looking at the shell.

I got an "ALERT! /dev/sdb1 does not exist. Dropping to a shell!"

---

### Post by fantab on 2013-10-23
It looks like you installed grub to /dev/sdb1 which I think is your USB pendrive. You should install grub to /dev/sda the HDD and not the partition like /dev/sda2 or /dev/sda3.
If you have two hard drives and if you have installed Lubuntu to the second hard drive which will be /dev/sdb then install grub to /dev/sdb and not the partition like /dev/sdb1, /dev/sdb3 etc.

---

### Post by Michael_Kearney on 2013-10-23
Ok... Thanks. I will try that. I was confused because it seemed like it was waffling between sda and sdb, I didn't realize my flash drive was showing up. That may be it.
but didn't it try earlier? See where it told me it failed to install grub to /dev/sda, why would I get that? And that is what I need to get done, right?

also, thought I mentioned, but once grub didn't install, it prompted me to install LILO instead. It seemed to go correctly and I was able to finish the install and reboot. That is when I got the error of /dev/sdb1 not existing.

---

### Post by Michael_Kearney on 2013-10-24
ok, it's seeing the flash drive as sda and the hdd as sdb, so I need to instal to sdb, right, does it matter what it sees as sda or sdb? they're just names, right?

---

### Post by Michael_Kearney on 2013-10-24
Alright.... this time when it asked if I wanted to install grub to the mbr i said no, and had it install to dev/sdb1 which should have been my hard drive. It finished install with no errors and installed lubuntu core. but now it won't boot to the desktop. well, it does but I can't see it. the display is either just blank or shows a garbled display. I can boot into the root shell fine.

---

### Post by fantab on 2013-10-24
Grub should be installd on the HDD not its partition, in linux terms on /dev/sdb and NOT on /dev/sdb1... You can fix this with [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") you can run boot-repair from either Ubuntu dvd/usb or from the working ubuntu install.

What Graphics card do you have on board? 
Meanwhile try [NOMODESET]("http://ubuntuforums.org/showthread.php?t=1613132") Option at boot. Nomodeset option runs with basic, generic opensource drivers.

---

### Post by Michael_Kearney on 2013-10-24
Thanks for the help. I'll try. it's running onboard graphics, which is VIA S3 Savage4 if I remember correctly. 32mb.

---

### Post by Michael_Kearney on 2013-10-24
Can I set it to nomodeset with the minimal install?

---

### Post by Michael_Kearney on 2013-10-24
I ran the Live CD with the nomodeset option enabled and still had video errors displaying the desktop, so it also won't work if I go through and install it, right? Is my onboard graphics just incapable of using any new-ish version of ubuntu?

---

### Post by mörgæs on 2013-10-24
> **Michael_Kearney said:**
> ... when it asked if I wanted to install grub to the mbr i said no

Let's take this in small steps. Please try to install the mini.iso with Grub on MBR, nothing more.

---

### Post by Michael_Kearney on 2013-10-24
Well, when I did id tried to do that on the USB drive. I have it on /dev/sdb/ now. it seems to be working ok but I suppose I can change it.

At any rate, I'm now just trying to connect remotely to this computer since I'm just wanting to use it as a server anyway for files and for a connected printer. I can connect to it through terminal from my laptop but I can't get Remmina to connect.

---

### Post by Michael_Kearney on 2013-10-24
okay... got boot repair run and here we go:

[http://paste.ubuntu.com/6298537/](http://paste.ubuntu.com/6298537/)

so i'm good, right?

---

### Post by fantab on 2013-10-25
It does look good...

---

### Post by Michael_Kearney on 2013-10-25
So... Everything is installed correctly. It boots. I can login remotely via terminal and do anything there. I can't figure out how to display the desktop remotely yet, but basically, if I want to boot this system itself I need another graphics card? I tried booting with nomodeset and it still wouldn't work. Is there anything else I can try?

---

### Post by mörgæs on 2013-10-25
Your last post has been moved to a new thread.
If case is closed regarding the old card please mark this one solved.

---

