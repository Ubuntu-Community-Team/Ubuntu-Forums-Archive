---
title: "Wacom tablet kernel issues"
date: 2012-12-06
forum: New to Ubuntu
---

### Post by Cdraam on 2012-12-06
First, I know there are posts and pages all over that describe how to do this, but none of them have worked for me because of this. 
So, [HTML]http://ubuntuforums.org/showthread.php?t=1515562[/HTML] . When going through step 1 compiling the driver, I get all the way down to "./configure --prefix=/usr". When I input that, I get this error:

make[1]: Entering directory `/home/user/Desktop/input-wacom-0.13.0'
make[2]: Entering directory `/home/user/Desktop/input-wacom-0.13.0'
make[2]: Leaving directory `/home/user/Desktop/input-wacom-0.13.0'
make[1]: Leaving directory `/home/user/Desktop/input-wacom-0.13.0'

----------------------------------------
  BUILD ENVIRONMENT:
       linux kernel - yes 
      kernel source - no 

We could not find the kernel development environment to build the driver.
Please install the kernel source or the kernel development package and try again.
 
I am currently running Ubuntu 11.04 fresh install. I first tried the same process along with some PPA's on 12.10, 11.10 and now 11.04. I've gotten the same errors across the board, so I want to figure out what I need to do. Thanks!

---

### Post by levlaz on 2012-12-07
Have you read through this? 

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) 

What exactly are you trying to compile?

---

### Post by Cdraam on 2012-12-07
The USB Kernel drive I believe. 
Out of the box it won't run the 3rd gen tablets, but when you get the 3.3 kernel it does. I'm really unfamiliar with Linux, so excuse me if I'm not making sense.

---

### Post by Favux on 2012-12-07
Hi Cdraam,

Welcome to Ubuntu forums!


Looks like you skipped a step, probably the linux-headers one.

I don't know about Natty 11.04 as a choice for release as it is past its 18 month support period so it is no longer supported.

Also the HOW TO isn't updated so there are newer versions of input-wacom and xf86-input-wacom.  See the update post:  [http://ubuntuforums.org/showpost.php?p=12374240&postcount=1081](http://ubuntuforums.org/showpost.php?p=12374240&postcount=1081)

Or you could use this [updated HOW TO]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110408&sid=3c81d92a4ec5c4a1676560cf1ae94b2c").

Please feel free to ask if you have more questions.

---

### Post by Cdraam on 2012-12-07
I chose Natty because with the other two versions it did the same thing. and on the Howto there are 3(?) PPA's that only went as high as Natty. So I decided to move back to that after the other two obviously weren't going to work. 
I don't have time until later to try the updated howto, but what about the kernel issue I have? I didn't skip the kernel headers step. Like I've said, I've done the whole process probably 6 times now, through all the Ubuntu versions.
I should add, it doesn't only bring up the kernel issue on the compiling, I found one of the PPA's he lists and tried it and it came up with a similar error at the end.

---

### Post by Favux on 2012-12-07
OK, What's the output of this command in a terminal?
```
uname -a
```
> I should add, it doesn't only bring up the kernel issue on the compiling, I found one of the PPA's he lists and tried it and it came up with a similar error at the end. 

BUILD ENVIRONMENT:
linux kernel - yes
kernel source - no

We could not find the kernel development environment to build the driver.
Please install the kernel source or the kernel development package and try again.
I don't remember that being a problem with input-wacom-0.13.0.  Although there have been occasional build problems in specific instances that have been fixed so it would be interesting if that happens with 0.15.0 too.

Is it complaining about build-essential not being installed?  When you run the library/dependency line:
```
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libncurses5-dev autoconf libtool
```
you're getting the whole thing and it isn't complaining or throwing errors?

Another thought is with Update Manager open Settings on the bottom left.  Is Source code checked in the Ubuntu software tab?

---

