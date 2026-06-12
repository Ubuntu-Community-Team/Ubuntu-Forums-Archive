---
title: "HOWTO: Extend the Life of Your Thinkpad's Battery (tp_smapi)"
date: 2007-09-09
forum: Outdated Tutorials &amp; Tips
---

### Post by mbsullivan on 2007-09-09
**** EDIT: With newer versions of Ubuntu, the procedure for installing tm_smapi has gotten much easier. See [Thinkwiki]("http://www.thinkwiki.org/wiki/Tp_smapi#Installation_on_Ubuntu"). Do not follow the instructions to the letter anymore... This thread is probably only useful for historical reference, debugging, and for motivating the problem. ** **

You may or may not be aware that lithium ion batteries (like those present in the newer Thinkpad models) survive best when kept charged between 30%-85%.  They should not be kept fully charged, and should be left off for long periods of time charged to ~%40.  See [here]("http://www.thinkwiki.org/wiki/Maintenance#Battery_treatment") for more tips on Thinkpad battery treatment.

One way to extend the life of your Thinkpad's battery is to control the way it charges -- that is, to make sure that you keep it in the 30%-85% charged range whenever possible.  This is possible easily and quickly through the tp_smapi kernel module.

**Installing the tp_smapi Module:**

(1) Download the tp_smapi code [here]("http://sourceforge.net/project/showfiles.php?group_id=1212&package_id=171579").  For the examples presented here, let's assume that you download the tarball to your home directory (~/):

```
 wget http://superb-east.dl.sourceforge.net/sourceforge/tpctl/tp_smapi-0.39.tgz ~/tp_smapi-0.39.tgz
```(2) Make sure that you have the necessary pre-requisites installed.  You must have the necessary compiler and build tools (build-essentials), and the kernel source code for your kernel (linux-source-`uname -r`).  For the example below, it is assumed that you are using the newest kernel in the repository:

```
sudo aptitude install build-essential linux-source-`uname -r`
```(2b)  If you haven't gotten and extracted the kernel source code before, goto /usr/src, and extract the kernel source you got from the above step (which should be in a file called linux-source-2.6.2x.tar.bz2):

```
sudo -s
cd /usr/src
tar -xjf linux-source-2.6.2x.tar.bz2
```This should extract the source to linux-source-2.6.2x.  Be patient... decompressing bzip2 files takes forever!  (If you'd care to speed it up, however, there is a program in the Ubuntu repositories called pbzip2 which can decompress it with multiple threads, taking advantage of both CPU cores.)

(2c) Now go into /lib/modules/`uname -r`.  Both the "build" and "source" symbollic links should point to your source folder.  You can check this by observing the output of ln -l, or just create it this way with the following:

```
sudo -s
rm -i /lib/modules/`uname -r`/source /lib/modules/`uname -r`/build
ln -s /usr/src/linux-source-2.6.22 /lib/modules/`uname -r`/source
ln -s /usr/src/linux-source-2.6.22 /lib/modules/`uname -r`/build

```(3) Extract the tp_smapi code:

```
tar -xzf ~/tp_smapi-0.39.tgz
```(4) Change to the new directory, make and install tp_smapi:

```
cd tp_smapi-0.39 && make && sudo make install
```Should you want to use [HDAPS]("http://www.thinkwiki.org/wiki/HDAPS") (the IBM Active Protection System Linux Drive) in the future, include the HDAPS module in your build:

```
cd tp_smapi-0.32 && make && sudo make install HDAPS=1
```(5) Make sure that the tp_smapi module is loaded upon startup:

```
sudo -s;
echo "tp_smapi" >> /etc/modules
```(6) Now reboot, or load the tp_smapi module:

```
sudo modprobe tp_smapi
```(7) To set the charge thresholds, edit the following files:

> /sys/devices/platform/smapi/BAT0/start_charge_thresh 
/sys/devices/platform/smapi/BAT0/stop_charge_thresh For example, to keep the charge constantly varying between 30 and 85% while plugged into AC, use the following commands:

```
sudo -s;
echo "30" > /sys/devices/platform/smapi/BAT0/start_charge_thresh;
echo "85" > /sys/devices/platform/smapi/BAT0/stop_charge_thresh;
```This may interfere with your ACPI battery charge reports, since it will technically report "charged" at 30% battery (even though it will continue to cycle between 30 and 85 while plugged in).  Thus, for those who use a system monitor (such as Conky or GKrellM), the following may be a more practical solution:

```
sudo -s;
echo "81" > /sys/devices/platform/smapi/BAT0/start_charge_thresh;
echo "85" > /sys/devices/platform/smapi/BAT0/stop_charge_thresh;
```This will keep the charge below 85% when charged.

**Making the Change Permanent:**


Once it seems that you have charge control working on your laptop, it is possible to make the thresholds permanent. The way that I would recommend to do this is to use the sysfsutils, which should keep the battery set without any nastiness.  To do so:

(1) install sysfsutils, if they are not already installed
```
sudo aptitude install sysfsutils
```(2) add the appropriate lines to the end of /etc/sysfs.conf in the following format:

```
device=value
```For example, my sysfs.conf contains the following lines:

```
devices/platform/smapi/BAT0/start_charge_thresh=81
devices/platform/smapi/BAT0/stop_charge_thresh=85
```Hope this helps! Please let me know if you have any problems.

Mike

**Version History:**
1.0 (September, 2007) - Initial Post
1.1 (November, 2008)  - Updated Version Numbers and Added Permanent Insts
1.2 (March, 2011) - Added disclaimer to top (deprecated)

---

### Post by t.alex on 2008-01-26
Hi,

do you know how you can make the settings permanent? After i remove the battery/unplug the cord they're gone.

Greetings,
Alex

---

### Post by vronski on 2008-01-26
I keep receiving error message while trying to make and install tp_smapi:

```
sudo make install tp_smapi
Makefile:25: *** This driver requires kernel 2.6.19 or newer, and matching kernel sources. 
You may need to override KVER=2.6.22-14-generic or KSRC=/lib/modules/2.6.22-14-generic/source
 or KBUILD=/lib/modules/2.6.22-14-generic/build or
 MOD_DIR=/lib/modules/2.6.22-14-generic/kernel.  Stop.
```


As far as I know I fulfilled any requirements mentioned in wiki page of the project - The outcome of suggested steps is as follows:

1) apt-get install build-essential
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

