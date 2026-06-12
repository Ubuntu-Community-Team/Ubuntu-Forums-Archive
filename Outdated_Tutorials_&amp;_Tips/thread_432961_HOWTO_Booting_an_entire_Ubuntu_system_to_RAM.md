---
title: "HOWTO: Booting an entire Ubuntu system to RAM"
date: 2007-05-04
forum: Outdated Tutorials &amp; Tips
---

### Post by jdong on 2007-05-04
[https://wiki.ubuntu.com/BootToRAM](https://wiki.ubuntu.com/BootToRAM)

I just wrote this Wiki Howto to chronicle my last 3 days of experimenting with what it's like to boot a system into RAM. I found it highly practical and useful, so I made a HOWTO from it...

A few teaser quotes:

> 
This article aims to document the process of creating a customized Ubuntu that loads an image from the hard disk to RAM, then boots an entire Ubuntu session out of RAM. It is intended for intermediate to advanced Ubuntu users who are familiar with the shell, and may have limited experience customizing the livecd (LiveCDCustomization) and shell scripting. We will customize a LiveCD and copy it to the hard drive, and make a few modifications to bootup scripts so that it copies to RAM via our good friend tmpfs.

There are many cases where one would like to boot Ubuntu to RAM:

    *  Performance: The desktop performance is dramatically improved. A 400MB squashed filesystem in RAM, that holds 1200MB of data, is read back on a 1.6GHz Core Duo in about 3 seconds, including decompression time.
    *  Power, Noise, Durability: Although modern hard disks don't use much power compared to other system components, this may still be important for some. In laptops, hard disks are often the noisiest components, so this setup can reduce system noise. With the hard disk spun down, a laptop can potentially withstand greater shocks without damage.
    *  Abrupt poweroff: Since the hard disk is only momentarily used in read-only mode during boot, then never touched again, there are few or no negative consequences of an abrupt poweroff. If a system is used where power is inconsistent, or the system is regularly used in a context where fast shutoffs are required, this is very handy.
    *  Privacy: Anything you do in this session are lost when you reboot or power off. This is great for kiosks or other systems where permanent modification are not desired. (Note that by default the livecd user has full sudo access, so potentially a malicious user can still make permanent changes by mounting the hard drive and following this HOWTO)



Note that this is a **fairly advanced topic** but not hopelessly complex or intrusive.

**Note** There probably could be some mistakes in there. Please let me know if something doesn't work, sounds wrong, or is confusing, and I'll do my best to fix it. Feel free to contribute ideas or expand on any points I made.

---

### Post by sad_iq on 2007-05-05
> **jdong said:**
> [https://wiki.ubuntu.com/BootToRAM](https://wiki.ubuntu.com/BootToRAM)

 Feel free to contribute ideas or expand on any points I made.

Great HowTo!!!! 
I'm struggling to make my own LiveCd for a few days now(doing battle with some man pages for the last 5 or 6 hours right now :) ) .
 ..About an idea....could you make use of the memory from the video card as well(I know it's possible)?? Users with 256 MB of video ram will barely use it all in a LiveCd session wright? 
 Also in the wiki page there is a "share any cool things you do with this HOWTO" line...well please tell us your's and if possible some type of benchmarks so that the users will see the difference from a normal LiveCd session and a Ram LiveCd session !!!

---

### Post by jdong on 2007-05-05
Video RAM is specialized RAM; there is currently no mechanism for regular programs to occupy video RAM.

As far as benchmarks... Firefox starts in about 1 second, abiword in 0.5 seconds, things like the GNOME terminal or gaim start instantly.

---

### Post by ghost16825 on 2007-05-13
> **jdong said:**
> Video RAM is specialized RAM; there is currently no mechanism for regular programs to occupy video RAM.

Well actually there is a way:

[http://gentoo-wiki.com/TIP_Use_memory_on_video_card_as_swap](http://gentoo-wiki.com/TIP_Use_memory_on_video_card_as_swap)

---

### Post by jdong on 2007-05-13
VERY interesting, though it has enough side effects that'd just make it something "cool" and probably not practical :D

---

### Post by Finch75 on 2007-07-04
Hello John,

I just discovered your BootToRam tutorial and it's great!
Almost exactly what I was looking for! :-)

> **jdong said:**
> [https://wiki.ubuntu.com/BootToRAM](https://wiki.ubuntu.com/BootToRAM)
...
I just wrote this Wiki Howto to chronicle my last 3 days of experimenting with what it's like to boot a system into RAM. I found it highly practical and useful, so I made a HOWTO from it...

A few teaser quotes:
...It is intended for intermediate to advanced Ubuntu users who are familiar with the shell...

Note that this is a **fairly advanced topic** but not hopelessly complex or intrusive.

Well, I'm almost a complete Linux newbie (but a very fast learner!) and got it to work in about half an hour :-)
It's cool! BUT...

> **jdong said:**
> Feel free to contribute ideas or expand on any points I made.

... you know what would be EVEN COOLER? I'm really looking for a way to load *my existing system* into RAM and run from there! A Live-CD is very nice for some special circumstances, but a full system is great for every day! It offers all the advantages you mentioned. And then some... :-)
It would be much easier to customize than a LiveCD in a chroot (actually, it's taking me days to install and configure the entire system and that is NOT possible with a LiveCD). It could contain all the drivers for all my hardware and should of course run with a user (me) and password... then I could store my persistent data /home on a flash drive and have a totally silent system! :-)

Here's something I'd like to do:
[http://ubuntuforums.org/showpost.php?p=2942867&postcount=19](http://ubuntuforums.org/showpost.php?p=2942867&postcount=19)

(written before I discovered this thread here).

Since I'm new to Linux, I probably underestimate how different this is?
However, it could even be easier (? - easier in general, maybe not easier than customizing a complete solution).
I've already taken a look at some casper scripts and I guess that stuff has to be very different. Is there an easy way to create a ramdisk during system boot, copy files and then mount it as root? For me personally, it wouldn't even have to be compressed :-):-):-) However, running a script that compresses my disk into a squashfs file for the next reboot would also be cool... (the way I understand it, a readonly filesystem as root filesystem is much harder to work with? Can I somehow copy my existing installation into the LiveCD structure? I guess the main difference would be the user and the permissions...)

Do you think this can be done with a reasonable amount of work or would this be a huuuge project all by itself?
I'd be really happy to hear from you and eager to make this work! :-)

Finch

---

### Post by Finch75 on 2007-07-05
Just a quick update...
I have done some searching and I am now convinced that what I'm trying to achieve is quite doable and probably easier than I thought. As a matter of fast, it should be "relatively easy" for a Linux expert (which I'm not).

The main challenges for a Live-CD are:
- running on unknown hardware without extra configuration
- not knowing where the root filesystem is
- read-only filesystem
- no user data (e.g. login as "casper")

None of that would really apply to my plans. What I'm trying to do shouldn't be all that different from booting an encrypted root partition. Unfortunately, I haven't yet had the time to investigate this in detail (and probably won't have the time for the next couple of days), but just in case somebody else wants to do some research, I thought I'd post my latest insights:
In the normal Linux booting process, an "initial ramdisk" (initrd) is loaded. This ramdisk contains the code to mount the "real root filesystem" and then "switch root" (seems like this is done using pivot_root, but I am not sure if this is true for all systems and all versions of Linux/Ubuntu...). For an encrypted root, this ramdisk loads the encryption/decryption drivers, prompts for the password, mounts the encrypted partition and then "switches" to that partition (In systems without hard disk, the initial ramdisk can "remain" the root directory).

My plan is even easier (if you know what you're doing): I don't want to compress my entire hard disk into a ramdisk image, so I keep the two step process. The initial ramdisk creates a large "final ramdisk" and copies all the directories/files it needs. Then it switches to that ramdisk and everything should work smoothly. I fully expect to encounter some totally unexpected problems *g* - BUT this is *really* similar to the encrypted filesystem root and should be doable with some competent help (or even without, just using how-tos...).

This is a rather flexible approach. For example, I can copy a few directories and symlink the others (e.g. some rarely used programs). Some directories will be only in memory, others can remain on disk (must be careful not to create inconsistent states after reboot). I could even create a cron job that will "persist my changes" once a day... 

One "issue" might be the filesystem. Seems like most compressed filesystems are read-only. I've read something about a compressed ext3 filesystem - is that stable? Some compression would be good, I guess... After all, I don't want to occupy more than half my RAM with the hard disk image :-)
Hmm... I guess I should take a look at UnionFS? I have no clue what that is (yet), but it sounds good :-)

