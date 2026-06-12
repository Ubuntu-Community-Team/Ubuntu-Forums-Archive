---
title: "Over 1 month"
date: 2012-04-16
forum: New to Ubuntu
---

### Post by manners2345 on 2012-04-16
Back on March 7, I tried to get some help on reloading my OS. I wanted to reload 10.04, so I would not be stuck doing new OS's every months or so. I was having many problems, which I did not explain, such as there were 3  Firefox's on my system and it was crashing all the time. My Cd did not work, it does not recognise when I put a cd in. I do not understand why everything is cd based, it is an electro-mechanical device, and very easy for it to go bad. Where as Flash Drives being purely electrical are much more reliable, especially if you have a battery backup system, for power outages which we have all the time. Really wanted to be able to format drive or used a different drive as I have a 500Gb and 250Gb. The 500 has nothing on it. apparently I have to be able start from scratch to be able to format or use different hard drive

A little over 4 years age I was told that Ubuntu, assume that you know what you are doing. That is not very good PR when trying to get ordinary users to switch from Windows.

I started to use the USB Startup Disk Creator to a 4GB flashdrive using torrent downloads, because supposedly no need to do checksums. After about 30 attempts I was able to create one with supposedly no errors. I tried loading, no luck, had problems with WUBI, so I tried Debian figured it was still using GRUB, still no luck, also tried Centos, same result. right now downloading Fedora to try.

Can I use USB disk creator to do other Linux Distros??  

I would not mind paying for help, my experience is that the paid help you get is not really any better than free help.

---

### Post by zdeuyo on 2012-04-16
Hello

I am not sure what your question is. When trying to boot make sure that you BIOS is set up to boot from usb first. Any other questions?

---

### Post by uRock on 2012-04-16
What errors are StartupDisk Creator giving you? You can easily place the LiveCD image on a thumb drive by following the instructions posted here. [http://ubuntuforums.org/showpost.php?p=11813568&postcount=2](http://ubuntuforums.org/showpost.php?p=11813568&postcount=2) I have done it a few times and they have come out working great.

---

### Post by PapaGary on 2012-04-16
> **manners2345 said:**
> 
Can I use USB disk creator to do other Linux Distros??  
Yes. Use [unetbootin]("http://unetbootin.sourceforge.net/").

---

### Post by anewguy on 2012-04-17
+1 unetbootin  - it has worked everytime for me.

As far as "bad P/R" for Linux/Ubuntu, someone told you wrong.  It's not Windows - it's a much different and far more powerful OS.  It's free.  Patches are free. Updates/upgrades are free.  Tech support?  This forum, and the other forums within the Ubuntu Forums umbrella, are fantastic, and they are free.  If you need immediate help, paid support is available via Canonical.

Because it's not Windows, some people try it thinking it SHOULD be, and therefore fail.  They don't take a little time to learn it - but some point in their life they had to learn Windows!  Once you have the basics down, particularly if you are like the majority of PC users in the world and mainly use it for web surfing, email, perhaps Skype or some other VOIP, perhaps movies or TV via Hulu, NetFlix, etc., word processing, budgeting, etc., these things are so similar to Windows and extremely easy to use. 

So, use unetbootin, and pay no attention to those who say you have to know what you're doing to use Ubuntu.  Ubuntu is probably the easiest Linux distribution you'll find.

Best of luck!

Dave ;)

---

### Post by manners2345 on 2012-04-17
USB is first, then cd, then hdd. This is a torrent download

This is what I get by trying to run wubi

7-Zip 9.04 beta  Copyright (c) 1999-2009 Igor Pavlov  2009-05-30
p7zip Version 9.04 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,2 CPUs)

Error: /media/A925-A5ED/wubi.exe: E_FAIL                

Errors: 1

If I open  setup.exe, There are two folders in it
$INSTDIR and $PLUGINSDIR  with lots of files

So what do I do now???

---