2) kernel version:
```

uname -r
2.6.22-14-generic 
```

3) sources:
```

sudo apt-get install linux-source-2.6.22
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-source-2.6.22 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

```

4) make & install:
```

sudo make install tp_smapi
Makefile:25: *** This driver requires kernel 2.6.19 or newer, and matching kernel sources. 
You may need to override KVER=2.6.22-14-generic or
 KSRC=/lib/modules/2.6.22-14-generic/source or
 KBUILD=/lib/modules/2.6.22-14-generic/build or
 MOD_DIR=/lib/modules/2.6.22-14-generic/kernel.  Stop.

```


Also, the solution of above problem listed in wiki does not help: 
*If you get an error that the kernel version isn't matching (or that you need to set KSRC/KBUILD), please check that there is a symlink from the modules dir to the kernel source *


And the proper symlink exists:
```

 ls -l /lib/modules/2.6.22-14-generic
total 1736
lrwxrwxrwx  1 root root     40 2007-10-20 23:10 build -> /usr/src/linux-headers-2.6.22-14-generic
drwxr-xr-x  2 root root   4096 2007-12-19 21:30 initrd
drwxr-xr-x 10 root root   4096 2007-10-20 23:06 kernel
drwxr-xr-x  2 root root   4096 2007-11-24 14:19 madwifi
-rw-r--r--  1 root root 365097 2007-12-19 21:31 modules.alias
-rw-r--r--  1 root root     69 2007-12-19 21:31 modules.ccwmap
-rw-r--r--  1 root root 398630 2007-12-19 21:31 modules.dep
-rw-r--r--  1 root root    813 2007-12-19 21:31 modules.ieee1394map
-rw-r--r--  1 root root    527 2007-12-19 21:31 modules.inputmap
-rw-r--r--  1 root root  17714 2007-12-19 21:31 modules.isapnpmap
-rw-r--r--  1 root root     74 2007-12-19 21:31 modules.ofmap
-rw-r--r--  1 root root 272826 2007-12-19 21:31 modules.pcimap
-rw-r--r--  1 root root   1345 2007-12-19 21:31 modules.seriomap
-rw-r--r--  1 root root 170462 2007-12-19 21:31 modules.symbols
-rw-r--r--  1 root root 481106 2007-12-19 21:31 modules.usbmap
lrwxrwxrwx  1 root root     28 2008-01-25 20:05 source -> /usr/src/linux-source-2.6.22
drwxr-xr-x 10 root root   4096 2007-10-20 23:06 ubuntu
drwxr-xr-x  2 root root    380 2008-01-26 19:30 volatile

```


So, it seems that everything should work fine, but it is not.

I would appreciate any help.

---

### Post by jsroth on 2008-01-28
> **t.alex said:**
> Hi,

do you know how you can make the settings permanent? After i remove the battery/unplug the cord they're gone.

Greetings,
Alex


Hi,

I have the same problem and cant find any solution on the internet. If anybody had an idea i would love to hear about it!

---

### Post by sixela on 2008-01-29
Great How-to!

Just out of curiosity, what kind of thinkpad do you have?

Mine is a T61 and your how-to would be a great addition to the thinkwiki ubuntu install guide as this is not even mentioned there.

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_on_a_ThinkPad_T61)

---

### Post by Whiffle on 2008-01-30
To make it use the settings, I made a script called battery.sh in the /etc/acpi directory with this in it:
```

echo 90 > /sys/devices/platform/smapi/BAT0/stop_charge_thresh
echo 85 > /sys/devices/platform/smapi/BAT0/start_charge_thresh

```

I made that executable, and then in the directories ac.d, battery.d, resume.d and start.d I did:
```

ln -s /etc/acpi/battery.sh 41-battery.sh

```

Its kind of quick and dirty, but works great so far.

---

### Post by karvec on 2008-01-31
Quick question--  I'm pretty stupid with batteries, but just out of curiosity, doesn't a battery(rechargeable) have a limited number of recharges?  Like my Nintendo DS, reading the manual, I believe it has a li-ion battery, and it says it's good for about 500 charges...  So wouldn't the cycling between ~30%-85% be bad for it while plugged in?

Because, in essence, you are discharging it and charging it while plugged in, if that's what I'm reading...

So wouldn't that reduce the number of full cycles that it's chargeable, effectively reducing the life of the battery?

Just curious--  As I said, I'm pretty new to all this technology.  (For being 18 years old and living in US, that's saying something.  Heck, I just got a secondhand iPod a few weeks ago.)

