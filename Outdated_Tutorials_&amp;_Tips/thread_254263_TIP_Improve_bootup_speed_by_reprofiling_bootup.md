---
title: "TIP: Improve bootup speed by reprofiling bootup"
date: 2006-09-09
forum: Outdated Tutorials &amp; Tips
---

### Post by jdong on 2006-09-09
[Digg this story]("http://digg.com/linux_unix/Improve_Ubuntu_Bootup_Times_by_Refreshing_Readahead_List")

**This tip applies to Ubuntu Dapper 6.06 or newer. It won't do anything if you try it on an earlier version.** I typically don't like bootup gimmicks and other silly tweaks that really don't do much, but I seriously do believe you can benefit from this one... I've made an effort to explain how it works in addition to just doing it, so if you're impatient, start scrolling down.

**Disclaimer:** This is a safe procedure that utilizes well-tested and noninvasive code already contained in Ubuntu's bootup procedures, but are not activated by default. However, I can't be responsible for any misfortune it may inflict in your computer.


**Background**:
One cause of slow bootup is excessive disk seeking -- as files are being read off the disk in arbitrary order, the disk heads have to jump all around looking for the files. If during your bootup, you hear the disk making a constant grinding noise loading files, you could possibly help your bootup speeds through this tip. On the other hand, if the hard disk does not appear to be working that hard, and your slow bootup is caused by intermittent "pauses" in bootup, then this tip may not be as handy for you, and you should investigate into other reasons why your bootup is slow (i.e. trying to get an IP on a slow network, etc).


**What does this procedure do?**
Ubuntu has a mechanism called "readahead" that attempts to minimize disk seeking. During a profiled bootup, Ubuntu will make a list of all the files read from the disk during the bootup procedure. It then sorts the files by the order in which they appear on your hard disk, and saves it into the /etc/readahead folder. On subsequent bootups, Ubuntu will first read this list of files into RAM. Since this list of files are in order, it should be faster to read them all at once rather than on an as-needed basis at bootup. In addition, this gives your hard disk something to do during the loading drivers and getting IP address phases of bootup, where usually the hard drive would be idle. As a result, bootup will be faster.

**Isn't readahead something already set up in Ubuntu? Why am I running it again?**
Well, Ubuntu ships with a default readahead list. Basically, the developers ran this procedure on their computer, then you use their list. However, this list may not reflect how files are laid out on your hard drive. Also, it may not reflect what you load during bootup, especially if you've installed any extra services. In addition, if you're running a development build of Ubuntu, this list might not be accurate at all.

**Does it actually help?**

Well, on my system, it took around 10 seconds off the bootup. I can't say what it'll do to you, but it doesn't hurt to try!

However, if you have an insanely fast computer, it could be that readahead won't help your bootup times, as your system can handle bootup seeking without delay (and perhaps also your system doesn't wait long for the network to come up or hardware to be detected). So, your mileage may vary.

**Why isn't this done periodically by my computer, if it helps so much?**

Well, the process of refreshing the readahead list introduces overhead, and makes your system boot slower that one time. It's not really fair for the computer to arbitrarily decided that THIS bootup should be 25 seconds slower ;)

**How do I do it?**

(1) At the bootup menu (GRUB), select your default kernel. You may need to press ESC to see this menu.

(2) Press **e** for edit.

(3) Choose the first line (it should start with "kernel"). Press **e** again.

(4) Move to the end of the line, then add the word **profile**. Press enter.

(5) Press b to boot.

(6) Let the system boot to the login screen, and wait for all disk activity to stop. *Remember, during this one bootup, you've told Ubuntu to keep track of all disk activity going on, in order to build that list. Don't be surprised if it's significantly slower than your ordinary bootups -- that's why it's not activated by default, remember?*

(7) Reboot your system, and enjoy the results.

**How often should I repeat this procedure?**

I recommend doing it:

  * Once after you install Ubuntu and get the system set up the way you like.
  * After doing a major upgrade, such as to the next version of Ubuntu. No need to do it for regular updates, etc.
  * After setting up prelink (if you use it), since that could cause bootup files to change locations on your hard drive
  * After restoring your entire system from backups, as that would change locations of files on your hard drive.

-----

**BONUS HACK!**

Here's another related tweak that could help. It is a little more involved, but for me, the results shaved another 10 seconds off my bootup.

**How does this one work?**
By default, readahead is done in the background, while the rest of the system is booting up. I suspected that this could lead to more disk seekage, so I tried making readahead finish first, before allowing the rest of the bootup continue. To my delight, it took 10 seconds off my bootup.

**Why isn't this default?**
The three reasons I can think of are:

 (1) Users would falsely file bug reports or complain that "Reading Desktop Files" is taking a long time to run on bootup (~10 seconds on average), not realizing that in doing so it saves them LOADS of time through the rest of bootup.
 (2) The LiveCD would be agonizingly slow to load!
 (3) People with insufficient RAM to cache the readahead would not receive much benefit from this form of readahead, which can worsen bootup time.

**How do I do this?**

 (1) Perform the above profiling procedure. **It is important that the order is correct, else this form of readahead won't do a thing!**
 (2) Use your favorite text editor (under sudo or root privileges) to open **/etc/rcS.d/S01readahead**
 (3) Find line 21, which reads:
```

            if /sbin/start-stop-daemon --start --quiet --background \

```

Remove the --background, so that it reads:

```

            if /sbin/start-stop-daemon --start --quiet \

```
(4) Save, reboot.

**It didn't help. How do I go back?**
Just reverse step 3, putting --background back in.

**Whoa! This really helped! Make it default for the next Ubuntu release!**

It actually is in Edgy and beyond. A reverse of the hack is to add --background again, which some people reports is slightly faster. This completely depends on your hardware/software setup and whether your boot is IO bound or wait/modprobe-bound.

---

### Post by Rule on 2006-09-09
thanks for the tip im gonna try it now :biggrin:

---

### Post by berserker on 2006-09-09
WOW!  Significant decrease in boot time.  Thank you very much for this tip!

---

### Post by missmoondog on 2006-09-09
i found this topic early this morning. just now had a chance to try it. don't know if it really made any difference or not, but i'm wondering, should the word "profile" still show up in in the boot options line as the system is starting back up after having let the login screen fully load? the machine i'm on is a P4 1.4ghz that never did take to long to load. tomorrow i'll try it on one my older intel celerons. one is a 600mhz and the other is an 800mhz. should be able to notice something on one of those old  beasts!

---

### Post by stalefries on 2006-09-09
Should I remove the word profile after the first boot? Or just leave it there?

---

### Post by Anduu on 2006-09-10
Bummer no joy for me...I guess my speed was maxed already :p

Adding "profile" using jdong's method shouldn't make any permanent changes to your /boot/grub/menu.lst.If it is still there for some reason you should remove it.

---

### Post by jdong on 2006-09-10
The word profile won't stick there -- it only lasts that one bootup.

As I said, it may or may not make a big difference for everyone -- Ubuntu ships with a default readahead list that should theoretically be "correct".... I'd expect if everyone installs Ubuntu the same way onto the same filesystem (i.e. LiveCD installer, ext3), files would end up on the hard drive in a nearly identical way (I don't think ext3 uses a random number generator to pick where to store files!)

However, if you've modified your bootup services, switched to kubuntu, installed using the Alternate CD (which uses a different method of installation), or picked a different filesystem, it could very well be that files land on your HD in a different order than what was expected.

In addition, if your hard drive is very efficient at seeking, you'll notice less of an improvement.

---

### Post by missmoondog on 2006-09-10
yep, that's exactly how i've installed k/ubuntu on all 7 of my systems. just tried this trick on my 800mhz system. maybe a little difference. didn't really time it or watch it when i rebooted. 

i thought after doing this on this machie and watching/reading what was going on, that the word profile should only show up that one time.

thanks

---

### Post by jdong on 2006-09-10
Hmm, how much RAM you people have? If you've got insufficient RAM to load all the readahead files into RAM, it's not worth your time to do any readahead at all.


Another alternative way you can try to speed bootup is disabling readahead -- open up /etc/readahead/boot with a sudo'ed text editor of your choice, and delete its contents.


To get the contents back, just re-profile :)

---

### Post by zodwallop on 2006-09-10
Thanks for this!  My (X)ubuntu system now boots up almost 10 seconds faster.  Woot!

---

### Post by missmoondog on 2006-09-10
i have 384MB's ram on the 2 machines i've tried this on. that's the least amount on any of my machines. is that sufficient?

---

### Post by jdong on 2006-09-10
That should be sufficient, yes.

---

### Post by Hotaru on 2006-09-10
How cool. It's cut 6 seconds of my boot time :).

---

### Post by Johan! on 2006-09-10
According to bootchart, the boot-time went from 35 seconds to 33 seconds :wink: 

Probably it can't be faster than that on my pc :)

---

### Post by Anduu on 2006-09-10
I have a question jdong...

I had a look in my /etc/readahead folder.It also contains a file titled "desktop".

Does the profile command generate this file as well?If not how is this file generated and is it possible to "reprofile" it for a boost?

---