So much for today, I'll be back... :-)

---

### Post by jdong on 2007-07-06
Absolutely what you are describing is possible. You forgot about the biggest constraint: space. You are ultimately limited by the amount of RAM, or optical media space if making a live-CD or DVD.

It is not hard to convert your current system into a live system. You'd basically have to apt-get install casper, and then make the modifications I mentioned for patching the live environment. Voila!

Please do back up your system first if you plan on changing it with casper, or work on a cloned copy of your machine's hard drive.

---

### Post by steveneddy on 2007-07-06
I'm gonna try this on a spare PC one of these days. I bookmarked the links for future reference.

:popcorn:

---

### Post by Finch75 on 2007-07-07
> **jdong said:**
> Absolutely what you are describing is possible.Great!

> **jdong said:**
> You forgot about the biggest constraint: space. Nope, not at all.
The biggest constraint is my limited knowledge of Linux *g*. However, it's decreasing rapidly *g* (the limitation, that is...)
Also, I didn't forget about it at all. Oh yeah, and I did think about that space thing as well...

> **jdong said:**
> You are ultimately limited by the amount of RAM, or optical media space if making a live-CD or DVD.Yes. RAM prices have dropped to a new all-time low recently. That's not so new and probably happens frequently, but they've decreased by an amazing 75% since January. I decided to upgrade and couldn't resist... I now have 6 GB RAM :-)