### Post by Cdraam on 2012-12-07
Uname -a:
[HTML]Linux cr-48-ubuntu 3.4.0 #1 SMP Fri Oct 19 07:18:51 PDT 2012 i686 i686 i386 GNU/Linux[/HTML]

This sounds stupid that I didn't already do this. I'm going to do all the updates, I totally forgot. I'll do those then try and run the updated howTO and let you know. Sorry.

---

### Post by Cdraam on 2012-12-07
After the code you supplied that's in the part 1, I get this, so no error: 
[HTML]user@cr-48-ubuntu:~/Desktop$ sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libncurses5-dev autoconf libtool
Reading package lists... Done
Building dependency tree       
Reading state information... Done
autoconf is already the newest version.
build-essential is already the newest version.
libncurses5-dev is already the newest version.
libtool is already the newest version.
libx11-dev is already the newest version.
libxrandr-dev is already the newest version.
x11proto-input-dev is already the newest version.
xserver-xorg-dev is already the newest version.
libxi-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  libaccess-bridge-java-jni libaccess-bridge-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to r[/HTML]

And from the Linux-headers-generic line:
[HTML]user@cr-48-ubuntu:~/Desktop$ sudo apt-get install linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libaccess-bridge-java-jni libaccess-bridge-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/HTML]

And finally, the same as usual: 
[HTML]user@cr-48-ubuntu:~/Desktop/input-wacom-0.15.0$ ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... none
checking for kernel type... Linux
checking for linux-based kernel... yes
checking for kernel source/headers... not found
***
*** WARNING:
*** Unable to guess kernel source directory
***   Looked at /lib/modules/3.4.0/source, /lib/modules/3.4.0/build,
***     /usr/src/linux, /usr/src/linux-3.4.0, and
***     /usr/src/linux-2.6
*** Kernel modules will not be built
***

checking that generated files are newer than configure... done
configure: creating ./config.status
config.status: creating Makefile
config.status: creating 2.6.30/Makefile
config.status: creating 2.6.36/Makefile
config.status: creating 2.6.38/Makefile
config.status: creating 3.7/Makefile
config.status: creating config.h
config.status: executing depfiles commands
make  all-recursive
make[1]: Entering directory `/home/user/Desktop/input-wacom-0.15.0'
make[2]: Entering directory `/home/user/Desktop/input-wacom-0.15.0'
make[2]: Leaving directory `/home/user/Desktop/input-wacom-0.15.0'
make[1]: Leaving directory `/home/user/Desktop/input-wacom-0.15.0'

----------------------------------------
  BUILD ENVIRONMENT:
       linux kernel - yes 
      kernel source - no 

We could not find the kernel development environment to build the driver.
Please install the kernel source or the kernel development package and try again.
[/HTML]

Extremely frustrated at this point. Trying to get it up before I head to California on Tuesday!! Thanks.

---

### Post by Favux on 2012-12-07
Alright.  It is the linux-headers that's the problem.

You apparently have a non-standard kernel that isn't in a vanilla Ubuntu release.
> Linux cr-48-ubuntu 3.4.0 #1 SMP Fri Oct 19 07:18:51 PDT 2012 i686 i686 i386 GNU/Linux
None uses the 3.4 kernel that I am aware of anyway.  It appears to be a Chrome kernel.  Could you maybe explain how you got that?

And that is probably the explanation as to why installing linux-headers-generic isn't working.  Not the correct header.  We'd have to figure out if there is a Chrome header package available and apt-get install it.

---

### Post by Cdraam on 2012-12-07
> **Favux said:**
> Alright.  It is the linux-headers that's the problem.

You apparently have a non-standard kernel that isn't in a vanilla Ubuntu release.

None uses the 3.4 kernel that I am aware of anyway.  It appears to be a Chrome kernel.  Could you maybe explain how you got that?

And that is probably the explanation as to why installing linux-headers-generic isn't working.  Not the correct header.  We'd have to figure out if there is a Chrome header package available and apt-get install it.