### Post by jdong on 2006-09-10
The "desktop" file is only generated/used for LTSP/Edubuntu setups, where /usr and /var are on different partitions. If you're looking to accelerate GNOME/KDE or another application's startup via readahead, sadly this is not supported. In fact, I'm not sure... we might already be using the readahead technique to its full potential :)

---

### Post by Anduu on 2006-09-10
OKDK...thanx :)

---

### Post by anllogui on 2006-09-11
Hi jdong!

Can I translate this to spanish and put it on my blog, referencing it here?

---

### Post by jdong on 2006-09-11
Certainly! Go right ahead :)

---

### Post by jdong on 2006-09-11
An update to the HOWTO, I have added a **Bonus Hack** section that has readahead run in the foreground to further minimize disk seeking. This has proven very successful on my systems.

---

### Post by robzon on 2006-09-12
Tests on edgy:

Before tweaking: 45s
After profiling: 43s
After removing --background: 40s

Not much, but still better :)
Thanks!
And I'm gonna translate this to Polish if you don't mind :)

---

### Post by Melvil on 2006-09-13
Tests on edgy:

Before tweaking: 38s
After profiling: 35s
After removing --background: 35s-45s (somewhat inconsistent)

Strangely enough, I **can't boot** anymore after applying the "hack".
After 4 reboots now all kernels hang at different positions during bootup. I'm not sure it's related to the hack, though.
Adding "--background" back fixes this, however

---

### Post by sup on 2006-09-14
41 to 38 to 40 so maybe no difference at all when we take into account I hand-watched it

---

### Post by K.Mandla on 2006-09-15
Thanks for this. I think it only saves me a second or two in the end (I'm using a very sparse Xubuntu setup anyway), but it's definitely helpful. Cheers!

---

### Post by brainkilla on 2006-09-16
Definite improvement, I can't provide benchmark data, perhaps 8-10 sec less :) Thank you for this ;)

---

### Post by Wallakoala on 2006-09-16
this may sound weird, but this actually increased my boot time by 10 seconds. I followed both "hacks" and then I disabled the second one, and my boot time is 57 seconds were it is usually 45-46 seconds. Now this is every time I boot, not just the first time after the profiling thing. Basically what happens when it boots up is it kinda gets "stuck" on "Reading files needed to boot" It stays on that for a long time, and then usplash does that annoying thing where it quits and it goes to the text and then eventually after a while the boot proceeds.

This pisses me off quite a bit, so if anybody has any way that I can fix this it would be greatly appreciated.

---

### Post by jdong on 2006-09-16
Open up /etc/readahead/boot with a text editor (with admin privs) and delete all the contents.

---

### Post by Wallakoala on 2006-09-17
> **jdong said:**
> Open up /etc/readahead/boot with a text editor (with admin privs) and delete all the contents.

aah...it's all nice and back to normal. Thanks!

But do you think there was anything that I did wrong that would cause that to happen?

---

### Post by jdong on 2006-09-17
Nah, I don't think you did anything wrong... There's just something about your hardware/software configuration that means you don't benefit from readahead... and that certainly does happen.

---

### Post by Eddie Hung on 2006-09-23
Hmm.. on my nearly-latest edgy setup, the bonus hack is already implemented? (i.e. --background is already not present) - I imagine this is the same for everyone else on edgy (I'm sure I haven't already tried this hack!)

Also, seeing as edgy uses upstart rather than the old sysvinit system as per dapper, will this hack still have an effect?

Eddie

---

### Post by jdong on 2006-09-23
After I mentioned the results of this test to Scott James Remnant, Edgy's readahead program was changed in two ways:

(1) It's now done in the foreground
(2) On each bootup, the list is dynamically resorted to match on-disk layout


So, this should mean that Edgy will boot faster without the need for reprofiling, unless of course you start a lot of services that are not part of the default Edgy system.

---

### Post by Rob2687 on 2006-09-23
On my P3 laptop, profiling took it from 65s to 56s. Removing the --background thing didn't make a difference.

---

### Post by mjpatey on 2006-10-05
Nice, thanks!  The first hack shaved 3-4 seconds off my boot time, and the second one didn't apply, as --background had already been removed.

But good to know I'm now at maximum boot efficiency!

---

### Post by jdong on 2006-10-05
I have authorized for Edgy's readahead-list to be backported to Dapper. This makes foreground the default mode of readahead, and also resorts the list on-the-fly on each bootup.

Enjoy!

---

### Post by raphha on 2006-10-05
Hi jdong,
first, thanks and nice idea. this seems to improve bootup time for me, too (didn't take any measurements yet).
Just one thing I don't understand: why should I want to resort the list every time I boot? Normally, the standard boot files don't really change their places and resorting will surely cost some time - surely I'm missing something?

cheers, raph

---

### Post by jdong on 2006-10-05
> **raphha said:**
> Hi jdong,
first, thanks and nice idea. this seems to improve bootup time for me, too (didn't take any measurements yet).
Just one thing I don't understand: why should I want to resort the list every time I boot? Normally, the standard boot files don't really change their places and resorting will surely cost some time - surely I'm missing something?

cheers, raph

(1) Resorting the boot list takes about 50 milliseconds to do on my Celeron M 1.4GHz. If you notice this, then you need to step away from the caffeine pills :)

(2) The resort-on-boot is primarily designed so that the default, unprofiled boot.list that ships with readahead-list would be more valid on more systems. They are generated on fresh-installed Ubuntu's using ubiquity, which might be vastly different than what your box may be.

(3) Resort-on-boot can help you out when system packages get dist-upgraded. When files are replaced, there's no guarantee that they remain in the same locations. Even security updates might replace some of these bootup files.

---

### Post by Velox Letum on 2006-10-05
Had already profiled myself, but removing --background had a significant impact. Nice tip!

---

### Post by jdong on 2006-10-05
For "power users" who can do a bit of tinkering, you can build your own readahead lists. Run "sudo readahead-watch -o /etc/readahead/myapp.list" to start readahead monitoring and write a list to /etc/readahead/myapp.list. Run "sudo killall readahead-watch" to stop monitoring after you're done.

Then, run " (sudo) readahead-list /etc/readahead/myapp.list" to prefetch myapp.list. Running without sudo just means the app won't resort before reading.

So, you can tinker with readaheading various lengthy tasks. I've had good success with readaheading GNOME/KDE startup (hint: have /etc/rc.local prefetch your list, so if you don't immediately login, readahead will prefetch your login sequence anyway) and openoffice (just created a /usr/local/bin wrapper script). With firefox, there was no improvement, presumably not enough disk IO to make a real impact.

---

### Post by domino on 2006-10-06
Thanks for the how-to. What puzzles me in the Bonus hack is that "*--background*" was already removed even before i knew the file even existed on my box.

A picture is worth a thousand words. I didn't notice any performance gained by this how-to. Is it possible that anyone can glance at the boot chart and see where it's taking it's time?

Boot time before profile:

[[IMG]http://img96.imageshack.us/img96/5475/bootbeforehn0.th.jpg[/IMG]](http://img96.imageshack.us/my.php?image=bootbeforehn0.jpg)

Boot time after profile:

[[IMG]http://img145.imageshack.us/img145/3276/bootafternk9.th.jpg[/IMG]](http://img145.imageshack.us/my.php?image=bootafternk9.jpg)

Thanks

---

### Post by jdong on 2006-10-06
As I noted in post 36, dapper-backports now uses foreground as its default mode of operation.

---

### Post by dolphinsonar on 2006-10-08
I could not tell if the "profile" hack sped up my bootup time at all.  I am running dapper on an Inspiron B130 Dell Laptop.  I never timed the thing before, so it may have helped and I didn't notice.

---

### Post by dolphinsonar on 2006-10-08
> # Remember that any major changes to this script need to also be made to
# readahead-desktop.init

The file says that, is it a moot point or should I also change that file?

---

### Post by elsupermang on 2006-10-08
Using the mississipi counting method (yes not very scientific) I counted 25s to bootup to login screen and 34 seconds to boot up into a ready to use desktop (with beryl starting up too) so a very nice speed increase using the "profile"  tweak! Before i believe it took 30-35 seconds to reach the login screen

---

### Post by zenrox on 2006-10-08
i whent for 1.04 mins to 56sec
whole 8sec improvment
kewl 
edgy-20061008-1.png is before this tip
edgy-20061008-2.png is after

---

### Post by jdong on 2006-10-09
> **dolphinsonar said:**
> The file says that, is it a moot point or should I also change that file?

That's a moot point, an artifact that goes back to the Ubuntu packaging, where changing just that file does nothing, but you actually have to change debian/readahead.init to get the changes installed to the system. So, ignore it :)

---

### Post by matthew on 2006-10-09
I didn't see this thread until just now. Tried it and shaved 10 seconds off my boot time. Thanks, jdong!

---

### Post by BLTicklemonster on 2006-10-09
In addition to the above, how can I remove unnecessary stuff such as laptop stuff and things I really don't have or use that I see listed while my computer is booting, and then see being killed as it is being turned off? Seems to me that these things would add some time for sure.

---

### Post by ashrack on 2006-10-09
> **jdong said:**
> [Digg this story]("http://digg.com/linux_unix/Improve_Ubuntu_Bootup_Times_by_Refreshing_Readahead_List")
**How do I do this?**

 (1) Perform the above profiling procedure. **It is important that the order is correct, else this form of readahead won't do a thing!**
 (2) Use your favorite text editor (under sudo or root privileges) to open **/etc/rcS.d/S01readahead**
 (3) Find line 21, which reads:
```

            if /sbin/start-stop-daemon --start --quiet --background \

```

Remove the --background, so that it reads:

```

            if /sbin/start-stop-daemon --start --quiet \

```


I don't have that option! Using UBUNTU DAPPER! Mine looks like this:

```
#!/bin/sh -e
# init script for readahead

# Check the package is still installed
[ -x /sbin/readahead-list ] || exit 0

# Get LSB functions
. /lib/lsb/init-functions
. /etc/default/rcS


# Remember that any major changes to this script need to also be made to
# readahead-desktop.init

case "$1" in
    start|restart|force-reload)
	# This can take a while
	if type usplash_write >/dev/null 2>&1; then
	    usplash_write "TIMEOUT 360" || true
	fi

	# If "profile" is placed on the kernel command-line we watch the boot
	# sequence and generate new readahead lists, rather than read the lists
	if ! grep -q "profile" /proc/cmdline; then
	    log_begin_msg "Reading files needed to boot..."
	    if /sbin/start-stop-daemon --start --quiet \
		--pidfile /var/run/readahead-list.bogus \
		--startas /sbin/readahead-list -- -s /etc/readahead/boot; then
		log_end_msg 0
	    else
		log_end_msg $?
	    fi
	else
	    log_begin_msg "Preparing to profile boot sequence..."
	    if /sbin/start-stop-daemon --start --quiet \
		--pidfile /var/run/readahead-watch.bogus \
		--startas /sbin/readahead-watch -- -o /etc/readahead/boot; then
		log_end_msg 0	
	    else
		log_end_msg $? || true
	    fi 
	fi

	if type usplash_write >/dev/null 2>&1; then
	    usplash_write "TIMEOUT 15" || true
	fi
	;;
    stop)
	;;
    *)
	echo "Usage: /etc/init.d/readahead {start|stop|restart|force-reload}"
	exit 1
	;;
esac

exit 0

```
And upon further examination of the file I believe that when setting "profile" in grub it automaticly executes the following:
```
	    if /sbin/start-stop-daemon --start --quiet \
```
What do U thing?

---

### Post by jdong on 2006-10-09
ashrack -- you must be running dapper-backports, in which case the "bonus hack" is already applied. No further work is necessary on your part then :)

BLTicklemonster, the presence of those files in boot.list indicates that your system is using them during bootup. If you want to try to bypass them completely, then you're gonna have to take a bootup manager application of some sort and remove "unnecessary" rc scripts from /etc/rcS.d and /etc/rc2.d.... Messing something up there could render your system unbootable though!

Basically, I'd leave it alone. That's not what I'd consider to be a "safe hack" :)

---

### Post by BLTicklemonster on 2006-10-09
Well, yeah, but I'm like running a desktop, not a laptop. But okay.

---

### Post by jdong on 2006-10-09
Those things really don't take that long to execute anyway...

---

### Post by BLTicklemonster on 2006-10-09
Thanks, I have gone from 48 seconds to 43 seconds, and just checked, and background is already gone. 


(now, should I put it BACK, then profile again, then remove it? I noticed you said to make sure they were done in order, and apparently background was already missing before I profiled)

---

### Post by jdong on 2006-10-09
Like the 5th time I said it in this thread (maybe I'll edit the howto and update it with the tidbit), but background has been removed already for you if you use dapper-backports. Recently I authorized Edgy's readahead system to be backported to Dapper, which brings most of this tip's benefits to any Dapper system. Not saying that profiling won't make any difference -- as you noticed, apparently everyone's system is somewhat different after we finish installing our apps :)

As far as removing background vs adding it back in, all I can say is experiment and see which works best. For most systems, the new style of operation (without background) will be faster, but the difference should only be by a few seconds at most anyway.

---

### Post by zek725 on 2006-10-19
> **jdong said:**
> Hmm, how much RAM you people have? If you've got insufficient RAM to load all the readahead files into RAM, it's not worth your time to do any readahead at all.


Another alternative way you can try to speed bootup is disabling readahead -- open up /etc/readahead/boot with a sudo'ed text editor of your choice, and delete its contents.


To get the contents back, just re-profile :)

384Mb SDRAM

---

### Post by glotz on 2006-10-19
I'm on a Pentium 3 450@527MHz with whopping 192 megs of ram and an ancient harddisk. Results:

Initial 1.12
Profiling 2.57
Profiled 1.08 <---
No readahead 1.14

So a very small benefit for me. :)

---

### Post by ahaslam on 2006-10-23
Thank you, I went from 2 mins to 1 min 40 secs :)

