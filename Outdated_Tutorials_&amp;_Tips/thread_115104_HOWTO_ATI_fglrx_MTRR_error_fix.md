---
title: "HOWTO: ATI fglrx MTRR error fix"
date: 2006-01-09
forum: Outdated Tutorials &amp; Tips
---

### Post by flight_master on 2006-01-09
Hello,

This is my first how-to, so bear with me ;) Let's get started, shall we?

First off, this HOWTO addresses the issues thatmany users of ATI cards have had. The symptoms are like this:

You install the drivers (via apt-get, or from ATI's website). Everything loads, and looks good. BUT! glxgears gives very laggy output, you can't play 3-d games, and performance is low. If you open a k/console, and issue:
```
 cat /proc/mtrr 
``` 
You'll get an answer like this: 
 reg00: base=0x00000000 ( 0MB), size=**984064MB**: write-back, count=1
Yes, that's right, it's reporting close to **1 TB!!!!** of memory!


Congratulations! You qualify for solving the problem with this how-to :D 

** What does 'mtrr' have to do with drivers? Why is this an issue?**

It seems that some users have issues with the BIOS reporting the wrong amount of memory to the OS, which causes the mtrr regions to be much larger than the actual memory in the machine. Thus, when the drivers try to load the mtrr rages for the video card's memory, they are unable to do so.


**How is this problem fixed?**

Simple. Over-write the mtrr files manually.

**How do I go about doing that?**

First, boot up in text-only mode (use the failsafe boot option in GRUB).

Next, make sure you are root, and issue this command twice,  done by typing the following text, and hitting enter:

```

echo "disable=0" >| /proc/mtrr

``` This will clear the faulty entry.
Make sure the file is now empty:

```

cat /proc/mtrr

``` That command should return an empty line.

If it isn't blank, then repeat: ```

echo "disable=0" >| /proc/mtrr

``` 

If the line is empty, issue this command:
```

echo "base=0x00000000 size=<SIZE HERE> type=write-back" >| /proc/mtrr

``` 
Replace the <SIZE HERE> with a hex value for your * main* system memory. Table below:
0x10000000 = 256 MB
0x20000000 = 512 MB
0x40000000 = 1024 MB
0x80000000 = 2048 MB

Finally, issue:
** for KDE:**
```

kdm
``` ** for Gnome:**
```
gdm
``` 
** How do I test if it works?**

Open a console/Konsole, and type the following:
```

cat /proc/mtrr
``` 
You should have output like:

```

reg00: base=0x00000000 (   0MB), size= 512MB: write-back, count=1
reg01: base=0xd0000000 (3328MB), size= 128MB: write-combining, count=1
reg02: base=0xf0000000 (3840MB), size= 128MB: write-combining, count=1

``` 
If you do, do a video test:

```
 fgl_glxgears
``` 
If it flies, you have diagnosed the error, and you can use 3D accelleration...


[COLOR=Red]**But WAIT! What happens on Reboot?**[/COLOR]

The /proc/mtrr file is modified on each reboot. To keep our settings, we need to create a boot-up script, which writes the mtrr file on boot. To do this, open a console/konsole, and do the following:

1. As root, create a text file called fix_mtrr in **/etc/init.d/** You can use Nano as an editor in this case, so:
```
 sudo nano /etc/init.d/fix_mtrr
``` 
The file should have this content:

```
 
#!/bin/sh
# Fix wrong MTRR setting
echo "disable=0" >| /proc/mtrr
echo "disable=0" >| /proc/mtrr
echo "base=0x00000000  size=0x20000000 type=write-back" >| /proc/mtrr

``` 
Use CTRL + X to exit, then Y to save, then ENTER to use the filename provided in Nano.

Now, you'll need to give execute permissions to this file:
```
 sudo chmod +x fix_mtrr 
``` 
Finally, we need to link it to the rcS.d (startup-script) directory:
```

cd /etc/rcS.d/
sudo ln -s ../init.d/fix_mtrr S03fix_mtrr

``` 
Now, it'll be automatically fixed on restart.


** Credits**

I'd like to thank a lot of people - but I dont' know all their names, so I'll just thank everyone on the Rage3D boards! 
Most of this information is gathered from numerous threads at Rage3D, not the least of which: [http://www.rage3d.com/board/showthread.php?t=33831753]("http://www.rage3d.com/board/showthread.php?t=33831753")



Sincerely,
Christian

---

### Post by torx on 2006-03-01
Hi, i have done the above instruction and am still having problems with 3d accel. Firstly,this is my output

> reg00: base=0x00000000 (   0MB), size= 512MB: write-back, count=1
reg01: base=0x20000000 ( 512MB), size=983296MB: write-back, count=1


The reg00 seems normal enough (however, it should be noted that i actually have 768mb of RAM but i used 512 as i couldnt find the corresponding hex value[?]). However reg01 is still reporting close to a terrabyte of memory. Also, when i start up, i get a "unable to start HAL" error (or something to that effect).

Any help is greatly appreciated.

---

### Post by flight_master on 2006-03-01
Hi,

Is that output after launching KDE? Can you please boot into text-only mode, follow the first-half of the HOWTO, and then post the output of ```
cat /proc/mtrr
```

It seems that you added a new entry, instead of overwriting the old one.
Did you run ```
 echo "disable=0" >| /proc/mtrr 
``` twice?

Also, use ```
size=0x30000000
``` for that amount of RAM.

-Christian

---

### Post by simulant on 2006-03-08
Hi, after reading this how-to I decided that This must be the problem! This is why I can't get my ATI drivers to work propely. Well, after doing the tutorial, i got this:

dmesg:

```
[4294712.752000] mtrr: type mismatch for d7c00000,100000 old: write-back new: write-combining
[4294712.752000] mtrr: type mismatch for d7800000,400000 old: write-back new: write-combining
[4294712.752000] mtrr: type mismatch for d7000000,800000 old: write-back new: write-combining
[4294712.752000] mtrr: type mismatch for d6000000,1000000 old: write-back new: write-combining
[4294712.752000] mtrr: type mismatch for d4000000,2000000 old: write-back new: write-combining
[4294712.752000] mtrr: type mismatch for d0000000,4000000 old: write-back new: write-combining
```

and with cat /proc/mtrr:

```
reg00: base=0x00000000 (   0MB), size=984064MB: write-back, count=2
```

...i'm a bit confused now. I really can't see what I did wrong. I've done all the ATI tutorials (at least twice) but nothig seems to work, right now I'm using the radeon driver, so now watching a full screen video doesn't lag, but dragging around a window in gnome takes almost 100% CPU (as all other 2d operations).

Well, if someone can figure out what I might have done wrong I would be very thankful. I kinda need my graphics to work (flawless), at leat for 2d, and this has taken some 3, 4 months now...

Thanks in advance.

---

### Post by flight_master on 2006-03-09
Hello,


Actually, It seems you some-how typed the input wrong. Did you follow the first part of my tutorial, using just the command-line, and then starting gdm/kdm?

-Christian

---

### Post by simulant on 2006-03-09
Well, at first i did it in gnome, in the terminal. Then I did the exact same thing as you wrote it. Do you think I have to "undo" something?

I'm really grateful for any help, I'm going to buy a nvidia card in a week or so if this ATI card of mine doesn't just magically start working :)

---

### Post by simulant on 2006-03-10
it looks like this now:

```
reg00: base=0x00000000 (   0MB), size=1024MB: write-back, count=1
reg01: base=0xd0000000 (3328MB), size= 128MB: write-combining, count=1
```

....fglrx still not working though...

---

### Post by simulant on 2006-03-10
actually, when i rebooted once more i got:

```
reg00: base=0x00000000 (   0MB), size=1024MB: write-back, count=1
reg01: base=0xd0000000 (3328MB), size= 128MB: write-combining, count=7
reg02: base=0xf0000000 (3840MB), size= 128MB: write-combining, count=1
```

maybe this isn't that good after all?

EDIT: thanks for the help! it seems to work! thank you!

---

### Post by flight_master on 2006-03-10
Hi,


That looks about right... Glad you got it working, if you need any help, please post the output of ```
 cat /var/log/syslog 
```

Don't post the entire output, just what relates to fglrx ;)


Regards,
Christian

---

### Post by vsunitha on 2006-04-05
Hi ! 
I am using Kubuntu Breezy 5.10. I encountered a lot of problems with fglrx (I have a ATI radeon 9200 -128MB card).
Thanks to Christian.. I was able to follow the How-To that you had compiled to fix my MTRR settings. I was able to get decent numbers for fgl_glxgears. I also followed your instructions about including the fix_mtrr script in /etc/init.d.. But, I don't see the MTRR settings after rebooting! Somehow, the script is not functioning as it should. Could you please help me out!

Thanks a lot!

---

### Post by flight_master on 2006-04-05
[quote=vsunitha]Hi ! 
I am using Kubuntu Breezy 5.10. I encountered a lot of problems with fglrx (I have a ATI radeon 9200 -128MB card).
Thanks to Christian.. I was able to follow the How-To that you had compiled to fix my MTRR settings. I was able to get decent numbers for fgl_glxgears. I also followed your instructions about including the fix_mtrr script in /etc/init.d.. But, I don't see the MTRR settings after rebooting! Somehow, the script is not functioning as it should. Could you please help me out!

Thanks a lot![/quote]


Hi,


This issue was something which had me ](*,) Can you please reboot your machine, and without touching anything, post the output of 
```
cat /proc/mtrr 
```?


Regards,
Christian

---

### Post by vsunitha on 2006-04-05
Hi ! 
After fixing the MTRR cat /proc/mtrr gave me the following output -
```
reg00: base=0x00000000 (   0MB), size=1024MB: write-back, count=1
reg01: base=0xe0000000 (3584MB), size= 128MB: write-combining, count=1
reg02: base=0xf8000000 (3968MB), size=  64MB: write-combining, count=1
```
and fglrxinfo gave me -
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200 DDR Generic
OpenGL version string: 1.3.1010 (X4.3.0-8.16.20)
```

Now, when I reboot the machine and run cat /proc/mtrr from Konsole, this is what I see:
```
reg00: base=0x00000000 (   0MB), size=984064MB: write-back, count=2
```
So, the boot-up script is not functioning as it should as the MTRR settings keep reverting back to the wrong settings !!
Any suggestions are welcome.. Thanks!

---

### Post by flight_master on 2006-04-05
This is something which is annoying me too... let me take a look into this when I get home, and see what I come up with :)