Well damn. I installed Ubuntu on my Chromebook. Assuming I would be able to use the tablet with it, after seeing an article on it. I honestly didn't think that would matter.

---

### Post by Favux on 2012-12-07
A quick search of the Ubuntu packages doesn't look hopeful.

Best I can find on your topic is:  [http://ubuntuforums.org/showthread.php?t=2017563](http://ubuntuforums.org/showthread.php?t=2017563)  Which didn't get far.

Now apparently you can really get in the weeds:  [https://groups.google.com/forum/?fromgroups=#!topic/chromebook-central/PPQFpC7mYzk](https://groups.google.com/forum/?fromgroups=#!topic/chromebook-central/PPQFpC7mYzk)  That one is making my eyes glaze over.  A little background on the chrome kernel:  [http://www.chromium.org/chromium-os/chromiumos-design-docs/chromium-os-kernel](http://www.chromium.org/chromium-os/chromiumos-design-docs/chromium-os-kernel)

So you need to contact the Chromebook/Chromium OS folks on how to install a kernel header so you can compile a kernel module/driver.  There must be a forum somewhere.  It would be sweet if they had a package repository you could just point apt-get to.

---

### Post by Favux on 2012-12-07
Actually thinking about it a bit more the 3.4 kernel should be good enough for your tablet if it is a third generation BambooPT.  What tablet do you have anyway?  Unless the Chrome kernel doesn't include the wacom.ko.

What do you see when you run in a terminal?
```
lsmod | grep wacom
```
In other words is the Wacom kernel driver/module wacom.ko in lsmod (list modules) output?

Maybe it is just a configuration issue in xorg.conf.d?  If you see wacom in the output of lsmod what is the output of?
```
xinput list

and

xsetwacom -V
```

---

### Post by Cdraam on 2012-12-07
What do you think about this? I'm torrenting it right now, just to give it a shot. 
[HTML]http://news.softpedia.com/news/Chrome-OS-Linux-1-9-1077-Comes-with-Linux-Kernel-3-3-261743.shtml[/HTML]

---

### Post by Cdraam on 2012-12-07
From the "lsmod" it does nothing, at least form a regular terminal. It just goes to the next line for input. 

From the second things you said: 

```
ser@cr-48-ubuntu:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
user@cr-48-ubuntu:~$ xsetwacom -V
0.17.0

```

---

### Post by Favux on 2012-12-07
Duplicate.

---

### Post by Favux on 2012-12-07
Don't know about that Chrome version.  Does it say something about kernel module support or Wacom support?

> From the "lsmod" it does nothing, at least form a regular terminal. It just goes to the next line for input. 
Just run **lsmod** without the grep stuff.  Still no output?  If so it appears that Chrome OS doesn't anticipate you doing anything with kernel modules.  All Ubuntu releases have lsmod installed by default I think.  You'll have to see if it allows you to get it by installing the package it is in:
```
sudo apt-get install module-init-tools
```

When you ran xinput list did you have the tablet plugged in?

---

### Post by Cdraam on 2012-12-07
After running apt-get one. 
```
user@cr-48-ubuntu:~$ sudo apt-get install module-init-tools
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
module-init-tools is already the newest version.
The following packages were automatically installed and are no longer required:
  libaccess-bridge-java-jni libaccess-bridge-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
user@cr-48-ubuntu:~$ 

```

Xinput with board plugged in:
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
user@cr-48-ubuntu:~$ 

```
Don't believe it changed. That's what the whole idea is, it doesn't even identify it.

---

### Post by Cdraam on 2012-12-07
And just **lsmod**
```

r-48-ubuntu:~$ lsmod
Module                  Size  Used by

fuse                   51182  3 
joydev                 16432  0 
snd_hda_codec_realtek    41008  1 
uvcvideo               54888  0 
videobuf2_core         25128  1 uvcvideo
videodev               64292  1 uvcvideo
videobuf2_vmalloc      12305  1 uvcvideo
videobuf2_memops       12407  1 videobuf2_vmalloc
ath9k                 105145  0 
tsl2583                12336  0 
snd_hda_intel          20528  2 
industrialio           17203  1 tsl2583
snd_hda_codec          58171  2 snd_hda_codec_realtek,snd_hda_intel
mac80211              254230  1 ath9k
snd_hwdep              12366  1 snd_hda_codec
ath9k_common           12579  1 ath9k
ath9k_hw              338102  2 ath9k,ath9k_common
nm10_gpio              12336  0 
snd_pcm                52535  2 snd_hda_intel,snd_hda_codec
ath                    16858  3 ath9k,ath9k_common,ath9k_hw
cfg80211              119031  3 ath9k,mac80211,ath
snd_timer              20974  1 snd_pcm
snd_page_alloc         12669  2 snd_hda_intel,snd_pcm
rtc_cmos               16432  0 

```

---

### Post by Favux on 2012-12-07
Yes but do you see any output when you just run:
```
lsmod
```
in a terminal?  The wacom.ko just may not be autoloading.

Ah there you go.  Don't do anything and I'll post some instructions in this post.


You should have a file in /etc called modules.  If there is a wacom.ko module available we can force it to auto-load by adding it to the modules file.  So open it with gedit:
> gksudo gedit /etc/modules
You might see several modules already listed.  At the bottom of the list add **wacom**.  Save close and then reboot.  Now see if wacom shows in lsmod and what happens now with xinput list.

---

### Post by Cdraam on 2012-12-07
Just to be clear. When I ran it, this came up: 

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
```

So just put Wacom underneath lp?

---

### Post by Favux on 2012-12-07
Yes.

---

### Post by Cdraam on 2012-12-07
Of course. 

```
fuse                   51182  3 
snd_hda_codec_realtek    41008  1 
uvcvideo               54888  0 
videobuf2_core         25128  1 uvcvideo
videodev               64292  1 uvcvideo
videobuf2_vmalloc      12305  1 uvcvideo
videobuf2_memops       12407  1 videobuf2_vmalloc
snd_hda_intel          20528  2
snd_hda_codec          58171  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              12366  1 snd_hda_codec
tsl2583                12336  0 
industrialio           17203  1 tsl2583
snd_pcm                52535  2 snd_hda_intel,snd_hda_codec
nm10_gpio              12336  0 
ath9k                 105145  0 
mac80211              254230  1 ath9k
ath9k_common           12579  1 ath9k
ath9k_hw              338102  2 ath9k,ath9k_common
ath                    16858  3 ath9k,ath9k_common,ath9k_hw
cfg80211              119031  3 ath9k,mac80211,ath
snd_timer              20974  1 snd_pcm
snd_page_alloc         12669  2 snd_hda_intel,snd_pcm
rtc_cmos               16432  0 
user@cr-48-ubuntu:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Synaptics TouchPad                 	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]



```

---

### Post by Cdraam on 2012-12-07
Is it safe to assume we're pretty much SOL?

---

### Post by Favux on 2012-12-07
Yep, doesn't look like the wacom driver/module is included for some reason.

The location would be:
```
/lib/modules/`uname -r`/kernel/drivers/input/tablet
```
Where `uname -r` is the kernel name you get from running **uname -r** in a terminal.  But there appears to be a modules directory because there are modules.  Weird.

Anyway if there is no module you need to compile it.  Which you can't without the kernel headers.

---

### Post by Cdraam on 2012-12-07
Well, ******. But thanks for your help, I guess I'll just buy a new laptop.

---

### Post by Cdraam on 2012-12-07
I know in 12.04  there's already a wacom tablet built in program, that detects it from system settings, but it just doesn't show up. So I'll upgrade and try everything again I suppose.

---