This has more effect than InitNG and there's nothing to compile & set up ;)

I didn't require the second hack, it was already set as specified (only on line 23).

Thanks again,

Tony.

---

### Post by volanin on 2006-10-31
**Even more improvements:**

To make your boot times even faster, use these two options:

*profile single*

This way, you will after some time fall into the console without booting X.
This will remove a lot of unnecessary files from the readahead folder.
Once in the console, just type *reboot* and see if it is faster.

I shoved 7 more seconds from my boot time this way.
Please, check this and post the results.

---

### Post by jdong on 2006-10-31
Profiling in single-user mode will only accelerate /etc/rcS.d bootup.... X Windows, GDM, and HAL/D-Bus will not be preloaded... It may improve your boot speed, or it might cause it to decrease.

---

### Post by Eddie Hung on 2006-10-31
It doesn't seem to do anything for me according to bootchart... and I'm using the latest Edgy...?

Eddie

---

### Post by jdong on 2006-10-31
> **Eddie Hung said:**
> It doesn't seem to do anything for me according to bootchart... and I'm using the latest Edgy...?

Eddie

You'll get less of a boost in Edgy because all of the above techniques are applied by default.

---

### Post by domino on 2006-10-31
I tried this on Edgy before i read your comment about it already applied by default. I'm not really sure if it applies to this thread, but what made a 5 second difference is disabling FAT32 fs check in fstab. At fresh install my boot time was at ~36 +/- 2 seconds. shaved about 5 seconds disabling fschck.vfat, took off another 3 seconds when i uninstalled vmware ws and disabled usplash. Constant boot time now is 27 seconds on every reboot and cold boot.

Any chance to get it down to 15 without disabling any more services? :D

---

### Post by MetaMorfoziS on 2006-11-01
Thank you for this howto, it cutted about 8-10 seconds for me.
As you said, i'm not found the --background, but the profile worked well.

It's on kubuntu edgy on a notebook: 2000+amd mobile, 256mb ram (-92 video) and it boots in 46 seconds. I'm going to find other workarounds to speed up, and then i do all on my pc and come back the results (i i not forget that:))

So again, thanx.

---

### Post by Yink on 2006-12-21
Thank you for this. Definitely made a difference on my dell laptop 6400.

---

### Post by duns0014 on 2007-02-19
> **jdong said:**
> For "power users" who can do a bit of tinkering, you can build your own readahead lists. Run "sudo readahead-watch -o /etc/readahead/myapp.list" to start readahead monitoring and write a list to /etc/readahead/myapp.list. Run "sudo killall readahead-watch" to stop monitoring after you're done.

Then, run " (sudo) readahead-list /etc/readahead/myapp.list" to prefetch myapp.list. Running without sudo just means the app won't resort before reading.

So, you can tinker with readaheading various lengthy tasks. I've had good success with readaheading GNOME/KDE startup (hint: have /etc/rc.local prefetch your list, so if you don't immediately login, readahead will prefetch your login sequence anyway) and openoffice (just created a /usr/local/bin wrapper script). With firefox, there was no improvement, presumably not enough disk IO to make a real impact.

This sounds like a really good way to speed up gnome.  For me, it takes as long for gnome to finish loading after I get to gdm as it takes to get to gdm from grub.  But how exactly can I do this?  Will this even work for me if I have gdm log me automatically?

---

### Post by jdong on 2007-02-19
It's less effective if GNOME logs you in for you. and the performance speedup is not terribly significant. If it sped things up a mind-blowing amount I would already have posted a howto and sample readahead lists for GNOME and KDE already :D

---

### Post by duns0014 on 2007-02-19
Dang, but thanks.  Loading the files at the same time as the boot files wouldn't work?

It's really great that the ubuntu people are speeding up the boot process (collapsing cron, etc into it is good too), but desktop start up is where so much of the wait is now, I wonder if the kde people have something planned for kde4?

I've heard that feisty is going to be even faster than edgy, I'm looking forward to that.  Bootchart tells me it takes 27 seconds right now, any estimate what that'll be on feisty?

---

### Post by jdong on 2007-02-19
Well preloading does less good on accelerating desktop load time -- it helps to some degree for sure, but for me the improvement was like 5% or so... not worth the amount of effort I put into it. Basically, you'd edit /etc/rc2.d/S99stop-readahead and in the stop action, put in sleep 120 before it stops readahead.