-Christian

---

### Post by vsunitha on 2006-04-05
Hi ! I was looking into this for a while.. I figured that there was a typo in the code for fix_mtrr -
```
#!/bin/sh
# Fix wrong MTRR setting
echo "disable=0" |> /proc/mtrr
echo "disable=0" |> /proc/mtrr
echo "base=0x00000000  size=0x20000000 type=write-back" >| /proc/mtrr
```

I just changed |> to >| (following the commands that you had mentioned in the How-To).. Now, everything works fine. I rebooted twice and the mtrr settings seem to be fine. fglrx also seems to be working well. 
Thanks ever so much... I have finally been able to get the ATI card working :)

---

### Post by flight_master on 2006-04-16
Hi,


I've been looking around, and finally found that typo too :P I'm a dumbell! I'll change it in the original post.

-Christian

---

### Post by sha_man on 2006-04-18
i tried that with my 768 MB ram (size=0x30000000) and it did not work :( 

here is what i get:
typing this (after the first try, after typing it a second time. still getting it, and so on....): ```
echo "disable=0" >| /proc/mtrr
``` I get this: ```
4294800.712000]mtrr: MTRR 0 not used
```. And ```
cat /proc/mtrr
``` does not give an empty line...:confused: 

So I tried (just to try)```
echo "disable=**1**" >| /proc/mtrr
```, and then, I get it empty with ```
cat /proc/mtrr
```:) 

