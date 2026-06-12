---
title: "Trouble installing Ubuntu"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by tkaed on 2008-09-09
I was hoping that this install was going to be pretty easy and straight forward but looks like we're off to a problem right from the start.

I get to the main Ubuntu window to chose how I want to install. I tried using every method possible and after a 2-3 minute wait I get this error msg:
Buffer I/O Error on Device fd0

Can anyone tell me what's going on? 

Thanks in advance.

---

### Post by pytheas22 on 2008-09-09
This seems to be a [strange bug]("https://answers.launchpad.net/ubuntu/+question/7697") where the installer tries to access the floppy drive, which probably doesn't even exist (do you have one?).  Even if you don't have a floppy drive, try going into your BIOS and disable any floppy controllers on your motherboard before booting the Ubuntu CD; that may solve the problem.

If that doesn't work, you should be able to install by burning the alternative CD--go to [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and check the box that says, "Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer."  I think that the alternative installer, while not as pretty as that of the live CD, will work.

---

### Post by Threbus5 on 2008-09-09
Hmmmm.
Interesting that it would only try to install to the floppy.
Check bios settings to make sure that the hard drive is recognized and enabled.
If the hard drive is enabled, try another download of the installation file and another install.

---

### Post by jemate18 on 2008-09-09
> **tkaed said:**
> I was hoping that this install was going to be pretty easy and straight forward but looks like we're off to a problem right from the start.

I get to the main Ubuntu window to chose how I want to install. I tried using every method possible and after a 2-3 minute wait I get this error msg:
Buffer I/O Error on Device fd0

Can anyone tell me what's going on? 

Thanks in advance.

Download another ISO installer from another mirror and after booting the CD select check for errors to be sure that the installer you have burned contains no error. By the way, in burning the ISO file to the CD, try setting up a lower speed.

---

### Post by tkaed on 2008-09-09
Hey guys, 

Ok I had my boot settings CD>HD>FLOPPY. I'm going to try just completely disabling the floppy and see if that works. (I don't have a floppy drive, guess I should disable it in general.)

I did the burn on x2 and checked the CD for problems during one of the initial tries but always got the same problem. If the floppy problem doesn't fix it I'll try the other type of install and I'll burn it on 1x. 

I'll be in touch! Thanks guys!

---