Now you have 120 secs to perform actions you typically do. (log in. load Firefox/Openoffice?). Now wait or ps aux | grep readahead to see when readahead dies. When it does, reboot :)

---

### Post by duns0014 on 2007-02-22
So what's with that readahead-desktop that's under /etc/rcS.d/ ?  Looking through the code (I'm no expert at this though) it looks like it does the same thing except that it fills up /etc/readahead/desktop at a different point in the boot process.  But that doesn't have anything in it.  Why's it there if it doesn't do anything?  How can I make it work?

---

### Post by jdong on 2007-02-22
IIRC that's for Edubuntu/LTSP network boot so that readahead doesn't take absurdly long.

---

### Post by mshlin on 2007-02-27
Thanks for tip my thinkpad R51 seems to boot a bit quicker. The really cool bit is that I now know more about the boot up process.:)

---

### Post by John Nilsson on 2007-03-24
By inspiration from this [thread]("http://www.mail-archive.com/reiserfs-list@namesys.com/msg22212.html"). I threw together this little defragmentation scheme:

(For this to work make sure that the destination dir resides on the same file system as the copied files)
```
mkdir /refrag && cd /refrag
```

Backup (if you don't know how to rescue a dead system using only a LiveCD and this tar-file, stop reading now)
```
tar -c -T /etc/readahead/boot  -f backup.tar
```

Create a numbered list of files. (Maybe paranoid step, but at least we won't have any surprises)
```
cat -n /etc/readahead/boot > files.txt
```

Copy those files to single dir (should pack them together on the disk)
```
cat files.txt | while read num file; do cp -dp "$file" "./$num"; done
```

Relink the files to the copies
```
cat files.txt | while read num file; do test -e "./$num" && ln -f "./$num" "$file"; done
```

I haven't done any measuring. Maybe someone here might be interested enough to do that though.

---

### Post by glotz on 2007-03-25
Disregard this post, i'm tired and not thinking straight at all...



^ Should be  ```
tar -cvvf backup.tar /etc/readahead/boot
```

I'm getting tons of entries like > cp: cannot stat `/lib/modules/2.6.15-27-686/kernel/drivers/input/gameport/ns558.ko': No such file or directory
when copying to the dir, should this happen?
when executing the relinking, i'm give loads of stuff like
> ln: cannot remove `/bin/mount': Permission denied

which doesn't sound too promising!

---

### Post by John Nilsson on 2007-03-25
> **glotz said:**
> ^ Should be  ```
tar -cvvf backup.tar /etc/readahead/boot
```

Doesn't that just backup the /etc/readahead/boot file? Then intention was to backup all files listed in it...

> I'm getting tons of entries like when copying to the dir, should this happen?
If you haven't done a profile run I guess this file would list files that no longer exist.

> when executing the relinking, i'm give loads of stuff like
You need root permission to replace system files.

---

### Post by glotz on 2007-03-25
Uhmmm, yes. Sorries, shouldn't read no forums this tired. I'll go to sleep a bit now....

EDIT: one thing you actually could include in that post is the spell to use the backup, if need be.

---

### Post by Sencer on 2007-03-26
> **John Nilsson said:**
> I haven't done any measuring. Maybe someone here might be interested enough to do that though.

Hey John [#71], what a nice idea! I have a year old 2,5" HDD and made an upgrade from dapper to edgy (meaning, the hdd-speed is not great, and files were probably pretty defragmented). Bootchart showed that during readahead I had 100% Disk utilization, but very low throughput (and 1100 files in the readahead list) - so your idea looked promising.

So I tried out your method. After the initial profiling I was consistenly at 46 sec according to bootchart. After doing your method, bootchart shows a total of 40 seconds. **Improvement: 6 seconds (or 13%)**. Thank you. :)

Since in the last step you are making hard links, I assume we can simpy delete the entire refrag directory afterwards.
Also there should be no hindrance in doing the same for readahead-desktop, right?
Anybody have any idea on how to do the profiling (as in the first post of this thread) for readahead-desktop?

---

### Post by John Nilsson on 2007-03-26
> **Sencer said:**
> Hey John [#71], what a nice idea!
I can't take credit though, see the thread I linked to for the whole thing. Quinn Harris crated some python scripts and a patch for readahead to do this (only better because the patch sorted the files according to atime), the script didn't work for me though, thus this bash version.

> After doing your method, bootchart shows a total of 40 seconds. **Improvement: 6 seconds (or 13%)**. Thank you. :)
Cool =)

> Since in the last step you are making hard links, I assume we can simpy delete the entire refrag directory afterwards.
Should be safe.

> Also there should be no hindrance in doing the same for readahead-desktop, right?
I couldn't get this to work though. Assumed it was because of my weird mounting scheme (I bind mount /home/.var to /var).

---

### Post by pelago on 2007-03-31
Thanks for this thread. I've just shaved 10 seconds off my feisty system by doing the profile thing (the --background is of course already removed).

I noticed that the original boot file, before profiling, referred to a lot of files in /lib/modules/2.6.20-12-generic and /lib/linux-restricted-modules/2.6.20-12-generic when I was actually running 2.6.20-13, so profiling sorted that out. So I would recommended re-profiling for every kernel upgrade, not just major Ubuntu version upgrades, unlike the advice in the first post.

---

### Post by Mon on 2007-04-02
My boot time actually increased after doing this...
I've got a pretty old system, just keep dist-upgrading at every release and I'm running Feisty now. The number of files now read is way more then the original but that's to be expected and probably even a good thing I guess.
I did notice this by the way:
```

wc -l readahead
199 readahead

sort readahead|uniq|wc -l
179

```

So there are twenty files read "double" on boot, unless the profiler actually takes doubles in consideration...
Also there are lots of files that seem unnecessary to me. Cups banner pages and files in /var/log for example.
Then there are fglrx entries in my boot file while I have a nVidia card. or about two hundred python lines as well which seem pretty scary to me.

I could just remove these entries but I guess at boot those files are then still read so I would effectively slow the system down.

Only thing I can think of is a fresh Feisty reinstall, but that's the Windows way and not acceptible in my opinion.

Any ideas?

---

### Post by Sencer on 2007-04-03
> **Mon said:**
> My boot time actually increased after doing this...

Did you measure it, or is it just your impression? Just curious. Because for about 10-15 seconds (or longer) it will just read the necessary files which can seem like a long time, especially if you have usplash+quite - but it's worth it, as the total time does go down. 
Of course you can always go and reduce the number of files that are preloaded, or you can put the process in the background - while I doubt it would be faster, it will certainly remove the "stuck" feeling, as the progress bar keeps moving.

> wc -l readahead

Is it possible that you checked the readahead script? And that you intended to check the file-list which is in "/etc/readahead/boot"? Because 199 seems like an awfully low number, I have always had > 1000 in there (and no duplicates for me).

> Also there are lots of files that seem unnecessary to me. Cups banner pages and files in /var/log for example.

Yeah, I got those, too. As long as those files are touched on startup (there is a cupsys that is started on boot), readahead sticks them in there. As long as those files are in a more or less continous spot on the harddrive (see sugestion at the top of this page), the many small files hardly matter IMHO. Kicking out a lot of small files (due to removed services) hardly reduced the amount of time boot spends in readahead for me (bootchart is nice to check this).

> or about two hundred python lines as well which seem pretty scary to me.

due to hplib maybe? You can always try

> find /etc/rc* | xargs grep -i python

to get some hints (though it may not always work, since scripts from other locations are sourced and started).

> Any ideas?

After the above - check the services you have installed (sysv-rc-conf), and try out bootchart which will also give you an idea where time is spent. (Unnesseary interfaces? duplicate dhcp queries? unneeded services?).

---

### Post by jdong on 2007-04-04
> **Mon said:**
> My boot time actually increased after doing this...
I've got a pretty old system, just keep dist-upgrading at every release and I'm running Feisty now. The number of files now read is way more then the original but that's to be expected and probably even a good thing I guess.
I did notice this by the way:
```

wc -l readahead
199 readahead

sort readahead|uniq|wc -l
179

```

So there are twenty files read "double" on boot, unless the profiler actually takes doubles in consideration...

Duplication really doesn't matter; once a file is read once into cache, asking it to be read again is an instantaneous operation.

> 
Also there are lots of files that seem unnecessary to me. Cups banner pages and files in /var/log for example.
Then there are fglrx entries in my boot file while I have a nVidia card. or about two hundred python lines as well which seem pretty scary to me.

Any files being listed in there mean that your system bootup opened those files for read access. Hence, they are actually being read during bootup and readahead is doing you a favor to prefetch it. Python, if your bootup starts any Python apps, will indeed need to touch a few hundred module files.




However, it is important to point out that there is a break-even point for readahead. That is, there's a point where you are spending so much time prefetching when you could be booting, that you end up slowing down bootup. Try profiling, then truncating your readahead file by 25% or so at a time, seeing when you get the fastest boot. Reading everything ahead may not be the fastest.

---

### Post by tormod on 2007-04-06
Maybe you should update the original post, since readahead runs in foreground by default since Edgy.

---

### Post by jdong on 2007-04-06
> **tormod said:**
> Maybe you should update the original post, since readahead runs in foreground by default since Edgy.

Default Edgy, default is foreground. If you're using Backports repositories, then it runs in background.

---

### Post by bayley on 2007-04-23
Thanks for the tip Jdong.
It really helped my bootup speed.  It looks like the bonus hack made it into Edgy.  when I went to do it, it was already done.  Good work, thanks for making it clear enough for a newbie to follow.

---

### Post by duns0014 on 2007-06-11
When I had edgy, profiling worked for me.  Now with feisty, I put 'profile' in grub and it doesn't do anything different.  I looked at my logs and nothing even shows up except for the messages that are passed to the kernel.

---

### Post by moofhead on 2007-07-08
I recently "upgraded" (if you can call it that - I haven't been happy since) from Dapper to Edgy, then to Feisty. In moving from Dapper to Edgy, I noticed that my boot time was WAY longer. After reading this thread and trying a few things, I have settled on making readahead run in background. That dropped my boot time from 3:44 "HIDEOUS" to 1:51 merely "AWFUL."

I suspect that there are more problems yet to sort out for my pc, since I don't recall having to wait nearly two minutes for bootup when I was running Dapper, although I don't have any objective data to go on from that era. I do, after all, have a pretty decent pc.

My pc used to keep me better informed of what it was doing during bootup and shutdown, too, when I was running Dapper. Now, I get to stare at a black screen while I stew about how long things are taking.  :confused:

---

### Post by tormod on 2007-07-08
> **moofhead said:**
> I suspect that there are more problems yet to sort out for my pc, since I don't recall having to wait nearly two minutes for bootup when I was running Dapper, although I don't have any objective data to go on from that era. I do, after all, have a pretty decent pc.

My pc used to keep me better informed of what it was doing during bootup and shutdown, too, when I was running Dapper.
Just remove "quiet" or also "splash" from the boot parameters in grub, and you'll get start-up messages.

You can install bootchart to get objective time measurements on the boot-up process: [https://wiki.ubuntu.com/BootCharting](https://wiki.ubuntu.com/BootCharting)

---

### Post by moofhead on 2007-07-08
> **tormod said:**
> Just remove "quiet" or also "splash" from the boot parameters in grub, and you'll get start-up messages.

You can install bootchart to get objective time measurements on the boot-up process: [https://wiki.ubuntu.com/BootCharting](https://wiki.ubuntu.com/BootCharting)

Thanks, tormod. I have been using bootchart to track my progress as I try various things to reduce my boot time.

I have experimented with removing "quiet" and "splash" from the boot parameters as you recommended, with the following results:

Starting condition: quiet and splash - 1:50 boot time
no quiet, no splash - 0:56
quiet, no splash - 0:45
splash, no quiet - 1:49
no quiet, no splash (tried again, just for kicks) - 0:44

When I remove splash from the boot parameters, I can see startup and shutdown messages, which is what I wanted. I am uncertain, though, what removing quiet and/or splash do otherwise. It's nice to be able to boot faster, of course, but what are the consequences of removing quiet and/or splash?

---

### Post by tormod on 2007-07-08
> **moofhead said:**
> I am uncertain, though, what removing quiet and/or splash do otherwise. It's nice to be able to boot faster, of course, but what are the consequences of removing quiet and/or splash?

splash and quiet should have absolutely no consequences (bar bugs) whether they're on or off. The slower booting with "splash" is just because the animation uses extra system resources during boot. I am surprised how much impact it had on your machine though. "quiet" is just a flag for the kernel and start-up scripts to be less verbose.

---

### Post by jdong on 2007-07-08
Quiet tells Ubuntu's boot scripts and also the Linux kernel to suppress all console output except direly urgent ones.

Splash enables the graphical bootsplash.

This bootsplash can be very CPU intensive on some computers, which yields a bad bootup time with it enabled.

---

### Post by glotz on 2007-07-08
Very interesting. I'll be sure to test out those parameters myself. A fancy lookin' boot is nice, a quick boot is nicer! ;)

---

### Post by Brando569 on 2007-07-09
it looks like this hack already made its way into feisty :)

---

### Post by rahul_bhise on 2007-07-22
i did remove quiet and splash from the second line which starts with kernel but it keeps on adding the next time i reboot.
the time taken for booting with splash is 03.20 minutes
without splash it takes just                    00.40 minutes
what should i do so the change i made is saved at every boot up

---

### Post by tormod on 2007-07-22
> **rahul_bhise said:**
> i did remove quiet and splash from the second line which starts with kernel but it keeps on adding the next time i reboot.
the time taken for booting with splash is 03.20 minutes
without splash it takes just                    00.40 minutes
what should i do so the change i made is saved at every boot up

The kernel lines are auto-generated (see the explanation text inside menu.lst). You have to modify the #defoptions= line in /boot/grub/menu.lst to make permanent changes.

---

### Post by tormod on 2007-07-22
> **rahul_bhise said:**
> the time taken for booting with splash is 03.20 minutes
without splash it takes just                    00.40 minutes
From looking at the graphs it seems there's a problem with usplash spending a lot of CPU. Please file a bug against usplash and attach the two graphs there.

---

### Post by jdong on 2007-07-22
> **tormod said:**
> From looking at the graphs it seems there's a problem with usplash spending a lot of CPU. Please file a bug against usplash and attach the two graphs there.


Yep, you're correct -- this is clearly some sort of  bug with usplash that eats CPU.

---

### Post by rahul_bhise on 2007-07-23
where should i file for a bug report for usplash
> You have to modify the #defoptions= line in /boot/grub/menu.lst to make permanent changes.
thanks  i edited the menu.lst  and no problems now

---

### Post by DjBones on 2007-07-23
Thanks! my system boots considerably faster now..
i didn't need to do the additional 'hack' lol, mine didn't have --background listed.. spooky haha

---

### Post by st33med on 2007-08-21
Thanks. It improved times *slightly*. It was reduced from 26 seconds to 24 seconds.

Not bad, eh? :)

Also, will disabling readahead in bootup processes affect the profiling?

---

### Post by banewman on 2007-09-06
I went through the services that start by default in feisty and got some improvement but when I  reprofiled the boot readahead file that's when I got a significant decrease in boot times. 35 sec from grub to login with splash. Best thread I've found to decrease the boot time! 
On another note, there is, in /etc/readahead/, a desktop file that is outdated for my setup - how do I reprofile that?

---

### Post by jdong on 2007-09-06
The desktop file is not used in standard Ubuntu systems; but rather it is a LTSP (i.e. Edubuntu) specific file so that readahead at boot doesn't use a slow network link and delay total boot time.

---

### Post by markp1989 on 2007-09-06
wow that works extremely well. thank you 

boot time before was 50 seconds

now my boot time is about 35 secs, so that cut about 15 sec off

I still would like it to be faster,(fink DCHP on my network slows it down a bit)

anyone know any other way to speed up boot time?

---

### Post by glotz on 2007-09-07
You've seen this baby titled " HowTo: Speed up ubuntu boot process - the way you can feel it.", right?
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by nickless on 2007-10-28
:( Great using this I gained additional 5 seconds to my boot time :confused: I guess there is no way to restore the old profile? How can this be anyways??
(Using Gutsy on an Dell Inspiron 9400 laptop)

---

### Post by Mr. Picklesworth on 2007-11-05
Gutsy no longer seems to run readahead in the background, by the way. (So the bonus hack is just for previous versions).

---

### Post by jdong on 2007-11-05
Right, it was that way in Feisty too --- immediately after pointing this out to Scott James Remnant he made the change in Ubuntu to do readahead in the foreground by default.

---

### Post by cyberbuff on 2007-11-29
Yes it's working...thanks for the tip... :)

---

### Post by meindian523 on 2007-12-31
10 seconds less from Grub to Working Desktop.Thanks man!Though it's still a huge 50 secs... :(Shouldn't a 512 MB RAM make booting faster?

---

### Post by ~LoKe on 2008-01-01
Shaved about 3 seconds off my boot time, so I'm down to 18 seconds.  Better than I thought I'd get, but I'm looking for more. ;)

---

### Post by MamiyaOtaru on 2008-02-14
Bootchart went from 27 to 40 with readahead enabled :-/  

It seems it's set to run in the foreground, which as jdong said Scott James Remnant has made the default.  Setting readahead to run in the background brings it down to 37. 

Caveats:
I'm using bootchart to get these results. Bootchart seems to quit once KDM starts.  If readahead is reading in stuff used by KDM and thereby speeding up KDM, that speedup would appear not to be recorded by bootchart.  Further testing seems to show this to be the case.  Readahead's seems to speed up x start->kdm login and that is missed by bootchart.  Stopwatching it to usable desktop I get 1 second slower with readahead.   So readahead continues to have benefits after KDM starts, and bootchart misses them, but in my case they aren't enough to offset the slowdown prior to KDM.

At any rate, for me it is faster with readahead in the background than in the foreground.  As I said before, it gets to KDM 3 seconds faster with it in the background, and by that time it is in fact done running, so that's 3 seconds saved, though I save more by not having readahead enabled in the first place (barely).

---

### Post by frankos44 on 2008-03-08
On my Gutsy 64bit it made no difference, it still sits at around 32 seconds from grub to login screen.

On Hardy Herald using same PC there was an improvement of about 10 seconds but still slower to boot than Gutsy.

---

### Post by frankos44 on 2008-03-08
> **~LoKe said:**
> Shaved about 3 seconds off my boot time, so I'm down to 18 seconds.  Better than I thought I'd get, but I'm looking for more. ;)

18 seconds seems like a very good time. What is the spec?

---

### Post by cipher_no1 on 2008-04-28
thanx good howto shaved 10 secs of my hardy boot time :-)

---

### Post by _Stevie_ on 2008-04-28
hardy has the deb "readahead" installed by default. does that mean
all the tweaking is not necessary anymore?

---

### Post by jdong on 2008-04-28
> **_Stevie_ said:**
> hardy has the deb "readahead" installed by default. does that mean
all the tweaking is not necessary anymore?

This tweak works with the readahead package to see what *your* system uses at bootup, to gear the readahead sequence to your computer's needs.

---

### Post by _Stevie_ on 2008-04-29
ah okay, thanks for the clearification!

---

### Post by collegeKid28 on 2008-08-28
For some reason, gedit won't let me save the boot file after deleting its contents.  It says, "You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

Any suggestions?

Thanks

---

### Post by Locke_99GS on 2008-08-28
Try running gedit with sudo.

---

### Post by John Nilsson on 2008-08-29
Instead of sudo you can use gksudo. gksudo is a GUI version sudo so that you can use it in a launcher and such without having to open a terminal for the password verification.

---

### Post by glotz on 2008-08-29
You really **should** use gksudo to run graphical programs. Using sudo there could cause some nasty permissions issues. Use sudo for command line only apps.

As in, drop to the terminal and key in
[I]
gksudo gedit[/I] and then do the edit and it will save

---

### Post by collegeKid28 on 2008-09-03
Thanks to all who helped: glotz, jdong, locke_99gs, and john nilsson; deleting the contents of 'boot' shaved a few seconds off boot up!

---

### Post by Meetloaf13 on 2008-09-16
Man, I'm envious of all these sweet boot-times.

My boot-time is currently around 70-80s in Ubuntu HH 8.04

Specs:
T7300 C2D
7200RPM 160GB
4GB RAM
Dual-boot Ubuntu 8.04 x64/Vista x64

I boot Vista x64 ~40s...if I can boot Vista in that short amount of time, I know I've gotta be able to get Ubuntu to best it.

I've read through the posts, I tried removing the 'splash' command from the 'menu.lst" but it didn't do anything noticeable.

I've disabled a few things like bluetooth & braille, and a few other programs like Evolution, but I'm stuck here.

I'm much of a linux n00b (I know, I know).  But I know enough to tweak with a little help.

Here are two of my bootcharts (first with Splash on, second with it removed from menu.lst.)  Why do the bootcharts say ~35s when it takes much longer from grub to load?

Thanks for any help/suggestions.

---

### Post by Lord Udedenkz on 2008-09-18
Two Simple Question,
- This thread has been running 2 years, is it still revelant?
- is it add "profile" to the end or add " profile" to the end (notice the space)
Thank You :)

---

### Post by jdong on 2008-09-18
> **Lord Udedenkz said:**
> Two Simple Question,
- This thread has been running 2 years, is it still revelant?
- is it add "profile" to the end or add " profile" to the end (notice the space)
Thank You :)

Yes, this information is still relevant -- Ubuntu through Intrepid still uses the readahead-list system to accelerate bootup.

And you must add a space -- "profile" needs to show up as a separate word.

---

### Post by Meetloaf13 on 2008-09-18
This tip didn't do anything for me, any clues why?

---

### Post by jdong on 2008-09-18
> **Meetloaf13 said:**
> This tip didn't do anything for me, any clues why?

If you haven't installed any new bootup services since installing the base system, this probably won't have a huge impact. The most beneficial part of this trick (reordering readahead files to match layout of each user's disk) has been incorporated into recent Ubuntu releases based on the tremendous positive feedback here.

---

### Post by sarah.fauzia on 2008-10-28
> **jdong said:**
> If you haven't installed any new bootup services since installing the base system, this probably won't have a huge impact. The most beneficial part of this trick (reordering readahead files to match layout of each user's disk) has been incorporated into recent Ubuntu releases based on the tremendous positive feedback here.
[COLOR="Silver"]
So, since I have the latest build of Intrepid, does that mean I still have to go through the procedure, or it is automatic? I have to admit, I have a very fast boot-up...30.5 seconds from the black screen till when my computer is usable. I actually had the big improvement after I installed splashy...[/COLOR]

---

### Post by ShirishAg75 on 2008-11-03
Hi all, 
 The profiling helped, but as told by other posters read-ahead is now different. 

```

#!/bin/sh -e
### BEGIN INIT INFO
# Provides:          readahead
# Required-Start:    
# Required-Stop:
# X-Start-Before:    mountkernfs hostname
# Default-Start:     S
# Default-Stop:
# Short-Description: init script for readahead
### END INIT INFO

# Check the package is still installed
[ -x /sbin/readahead-list ] || exit 0

# Get LSB functions
. /lib/lsb/init-functions
. /etc/default/rcS


# Remember that any major changes to this script need to also be made to
# readahead-desktop.init

# Remove the boot list to disable this readhead phase
[ -r /etc/readahead/boot ] || exit 0

case "$1" in
    start|restart|force-reload)
    # This can take a while
    if type usplash_write >/dev/null 2>&1; then
        usplash_write "TIMEOUT 360" || true
    fi

    # If "profile" is placed on the kernel command-line we watch the boot
    # sequence and generate new readahead lists, rather than read the lists
    if ! grep -q "profile" /proc/cmdline; then
        log_begin_msg "Reading files needed to boot..."
        if /sbin/start-stop-daemon --start --quiet \
        --pidfile /var/run/readahead-list.bogus \
        --startas /sbin/readahead-list -- -s /etc/readahead/boot; then
        log_end_msg 0
        else
        log_end_msg $?
        fi
    else
        echo 524288 > /proc/sys/fs/inotify/max_user_watches

        log_begin_msg "Preparing to profile boot sequence..."
        if /sbin/start-stop-daemon --start --quiet \
        --pidfile /var/run/readahead-watch.bogus \
        --startas /sbin/readahead-watch -- -o /etc/readahead/boot; then
        log_end_msg 0    
        else
        log_end_msg $? || true
        fi 
    fi

    if type usplash_write >/dev/null 2>&1; then
        usplash_write "TIMEOUT 15" || true
    fi
    ;;
    stop)
    ;;
    *)
    echo "Usage: /etc/init.d/readahead {start|stop|restart|force-reload}"
    exit 1
    ;;