And, thirdly, but not lastly, would this work on any laptop, if it doesn't reduce said cycles of battery?

Thanks for any feedback, I may start a new thread with a link to this if noone answers, just to see what the responses are.

Lastly--  Does anyone have any ideas on how to reduce wakeups/second from acpi, kernel IPI, and kernel core?  I get about 60 wakeups per second from those three processes(?) alone...  I think that if I can reduce them, I can increase my battery life significantly as well.


P.S.--  System specs.  Acer Aspire 5630-6188 (kickbutt budget computer) with a 160 GB hd, Pentium Core 2 Duo Centrino 1.66 Ghz(usually in the 1000mhz range...  ;)) 2 gigs of RAM, dvd-rw/ram drive--  After following all the recommendations in powertop, it still continues to have about 60-70 wakeups per second when not using the mouse.

C3 state does manage to get to around 17 ms and 99.2% of the time it's in C3, however, I think it would be a lot longer without said interrupts.

Thanks!!

---

### Post by Gigamo on 2008-01-31
Would this work on non-Thinkpad notebooks with lithium ion batteries?

---

### Post by Whiffle on 2008-01-31
Well, its not just the number of cycles that determines how long it will last.  In general, fully charging it or fully draining is bad, with fully draining being more of a problem.  IIRC, it causes chemical changes within the battery that reduce its capacity.  

I doubt the tp_smapi module will work on any laptop, but I wouldn't be surprised if these kinds of features were available on other laptops.  You'll probably just have to spend some time with google to figure it out.

---

### Post by mbsullivan on 2008-02-06
Hey Everybody,

Sorry for not responding before... this HOWTO was posted a while ago!

> Hi,

do you know how you can make the settings permanent? After i remove the battery/unplug the cord they're gone.

Greetings,
Alex

There are a number of ways to do it, such as the script that Whiffle created.  As some of you are discovering, virtual file system devices don't tend to stay the way you set them, and scripts might not be the best way to keep them set (although making it an ACPI script will keep re-enabling it, so it's a start)!

The way that I would recommend to do this is to use the sysfsutils, which are made for things handling sysfs devices, and thus will keep the battery set without any nastiness.  To do so:

(1) install sysfsutils, if they are not already installed
```
sudo aptitude install sysfsutils
```

(2) add the appropriate lines to the end of /etc/sysfs.conf in the following format:

```
device=value
```

For example, my sysfs.conf contains the following lines:

```
devices/platform/smapi/BAT0/start_charge_thresh=81
devices/platform/smapi/BAT0/stop_charge_thresh=85
```

This is also the appropriate place to set your CPU governor, for those of you who use speedstep.

> Would this work on non-Thinkpad notebooks with lithium ion batteries?

Nope, sorry. As Whiffle said, there very well may be a way to do it on your laptop, though.

> Just out of curiosity, what kind of thinkpad do you have?

I have an x61... I've really been meaning to fix up the thinkwiki pages, but sometimes they're really quite messy. The information's free if anybody should want to put it there!

> 
So, it seems that everything should work fine, but it is not.

I would appreciate any help.

Hmmm... it looks like everything's okay.  Are you sure that the Linux source directory has been un-tar-bz2ed? i.e. /usr/src/linux-source-2.6.22 exists, and not just /usr/src/linux-source-2.6.22.tar.bz2?

> Quick question-- I'm pretty stupid with batteries, but just out of curiosity, doesn't a battery(rechargeable) have a limited number of recharges? Like my Nintendo DS, reading the manual, I believe it has a li-ion battery, and it says it's good for about 500 charges... So wouldn't the cycling between ~30%-85% be bad for it while plugged in?

Because, in essence, you are discharging it and charging it while plugged in, if that's what I'm reading...

So wouldn't that reduce the number of full cycles that it's chargeable, effectively reducing the life of the battery?

The real limit on the life of lithium-ion batteries is not the number of times they have been charged, but rather the fact that they age over time.  Even if not used, the battery will eventually die.  That being said, there are some things that you should do to extend the life of your battery. These include:

(1) Avoid keeping at maximum voltage for extended periods of time, which leads to corrosion, especially at elevated temperatures (such as in a running laptop).

(2) Avoid storing the battery while in a depleted state, which can shorten battery life.

(3) Store the battery at cool temperatures, charged to ~40%.

So... keeping the battery charged between ~20-30% and ~80% won't magically make the battery last forever, but it does make sure that you are within the "safe operating guidelines" as often as possible.  See [this site]("http://www.batteryuniversity.com/") if you want to know more than you ever wanted about batteries.

It's understandable to be confused, because batteries are confusing!  Much of this confusion might come from nickel-based batteries, which are subject to memory (requiring full periodic discharges to prevent greatly shortened lifespan) and have a limited number of discharge cycles in them (~1000 for nickel cadmium, less for nickel-metal-hydride).  So... if the Thinkpad laptops had nickel-based batteries, tp_smapi definitely would not make much sense.  Lithiom-ion and lithium polymer batteries don't have these shortcomings... they just have a limited life span, which can be extended to a certain degree.

> Lastly-- Does anyone have any ideas on how to reduce wakeups/second from acpi, kernel IPI, and kernel core? I get about 60 wakeups per second from those three processes(?) alone... I think that if I can reduce them, I can increase my battery life significantly as well.