Further, after typing then ```
echo "base=0x00000000 size=[COLOR="Red"]0x30000000[/COLOR] type=write-back" >| /proc/mtrr
```, because i have 768MB ram. I get this error: ```
[4294951.223000]mtrr: base (0x0000) is not aligned on a size(0x30000000) boundary
```.

With the parameter for 512MB (0x20000000), I don't get this error... However:

I made the boot script with the paramteres for 512 MB and this is what i get typing *cat /proc/mtrr* after rebooting: ```
reg00: base=0x00000000 (   0MB), size= 512MB: write-back, count=1
reg01: base=0x20000000 ( 512MB), size=983296MB: write-back, count=1

```
Any idea what's wrong?

---

### Post by sha_man on 2006-04-19
any help would be welcome since I think this is the cause of my ATI fglrx drivers not working.... :???:

---

### Post by sha_man on 2006-04-19
here a part of the /var/log/syslog:

```
Apr 18 00:41:00 localhost kernel: [4294712.628000] mtrr: type mismatch for d0000000,8000000 old: write-back new: write-combining
Apr 18 00:41:00 localhost kernel: [4294712.628000] [fglrx:firegl_addmap] *ERROR* mtrr allocation failed (-22)
Apr 18 00:41:00 localhost kernel: [4294712.629000] [fglrx] Internal AGP support requested, but kernel AGP support active.
Apr 18 00:41:00 localhost kernel: [4294712.629000] [fglrx] Have to use kernel AGP support to avoid conflicts.
Apr 18 00:41:00 localhost kernel: [4294712.629000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
Apr 18 00:41:00 localhost kernel: [4294712.629000] [fglrx] AGP detected, AgpState   = 0x1f004e1b (hardware caps of chipset)
Apr 18 00:41:00 localhost kernel: [4294712.629000] mtrr: type mismatch for e0000000,4000000 old: write-back new: write-combining
Apr 18 00:41:00 localhost kernel: [4294712.629000] [fglrx:firegl_unlock] *ERROR* Process 7912 using kernel context 0
Apr 18 00:41:00 localhost hp: unable to open /var/run/hplip/hpiod.port: No such file or directory: prnt/hpijs/hplip_api.c 75 
Apr 18 00:41:00 localhost kernel: [4294712.931000] mtrr: type mismatch for d0000000,8000000 old: write-back new: write-combining
Apr 18 00:41:02 localhost kernel: [4294714.861000] eth0: no IPv6 routers present
```