Actually, I had this "boot to/from RAM" in mind from the very beginning ([http://ubuntuforums.org/showthread.php?t=463104](http://ubuntuforums.org/showthread.php?t=463104)). I guess 6 GB should be more than enough. I can use 4 GB to load my system into RAM and still have 2 GB left - which is as much as or more than most other people use for running their system :)
(including me until last week) And I wouldn't really need a disk cache for the system drive any more :-)

> **jdong said:**
> It is not hard to convert your current system into a live system. You'd basically have to apt-get install casper, and then make the modifications I mentioned for patching the live environment. Voila!Hmm. Can you tell me "in simple words" what casper is and does? I really couldn't find a short explanation even though I did look for it. How would it help me? I've installed it and taken a look at some of the scripts... Actually, the "casper-bottom" did make me laugh a bit:

01integrity_check
02_timezone
05mountpoints
10adduser
12fstab
13swap
14locales
15autologin
18hostname
19keyboard
20xconfig
22gnome_panel_data
22screensaver
23etc_modules
23networking
24preseed
25configure_init
30accessibility
31disable_update_notifier
32disable_hibernation
33enable_apport_crashes
34disable_kwallet
35fix_language_selector
40install_driver_updates
41apt_cdrom

*lol* - reminds me of 
10 print "Hello"
20 goto 10

Just kidding. No offense :-)

However, this seems to confirm what I wrote in my last post: Most of the "specific LiveCD problems" don't apply to what I'm trying to do... timezone, mountpoints, adduser, fstab, swap, locales, autologin, hostname, keyboard, xconfig... I don't think I need any of that...

I think what I'm trying to do is more similar to mounting an encrypted root partition.

Yesterday, I unpacked the standard init-rd and looked at it. VERY educational :-)
It seems quite possible that I don't need THAT many changes. The "init" script contains ```
log_begin_msg "Mounting root file system..."
. /scripts/${BOOT}
parse_numeric ${ROOT}
mountroot
``` and scripts/local contains```
modprobe -Qb ${FSTYPE}

	# FIXME This has no error checking
	# Mount root
	mount ${roflag} -t ${FSTYPE} ${ROOTFLAGS} ${ROOT} ${rootmnt}

	[ "$quiet" != "y" ] && log_begin_msg "Running /scripts/local-bottom"
	run_scripts /scripts/local-bottom
	[ "$quiet" != "y" ] && log_end_msg