### Post by bumanie on 2008-09-09
It may also be a good idea to do a md5checksum to ensure the integrity of the download. [Here's a guide]("https://help.ubuntu.com/community/HowToMD5SUM") to help you.

---

### Post by tkaed on 2008-09-09
I did the md5 before doing the initial burn.

I just tried changing my booting order and completely getting rid of floppy in the boot mgr but it still gave me the same problem so I'm going to try doing the alternative CD now see if that works.

---

### Post by tkaed on 2008-09-09
Ok burned the alternate cd at 1x speed to be safe. Seemed to start installer fine, but now it won't read my cdrom drive.

I built my own machine and this is the DVD drive I'm using. [http://www.newegg.com/Product/Product.aspx?Item=N82E16827151173](http://www.newegg.com/Product/Product.aspx?Item=N82E16827151173)

Maybe it won't recognize it because I'm using a dvd drive and not a cd drive? Idk? I thought Ubuntu installs were supposed to be easy...:p

---

### Post by vigyani on 2008-09-09
Sounds strange.

If the installer starts that means it is reading the CD from drive. Is it not?

Is there any error?

Please give detailed specs of your system and steps you are following to install.

regards
vig

---

### Post by tkaed on 2008-09-09
What kind of system specs do you need?

I tried installing Linux Mint and had the exact same fd0 error. Can anyone help me get to the bottom of this problem? Has anyone seen this before:

Buffer I/O Error on device fd0, logical block 0

---

### Post by bumanie on 2008-09-09
Don't know why the installation disk is trying to access your floppy drive. But what is your CPU, amount of RAM, Graphics card etc? I have installed ubuntu a number of times on various computers and never had an error message at all - so you are correct in thinking that ubuntu installations are easy, unfortunately in your case, something weird is happening.

---

### Post by tkaed on 2008-09-09
Here is most of my hardware, if you need to know more let me know. I just built this machine a few days ago.

ASUS P5Q Pro LGA 775 Intel P45 ATX Intel Motherboard
Intel Core 2 Duo E8400 Wolfdale 3.0GHz
G.SKILL 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 1000 (PC2 8000)
SAPPHIRE 100245L Radeon HD 4850 512MB 256-bit
CORSAIR CMPSU-650TX 650W
Western Digital Caviar SE16 WD6400AAKS 640GB 7200 RPM SATA
SAMSUNG 22X DVD±R DVD Burner with LightScribe Black SATA 

I did a clean install of Vista x64 with no problems.

---

### Post by bumanie on 2008-09-09
Certainly, hardware is not an issue, it should run ubuntu easily with plenty to spare for heavy apps etc. (Good system by the way). There is a mention of a similar bug when hardy was in alpha 2 release, but it would have been fixed by now - any way, the poster got the installation completed by using 'manual' at the partitioning stage. You could try to pre-partition the drive to ext3 with gparted. This can be run from the ubuntu live cd > sudo apt-get install gpartedFind it under System --> Administration --> Partition editor or download a dedicated gparted live cd from the gparted site. If prepartitioned ubuntu should see the partitions and you should be able to manually install to those partitions. Many users have three partitions - one for / one for swap and one for a separate /home. 8-10 gb / : 1-2gb swap and /home as large as you like. Hope something above helps.

---

### Post by tkaed on 2008-09-09
So should I try the livecd first? If that doesn't work I can try prepartitioning from windows.

---

### Post by tkaed on 2008-09-09
Er what I meant to say is should I try an older version of Ubuntu? I've read somewhere that that may be the way to do it.

---

### Post by Calabresi on 2008-09-09
Look, I read all the thread and your you are reading the wrong way, you told you dont have a floppy drive right? If thats the case you told you gone to the BIOS and set the ORDER of BOOT, that is not the right place to disable your FLOPPY in BIOS, go to the standart setup where you see the TIME settings and disks configuration, and completely disable your floppy, and try again.

---

### Post by tkaed on 2008-09-09
Thanks for the info Calabresi, I disabled the floppy completely and it seems to be a step in the right direction.

Now this is what happens. Ubuntu begins to load, I get the initial screen if I want to install, it loads for a while and then takes me to a shell prompt:

Busybox v1.1.3
(initramfs)

I can type help and it gives me a list of a lot of commands, and I can move around in the Linux directory. How do I get it to install though?

---

### Post by Calabresi on 2008-09-09
Ok, this one can be a lot of things, but will try to go on probabilities.

[This link]("http://ubuntuforums.org/showpost.php?p=3632827&postcount=1") can help you if all fail here, or you can go direct

1st- I read somewhere you have Vista there, so I suppose you want dual boot (That's my setup BTW, Ubuntu with Vista). Are you using alternate CD or Full graphical? You should use the full, the recommended in option by Ubuntu, that I presume is your 1st declared in this thread, note the alternate.

2nd- Did you get to the graphs, date options, local, formating, etc, before initramfs? If yes, what type of format are you trying? Use EXT3 if you can, it's the Linux actual format, it will not format your presumed Vista partition if you separeted it correctly with the percentage bar. Do this and try again

3rd- As I presume the Vista is there with a HD NTFS format, should not be a FAT or FAT32 problem, yet it can sometimes, even if Vista need NTFS, it can be instaled on FAT as I rarely saw, but can, without the security permissions set of course. You can then login in Vista and call Start botton-left and open >My Computer then >right click on your HD and >properties, search if FAT32 or NTFS, if FAT open DOS PROMPT and type

```
convert
```

follow instructions, finish, restart with Ubuntu CD inside, try install again.

If all that fail, you should read the link above and retrieve some logs to point exactly where is the fault.

---

### Post by tkaed on 2008-09-09
I have to be honest with you guys I've been trying to make this work since the morning and it is going pretty slow. If there was some kind of real time tech support I could get to install I would go ahead with it, but the way it's looking it's just not worth it for me to install Ubuntu.

Getting answers to problems is hard because most of the time people don't seem to know what is wrong, and it's not like there is an actual place to look to get all my answers.

If you guys could point me in the right direction for answers and real time support I'll give it a try, but spending an entire 8 hours plus without really getting anywhere is a bit too much for me.

---

### Post by pytheas22 on 2008-09-09
Yes, it can sometimes be frustrating to not receive responses as quickly as you'd like, especially when your problem is (as in your case) rather uncommon, meaning that few people can provide definitive answers.  But please keep in mind that everyone on here is volunteering--no one is paid or compensated in any way other than the satisfaction of helping other people use Linux.  If you want professional support, you can [buy it from Canonical]("http://www.ubuntu.com/support"), although I don't think it's intended for individuals as much as businesses etc.

I apologize for not responding sooner; I was busy with work all day.  But after reviewing your thread again, I think the best suggestion I can make right now is to tell you to try using [wubi]("http://wubi-installer.org"), which will allow you to install Ubuntu from within Windows (which I believe you have already installed on this computer) and hopefully bypass whatever issue is preventing the installer on the live CD from loading (which I suspect is a problem with the CD drive, but I'm not sure).

If wubi doesn't work for you, let me know and we can arrange a time where I can promise to be online and responsive for a few hours to help you try to figure this out all at once, without having to wait several hours for a response to your latest post.

---

### Post by Calabresi on 2008-09-09
It's frustrating as I done mine out-of-the-box.

I understand you and agree, I dont know what could be wrong with this install version, I have to say that lot of "new to Ubuntu" people are complaining about 2 weeks ago or so.

It's frustrating also that I know what Ubuntu is capable and I could not help you to know this great and beautyfull OS, that make me stop using my good Vista and XP that I have yet for couple of years now, sorry and hope you try it sometime later when this is fixed.

Sincerely,

Calabresi

---

### Post by cprofitt on 2008-09-09
I found two suggestions for this type of problem.. .I hope one of them works for you.

A workaround is to boot with "break=mount" and then when you have get the text prompt (press Enter to see it, because device detection messages hide it), type:
 rmmod floppy
 exit

The "floppy=off" boot option should also do the job. There's a long forum thread with many likely

---