esac

exit 0

```

Now its on line 37

```
 
if /sbin/start-stop-daemon --start --quiet \

```

So now we need to make this in the background?

---

### Post by jdong on 2008-11-03
```

       log_begin_msg "Reading files needed to boot..."
        if /sbin/start-stop-daemon --start --quiet \

```

Close to that invocation of start-stop-daemon. DO NOT background the second one in any case! That will not make for very productive profiling in the future!

---

### Post by ShirishAg75 on 2008-11-03
Jon, 
 Just so I didn't misread you are saying that changing line 37 of /etc/rcS.d/S01readahead 

```

log_begin_msg "Reading files needed to boot..."
        if /sbin/start-stop-daemon --start --quiet \

```to 

```
 
log_begin_msg "Reading files needed to boot..."
        if /sbin/start-stop-daemon --start --quiet --background \

```I am inserting background again and this would improve my performance?

I am confused :(

---

### Post by jdong on 2008-11-03
Depending on your system, hard drive speeds, NCQ support, amount of disk cache, filesystem, RAID configuration, and other variables, background may be faster, or foreground may be faster. Foreground is currently default. Background was default. There's no way for me to tell you what will work better on your system. Please put a space after background before the \ newline escape.

---

### Post by ba0bab on 2008-11-04
Hi,

I'm a bit nervous about tinkering with the GRUB loader, so I'd like if someone wrote the "full command" that you use, so far nobody have done that.

What mean is: after pressing "E" in GRUB, how should I write profile exactly? like this: (?)
```