and

```
Apr 19 21:11:34 localhost gdm[7841]: gdm_slave_xioerror_handler: Schwerwiegender X-Fehler - :0 wird neu gestartet
Apr 19 21:11:36 localhost kernel: [4295061.314000] mtrr: type mismatch for d0000000,8000000 old: write-back new: write-combining
Apr 19 21:11:36 localhost kernel: [4295061.314000] [fglrx:firegl_addmap] *ERROR* mtrr allocation failed (-22)
Apr 19 21:11:36 localhost kernel: [4295061.315000] Fire GL built-in AGP-support
Apr 19 21:11:36 localhost kernel: [4295061.315000] Based on agpgart interface v0.99 (c) Jeff Hartmann
Apr 19 21:11:36 localhost kernel: [4295061.315000] agpgart: Maximum main memory to use for agp memory: 690M
Apr 19 21:11:36 localhost kernel: [4295061.315000] agpgart: Detected SiS 645dx chipset
Apr 19 21:11:36 localhost kernel: [4295061.316000] agpgart: AGP aperture is 64M @ 0xe0000000
Apr 19 21:11:36 localhost kernel: [4295061.316000] Power management callback for AGP chipset installed
Apr 19 21:11:36 localhost kernel: [4295061.316000] [fglrx] AGP detected, AgpState   = 0x1f004e1b (hardware caps of chipset)
Apr 19 21:11:36 localhost kernel: [4295061.316000] mtrr: type mismatch for e0000000,4000000 old: write-back new: write-combining
Apr 19 21:11:36 localhost kernel: [4295061.317000] [fglrx:firegl_unlock] *ERROR* Process 8752 using kernel context 0
Apr 19 21:11:36 localhost kernel: [4295061.569000] mtrr: type mismatch for d0000000,8000000 old: write-back new: write-combining
```

---

### Post by flight_master on 2006-04-19
Hello,

Ok, first off, if you don't have 512MB of memory, then don't use that setting. Next, what is your video card's memory set to in the BIOS? And finally,  can you paste the output of cat /proc/mtrr without running anything else? (Remove the bootscript first though).

-Christian

---

### Post by sha_man on 2006-04-19
hello, could you tell me how to remove the bootscript with all the links to it?

> what is your video card's memory set to in the BIOS?

I checked all the bios menus and didn't find a setting for this. Where should it be?

---

### Post by sha_man on 2006-04-20
hmm I think since my card is a Radeon 9800 XT, it should be 256MB, at least that's what it says in property dialog in Windows.

---

### Post by flight_master on 2006-04-20
Hi,

First off, to remove the bootscript:
```

sudo rm /etc/rcS.d/S03fix_mtrr
sudo rm /etc/init.d/fix_mtrr

```

