---
title: "Howto: An easy way to enable CK patches"
date: 2010-12-03
forum: Packaging and Compiling Programs
---

### Post by NightwishFan on 2010-12-03
[COLOR="DarkRed"]**UPDATE: I am for now no longer maintaining this tutorial as I am not using the latest Ubuntu release. If anyone has questions or requests they can add them to this thread.**[/COLOR]

[COLOR="DarkRed"]**UPDATE!! This method works on lucid however the CK patches will not apply. You will have to use just BFS on its own (without CK) or just skip CK altogether and use the normal source.**[/COLOR]

[COLOR="DarkRed"]**Updating tutorial for MAVERICK this does not work on lucid.**[/COLOR]

[CENTER]**What is this about?**[/CENTER]

Hello and welcome, I am going to explain an easy way to successfully patch and compile the Ubuntu kernel with the CK patches. This works great for me, though I am far from an expert and may have done something a non optimal way. I am counting on you guys to point out what I could do better, and make a great tutorial on this. Please tell me immediately if you find any bugs in here. :)

[CENTER]**What the heck are the CK patches?**[/CENTER]

Renowned programmer Con Kolivas was unsatisfied with Linux desktop performance. He went about writing a series of patches to improve the situation. Most of them are not intended to be included in the main line kernel however they are quite stable. Some distributions and Android made use of them. More info here:
[http://en.wikipedia.org/wiki/Con_Kolivas](http://en.wikipedia.org/wiki/Con_Kolivas)

Now that you have the background we can begin. This process does involve patching and compiling the kernel. Thankfully this process is almost completely automated. Just pay attention as this tutorial is going to be written where just about everything I say is important, and what is not I will leave for power users to figure out. This focus is just on getting it done. Also, for this tutorial I am putting the code in QUOTE tags as I need formatting on them. There is only one line of code per quote. Forgive if you have difficulty in copy/pasting them.

First, there are several required packages that we may or may not use in the course of this tutorial. You will need a source repo installed. Just just source code in software sources. To get them in one fell swoop open a terminal and run:
> sudo apt-get install kernel-package build-essential libncurses5 libncurses5-dev dpkg-dev fakeroot

When that is finished we can move on to the next step, which is to get things organised and download the kernel source. A note before we continue. [COLOR="DarkRed"]This is important.[/COLOR] Any of the commands I post are designed to be run in order, and inside the appropriate directory. Pay attention to the "cd" commands to know which directory you are in. You will need to "cd" back to redo a step correctly. Also note anything I put in [COLOR="DarkRed"]**BOLD RED**[/COLOR] text is something that you should take notice of, and potentially something that may need manual editing. I am writing this tutorial with Ubuntu 10.04 in mind. Users of 10.10 will need to alter all instances of 2.6.32 to 2.6.35. I will make that quite clear as we go on.

Now, to organise things a bit:
> mkdir compile
Then do:
> cd compile

Now we have to download the kernel source. This needs to be the exact version of Linux you are running. Do not worry it is simple. To find your kernel version run the command below. It should say something along the lines of "linux-2.6.32-26-generic" if you are on 10.04. This is what to pay attention to.
> uname -a

Now to download and unpack the source run this command, replace the bold text with your kernel version reported.
> apt-get source linux-image-[COLOR="DarkRed"]**2.6.35-23-generic**[/COLOR]

Good, you should now have the kernel source, it will unpack to a directory. Do not change to it just yet though. First we have a few other steps. This method of compiling the kernel is called the "Debian way". It is quite simple however needs a quick workaround to get the initramfs to work. Simply run:
> cp -r /usr/share/kernel-package $HOME/compile/kernel-package

This next part you may need to replace the bold letters with the first 3 numbers of your kernel version. (example: 2.6.35) Run:
> cp linux-[COLOR="DarkRed"]**2.6.35**[/COLOR]/debian/control-scripts/{postinst,postrm,preinst,prerm} kernel-package/pkg/image/ && cp linux-[COLOR="DarkRed"]**2.6.35**[/COLOR]/debian/control-scripts/headers-postinst kernel-package/pkg/headers/

The next step is to download the CK patch for your kernel version. This one is a bit more manual. Go to: [http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/](http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/)

Find the directory name matching your version of Linux. Under the subdirectory either ck1 or ck2 is fine. (You may only see ck1). Copy the link for the file called "patch-**2.6.35-ck1**.bz2". Now back to the terminal run:
> wget [COLOR="DarkRed"]**paste-link-from-browser**[/COLOR]

Then to extract and patch (remember to edit manually if you are on a different kernel) run:
> bzip2 -d patch-[COLOR="DarkRed"]**2.6.35-ck1**[/COLOR].bz2
Then:
> cd linux-[COLOR="DarkRed"]**2.6.35**[/COLOR]/
Finally this to patch:
> patch -p1 < $HOME/compile/patch-[COLOR="DarkRed"]**2.6.35-ck1**[/COLOR]

Whew, now that is over, the fun (some may say hard part) is coming up. Configuring the kernel. Lucky for us, we do not have to do the whole thing by hand. We want to match the Ubuntu kernel configuration as closely as possible. To copy the current config run:
> cp -vi /boot/config-`uname -r` .config

Next we need to get things ready. When you run this command you will get a prompt asking you to enable SCHED_BFS. Choose &#8220;YES&#8221;. (press y)
> make oldconfig

Now the final part of configuring the kernel. When you run &#8220;make menuconfig&#8221; this is the kernel configuration. By default it should match exactly the current Ubuntu config you are using, except it will have the CK patch set enabled. This is good as you only need to edit what you want to change. It is quite simple, poke around in a few of the settings. Use Enter to go into a sub-menu, use Space to enable or disable a setting. Hit Tab to choose one of the options at the bottom. If you do not understand an option, use Help. If you STILL do not understand an option. Do not change it. Have fun, though please not a lot of the options do not need to be changed.
> make menuconfig

A mandatory value to change is [COLOR="DarkRed"]**General Setup &#8594; Control Group Support**[/COLOR]. Please use the spacebar to disable it. Also, on 2.6.32 you may also have the option: [COLOR="DarkRed"]**General Setup &#8594; Group CPU Scheduler**[/COLOR]. Disable that as well. The BFS scheduler does not use control groups.

Recommended values to change are [COLOR="DarkRed"]**Processor Type &#8594; Timer Frequency**[/COLOR] set to 1000hz (DO NOT SET IT ANY HIGHER). You should also set [COLOR="DarkRed"]**Processor Type &#8594; Preemption Model**[/COLOR] to Preemptible Kernel (Low-Latency Desktop). When you are done, hit &#8220;Exit&#8221; and choose to save your new configuration.

This is optional, I would run it though. It cleans the build in case of previous failed attempts to build:
> make-kpkg clean

Now finally to compile. Ensure you are still in the linux-[COLOR="DarkRed"]**2.6.35**[/COLOR] directory. I set up the command below to run in fakeroot so no root privileges needed. It also will run as nice 10 so you can still use your machine during the compile. The &#8220;--append-to-version=&#8221; please leave the dash &#8220;-&#8221; right after the equals. You can replace the text in bold with whatever you want. When you are satisfied, hit enter to begin! This will take a while, and may fail if you set up a crazy configuration. :)
> nice fakeroot make-kpkg --initrd --append-to-version=-[COLOR="DarkRed"]**customkernelname**[/COLOR] --overlay-dir=$HOME/compile/kernel-package kernel-image kernel-headers

It worked! Now how do I install? Simply run the commands below:
> cd $HOME/compile/
Then:
> sudo dpkg -i *.deb

Reboot and you are running your own custom kernel build, optionally with the performance enhancing CK patch set. :)