kernel xxxxx--profile

```
or
```

kernel xxxx --profile

```
or..

you get the idea.

Thank you!

---

### Post by jdong on 2008-11-04
There are no dashes:

```

kernel xxxx profile

```

---

### Post by ShirishAg75 on 2008-11-04
Hi Jon, 
 Put up your tip and gave reference to this thread on [http://flossexperiences.wordpress.com/2008/11/04/apcupsd-reducing-boot-time/](http://flossexperiences.wordpress.com/2008/11/04/apcupsd-reducing-boot-time/)

---

### Post by kuad on 2008-11-18
After pressing "e" the first time I get 4 options:

1) UUID [a whole bunch of numbers letters]
2) kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=[same id as in 1] ro quiet splash
3) initrd /boot/initrd.img-2.6.27-7-generic
4) quiet

I assume I should be choosing option 2 and appending "profile" to that line?

What do the other options mean?

Thanks

---

### Post by anonymous_user on 2008-11-28
Along with kuad's question, would it do any harm if I added profile to the first and second choices (on separate reboots)?

---

### Post by jdong on 2008-11-28
The system only remembers one profile run. Subsequent profiles will overwrite previous ones. You should add profile to the boot option that most reflects your typical bootup scenario, i.e. the default choice.

---

### Post by latinoguy18 on 2008-12-05
kk

---

### Post by seenxu on 2008-12-06
This tip doesn't help me at all, before profile 33s, after profile 33s, no change at all. :(
It's also possible that My system won't need any further optimization. :D

---

### Post by macvr on 2009-01-15
> **seenxu said:**
> This tip doesn't help me at all, before profile 33s, after profile 33s, no change at all. :(
It's also possible that My system won't need any further optimization. :D

are u kidding? ur boot is already 33secs! why do u need to optimize it?!!

---

### Post by macvr on 2009-01-18
i used profile... but it didnt help me ! my boot time remained the same...

my total boot time from switching on is 1min35secs till i can use the system...

split:>
till end of grub options:12s
boot according to bootchart:38s
[COLOR="Red"]??????????????[/COLOR]:[COLOR="DarkRed"]21s[/COLOR]
login after a logout:24 secs

ok, i'm just a noob but this may be a silly question !
why is there a gap of 21s? what happens during that time? 

could someone look at the bootchart and check if anything can be improved?


i'm using an Acer laptop with INTEL centrino DUAL CORE 1.66GHz , with 2 GB ram , would this be a reasonable startup time or is it slow?
 its just that i hear startup times of 33 secs i'm wondering if my settings are correct!

---

### Post by tormod on 2009-01-20
Boot without "splash" and "quiet" and see if it hangs for a while at some point. Are you talking about 21s after logging in? Please explain more clearly which steps your timings refer to.

---

### Post by macvr on 2009-01-20
> **tormod said:**
> Boot without "splash" and "quiet" and see if it hangs for a while at some point. Are you talking about 21s after logging in? Please explain more clearly which steps your timings refer to.

my total boot time from switching on is 1min35secs till i can use the system...

so i counted from switching on 

till end of grub options:12s [i'v set grub to AUTO select the option in 1 sec]

boot according to bootchart:38s


but it takes me 1min35secs for me to be able to use my system...
SO i logged out and measured the time it takes for full login >24secs ...

so when i add up the time it accounts for 1min14secs... so there is an unaccounted 21secs... so i thought that it existed between the boot and the user login.....

so i was wondering what the 21secs was used for? if i could cut it down...
i'v also tried jdong's other readahead method ...  BUT the readahead increases the startup times to 1min50secs...! so i'v undone all those steps i had done for readahead...

oh... i dont have "quiet" in my grub... but use the finger print splash theme, so i can see the boot messages, and i dont see any hangs during boot...

---

### Post by tormod on 2009-01-21
> **macvr said:**
> but it takes me 1min35secs for me to be able to use my system...
SO i logged out and measured the time it takes for full login >24secs ...

so when i add up the time it accounts for 1min14secs... so there is an unaccounted 21secs... so i thought that it existed between the boot and the user login.....

The second time you log in will be faster than the first time, so you can't do arithmetics like this.

Ok, so your refererence (zero) is power on. How many seconds before X starts? before the gdm greeter? time between log in and useable system?

There is a gap between grub and when bootchart starts, so the bootchart total time does not tell everything, it just useful to compare betweeen bootcharts.

---

### Post by macvr on 2009-01-21
> **tormod said:**
> The second time you log in will be faster than the first time, so you can't do arithmetics like this.

Ok, so your refererence (zero) is power on. How many seconds before X starts? before the gdm greeter? time between log in and useable system?

There is a gap between grub and when bootchart starts, so the bootchart total time does not tell everything, it just useful to compare betweeen bootcharts.

ok...
previously i had auto login enabled... now i disabled it and recored times...

refererence (zero) is power on
grub ends at 0:12
_how do i know/say when x starts? _ is it the appearance of the X ? if so then 0:58secs
gdm greeter appears at 1:05
usable system is 1:37

---

### Post by hyper_ch on 2009-01-21
install bootchart and it will tell you how long it takes from grub until gdm.

---

### Post by macvr on 2009-01-21
> **hyper_ch said:**
> install bootchart and it will tell you how long it takes from grub until gdm.

i have attached my bootchart  to this post
[http://ubuntuforums.org/showpost.php?p=6569848&postcount=140]("http://ubuntuforums.org/showpost.php?p=6569848&postcount=140")

i think according to it , its 38 secs

---

### Post by hyper_ch on 2009-01-21
38 seconds ain't that bad... however it should take 21 seconds afterwards to load *dm and xserver...

---

### Post by macvr on 2009-01-21
> **hyper_ch said:**
> 38 seconds ain't that bad... however it should take 21 seconds afterwards to load *dm and xserver...

well hearing that some get startup times of totally 33 secs , my 1:37 was disappointing! , i guess they were talking of only the boot time...!

---

### Post by hyper_ch on 2009-01-21
you can even start it in 5 seconds... if you heavily modify everything...

[http://www.slashgear.com/five-second-boot-mod-for-asus-eee-pc-0618430/](http://www.slashgear.com/five-second-boot-mod-for-asus-eee-pc-0618430/)

---

### Post by macvr on 2009-01-21
> **hyper_ch said:**
> you can even start it in 5 seconds... if you heavily modify everything...

[http://www.slashgear.com/five-second-boot-mod-for-asus-eee-pc-0618430/](http://www.slashgear.com/five-second-boot-mod-for-asus-eee-pc-0618430/)

aint that greedy !

its just that when i was using XP my boot times were around 1:30 and i cut it down to 55secs... was hoping to do the same with ubuntu...

well i'm planning on using *sysv-rc-conf* to cut down the times... think that would work...
but reading up on all the services , else i might mess up my system disabling the wrong ones!!!

---

### Post by tormod on 2009-01-21
> **macvr said:**
> how do i know/say when x starts? is it the appearance of the X ?
X is starting when the usplash screen disappears and the screen blanks (and often flashes a bit). Sometimes it takes X a while (probing screens and outputs, setting up) before it displays the cursor. Once the cursor is there, it's the login manager (or session-manager if autologin) which is starting.

---

### Post by macvr on 2009-01-21
> **tormod said:**
> X is starting when the usplash screen disappears and the screen blanks (and often flashes a bit). Sometimes it takes X a while (probing screens and outputs, setting up) before it displays the cursor. Once the cursor is there, it's the login manager (or session-manager if autologin) which is starting.


refererence (zero) is power on
grub ends at 0:12
[COLOR="DarkRed"]the flashing blank screen appears at 0:51 secs [X][/COLOR]
gdm greeter appears at 1:05
usable system is 1:37

any thing that could be reduced?

---

### Post by tormod on 2009-01-21
> **macvr said:**
> i have attached my bootchart  to this post
[http://ubuntuforums.org/showpost.php?p=6569848&postcount=140]("http://ubuntuforums.org/showpost.php?p=6569848&postcount=140")

i think according to it , its 38 secs

Your bootchart looks ok, nothing really bad in there. The readahead list takes about one third of the time though. As an experiment try to disable it completely. You also have a bunch of extra things installed, virtualization, samba, dkms, etc which takes time. The more specialized your system is, the more reason to reprofile it.

BTW, I installed the Jaunty kernel in Intrepid and it sped up my boot because it has more drivers built in so less probing and loading is done in the initrd. However I will encourage interested people to install Jaunty to a separate partition and help sorting out boot performance issues as it is being developed, it is a stated goal of Jaunty to get the boot time down, but more testing on different hardware will help.

---

### Post by macvr on 2009-01-21
> **tormod said:**
> Your bootchart looks ok, nothing really bad in there. The readahead list takes about one third of the time though. As an experiment try to disable it completely. You also have a bunch of extra things installed, virtualization, samba, dkms, etc which takes time. The more specialized your system is, the more reason to reprofile it.
was thinking of disabling readahead, but was worried if i might mess up my system... i'v noticed it takes nearly 10secs!
will try that

> **tormod said:**
> BTW, I installed the Jaunty kernel in Intrepid and it sped up my boot because it has more drivers built in so less probing and loading is done in the initrd. However I will encourage interested people to install Jaunty to a separate partition and help sorting out boot performance issues as it is being developed, it is a stated goal of Jaunty to get the boot time down, but more testing on different hardware will help.
ya have been hearing a lot of good things bout jaunty

how did u install jaunty kernel on intrepid??? i have a separate 9GB partition where i could install it... i will try it when i have some spare time...

---

### Post by tormod on 2009-01-21
> **macvr said:**
> how did u install jaunty kernel on intrepid???
Find the latest release on [https://launchpad.net/ubuntu/+source/linux/](https://launchpad.net/ubuntu/+source/linux/)
and then click through the right package (for instance linux-image-2.6.28-5-generic) and find the .deb for your architecture. It will install along with the old one, so you can choose which kernel to boot in the grub menu.

This will void all warranties of course :)

For some hardware you might need an updated corresponding linux-firmware package as well, [https://launchpad.net/ubuntu/+source/linux-firmware/](https://launchpad.net/ubuntu/+source/linux-firmware/)

Note that I don't post more direct links, they will change with newer releases, and also, those who don't understand much of this should probably not try it.

---

### Post by macvr on 2009-01-21
> **tormod said:**
> 
This will void all warranties of course :)



WARRANTY!!!!!:o

since when does ubuntu come with warranty ?;) [maybe for preinstalled ubuntu dell systems!]
[http://www.ubuntu.com/legal]("http://www.ubuntu.com/legal")

will be trying the newer kernel or also the alpha jaunty in the separate partition...

thank you...

---

### Post by Xgamer on 2009-01-30
My ubuntu 8.04 boot 29s... with complete localhost server = lighttpd + php5-cgi + mysql5-server

---

### Post by kyeh on 2009-03-24
My system takes roughly 40 seconds just reading the file list, which has about 3500 lines, is this normal?

---

### Post by tormod on 2009-03-24
> **kyeh said:**
> My system takes roughly 40 seconds just reading the file list, which has about 3500 lines, is this normal?
That sounds like way too many lines. My /etc/readahead/boot has 730 lines, /etc/readahead/desktop 274 (stock Jaunty).

---

### Post by Yashiro on 2009-03-30
I had used these tweaks a long time ago.
All had been fine until recently. After running a profile from the kernel line my machine randomly failed to get a DHCP address on boot.

Re-adding the --background switch to S01readahead fixed it completely.
This issue seems very timing specific.

If you start init.d/networking a few milliseconds later, as S60, it works fine.
Or you could run /etc/init.d/networking restart at a much later point, and again, it's fine.

So, if you have connectivity issues using anything but 'roaming mode' in Network Manager this is a possible reason for failure.
Something to keep in mind when you tweak your readahead.

---

### Post by jdong on 2009-03-30
Interesting, that sounds like a boot race condition of some sort worth investigating. It's probably just the difference in disk read speed that's resulting in a network card not being ready when the bootup script runs to that point.

---

### Post by Yashiro on 2009-03-30
That's what I thought. The window for failure was pretty small too. Fractions of a second.
The interesting side effect is that the only obvious sign of failure at first is not getting an IP address. Which usually results in cursing at network manager.

It took about 2 days of messing around and config restores to find the problem.

---

### Post by jdong on 2009-03-30
> **Yashiro said:**
> That's what I thought. The window for failure was pretty small too. Fractions of a second.
The interesting side effect is that the only obvious sign of failure at first is not getting an IP address. Which usually results in cursing at network manager.

It took about 2 days of messing around and config restores to find the problem.

Fascinating. It would be interesting to chase down exactly why it happens; after all readahead is just "exposing" a bug, not really the culprit per se. A slightly faster hard drive would've probably done the same.

---

### Post by jward3010 on 2009-04-04
I've just tried this on a fresh install of Jaunty beta, fully up to date. My machine is pretty decent so I was wondering if ther would be a big difference - Athlon64 3700 overclocked to 2.53GHz, 1GB DDR550 RAM, Seagate Barracuda S-ATA II 250GB drive, nForce4 motherboard.

Without profiling: From the GRUB loader screen to full desktop took around **35.8** seconds.

With profiling: From the GRUB loader screen to full desktop took around **33.2** seconds.

Nothing incredible but worth having nonetheless.

---

### Post by glotz on 2009-04-04
Do you know, where on the disk is the profiling data written?

---

### Post by anthonyp on 2009-04-14
My boot on intrepid went from 31s to 35s :(

---

### Post by Locke_99GS on 2009-04-14
Thats better than nothing. Greater improvements could be had from removing useless or unused modules.

---

### Post by crjackson on 2009-04-15
> **anthonyp said:**
> My boot on intrepid went from 31s to 35s :(

I've been in that boot (I mean boat) too. Sometimes it will actually increase the boot times. :frown:

---

### Post by twl on 2009-04-29
> **crjackson said:**
> I've been in that boot (I mean boat) too. Sometimes it will actually increase the boot times. :frown:

Wish I'd known aboot (I mean about) that before I tried it.

My boot time went from 67s to 79s.

Then I emptied /etc/readahead/boot, and it went to down to 74s.

Which I guess I can live with.  74s and 67s feel the same to me (ie, slow).  But I wish I'd read a little more of this thread first.  And backed up /etc/readahead/boot.  And maybe it wouldn't be a bad idea to include /etc in my periodic backups.  (Ya think?)

Note to self: learn to leave well enough alone. :)

---

### Post by jdong on 2009-04-29
Purge readahead then reinstall the package to restore the default list.

---

### Post by twl on 2009-04-29
> **jdong said:**
> Purge readahead then reinstall the package to restore the default list.

Back to 67s.  Thank you.

---

### Post by Ubuntu Terrier on 2009-04-29
Interesting thread. I tried to optimize with profiling the booting process of my rig (Intel G45 mainboard, E8500 Core 2 Duo downclocked @ 2.53 Ghz, Western Digital Raptor 74GB 10k rpm) on Ubuntu 9.10 Karmic Koala (development-testing) and to track the changes with Bootchart:

Without profiling: 12 seconds
With profiling: 12 seconds
With profiling and --background read-ahead: 12 seconds

It looks like I hit a wall, though with optimizations, according to Bootchart, I/O transfer speed seems to have increased and Hard Disk usage maxed out. Probably the boot time decreased by less than one second.

This is a video of a cold-start complete bootup of my pc before profiling: [http://www.youtube.com/watch?v=3wj6n66d9b4](http://www.youtube.com/watch?v=3wj6n66d9b4)

---

### Post by Fyrzen_ on 2009-05-02
Mystifying...:confused:

After profiling boot time went from 25s to 30s(according to bootchart.

The bonus hack seems to be enabled by default as there is no "--background" anywhere in the file. 

Since i have only 256MB RAM I considered disabling readahead altogether. The "boot" file was already empty however the "desktop" file was loaded with useless stuff like:
```