60 wakeups really isn't that bad... you could always halt the acpi daemon (acpid) from running if it's driving you that crazy, but it may seriously hamper the functionality of your laptop.  There are kernel options that will reduce power usage (tickless timer, etc), but if you're not rolling your own, they're probably already as good as you're gonna get.  The kernel will keep requiring fewer wakeups in the future, I'm sure. Have you tried other [tweaks]("http://www.lesswatts.org/tips/"), such as putting your Wifi card in low-power mode, etc?

Hope this helps!
Mike

---

### Post by Whiffle on 2008-02-06
Yeah I intend to roll my own kernel here pretty soon, once I find the time.  Pretty much everything works but its kind of a power hog ( around 17 watts).  According to think wiki, someones gotten an 1871 T43 down to 10 watts.  I think some kernel tweaking should bring that up, the standard feisty kernel doesn't seem to have any of the new power saving features.  I still get ~2 hours of battery life out of it though, although I never drain it below 40% or so.  

Just did the sysfsutils thing, thanks!

---

### Post by t.alex on 2008-02-07
> **mbsullivan said:**
> 
There are a number of ways to do it, such as the script that Whiffle created.  As some of you are discovering, virtual file system devices don't tend to stay the way you set them, and scripts might not be the best way to keep them set (although making it an ACPI script will keep re-enabling it, so it's a start)!

The way that I would recommend to do this is to use the sysfsutils, which are made for things handling sysfs devices, and thus will keep the battery set without any nastiness.  To do so:

(1) install sysfsutils, if they are not already installed
```
sudo aptitude install sysfsutils
```

(2) add the appropriate lines to the end of /etc/sysfs.conf in the following format:

```
device=value
```

For example, my sysfs.conf contains the following lines:

```
devices/platform/smapi/BAT0/start_charge_thresh=81
devices/platform/smapi/BAT0/stop_charge_thresh=85
```
Hope this helps!
Mike

Hi,
i already did that. I was wondering more if i can address/program the BIOS/firmware directly, make the changes and the charge levels would still be remembered if the laptop is shut down and charging... but i guess that can't be done.
Thanks,
Alex

---

### Post by Krydahl on 2008-02-07
I have  lenovo 3000 n200 - which is nearly a thinkpad. Do you know if this will work for that?

---

### Post by mbsullivan on 2008-02-07
> Hi,
i already did that. I was wondering more if i can address/program the BIOS/firmware directly, make the changes and the charge levels would still be remembered if the laptop is shut down and charging... but i guess that can't be done.
Thanks,
Alex

Yeah... it'll charge to 100% if you leave it plugged in whilst off.  Nothing really can be done about that.

> I have lenovo 3000 n200 - which is nearly a thinkpad. Do you know if this will work for that?

I'm honestly not sure... if you try it, keep us posted! Also, if you try it and get a "thinkpad_ec: no ThinkPad embedded controller!" error, try updating your BIOS.

Mike

---

### Post by kernalsanders123 on 2008-02-09
Hello all. I'm relatively new to Ubuntu, been using it on my desktop machine for the better part of a year, and am liking it. When the XP install on my T61 laptop went, I thought I'd tinker with Ubuntu on it. It's been good so far, except for being able to change my battery charging parameters. Anyway, I've been trying to install tp_smapi, but I've run into a bit of a stumbling block. I've followed the steps according to this thread, but when I try a make install for the tp_smapi code, it gives me a bunch of jibberish too long to post here. 

I think the problem may be that I don't have a proper symlink for build. For example, my output for symlinks for /lib/modules/2.6.22-14-generic is as follows:

```
dave@dave-laptop:~$ ls -l /lib/modules/2.6.22-14-generic
total 1648
lrwxrwxrwx  1 root root     28 2008-02-09 22:04 build -> /usr/src/linux-source-2.6.22
drwxr-xr-x  2 root root   4096 2008-01-29 17:19 initrd
drwxr-xr-x 10 root root   4096 2007-10-15 19:22 kernel
drwxr-xr-x  2 root root   4096 2008-01-29 17:22 madwifi
-rw-r--r--  1 root root 351274 2008-01-29 20:43 modules.alias
-rw-r--r--  1 root root     69 2008-01-29 20:43 modules.ccwmap
-rw-r--r--  1 root root 346289 2008-01-29 20:43 modules.dep
-rw-r--r--  1 root root    813 2008-01-29 20:43 modules.ieee1394map
-rw-r--r--  1 root root    527 2008-01-29 20:43 modules.inputmap
-rw-r--r--  1 root root   2622 2008-01-29 20:43 modules.isapnpmap
-rw-r--r--  1 root root     74 2008-01-29 20:43 modules.ofmap
-rw-r--r--  1 root root 267548 2008-01-29 20:43 modules.pcimap
-rw-r--r--  1 root root   1135 2008-01-29 20:43 modules.seriomap
-rw-r--r--  1 root root 164049 2008-01-29 20:43 modules.symbols
-rw-r--r--  1 root root 480020 2008-01-29 20:43 modules.usbmap
drwxr-xr-x  2 root root   4096 2008-01-29 20:43 nvidia
lrwxrwxrwx  1 root root     28 2008-02-09 22:04 source -> /usr/src/linux-source-2.6.22
drwxr-xr-x 10 root root   4096 2007-10-15 19:22 ubuntu
drwxr-xr-x  2 root root    220 2008-02-09 21:49 volatile

```

I noticed that a symlink for source is there, but there isn't one for build. I then attempted to add one:

```
root@dave-laptop:~# uname -r
2.6.22-14-generic
root@dave-laptop:~# rm -i /lib/modules/2.6.22-14-generic/build
rm: remove symbolic link `/lib/modules/2.6.22-14-generic/build'? y
root@dave-laptop:~# ln -s /urs/src/linux-source-2.6.22 /lib/modules/2.6.22-14-generic/build
root@dave-laptop:~# 

```

However, the symlinks for /lib/modules/2.6.22-14-generic still read as I posted above. So, my question ultimately is this: how do I add a symlink for build? I apologize if my post is a bit lengthy. Much of this is still a bit new to me, as this is about the deepest I've delved into the operating system, so to speak, so bear with me. Thank you in adavance.

P.S. I'm using Gutsy

---

### Post by kernalsanders123 on 2008-02-10
Please disregard my previous post, updated my kernel, and it installed without a hitch!

---

### Post by tastatur on 2008-04-10
I want to confirm that it works perfectly on my T60. If anyone, who comes later, has problem with install process can see my example below:

**1. Newest version of tp_smapi is 0.37**:
```
wget http://easynews.dl.sourceforge.net/sourceforge/tpctl/tp_smapi-0.37.tgz ~/tp_smapi-0.37.tgz"]wget http://easynews.dl.sourceforge.net/sourceforge/tpctl/tp_smapi-0.37.tgz ~/tp_smapi-0.37.tgz
```
Don't forget to extract this file :KS
**2. Install build-essential**
```
sudo aptitude install build-essential
```
**3. Check if you have linux-header on your computer**
```
ls -lah /usr/src/linux-headers-2.6.22-14
```
If you have something like this, OK, no need to install package linux-source-2.6.22 -->***[COLOR="Sienna"] go to step 5[/COLOR]***
```
drwxr-xr-x 19 root root 4.0K 2008-03-02 13:46 .
drwxrwsr-x  5 root src  4.0K 2008-04-10 12:50 ..
drwxr-xr-x 28 root root 4.0K 2007-10-16 01:22 arch
drwxr-xr-x  2 root root 4.0K 2008-03-02 13:46 block
drwxr-xr-x  2 root root 4.0K 2008-03-02 13:46 crypto
drwxr-xr-x  7 root root 4.0K 2007-10-16 01:22 Documentation
drwxr-xr-x 66 root root 4.0K 2008-03-02 13:46 drivers
drwxr-xr-x 62 root root 4.0K 2008-03-02 13:46 fs
drwxr-xr-x 43 root root 4.0K 2008-03-02 13:46 include
drwxr-xr-x  2 root root 4.0K 2008-03-02 13:46 init
drwxr-xr-x  2 root root 4.0K 2008-03-02 13:46 ipc
-rw-r--r--  1 root root 1.5K 2007-07-09 01:32 Kbuild
drwxr-xr-x  5 root root 4.0K 2008-03-02 13:46 kernel
drwxr-xr-x  5 root root 4.0K 2008-03-02 13:46 lib
-rw-r--r--  1 root root  50K 2008-02-12 08:08 Makefile
drwxr-xr-x  2 root root 4.0K 2008-03-02 13:46 mm
drwxr-xr-x 41 root root 4.0K 2008-03-02 13:46 net
drwxr-xr-x  9 root root 4.0K 2008-03-02 13:46 scripts
drwxr-xr-x  4 root root 4.0K 2008-03-02 13:46 security
drwxr-xr-x 18 root root 4.0K 2008-03-02 13:46 sound
drwxr-xr-x  2 root root 4.0K 2008-03-02 13:46 usr
```
**4. Download & Extract linux-source-2.6.22**
```
sudo aptitude install linux-source-2.6.22
cd /usr/src
sudo -s
tar -xjf linux-source-2.6.22.tar.bz2
```
You will have your linux-source at /usr/src/linux-source-2.6.22 -->***[COLOR="Sienna"] go to step 6[/COLOR]***
**5. Install**
- Go to folder, where you extracted tp_smapi-0.37.tgz, for my example: ~/tp_smapi-0.37
```
sudo make install HDAPS=1 KSRC=/usr/src/linux-headers-2.6.22-14
```
or without HDAPS:
```
sudo make install KSRC=/usr/src/linux-headers-2.6.22-14
```
Install successfull  -->***[COLOR="Sienna"] go to step 7[/COLOR]***
**6. Install with downloaded /usr/src/linux-source-2.6.22**
- Go to folder, where you extracted tp_smapi-0.37.tgz, for my example: ~/tp_smapi-0.37
```
sudo make install HDAPS=1 KSRC=/usr/src/linux-source-2.6.22
```
or without HDAPS:
```
sudo make install KSRC=/usr/src/linux-source-2.6.22
```
Install successfull  -->***[COLOR="Sienna"] go to step 7[/COLOR]***
**7. Post-Configuration**
- tp_smapi auto loaded at startup
```
sudo -s
echo "tp_smapi" >> /etc/modules
```
- set start-, stopcharge value auto at startup
```
cd /etc/acpi
gedit power.sh
```

**[COLOR="Sienna"]Here is my example for edited power.sh[/COLOR]**: add 2 new lines
```
#!/bin/bash

. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs

echo 95 > /sys/devices/platform/smapi/BAT0/stop_charge_thresh
echo 60 > /sys/devices/platform/smapi/BAT0/start_charge_thresh
.....