---

### Post by NightwishFan on 2010-12-04
Fixed a few bugs in commands, sorry folks!

---

### Post by NightwishFan on 2010-12-04
Found the answer, kernel compile fails with 2.6.32:
[http://ubuntuforums.org/showpost.php?p=10130787&postcount=62](http://ubuntuforums.org/showpost.php?p=10130787&postcount=62)

If I get this updated and working for lucid I will bump the post, it is hit or miss really.

This tutorial works on Maverick, I have mine running now.

---

### Post by mikebugman1968 on 2010-12-04
kool hope you get it all worked out for us nebs to run it also

---

### Post by NightwishFan on 2010-12-04
I will keep digging, I already bothered Con Kolivas once today I will wait a few days to ask him anything (after all he is not personal pc help). For now, disregard the tutorial if you run lucid, you need the Maverick kernel source for it to work.

---

### Post by mc4man on 2010-12-04
The one thing I'm seeing atm moment concerns this
> Recommended values to change are Processor Type &#8594; Timer Frequency set to 1000hz (DO NOT SET IT ANY HIGHER). You should also set Processor Type &#8594; Preemption Model to Preemptible Kernel (Low-Latency Desktop).

It seems those where set from make oldconfig and now in menuconfig are not editable
From oldconfig step (clipped
> Preemption Model
  1. No Forced Preemption (Server) (PREEMPT_NONE)
> 2. Voluntary Kernel Preemption (Nothing) (PREEMPT_VOLUNTARY)
  3. Preemptible Kernel (Low-Latency Desktop) (PREEMPT)
choice[1-3]: 2

The Timer Frequency was set in oldconfig to 1000
screen shows in menuconfig - cannot enter the submenu
Any thoughts there

---

### Post by NightwishFan on 2010-12-04
That is strange. Did you do the step where you copy the config from your current kernel? Also what kernel version did you try to build? I tested it doing those steps using Maverick (2.6.35). I tried lucid and it was many levels of fail as the patch isn't compatible due to some bug.

If I run make menuconfig right now I am able to run change it.

---

### Post by mc4man on 2010-12-04
> Also what kernel version did you try to build
This is what I'm on
2.6.35-23-generic #41-Ubuntu SMP
series of commands from history
> cd compile 
apt-get source linux-image-2.6.35-23-generic
cp -r /usr/share/kernel-package $HOME/compile/kernel-package
cp linux-2.6.35/debian/control-scripts/{postinst,postrm,preinst,prerm} kernel-package/pkg/image/ && cp linux-2.6.35/debian/control-scripts/headers-postinst kernel-package/pkg/headers/ 
wget [http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/2.6.35/2.6.35-ck1/patch-2.6.35-ck1.bz2](http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/2.6.35/2.6.35-ck1/patch-2.6.35-ck1.bz2)
bzip2 -d patch-2.6.35-ck1.bz2
cd linux-2.6.35/ 
patch -p1 < $HOME/compile/patch-2.6.35-ck1
cp -vi /boot/config-`uname -r` .config 
make oldconfig 
make menuconfig 

Maybe I'll start fresh or can you post the section of .config as edited
current here
> CONFIG_SCHED_SMT=y
CONFIG_SCHED_MC=y
# CONFIG_PREEMPT_NONE is not set
CONFIG_PREEMPT_VOLUNTARY=y
# CONFIG_PREEMPT is not set
CONFIG_X86_LOCAL_APIC=y

---

### Post by NightwishFan on 2010-12-04
I can upload my .config if you want. Just rename it to use.

---

### Post by mc4man on 2010-12-04
Will ck. that out
You'll have to excuse these next 3 ?'s due to overall ignorance in kernel stuff (though I think I'll have to do some reading ect.

I'm somewhat assuming this setting is the same as a realtime kernel?, if so is it possible the source I've downloaded can't be set with that option?

Is this 'Preemptible Kernel (Low-Latency Desktop' something that makes doing/using the patch worthless or close to in it's absence?

---

### Post by NightwishFan on 2010-12-04
Well the ck patch writer is a famed kernel hacker, and he recommends it. It is not the same as the realtime kernel, it is not designed for hard latencies. Here is the logic: [http://ck.kolivas.org/patches/bfs/bfs-faq.txt](http://ck.kolivas.org/patches/bfs/bfs-faq.txt)

You are able to do it from the standard Ubuntu kernel sources. I might have done the tutorial wrong, but if I follow it, it works fine.

I will double check.

---

### Post by mc4man on 2010-12-04
Hand edited the line(s) in question, will see what occurs
Also to mention the 'Timer Frequency' was also non-editable though had been set as wanted when running the make oldconfig

(may also try later on desktop (maverick

edit: in any event am glad to see this thread/how-to, very interesting stuff

The kernel is building, did, after about 30 secs or so present me with some add. options requiring an answer to proceed, took a guess there... (possibly i'l post that, have terminal set to unlimited scrollback so can retrieve

---

### Post by NightwishFan on 2010-12-04
Edit, youtube hates me. :D

Well, why not try to cd to the kernel source and run make oldconfig/make menuconfig again?

---

### Post by mc4man on 2010-12-05
Actually went ahead and rightly or wrongly just edited those 2 lines in the .config to 
> # CONFIG_PREEMPT_VOLUNTARY is not set
CONFIG_PREEMPT=y
Then proceeded with the build which just finished, am currently using that kernel.
I think making the changes after the fact prompted having to set a new option at the beginning of the build. (forgot to save the terminal output)
It was asking something about enabling debug related to preempt kernel. Answering that lead to one more about 'trace', then the build proceeded along.

So i think your instr.'s are quite fine, must be some local oddity here that wouldn't allow entering some sub menu's. (what, is beyond me..

Because I tend to make a number of changes (though can't see why it would affect this), probably will do a fresh install soon, build the kernel and see. I use a local repo for packages I modify, so a new install is quite quick and easy. I'll build the kernel first.

Anyway the kernel built and installed fine, did it's thing with nvidia without issue, ect.
> $ uname -a
Linux doug-XPS-M1330 2.6.35.7-ck1-wellsee #1 SMP PREEMPT Sat Dec 4 22:08:17 EST 2010 i686 GNU/Linux
A bit late to ck. out though I did set up a large I/O and saw no slowdowns or lag whatsoever.
Thanks for posting this up, will let you know if I ever figure out the submenu deal.

If come natty you find any useful info related to this and how to do ect. that would be great. 
On my main desktop which runs natty the new compiz is much 'snappier', so a combo of the 2 would be a good deal..

---

### Post by NightwishFan on 2010-12-05
To be honest, the tutorial should work with Natty as well, as long as CK has a patch for it. He only is at 2.6.36 now and I am quite sure Natty uses .37 (.38 when launched). So we will have to wait for him to catch up.

It fails on all .32 kernels (Lucid) and not just the Ubuntu one I believe.

Here is the BFS FAQ if you are curious about it. It is actually more than just a new scheduler and has a lot of interesting patches now. A nice tip is to install the package 'schedtool' and then you can use the new sched_iso and sched_idlepro see: (man schedtool).
[http://ck.kolivas.org/patches/bfs/bfs-faq.txt](http://ck.kolivas.org/patches/bfs/bfs-faq.txt)

Thanks for posting your results. Hopefully I can make this a little more in depth soon enough.

---

### Post by mc4man on 2010-12-12
Just as a bit of follow up - did on my mav. desktop and there were no issues about entering any sub menus, so just some unexplainable nonsense on that laptop.

---

### Post by NightwishFan on 2010-12-12
Excellent I am glad it works for you.

---

### Post by criticalsmile on 2010-12-27
**Ok, I'm not a 'noob' but I'm just a kernel compiler from back in the day. Old school. Remember the old steps?**
./configure
make menuconfig  (make xconfig or gconfig if you're really awesome)
make modules
make
make install

**Why on earth doesn't this work anymore? :-(**
[B]
What the heck is this jazz for? What is it?[/B]
cp linux-[COLOR=DarkRed]**2.6.35**[/COLOR]/debian/control-scripts/{postinst,postrm,preinst,prerm} kernel-package/pkg/image/ && cp linux-[COLOR=DarkRed]**2.6.35**[/COLOR]/debian/control-scripts/headers-postinst kernel-package/pkg/headers/

**This part confuses me because it's not like the other patch files I saw in the directory linked on this tutorial.** **They were *cpufreq-bfs_tweaks.patch* and *preempt-desktop-tune.patch*. Does this patch include all of those?**
bzip2 -d patch-[COLOR=DarkRed]**2.6.35-ck1**[/COLOR].bz2
patch -p1 < $HOME/compile/patch-[COLOR=DarkRed]**2.6.35-ck1**[/COLOR]

**What about this after *make oldconfig***?
make localmodconfig

**Finally, could a 'noob' please get a description of what this is? Fakeroot? Why? What does this do that we need it? Why doesn't old school work anymore? :-(**
nice fakeroot make-kpkg --initrd --append-to-version=-[COLOR=DarkRed]**customkernelname**[/COLOR] --overlay-dir=$HOME/compile/kernel-package kernel-image kernel-headers

**I loved your tutorial, NightWishFan, because for the FIRST TIME ever, I compiled a successful kernel which wasn't broken. My WiFi worked, sound worked, AND my stupid ATI drivers worked. Sadly though, the kernel was super pokey. I tried removing things after but then the second time I ran through the steps it ended with an error of too many 'debug' something. Whatever. I'm going to try everything again from scratch using my new .config. The new .config has removed a lot of stuff and I'm going to enable cgroups.**
[B]
Can you please address these questions in your tutorial so your tutorial can be the most awesomeness? Would very much appreciate it! Thank you very much! :-D

[/B]*For super added bonus....Could any of this work on Ubuntu 10.10 with the vanilla Kernel from kernel.org? I really really wanted to use that kernel but I when I use it, usually my WiFi, sound and/or ATI video stops working. :-(*

---

### Post by criticalsmile on 2010-12-27
AS      arch/x86/lib/rwlock_64.o
  AS      arch/x86/lib/rwsem_64.o
  AS      arch/x86/lib/thunk_64.o
  CC      arch/x86/lib/usercopy_64.o
  AR      arch/x86/lib/lib.a
  LD      vmlinux.o
ubuntu/built-in.o:(.bss+0x990): multiple definition of `debug'
arch/x86/built-in.o:(.kprobes.text+0x1d0): first defined here
ld: Warning: size of symbol `debug' changed from 61 in arch/x86/built-in.o to 4 in ubuntu/built-in.o
make[1]: *** [vmlinux.o] Error 1
make[1]: Leaving directory `/home/compile/linux-2.6.35'
make: *** [debian/stamp/build/kernel] Error 2
root@nacho:/home/compile/linux-2.6.35# 


***BIG FROWN* Any ideas? It's my config, I just know it. ;-)**

---

### Post by NightwishFan on 2010-12-28
> **Ok, I'm not a 'noob' but I'm just a kernel compiler from back in the day. Old school. Remember the old steps?**
./configure
make menuconfig  (make xconfig or gconfig if you're really awesome)
make modules
make
make install
Why on earth doesn't this work anymore? :-(

It does, however that method will hardly make you a Debian package, and give you the Ubuntu sources.


> What the heck is this jazz for? What is it?
cp linux-[COLOR=DarkRed]**2.6.35**[/COLOR]/debian/control-scripts/{postinst,postrm,preinst,prerm} kernel-package/pkg/image/ && cp linux-[COLOR=DarkRed]**2.6.35**[/COLOR]/debian/control-scripts/headers-postinst kernel-package/pkg/headers/

The kernel will not boot using this method unless you use the correct control scripts from the kernel-package... package.

> This part confuses me because it's not like the other patch files I saw in the directory linked on this tutorial.[/B] [B]They were *cpufreq-bfs_tweaks.patch* and *preempt-desktop-tune.patch*. Does this patch include all of those?

Yes, if you want them separate, use the "broken out" file in the same place. Personally I just use BFS itself.

> What about this after make oldconfig?
make localmodconfig

Because sometimes a user inserts a piece of hardware and it will not work. It is not a necessary step. If I wanted to do this, I would have just made the user compile a kernel in a different way and made sure they set up optimize by size and etc.

> Finally, could a 'noob' please get a description of what this is? Fakeroot? Why? What does this do that we need it? Why doesn't old school work anymore? :-(

Fakeroot simply runs a task in a fake root environment which is useful for compiling. The kicker is "make-kpkg" which creates the ready made ".deb" file for you.

> I loved your tutorial, NightWishFan, because for the FIRST TIME ever, I compiled a successful kernel which wasn't broken. My WiFi worked, sound worked, AND my stupid ATI drivers worked. Sadly though, the kernel was super pokey. I tried removing things after but then the second time I ran through the steps it ended with an error of too many 'debug' something. Whatever. I'm going to try everything again from scratch using my new .config. The new .config has removed a lot of stuff and I'm going to enable cgroups.

BFS does not support cgroups I am about 95% sure.

> Can you please address these questions in your tutorial so your tutorial can be the most awesomeness? Would very much appreciate it! Thank you very much! :-D 

I will update it when I can.

> For super added bonus....Could any of this work on Ubuntu 10.10 with the vanilla Kernel from kernel.org? I really really wanted to use that kernel but I when I use it, usually my WiFi, sound and/or ATI video stops working. :-(

The traditional way should work similarly. This is how you compile a kernel the Debian way. There are more Ubuntu specific ways, however this is how I always compile it myself.

---

### Post by NightwishFan on 2011-02-07
If any one is interested, you can compile a Lucid kernel with just the BFS scheduler (I normally just do only this myself). Just replace the step in the tutorial where you patch CK and patch this instead (pick one for your arch)

[http://ck.kolivas.org/patches/bfs/](http://ck.kolivas.org/patches/bfs/)

---

### Post by Turtle.net on 2011-03-19
Hi,
I followed your tutorial, but it doesn't compile.
The reported error is > In file included from kernel/sched.c:2:
kernel/sched_bfs.c:1785: error: conflicting types for ‘calc_global_load’
include/linux/sched.h:158: note: previous declaration of ‘calc_global_load’ was here


do you have any idea on the setting I should change in .config to make it work ?
I tried this on a desktop and a laptop under maverick.

Thanks

---

### Post by NightwishFan on 2011-03-19
That seems like an error with the BFS/CK patch. You might be using one that is out of date or "too new" for the Ubuntu kernel. I believe Maverick is using 2.6.35.11, you will need a patch to match that.

Try just the BFS patch if CK fails to build.
[http://ck.kolivas.org/patches/bfs/](http://ck.kolivas.org/patches/bfs/)

---

### Post by Turtle.net on 2011-03-19
I used this ck1 patch [http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/2.6.35/2.6.35-ck1/](http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/2.6.35/2.6.35-ck1/) (since I'm running 2.6.35-28 under maverick).
After posting my message I found [this]("http://forums.gentoo.org/viewtopic-t-832201-postdays-0-postorder-asc-start-325.html?sid=ee71ed819b5eb7834afff167147c9914") post on the Gentoo forum, that refer to [this discussion]("http://webcache.googleusercontent.com/search?q=cache:Pbaub0h6Kt0J:ck-hack.blogspot.com/2011/01/2637-ck1-bfs-0363-for-2637-grouping-by.html+ck+patch+calc_global_load&cd=1&hl=fr&ct=clnk&gl=ca&client=ubuntu&source=www.google.ca") on ck's blog.
So I patched the patch by replacing > void calc_global_load(void) by> void calc_global_load(unsigned long ticks)  and I also changed in .config CONFIG_NO_HZ=y by CONFIG_NO_HZ=n

It's compiling as we speak, the problem is : i don't really understand why ...

---

### Post by NightwishFan on 2011-03-19
Hopefully it compiles. Sorry to say I am not a C coder (yet) so I do not have the why without some reading of my own. Hopefully it works for you.

---

### Post by Turtle.net on 2011-03-19
It compiles all right ... but Segmentation Fault is not a good sign, right ?
It doesn't boot, so back to square one.

---

### Post by NightwishFan on 2011-03-19
Try an older kernel image if you can find one. Try: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by mc4man on 2011-03-26
Whether better or no difference can't say yet (will ck. out over weekend
Just to say builds and installs, ect.  quite fine in the current natty

---

### Post by NightwishFan on 2011-03-26
Thanks, I have not had a chance to test this as I currently am on Maverick. Also I have updated a bit of info in the first post about building on lucid and maverick.

Basically ensure that the patches correctly match the kernel version. Also I noted that building "just BFS" and not the whole CK patches sometimes works better, especially on 2.6.32.

---

### Post by mc4man on 2011-03-26
I had hoped to get in earlier in the night to ck. out but made the mistake of trying on a small 10 GB tester partition with a few things installed
With about 15 min. left realized I wasn't going to make it on space - even with some emergency package removal still came up a hair short (I bet less than 100MB
So had to do  a new larger natty install, ect.

Edit: have seen some unexpected behavior with certain actions, like closing a terminal or synaptic after installing or removing a package(s), causes unity/compiz to reset.
So have returned to current natty build, may revisit

(have lowered the natty's  ondemand up_threshold from the default of 95 to something more reasonable (70), always found that to be helpful

---

### Post by NightwishFan on 2011-03-26
I actually have just been using a preemptive kernel with CFS, and no longer use BFS/CK. I might do some testing to see how BFS works for my screen casts though.

---

### Post by HellBoyz77 on 2011-05-31
I can confirm the the CK patch correctly for Natty, kernel 2.6.38. The kernel compiled well.

I used the patch from here:
[http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/2.6.38/2.6.38-ck3/](http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/2.6.38/2.6.38-ck3/)

The kernel source was installed by apt-get install linux-source.

Will report if i noticed some performance boost.

---

### Post by NightwishFan on 2011-06-23
For now I am no longer going to update this tutorial as I can see no convenient way to keep up to date with Ubuntu releases and testing the patches.

If there are any questions or concerns, or even enough desire that I maintain this please feel free to post them here.

Hope you all found this useful. :popcorn:

---

### Post by Kova78 on 2011-07-28
Hi all :),
I'm a newbie :D
I'm trying to apply the CK1 patch to my Ubuntu 11.04 (2.6.38.8) version installed on my pendrive (thanks to the pendrivelinux.com.) that I use on my laptop.
I have to apply this patch because I have a problem with "ticks" used in an application developed in an old linux distribution (red hat 5.5 if I'm not wrong).

I executed these commands:
```

sudo apt-get install linux-source
patch -p1 < '/home/ubuntu/Desktop/patch-2.6.38-ck1'

```But I receive this message:
```
patching file arch/powerpc/platforms/cell/spufs/sched.c
Hunk #1 FAILED at 64.
patch: **** Can't create file arch/powerpc/platforms/cell/spufs/sched.c.orig : No such file or directory

```In the past  I tried to apply some mods to the /boot/config-2.6.38-8-generic file:
```
CONFIG_GENERIC_CLOCKEVENTS=n
CONFIG_GENERIC_CLOCKEVENTS_BROADCAST=n
CONFIG_RCU_FAST_NO_HZ=n
CONFIG_TICK_ONESHOT=n
CONFIG_NO_HZ=n
CONFIG_HIGH_RES_TIMERS=n
CONFIG_SCHED_HRTICK=n
CONFIG_HZ_100=y
CONFIG_HZ=250
```
In base to some info found on the net, but nothing the application doesn't work correctly.

Somebody can help me?
Thanks a lot for the help!
Have a nice day :)

---

### Post by NightwishFan on 2011-07-28
If you have the correct patch and it still does not want to patch right this means that it likely is out of sync with your specific kernel version. Perhaps try a different kernel version or use a mainline kernel.

---

### Post by Faffin on 2012-01-05
I managed to patch CK 3.0.0 to the Ubuntu 10.10 source. You have to edit a file. Details at: [Creating Debian packages for Linux kernels >= 3.0.0 in Ubuntu]("http://mjanja.co.ke/#2011/10/creating-debian-packages-for-linux-kernels-3-0-0-in-ubuntu/"). Apart from that, everything is working fine from just following the Howto.

```
warren@midnight:~$ uname -r
3.0.9-ck1-ck1
warren@midnight:~$ 
```

I don't know why the source was 3.0.9, when 10.10 is at 3.0.14 though.

---