```Sooo... it looks like I should change this to:
- mount "normal root" at a different mountpoint
- create a ramdisk at ${rootmnt}
- copy everything I need
- proceed

Looks "doable"... However, I'd like to control this behavior from the boot command line so I can still use the scripts for "a normal boot".

I guess I can start out by using ramfs, but ultimately, I'll need something that is compressed and ramfs doesn't seem to have that option?! :-(

Oh well... maybe I should try the first step before thinking about the third one...
> **jdong said:**
> 

Please do back up your system first if you plan on changing it with casper, or work on a cloned copy of your machine's hard drive.Oh yes, of course! I use a spare hard disk for that and I'm even so scared that I will disconnect the other disks while I experiment :-) Too bad I can't do any of that today because my computer will probably be busy recording some parts of the "Earth Day" concerts :-)

Anyway... This has now moved up to #2 of my "to do list"... I think I'll be making some progress soon. I really don't have a lot of time to play with this but I've wanted to do sth like this for such a long time that I just cannot stop myself... 
> **steveneddy said:**
> I'm gonna try this on a spare PC one of these days. I bookmarked the links for future reference.Any helpful input welcome!

---

### Post by Iarwain ben-adar on 2007-07-10
So, after a couple of days it worked out.

The problem now is, it boots slow as hell (compared to ram's speed)
It takes about 40-50 seconds to boot the complete image into ram.

The filesystem.squashfs is around 500mB big but i have 2 GB ram, so that can't be the problem.

What i am also wondering; when i chroot into my casper/chroot i can't get any internet in that environment.
```
root@iarwain-laptop:/# ifconfig
Warning: cannot open /proc/net/dev (No such file or directory). Limited output.

```

```
root@iarwain-laptop:/# ifup eth0
ifup: failed to open statefile /var/run/network/ifstate: No such file or directory

```

What could be the cause of those problems?


Iarwain

---

### Post by jdong on 2007-07-10
> **Iarwain ben-adar said:**
> So, after a couple of days it worked out.

The problem now is, it boots slow as hell (compared to ram's speed)
It takes about 40-50 seconds to boot the complete image into ram.


The filesystem.squashfs is around 500mB big but i have 2 GB ram, so that can't be the problem.


How much time does it spend on the initial copy phase (i.e. where all the disk activity is concentrated)?

After that, it should be like a 15 second bootup.

> 
What i am also wondering; when i chroot into my casper/chroot i can't get any internet in that environment.
```
root@iarwain-laptop:/# ifconfig
Warning: cannot open /proc/net/dev (No such file or directory). Limited output.

```

```
root@iarwain-laptop:/# ifup eth0
ifup: failed to open statefile /var/run/network/ifstate: No such file or directory