/usr/lib/bluetooth/plugins/audio.so
/usr/lib/bluetooth/plugins/hal.so
/usr/lib/bluetooth/plugins/input.so
/usr/lib/bluetooth/plugins/netlink.so
/usr/lib/bluetooth/plugins/network.so
/usr/lib/bluetooth/plugins/serial.so
/usr/lib/bluetooth/plugins/service.so

```
I'm running Jaunty 9.04 which was upgraded from 8.10 using aptitude safe-upgrade. Googling yields bug reports on Intrepid having an overenthusiastic readahead file and preloading stuff like screensavers. 

With readahead disabled boot time increased to 31s... :confused:

Is there any way i can get it back to 25s? :(

EDIT: I purged readahead and reinstalled, got it down to 26s.

---

### Post by H3g3m0n on 2009-07-12
I have a OCZ vertex and an i7 920. Jaunty boots in 15sec according to bootchart with no profiling (I am using preload, haven't checked if that changing boot speed).

After profiling this went up to 27sec (purging readahead fixed it), so it seems fairly pointless for those of us with SSDs.

---

### Post by kaenlsp on 2010-01-30
Id like to save boot up time but ive got a problem...
when my grub loads i press ESC as you said and nothing seems to happen, after some time itll just boot up normally, ignoring what i pressed.
any help?

---

### Post by emarkay on 2010-06-10
Confirm please - this is now invalid (no longer applicable) for Lucid and Maverick?

---

### Post by Alfons81 on 2010-07-02
If you are using Lucid Lynx and you don't have another operating system on your computer, to show up your grub, you should edit the follow archive:

sudo gedit /etc/default/grub

It shows your grub configuration, find the following line and comment it with this simbol '#':

GRUB_HIDDEN_TIMEOUT=0

Like this:

#GRUB_HIDDEN_TIMEOUT=0

Save this new configuration, and run the following command in your terminal:

sudo update-grub

##To come back to the default configuration, uncoment the line and run again:

sudo update-grub

I hope it helps, but with the default grub in Lucid Lynx 10.04 the line begining by 'kernel' doesn't exist. Then were to put 'profile'?

---

### Post by tormod on 2010-07-02
> **Alfons81 said:**
> I hope it helps, but with the default grub in Lucid Lynx 10.04 the line begining by 'kernel' doesn't exist. Then were to put 'profile'?
/etc/default/grub has this line: ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
``` where you can add kernel options and run update-grub.

However, to reprofile ureadahead, just delete /var/lib/ureadahead/pack

---

### Post by nutellajunkie on 2010-08-13
spiffing, if it works..

But we shoudl only be rebooting with kernal updates ;) come on folks, uptimes important, not boot-time* ;)

*sarcasm

---

### Post by malspa on 2010-08-15
Quite a long-running thread!

Looks like the technique mentioned in the following article accomplishes pretty much the same thing:

[http://www.techtipsgeek.com/speed-up-boot-up-process-ubuntu-10-04-lucid-lynx/9496/](http://www.techtipsgeek.com/speed-up-boot-up-process-ubuntu-10-04-lucid-lynx/9496/)

Ubuntu boot times have gotten a lot better since this thread started -- so much so that I don't think I'll bother using "profiling."  But, fascinating stuff!

---