The values you specify in that file are for main memory, not motherboard memory.

-Christian

---

### Post by sha_man on 2006-04-20
here the output of "cat proc/mtrr" with nothing running:

```
reg00: base=0x00000000 (   0MB), size=983552MB: write-back, count=1
reg01: base=0x20000000 ( 512MB), size=983296MB: write-back, count=1

```
:(

---

### Post by sha_man on 2006-04-21
so? :D

---

### Post by flight_master on 2006-04-22
Hi,


What happens when you try:

(boot into text mode, that would mean the failsafe boot option)

```

echo "disable=0" >| /proc/mtrr &&
echo "disable=1" >| /proc/mtrr &&
echo "base=0x0 size=0x30000000 type=write-back" >| /proc/mtrr &&
gdm

```


Type the whole thing in, not line by line ;)

-Christian

---

### Post by sha_man on 2006-04-22
ok, i did, and i got this:

```
[4294951.223000]mtrr: base (0x0000) is not aligned on a size(0x30000000) boundary
```

and entering it again, this:

```
4294800.712000]mtrr: MTRR 0 not used
```

:confused: :confused: :confused:

---

### Post by sha_man on 2006-04-25
Found this on Gentoo forums: 

> Seems this was a bug in linux kernels >2.6.12. The bug causes MTRR's not to be set correctly on certain steppings of Intel Pentium 4's and Xeon's. Found a patch on the kernel mailing list. Here's a link in case anyone else has this problem.

[http://lkml.org/lkml/diff/2005/9/28/323/1](http://lkml.org/lkml/diff/2005/9/28/323/1) 

Well i have a Pentium 4 and the 2.6.12-10-686 Kernel, but i don't know how to apply this patch :confused: 

Also found a howto to fix this error, but didn't work for me, maybe for others? 
[http://www.rage3d.com/board/showthread.php?threadid=33736241](http://www.rage3d.com/board/showthread.php?threadid=33736241)

---

### Post by flapane on 2006-09-27
hi
i have the same mtrr problems, and i set up this script:
#!/bin/sh
# Fix wrong MTRR setting
echo "disable=0" >| /proc/mtrr
echo "disable=1" >| /proc/mtrr 
echo "disable=2" >| /proc/mtrr 
echo "disable=3" >| /proc/mtrr
echo "disable=4" >| /proc/mtrr 
echo "disable=5" >| /proc/mtrr
echo "disable=6" >| /proc/mtrr
echo "disable=7" >| /proc/mtrr 
echo "base=0x0 size=0x40000000 type=write-back" >| /proc/mtrr
echo 'base=0xd0000000 size=0x10000000 type=write-combining' >| /proc/mtrr

I linked it correctly in rcS and did all the things, but if I try to reboot, it seems the script doesn't have any effect at all! The mtrr is still messed with 8entries as nothing have been done. If I manually launch the script, I get 
reg00: base=0x00000000 (   0MB), size=1024MB: write-back, count=1
reg01: base=0xd0000000 (3328MB), size= 256MB: write-combining, count=1

where 1024mb is my ram and 256mb on d0000000 is my x800gt, but obviously, it's useless to change the mtrr in graphic mode...
If I boot in text mode, launch manually the script and then boot in kdm, the mtrr is still messed, as the mtrr wouldn't care about my just-launched script

---

### Post by flight_master on 2006-09-27
Hi,


Can you post the output of 
```
 cat /proc/mtrr
```, when normally booting your computer?

Regards,
Christian

---

### Post by flapane on 2006-09-28
hi
the output is

reg00: base=0x00000000 (   0MB), size=1024MB: write-back, count=1
reg01: base=0xd7fc0000 (3455MB), size= 128KB: write-combining, count=1
reg02: base=0xd7f80000 (3455MB), size= 256KB: write-combining, count=1
reg03: base=0xd7f00000 (3455MB), size= 512KB: write-combining, count=1
reg04: base=0xd7e00000 (3454MB), size=   1MB: write-combining, count=1
reg05: base=0xd7c00000 (3452MB), size=   2MB: write-combining, count=1
reg06: base=0xd7800000 (3448MB), size=   4MB: write-combining, count=1
reg07: base=0xd7000000 (3440MB), size=   8MB: write-combining, count=1

---