```
Save & Restart
**8. Check configuration**
After restart your computer, use this 2 commands to check if your configuration was executed correctly.
```
cat /sys/devices/platform/smapi/BAT0/start_charge_thresh
cat /sys/devices/platform/smapi/BAT0/stop_charge_thresh
```
Have fun !

@tastatur
-----------
Reference: why do i use power.sh to set configuration at startup
Check /etc/acpi/events/ac
```
# /etc/acpi/events/ac
# Called when the user connects ac power to us
# 

event=ac_adapter
action=/etc/acpi/power.sh
```
You dont need to set start-, stopcharge when you use "only" battery right :)

---

### Post by miga on 2008-05-18
> **tastatur said:**
> 

**[COLOR="Sienna"]Here is my example for edited power.sh[/COLOR]**: add 2 new lines
```
#!/bin/bash

. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs

echo 95 > /sys/devices/platform/smapi/BAT0/stop_charge_thresh
echo 60 > /sys/devices/platform/smapi/BAT0/start_charge_thresh
.....

```
Save & Restart
**8. Check configuration**
After restart your computer, use this 2 commands to check if your configuration was executed correctly.
```
cat /sys/devices/platform/smapi/BAT0/start_charge_thresh
cat /sys/devices/platform/smapi/BAT0/stop_charge_thresh
```



Hey, I'm using this at the moment.. but I get spammed with
[17539.965688] smapi smapi: set_real_thresh: set stop to 95 for bat=0
[17540.190538] smapi smapi: set_real_thresh: set start to 59 for bat=0
in systemlog (dmesg entries)
every 5 or so seconds.. 

Is that a normal function? if not, how do I reduce the ammount of checks done.. oh, and the charging of my battery is superslow while powered up and being used, but I guess that's how it is (brand new laptop, never tested in windows, tp R61i) Recharging done when powered off is fast, however :)

regards

---

### Post by mbsullivan on 2008-06-07
Hi Miga,

> Is that a normal function? if not, how do I reduce the ammount of checks done

Instead of adjusting the power settings with power.sh as shown, try using the sysfsutils (mentioned in one of my entries before). I should add this to the original post... I apologize.

The sysfsutils are made for things handling sysfs devices, and thus will keep the battery set without any nastiness (you'll see the message once in your log). To do so:

(1) install sysfsutils, if they are not already installed

```
sudo aptitude install sysfsutils
```

(2) add the appropriate lines to the end of /etc/sysfs.conf in the following format:

```
device=value
```

For example, my sysfs.conf contains the following lines:

```
devices/platform/smapi/BAT0/start_charge_thresh=81
devices/platform/smapi/BAT0/stop_charge_thresh=85
```

Thus, you have no "echo" commands, and the spamming should stop.

Let me know how it goes! Sorry for the slow response!
Mike

---

### Post by mike-g2 on 2008-10-03
Thanks for the very useful post.  

I would just add that you might want to add

        echo 15 > /sys/devices/platform/smapi/BAT0/inhibit_charge_minutes

in your power.sh file.  This will prevent your laptop from charging if it's plugged in for just a few minutes.

---

### Post by Porter Doran on 2008-10-20
Just how damaging to a battery is keeping it fully-charged? Would it really ruin a battery in, say, three months? My T61, which really is brand-new, has been kept mostly fully-charged. Last week Ubuntu popped up a notification that my battery seems to be damaged and cannot be charged more than half-way. Since then, I've noticed my laptop running out of battery power in -- oh -- fifteen minutes. An alarming thing for a new laptop! Any advice? (I am running 8.04.)

---

### Post by mbsullivan on 2008-11-13
> Just how damaging to a battery is keeping it fully-charged? Would it really ruin a battery in, say, three months? My T61, which really is brand-new, has been kept mostly fully-charged.

Hi Porter,

It's really not clear... it depends a lot on the charge regulation and charge termination rules that the integrated circuit used inside of the T61 charger uses. I've never really researched this, but my guess is that Lenovo is using a higher priced IC for charging the battery, so it really shouldn't make much difference.

Three months before a dead battery seems extreme... Perhaps your battery was faulty. I'm sure I had kept my battery (mostly) fully charged for a longer period than that after buying it, with no noticeable battery degradation.

I'm sorry to hear that about your battery... but at least it may be of some consolation to know that it wasn't you who ruined it.

Mike

---

### Post by Porter Doran on 2008-11-17
Lenovo's replacing my battery free of charge, next day shipping.

I'll certainly be putting into use the instructions in this thread in future! :)

---

### Post by mbsullivan on 2008-11-21
> Lenovo's replacing my battery free of charge, next day shipping.

I'll certainly be putting into use the instructions in this thread in future! 

Great! Thanks for the update!

Let me know if you have any problems following the instructions... One of these days I should update them -- they're starting to show their age, probably.

Mike

EDIT (11/27/08): I just updated the links to the newest version of tp_smapi, and cleaned some things up. Everybody, please let me know any suggestions you have as to things that would make this tutorial better.

---

### Post by ezzieyguywuf on 2008-12-04
My comp doesn't seem to discharge at all. Everything seems to work fine, but it appears as if my computer just doesn't charge at all when its within the range that I set. Is this normal?

---

### Post by mbsullivan on 2008-12-05
> My comp doesn't seem to discharge at all. Everything seems to work fine, but it appears as if my computer just doesn't charge at all when its within the range that I set. Is this normal?

If you mean that the battery stays at the threshold charge and doesn't oscillate between the bounds when plugged in... then "yes", this is proper behavior.

Mike

---

### Post by ezzieyguywuf on 2008-12-05
so then whats the point of setting a minimum and maximum threshold? this doesn't make sense to me.

---

### Post by civetta on 2009-05-04
Does anyone know if tp_smapi would work with the T500 with Jaunty? My main question is whether I could enable the battery-saving features, like powering off the cd drive. Now, without tp_smapi compiled, the led light on the ultrabay cd drive stays on all the time, even when suspended.

---

### Post by yaneurabeya on 2009-08-13
I found this link trolling around looking for a battery cycling scheme for my work T61. 

Here is an expedited way to get everything installed from start to finish --

Install script:

```
#!/bin/sh
#
# tp-smapi-source-install.sh
#
# Installs any and all required debian pkgs if missing, then proceeds to build the 
# kernel module from scratch, and install it.
#
# This script only installs / modifies as necessary.
#