```

What could be the cause of those problems?


Iarwain

Make sure /proc is mounted inside /casper/chroot/proc, and also that /etc/resolv.conf is copied to /chroot/casper/etc

---

### Post by Iarwain ben-adar on 2007-07-10
> **jdong said:**
> How much time does it spend on the initial copy phase (i.e. where all the disk activity is concentrated)?

After that, it should be like a 15 second bootup.


What do you mean with a copy phase? I just know it hangs a while when it's like uncompressing the image.


Iarwain

---

### Post by jdong on 2007-07-10
Yeah, it's that hang that I'm referring to -- that's the stage where it copies the squashfs image from your HDD to RAM. On my systems (laptops)  it is the most time consuming stage of bootup.

---

### Post by Iarwain ben-adar on 2007-07-11
Well,
but it's still slow as hell (my Kubuntu install is almost faster to boot).

I thought that yours booted in 3seconds? How come mine is so slow?


Iarwain

---

### Post by jdong on 2007-07-11
> **Iarwain ben-adar said:**
> Well,
but it's still slow as hell (my Kubuntu install is almost faster to boot).

I thought that yours booted in 3seconds? How come mine is so slow?


Iarwain

Did I really say that? If so, I didn't mean it. It doesn't boot that fast at all. 30 seconds is more like it. 10 seconds to read the image off the disk, 20 seconds to perform bootup...

Ubuntu still uses a largely sequential boot sequence which is definitely holding back boot speed.

---

### Post by Iarwain ben-adar on 2007-07-11
> Performance: The desktop performance is dramatically improved. A 400MB squashed filesystem in RAM, that holds 1200MB of data, is read back on a 1.6GHz Core Duo in about 3 seconds, including decompression time.
From [https://wiki.ubuntu.com/BootToRAM](https://wiki.ubuntu.com/BootToRAM)

Better change that then ;)

Hmm,
Is this also doable with other distro's? How come you use "root=casper" in the Grub entry?


Iarwain

---

### Post by jdong on 2007-07-11
> **Iarwain ben-adar said:**
> From [https://wiki.ubuntu.com/BootToRAM](https://wiki.ubuntu.com/BootToRAM)

Better change that then ;)

Hmm,
Is this also doable with other distro's? How come you use "root=casper" in the Grub entry?


Iarwain

3 seconds is the amount of time to uncompress filesystem.squashfs from RAM to /dev/null. This is a test showing that livecd compression does not have a significant CPU overhead. It is not referring to bootup speed.

And yeah, you can use similar techniques with any distro, but Casper won't necessarily work. Each distro has its own set of LiveCD scripts, etc.

root=casper is required to instruct the initrd boot script to attempt livecd boot procedures.

---

### Post by Iarwain ben-adar on 2007-07-15
Sorry for the delay, didn't have my pc around for a couple of days.

So in theory all distro's can be booted to ram? How can one find out what boot scripts are being used, and what root= should be used?


Iarwain

---

### Post by Pheodax on 2007-07-16
It worked like a charm here! :) Thanks a lot.

Booting is very slow as well here, but I didn't expect anything else. The squashed filesystem has to be first copied (and uncompressed?) from the slow HDD to the fast RAM. Actual booting hasn't even started at that point. But who cares? Ubuntu is a crazy fast once you're logged in.

---

### Post by jdong on 2007-07-16
> **Pheodax said:**
> It worked like a charm here! :) Thanks a lot.

Booting is very slow as well here, but I didn't expect anything else. The squashed filesystem has to be first copied (and uncompressed?) from the slow HDD to the fast RAM. Actual booting hasn't even started at that point. But who cares? Ubuntu is a crazy fast once you're logged in.

No not uncompressed -- just copied. However long it takes your disk to read a file the size of the squashed filesystem, is how long boot will hang initially.

Vut yeah, once it comes up the speed is substantial, particularly while multitasking!

---

### Post by Genecks on 2007-07-16
Ahh, nevermind. Delete this post.
p.s. update your post if you can, administrator.

> **jdong said:**
> Video RAM is specialized RAM; there is currently no mechanism for regular programs to occupy video RAM.

As far as benchmarks... Firefox starts in about 1 second, abiword in 0.5 seconds, things like the GNOME terminal or gaim start instantly.

Wrong. I read an article about using VRAM maybe last week. It was dated around 2005, I think. It has an interesting process. It had to use something like MTD or MTRD. I can't remember. Afterwards, this thing allowed a person to split-up VRAM and convert it into some for video graphics and some for storage.

I came across it by chance, but I wasn't too interested in using it.

---

### Post by kiv on 2007-07-17
ahh im gonna give this a go just cos it's so damn cool!

A partially related question..

Also.. when running ubtuntu from the hard drive ... because ubuntu only uses a fraction of my ram with nothing running (about 10%) is there a way to load any extra system files into the ram to improve performance?

You could do this with a reg tweak on xp.. just wondering if its possible on ubuntu?!

---

### Post by jdong on 2007-07-17
> **kiv said:**
> ahh im gonna give this a go just cos it's so damn cool!

A partially related question..

Also.. when running ubtuntu from the hard drive ... because ubuntu only uses a fraction of my ram with nothing running (about 10%) is there a way to load any extra system files into the ram to improve performance?

You could do this with a reg tweak on xp.. just wondering if its possible on ubuntu?!

The operating system does this already on its own. The readahead application preloads the most critical pieces of the OS into RAM before booting up. In addition, any files read off the disk are kept in RAM until another application (or more worthy files) are read into the RAM. This method simply forces all of the OS to stay in the RAM at all costs.

And the XP reg tweaks (disabling Executive paging, SuperPrefetch, etc) don't do exactly what you think they're doing...

---

### Post by capink on 2008-02-29
I wish I have seen this guide 4 days ago. I already customized the original wiki to make it possible to boot your installed system to RAM instead of using the live CD image. here is the [link]("http://ubuntuforums.org/showthread.php?t=707230").

---

### Post by Tu13erhead on 2008-02-29
I was bored and gave this a shot.  When it boots, it dumps me to a

```
(initramfs)
```

prompt.   Any ideas?  I'm on Gutsy, if that matters.

---

### Post by capink on 2008-02-29
There is a log file that you can look for once dropped in busybox shell. I think its name is something like live.log.

You can see the contents of the temporary filesystem in (initramfs) by typying the command:

```
ls
```

Now identify the name of the log file and see what it says:

```
cat /name/of/the/log/file
```

---