### Post by manners2345 on 2012-04-17
I have tried unetbootin, with out much success. my biggest problem is what I try to learn today I have forgotten by tomorrow, so I start all over, which tends to take hours.

---

### Post by mastablasta on 2012-04-17
> **manners2345 said:**
> I have tried unetbootin, with out much success. my biggest problem is what I try to learn today I have forgotten by tomorrow, so I start all over, which tends to take hours.
 
it is really difficult to help yiu if all you post is "not working". what si not working? at what point it stops? what are the errors?
 
for wubi install you create a folder put the .iso image you donwloaded in it and put the wubi exe file also in it. then you run wubi.exe and continue with install.
if you like pictures:
[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)
 
unetbootin couldn't be simpler to use select the downloaded .iso image file, select the place where you want it (your USB drive, which has to be pluged in) and then create the liveUSB. 3 steps. not sure what could go wrong ig the image is correct/good.
when i started i first read a book abotu older version of Ubutn and then i read this: [http://ubuntu-manual.org/](http://ubuntu-manual.org/)
 
windows also assumes you know what you are doing that's why so many people manage to install various viruses and malware on it. not to mention delete the system files like i did once thinking they are temporary files only...

---

### Post by manners2345 on 2012-04-18
I have tried to run unetbootin. no luck. no application to run exe's. If I try to open almost anything such as update manager, synaptic manager, computer janitor, they just kind of blinks at me(tries to open then immediately closes.

I am upgraded from 10.04 so I think am running maverick merkat, with this new desktop have not figured out to check version.

I tried to run  sudo apt-get check, everything seems okay.

---

### Post by mastablasta on 2012-04-18
> **manners2345 said:**
> I have tried to run unetbootin. no luck. no application to run exe's. 
if you are trying to run unetbootin in linux then: .exe files can not be run in linux. you need to use the linux version of unetbootin, not windows .exe version.
 
[https://launchpad.net/~gezakovacs/+archive/ppa](https://launchpad.net/~gezakovacs/+archive/ppa)
 
if oyu are trying to run it in windows it will run unless you have a computer virus/malware or something
 
 > 
I am upgraded from 10.04 so I think am running maverick merkat, with this new desktop have not figured out to check version.

 
you can check the version with terminal command
```
 
uname -a

```

---

### Post by manners2345 on 2012-04-19
I used unetbootin, this what I got from it,when I tried to run this also a torrent download

7-Zip 9.04 beta  Copyright (c) 1999-2009 Igor Pavlov  2009-05-30
p7zip Version 9.04 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,2 CPUs)

Error: /media/New Volume/wubi.exe: E_FAIL                

Errors: 1


This what is on the flash drive

/media/New Volume/casper
/media/New Volume/dists
/media/New Volume/install
/media/New Volume/isolinux
/media/New Volume/pics
/media/New Volume/pool
/media/New Volume/preseed
/media/New Volume/autorun.inf
/media/New Volume/ldlinux.sys
/media/New Volume/md5sum.txt
/media/New Volume/menu.c32
/media/New Volume/README.diskdefines
/media/New Volume/syslinux.cfg
/media/New Volume/ubnfilel.txt
/media/New Volume/ubninit
/media/New Volume/ubnkern
/media/New Volume/ubnpathl.txt
/media/New Volume/ubuntu
/media/New Volume/wubi.exe

I am beginning to think my BIOS maybe corrupted. I saw a line in a system log saying BIOS maybe corrupt, cannot find where I saw it to reference it

If I try to run autorun.inf,by double clicking, says it cannot find it

---

### Post by codemaniac on 2012-04-19
> **manners2345 said:**
> I am upgraded from 10.04 so I think am running maverick merkat, with this new desktop have not figured out to check version.

I tried to run  sudo apt-get check, everything seems okay.

You can see the Ubuntu version in a file called /etc/issue .Open up a terminal and place the below command .
```
cat /etc/issue
```

---