#
# Nuke the old source directory, just in case. Not sure if there's a *-install script that 
# goes off  and does this automatically with the .deb pkg, but just to be on the safe 
# side, this is here.
#
[ -d /usr/src/modules/tp-smapi ] && rm -Rf /usr/src/modules/tp-smapi

# Error out any atomic commands immediately if anything fails below here.
set -e

# Install the packages if necessary.
# This should install the rest of the required dependencies for building the module.
for pkg in sysfsutils tp-smapi-source; do
    dpkg-query -W -f='${Status}' $pkg | grep -q 'install ok installed' || apt-get install $pkg
done

# Setup sysfs -- modify the thresholds to suit your needs.

SYSFS_NODE=devices/platform/smapi/BAT0
if ! egrep -q "^[[:space:]]*$SYSFS_NODE" /etc/sysfs.conf; then
    cat <<EOF >> /etc/sysfs.conf
$SYSFS_NODE/stop_charge_thresh=81
$SYSFS_NODE/start_charge_thresh=85
EOF
fi

cd /usr/src && tar xvjf tp-smapi.tar.bz2

for i in clean all install; do 
    make -f "$(dirname "$0")/Makefile.tp-smapi" $i
done

egrep -q '^[[:space:]]*tp_smapi' /etc/modules || echo "tp_smapi" >> /etc/modules

# Update the modules database.
module-assistant update

```Makefile (put in the same directory as the script):
```

# Makefile.tp-smapi
#
# NOTE: keep the tabs intact!
#

# What's our kernel version?
kernel_ver        ?= $(shell uname -r)

# Where are we going to pick up the sources from?
tp_smapi_dir        ?= /usr/src/modules/tp-smapi

.PHONY: all clean install

all:
    $(MAKE) -C $(tp_smapi_dir) \
    KBUILD=/lib/modules/$(kernel_ver)/build \
    KVER=$(kernel_ver)

clean install:
    $(MAKE) -C $(tp_smapi_dir) \
    KBUILD=/lib/modules/$(kernel_ver)/build \
    KVER=$(kernel_ver) \
    $@

# END Makefile
```

After that, just do:

1. sh tp-smapi-source-install.sh
2. lsmod | grep tp_smapi && rmmod tp_smapi && modprobe tp_smapi

Cheers and thanks for all of the information!

-Garrett

---

### Post by yaneurabeya on 2009-08-13
> **Porter Doran said:**
> Just how damaging to a battery is keeping it fully-charged? Would it really ruin a battery in, say, three months? My T61, which really is brand-new, has been kept mostly fully-charged. Last week Ubuntu popped up a notification that my battery seems to be damaged and cannot be charged more than half-way. Since then, I've noticed my laptop running out of battery power in -- oh -- fifteen minutes. An alarming thing for a new laptop! Any advice? (I am running 8.04.)

Li ION batteries have a bad tendency to develop memories, but they aren't as bad as some other battery technologies (NiCd's, anyone :)?). Here's a piece of advice I learned from a fellow tech after killing 2 Macbook batteries (2nd one after 6 months `use'):

1. Habitually charging batteries on a `schedule' / pattern will kill a battery quicker, e.g. drain, then fully charge, then fully drain, or maintain a full charge (common mistake) etc. Randomizing their charging helps.
2. You should cycle the battery at least once a week if you use it regularly, e.g. go from 0% to 100% (not literally), from 50% to 100% to 50%, etc. Batteries will only cycle so many times though before wearing out, and there's no way to get around that point.
3. Do not leave the laptop on standby for extended periods of time (my issue with my Macbook >.<). Shutting down the laptop is critical if it's going to sit for more than a few days.
4. Try to keep the percentage before shutting down above 50% if at all possible. The charge in the battery will naturally dissipate over time, even when shutdown as there are parasitics in your laptop (inherent capacitors, inductors, and resistors).

Lenovo's thinkpad powermiser app does some interesting things with the battery, randomizing the charge and discharge cycles and what not, from what I understand. My mentor has been using the same battery for the past 2 years and it's held strong at 4 hours capacity.

My battery on the other hand is 1.5 years old and I only have 1.5~2.0 hours charge left on its current power settings, because I used to keep it plugged into a dock 24/7 (-_-)... My 3rd Macbook's battery is now 7 months old and still holds a 4.5 hour charge however.

HTH,
-Garrett

---

### Post by Axx83 on 2009-11-04
Guys sysfsutils in Karmic doesn't work as well as before, probably the kernel's fault. More than once it hasn't started on login and the battery got charged up to its maximum.

What could be the reason ?

---

### Post by hellmet on 2009-11-06
Is there any way we could make a .deb file for 32 and 64 bit for tp_smapi ? I'd be interested and I'll help as far as I can(including hosting the file). You can PM me if you need anything.

**UPDATE:** I've written a script that really eases the process of setting battery thresholds. I'm writing a GUI for it, and will create a new thread when it reaches usability. Let me know if you need the script.

---

### Post by Axx83 on 2009-11-10
Yes that would be good, actually in karmic sysfs is giving me a lot of problems

---

### Post by hellmet on 2009-11-10
Umm.. Actually.. my script does use sysfs to save settings on reboot. Its been working pretty well on my R500. 
What problems are you facing with sysfs? It would be helpful to know.

**UPDATE2**
A new thread has been created for the script and it is available here for download and testing: [http://ubuntuforums.org/showthread.php?t=1325674](http://ubuntuforums.org/showthread.php?t=1325674)
**UPDATE**
Putting GUI on hold for the moment. Trying to complete script functionality first.

**Script Features that work :**
View and set/remove thresholds for integrated battery.
Auto add settings to sysfs to save thresholds on reboot.
Automating installation of tp_smapi and sysfsutils
Writing to /etc/modules to add tp_smapi

**Working on:**

Adding support for second (UltraBay) battery. Should be easy. But, I'm new with python and I don't have an UltraBay battery.
Displaying battery details. The Ubuntu power manager already displays all info except for cycle count. 

Will attach script once above features work well. A screenshot has been attached for those interested.

---

### Post by hugmenot on 2009-11-19
This is a quicker way of installation:

```

