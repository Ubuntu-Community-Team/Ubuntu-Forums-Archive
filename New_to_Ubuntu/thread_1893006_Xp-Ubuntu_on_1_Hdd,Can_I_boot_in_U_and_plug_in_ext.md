---
title: "Xp-Ubuntu on 1 Hdd,Can I boot in U* and plug in ext-hdd and not worry of Virus jumpin"
date: 2011-12-09
forum: New to Ubuntu
---

### Post by EngineersGarage on 2011-12-09
just a quick question, 
If i have Xp on my laptop and Ubuntu, and I want  to check for viruses on a friends Hdd before I download some of his apps  &stuff. 

Can I boot in Ubuntu, then plug in his hdd and run a virus  check and not worry that if there is one(or many viruses) that it wont jump over to my Xp  partition?

And if there was a virus(s) found(lets say using avast), could i use Avast for ubuntu to  remove the virus then boot the hdd(PC) in my Xp installation to copy over the  apps and know that i would be safe following this procedure??

Thanx.

---

### Post by BC59 on 2011-12-09
The best way to clean a Windows computer is with a Live CD, or USB. Boot--try and then download Avast from the website. 

Here is explained how:

[http://www.howtogeek.com/howto/14434/scan-a-windows-pc-for-viruses-from-a-ubuntu-live-cd/](http://www.howtogeek.com/howto/14434/scan-a-windows-pc-for-viruses-from-a-ubuntu-live-cd/)

---

### Post by EngineersGarage on 2011-12-09
im not sure if you understood what i meant...

I already have OS on my pc.... I want some software from my friend but i suspect that he has viruses on there.

So what i want to do, if i understand the process correctly, is boot up in ubuntu, connect the ext hdd. run avast.kill the virus . (HERE IS THE QUESTION>>>DID THE VIRUS JUMP TO MY XP PARTICIAN??) then shutdown, boot up Xp. connect the hdd and download the software that i want knowing there is no more virus threat!

Is this how it works and will i be safe using this procedure?

---

### Post by BC59 on 2011-12-09
If you are not going to pass files to your partition there is no problem. The viruses are working only in Windows environment, they cannot be activated under Linux.

---

### Post by jaimeaux on 2011-12-09
> **EngineersGarage said:**
> im not sure if you understood what i meant...

I already have OS on my pc.... I want some software from my friend but i suspect that he has viruses on there.

So what i want to do, if i understand the process correctly, is boot up in ubuntu, connect the ext hdd. run avast.kill the virus . (HERE IS THE QUESTION>>>DID THE VIRUS JUMP TO MY XP PARTICIAN??) then shutdown, boot up Xp. connect the hdd and download the software that i want knowing there is no more virus threat!

Is this how it works and will i be safe using this procedure?

this will be safe, but nothing can be gauranteed. I would recommend several scans with different scanners, and as bc59 suggested, use a live cd to scan your hard drive as well. 

Even if it does get on your windows partition, you can remove it. It's a computer, it does what you tell it to do.

Hope this helps,

Jaimeaux"

---

### Post by EngineersGarage on 2011-12-09
Not when you get the win32vitro virus!!!

that smashed 3pc's and my ext hdd's... had to nuke the hdd just to get rid of it. there is no fix for it...the scaners only pick it up but cant get rid of it... 

This is the reason why I am here talking to you guys...wanting to switch to linux completely...windows is destructive... ive lost thousands of family photos etc over the years.

---

### Post by EngineersGarage on 2011-12-09
but i understand what he meant by running it through the live cd...

But why would i want to do that if i already have ubuntu on my pc?

---

### Post by EngineersGarage on 2011-12-09
i have 3 particaians, c: XP  e: Ubuntu  f: open space for music,pics,etc.

could the virus jump to any of the other particians while im in ubuntu doing the scans??

---

### Post by N00b-un-2 on 2011-12-09
being that Ubuntu is Linux and Windows viruses can not infect a linux system (at least not do any damage) because Windows bytecode can not be executed in Linux **unless you use Wine**, which is doubtful that the virus could do any harm.
In short, no.  Don't worry about it.  I boot into linux to clean viruses from infected computers all the time.  Use clam AV to run a scan if you're worried about potential infection.

---

### Post by EngineersGarage on 2011-12-09
Ok..Thanx alot!!

---

### Post by EngineersGarage on 2011-12-12
> **jaimeaux said:**
> this will be safe, but nothing can be gauranteed. I would recommend several scans with different scanners, and as bc59 suggested, use a live cd to scan your hard drive as well. 

Even if it does get on your windows partition, you can remove it. It's a computer, it does what you tell it to do.

Hope this helps,

Jaimeaux"

how do i scan with live cd if there is no anti virus on there??

---

### Post by N00b-un-2 on 2011-12-12
the easiest one to use I suppose would be clamtk.  Just open a terminal and 
```
sudo apt-get install clamtk
```
which installs an easy to use GTK frontend for Clam AV.  Refresh the Virus signature database, and then scan the directory you have Windows mounted to (should be /media/something).  If your windows partition is not mounted or won't mount in nautilus/thunar/dolphin, then you may need to mount it manually.

```
sudo -s
mkdir /media/Windows
fdisk -l
## pick your windows partition.  should be /dev/sdX something
mount -t ntfs /dev/sdX /media/Windows # replacing X with the partition number Windows is on.

```

Then point ClamTK to /media/Windows and run a scan.  I just repaired a friends computer using this method.

---

### Post by EngineersGarage on 2011-12-13
so would that be downloading the clam programe and then i could use it to do the scan??

And if im finished and I remove the cd, will i lose the downloaded clam av?

If, couldnt i make a live cd with the downloaded av on it and the i wouldnt have to download it every time i need to make a scan??

Thanx for the help sofar!

---

### Post by N00b-un-2 on 2011-12-13
> so would that be downloading the clam programe and then i could use it to do the scan??
Yes, installing ClamTK installs the ClamAV backend and and an easy to use graphical user interface.
> 
And if im finished and I remove the cd, will i lose the downloaded clam av?

yes, if you're booting from a live CD you will lose all data and apps once you reboot.  [I would recommend making a live USB with a persistence file]("https://help.ubuntu.com/community/Installation/FromUSBStick"), as it will store these after reboot.

> If, couldnt i make a live cd with the downloaded av on it and the i wouldnt have to download it every time i need to make a scan??

yes and no.  The way that a standard Ubuntu iso comes, yes.  However you could use Ubuntu Customization Kit, Remastersys or other tools to add custom packages to the iso.

---

### Post by EngineersGarage on 2011-12-16
Ok, but I have no Idea how to do something like that... Ive tried using remaster before but to no success...
could you give me like a walkthrough or something like that?

Thanx!

---

### Post by N00b-un-2 on 2011-12-16
the easiest thing to do is create a bootable USB with a persistence file.  There's about a dozen ways to do this on ANY operating system, but the easiest ways would be to use Linux Live USB creator on Windows [http://www.linuxliveusb.com/]("http://www.linuxliveusb.com/")
or use the Ubuntu USB creator ```
usb-creator-gtk
``` on Ubuntu.   You can also use Unetbootin, but I'm not sure if it is capable of creating a persistence file.

---

### Post by N00b-un-2 on 2011-12-16
As for remastersys, you must install it on a working ubuntu install.  The repo does not have a version packaged for Ubuntu after Karmic, but it should still be capable of spinning a custom distro based on Lucid, Maverick, Natty or Oneiric.

```

sudo nano /etc/apt/sources.list
## add the following line
deb http://www.geekconnection.org/remastersys/repository karmic/
## save /etc/apt/sources.list
sudo apt-get update
sudo apt-get install remastersys
```

---

### Post by EngineersGarage on 2011-12-19
I got the latest version of remastersys from the creator of the app. but it had problems running on a updated system, he said i should rather do a fresh install and then try it... he said something went wrong when i updated from 10.10 to 11.04... so i decided to download mint and start from there...havent got to do the backup yet though... will try this week...

---