sudo aptitude install tp-smapi-source
sudo m-a a-i tp-smapi
sudo modprobe tp_smapi

```

---

### Post by hellmet on 2009-11-19
or
```

sudo m-a a-i tp-smapi-source
sudo modprobe tp_smapi 
```

---

### Post by bademeister on 2009-12-05
> **yaneurabeya said:**
> . My 3rd Macbook's battery is now 7 months old and still holds a 4.5 hour charge however.

HTH,
-Garrett

Hey Garret,

interesting to read that you're also on a macbook. I just got a macbook pro, cloudn't really get along with MacOS and threw it out, but I am nowlooking for a way to limit charging its battery under Ubuntu. Have you looked into that?

thanks
Paul

---

### Post by n.l.o on 2010-05-26
how do I delete my message?!

---

### Post by dante.jones on 2010-08-03
Hi mbsullivan,

Thanks for your great guide over a good period of time.

As mentioned in this page on [ThinkWiki]("http://www.thinkwiki.org/wiki/Tp_smapi#Installation_on_Ubuntu_Lucid"), getting tp_smapi running under Ubuntu 10.04 is now particularly easy:

> 
    $ sudo aptitude install tp-smapi-dkms 
    $ sudo modprobe tp_smapi 


Of course you still need to add tp_smapi to:

> 
/etc/modules


And make the necessary config changes to keep battery threshold settings permanent, but installing it has become quite pleasantly easy.

---

### Post by mbsullivan on 2010-08-04
> 
Hi mbsullivan,

Thanks for your great guide over a good period of time.

As mentioned in this page on ThinkWiki, getting tp_smapi running under Ubuntu 10.04 is now particularly easy:

Quote:
$ sudo aptitude install tp-smapi-dkms
$ sudo modprobe tp_smapi
Of course you still need to add tp_smapi to:

Quote:
/etc/modules
And make the necessary config changes to keep battery threshold settings permanent, but installing it has become quite pleasantly easy.

That's true. This tutorial is pretty much no longer needed, or at the very least deprecated. I will update it soon so that it doesn't mislead any newcomers.

Thanks,
Mike

---

### Post by lunatico on 2010-09-21
> **mbsullivan said:**
> Yeah... it'll charge to 100% if you leave it plugged in whilst off.  Nothing really can be done about that.



I'm honestly not sure... if you try it, keep us posted! Also, if you try it and get a "thinkpad_ec: no ThinkPad embedded controller!" error, try updating your BIOS.

Mike

Anyone figured out how to apply the threshold values to the BIOS?
I know that if you install the Lenovo power software in Windows this changes get written the the BIOS as well but I don't know how to do that from Linux.

---

### Post by kabturek on 2011-02-15
> **lunatico said:**
> Anyone figured out how to apply the threshold values to the BIOS?
I know that if you install the Lenovo power software in Windows this changes get written the the BIOS as well but I don't know how to do that from Linux.
Aren't they saved to the battery ? It worked that way before i.e. they were saved until you disconnect the battery.

---

### Post by jeremija on 2011-08-05
They are saved to the embedded controller in the battery, but this data is lost as soon as you turn off the pc and disconnect the charger. 

I use a T60p and am having a problem: **stop_charge_thresh** works ok, but **start_charge_thresh** seems to have no effect. No matter what value I set to it, the battery will always charge to **stop_charge_thresh** value.

For example, I have set the following values:
**start_charge_thresh = 80**
**stop_charge_thresh = 90**
and the PC is running on battery which is at **85%**. When I connect the charger, the battery will charge to **90%**. Shouldn't it only be charging if it were below **80%**?

It seems that setting the **start_charge_thresh** value only has an effect for a brief second, and then the battery resumes with charging (???)

**edit:**
I noticed that what I wrote up there happens only when I turn on the PC while it was totally disconnected to from the power supply and connect the charger before ubuntu boots up. It seems that if I connect the charger after the ubuntu has booted and the values set, it works ok. Is that the way it was supposed to work? I should iether leave the PC on charger all night or connect it after ubuntu has booted?

---

