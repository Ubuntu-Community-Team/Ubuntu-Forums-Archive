---
title: "CK patch set"
date: 2010-05-06
forum: Packaging and Compiling Programs
---

### Post by danbh on 2010-05-06
Hello forum folks.  I'm not sure where to put this.  Can you please move this to an appropriate spot?  

I am creating this forum topic to support this bug report which involves the CK patchset for the kernel: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/424927](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/424927)
Please post any and all comments and bugs and crashes and help requests to this forum topic.  If you find something wrong with, or have a request regarding, the packaging or confguration of the ck patched kernel, please post on the bug report.  Thanks!

The CK patch set is intended to improve desktop interactivity performance. The biggest change is the inclusion of BFS: [http://en.wikipedia.org/wiki/Brain_****_Scheduler]("http://en.wikipedia.org/wiki/Brain_****_Scheduler")  (The link is censored because it includes a common swear word)

[https://launchpad.net/~chogydan/+archive/ppa](https://launchpad.net/~chogydan/+archive/ppa)

---

### Post by NightwishFan on 2010-05-08
Hi! I plan on using and testing your packages. Everything seems to go well. Need any assistance?

---

### Post by danbh on 2010-05-18
I'm finally able to push an update to a released kernel.  I hadn't been able to get the source code till last week.

NightwishFan, I don't really know about the bigger picture, ie getting this into the main archives, but I think it would be useful if people could figure out whether this patch is worth it.  I know that it was _way_ better in karmic.  Please, report back what kind of performance you are getting.  better? worse? the same?  I haven't had a chance to test myself.  I had been waiting for a new release, just because I was having trouble with the older releases.

---

### Post by chronniff on 2010-05-18
Hey, I have been using your build with the BFS patch...First of let me say thank you for taking the time to do it, and second of all, one major difference I have noted in lucid using your ck-preempt compared to the mainline preempt is a way lower load level, plus when it comes to compiling anything, the BFS scheduler really shows its worth, it has been cutting down most of my compile times by around half!!...of course nothing's perfect, I have been having issues with waking up from suspend...but I noticed that today Con Kolivas updated his patch and the changelog hints that it may address this, and now it seems that you are updating the ppa, so we will see..........thanks again

---

### Post by danbh on 2010-05-18
I'm glad you are getting such good results chronniff.  At some point we will have to tabulate all of our experiences.  

I realized that I was pretty vague about what I meant with "new release."  Since 2.6.32-20 through 2.6.32-22, I had always been getting -21 when I tried to download the source.  I didn't get it, it was weird, but it looks like it is over.  Thusly, I was able to send an update to the ppa.

Also of note, I reconfigured.  I think I got it right.  AMD64 server builds should be configured to 100HZ, and everything else should be 1000HZ.  Hopefully that fixes the AMD64 being at 250Hz that was reported earlier.

---

### Post by NightwishFan on 2010-05-19
I thank your hard effort. After I solve my bout of personal tragedy I will be in touch. I really like easy access to the desktop oriented kernel patches and I pledge my support in keeping it going. I will probably be settled in a week and be able to help out, even if only with testing.

Feel free to contact me here or otherwise, my email is:
[email]uraharakisuke153@gmail.com[/email]

---

### Post by mervinb on 2010-05-21
Dan, thanks for making the ppa available. I've tried the ck kernels on several laptops and desktops, and the results (seem to) range from little different to apparently smoother user experience. Great work!

It would be useful if you indicate that metrics are meaningful for you in comparing performance of bfs v cfs scheduling. At the moment it seems like keyboard and interactive graphics (eg. OpenOffice) are the areas there is noticeable improvement, but even then, it is purely qualitative.

---

### Post by chronniff on 2010-05-22
just to specify my testing of this, I have used it on both my new custom core i7 960 desktop, and also on an old dell inspiron 1420 with core 2 duo chip and integrated (yup those first ones dell sold with ubuntu preinstalled lol!).....results on the laptop are minimal performance enhancement, although I haven't tested it much
  On the core i7 however, there is an extremely noticeable performance boost..it's a quad core using hyperthreading remember, so  4 x2 equals 8 logical cpu cores.  BFS does a much better job taking advantage of the multiple cores...If we are trusting what conky shows for each core's % of use, when running BFS the use of each core is relatively equally distributed...as opposed to the mainline CFS which makes use of only a few cores at a time for the most part resulting in some cores not even being used while others are over 50% usage....I haven't done any real benchmarking, but am happy to if someone has a particular benchmark in mind let me know.  
I can say that everything is much faster on the i7, and I know for sure that to compile a kernel takes somewhere between 15-20 minutes on the mainline CFS preempt kernel, and using the BFS-preempt it takes 8 to 10 minutes

---

### Post by chronniff on 2010-05-22
also, Dan feel free contact me if you need my help testing anyting as well.

I'm at:
[email]daveconniff@gmail.com[/email]

---

### Post by mervinb on 2010-05-22
Heads up - there is a possible problem.

I was using -22ck kernel (AMD64) on my Dell Studio 15 with Radeon RV620 graphics. What I noticed a couple of times, fairly consistently, was that after 2-3 suspend/resume cycles, X performance would slow down. Response to mouseclicks, cycling through windows, window refreshes all became jerky.

I had previously never seen this on my system. I have reverted to the non BFS kernel, and will look out for this slowdown problem.

On my MSI Wind netbook, repeated suspend/resume cycles does not show this problem with -22ck kernel.

---

### Post by NightwishFan on 2010-05-23
I will keep a heads up and test this; though I am on an Asus Laptop here.

No such issues as of yet, but I can confirm the better load balancing.

---

### Post by kaotik2003 on 2010-05-26
Hi there.

It is a pleasure to see this post.

I'm currently installing the kernel ck patched.  

Hope everything works well.

---

### Post by sinsane on 2010-06-21
I have a bug. I cannot to install linux-ck-backports-modules-headers-lucid-preempt, linux-ck-backports-modules-wireless-lucid-preempt, linux-ck-backports-modules-alsa-lucid-preempt.

[I][B]linux-ck-backports-modules-headers-lucid-preempt:
 Depends: linux-ck-headers-lbm-2.6.32-22ck-preempt  but it is not installable

linux-ck-backports-modules-wireless-lucid-preempt:
 Depends: linux-ck-backports-modules-wireless-2.6.32-22ck-preempt  but it is not installable

linux-ck-backports-modules-alsa-lucid-preempt:
 Depends: linux-ck-backports-modules-alsa-2.6.32-22ck-preempt  but it is not installable[/B][/I]

---

### Post by danbh on 2010-06-25
@sinsane
If it is a problem with the packaging, I would certainly fix it.  I don't know.  

I worry that it would involve having to re-package the module backports, which I'm not interested in.  It is just drivers from later kernel releases, so I would assume you get those drivers in the later kernels.

---

### Post by NightwishFan on 2010-06-26
I can confirm this:
```
sudo aptitude install linux-ck-backports-modules-wireless-2.6.32-22ck-generic 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No candidate version found for linux-ck-backports-modules-wireless-2.6.32-22ck-generic
No candidate version found for linux-ck-backports-modules-wireless-2.6.32-22ck-generic
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
```

```
sudo aptitude install linux-ck-backports-modules-wireless-lucid-generic 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  linux-ck-backports-modules-wireless-lucid-generic 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,122B of archives. After unpacking 32.8kB will be used.
The following packages have unmet dependencies:
  linux-ck-backports-modules-wireless-lucid-generic: Depends: linux-ck-backports-modules-wireless-2.6.32-22ck-generic which is a virtual package.
Unable to resolve dependencies!  Giving up...
The following packages are BROKEN:
  linux-ck-backports-modules-wireless-lucid-generic 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,122B of archives. After unpacking 32.8kB will be used.
aptitude failed to find a solution to these dependencies.  You can solve them yourself by hand or type 'n' to quit.
The following packages have unmet dependencies:
  linux-ck-backports-modules-wireless-lucid-generic: Depends: linux-ck-backports-modules-wireless-2.6.32-22ck-generic which is a virtual package.
Resolve these dependencies by hand? [N/+/-/_/:/?]
```

---

### Post by mikko.talvi on 2010-07-10
Rebuild a new kernel -24, plz?

---

### Post by mervinb on 2010-07-19
Dan, thanks for the latest -23ck updates. Any chance of a -pae (32-bit extended addressing) version? Now when using the ck patch, I give 1GB on my laptop ;(

---

### Post by danbh on 2010-07-19
> **mervinb said:**
> Dan, thanks for the latest -23ck updates. Any chance of a -pae (32-bit extended addressing) version? Now when using the ck patch, I give 1GB on my laptop ;(

I don't know much about pae, but there should be linux-ck-generic-pae type stuff that is installable.

---

### Post by mervinb on 2010-07-19
Yes, my system has 4GB ram, so a pae kernel was installed automatically. I was hoping for a pae kernel + CK BFS patches to test out ;) ;).

---

### Post by danbh on 2010-07-19
Have you tried:```
sudo apt-get install linux-ck-headers-generic-pae linux-ck-image-generic-pae
```?

---

### Post by NightwishFan on 2010-07-19
Ah, good you are around danbh. I noticed a few things about the build. You have it set to 1000hz and I will have to say that this is a huge improvement on my system. Everything seems snappy and it logs in faster than the stock kernel easily.

Also I noticed the ability to set it to 10,000hz and etc in the kernel config. What does this entail and it is worth building a special extremely low latency kernel with it or no. My intuition says no, but then again I am no expert.

Thanks for all the hard work, its running like a greased gear for me! I hope to get back some benchmarks if I can.

---

### Post by danbh on 2010-07-19
I don't know much about frequency selection, though I imagine that overall efficiency would go down as the frequency gets higher.

The recommended value is 1000Hz, and it was a mistake on my part that it was set otherwise.  

As an aside, I've been thinking that it might be cool to find a forum that ck himself looks at, that way we can have some more interesting discussions.

---

### Post by stalker1001 on 2010-07-20
It looks that the version of BFS  used in your kernel is outdated . 
From the logs : 
[    0.613552] BFS CPU scheduler v0.311 by Con Kolivas

On the [http://ck.kolivas.org/patches/bfs/ ]("http://ck.kolivas.org/patches/bfs/")you can find 318 version available .

---

### Post by NightwishFan on 2010-07-20
I wonder if it might be better to brand the 1000hz kernel as just linux-ck. The AMD64 Generic kernel for Ubuntu uses 100hz, but the linux-ck-generic uses 1000hz, which is an inconsistency. Just a thought, I have no personal issue with the way it is working.

---

### Post by mervinb on 2010-07-21
> **danbh said:**
> Have you tried:```
sudo apt-get install linux-ck-headers-generic-pae linux-ck-image-generic-pae
```?

Wow... why didn't I think of that!! Thanks.

---

### Post by danbh on 2010-07-26
@stalker I am going to look into moving to a later version.  I may drop the ck patches in favor of just moving to BFS.  The riskiest thing would be to mix the old ck patches with a newer BFS.  Might be possible, but I'm not sure how much I want to experiment.  I just asked ck about that, and he favors a later BFS

@nightwish I was asked to set the Hz on AMD64 to 1000, as that is the recommended value for BFS.  Beyond that, I dunno.

---

### Post by mervinb on 2010-07-29
Dan, thanks again for making the kernels available.

I had reported about system slowdowns after suspend/resume using the ck kernels, and I can confirm them. It occurs on 64-bit ck and 32-bit pae ck kernels.

On 64-bit and 32-bit -pae kernels, after suspend/resume, the system becomes sluggish, eg. page down <space> on firefox lags by what seems like 1/4 to 1/3 sec. On first bootup it pages down *instantly*. This is repeatable on my system. If I boot a non-pae ck kernel on my 32-bit 10.04, suspend/resume does not affect system response.

---

### Post by danbh on 2010-07-30
hey folks, I uploaded a kernel here [0] as an experiment.  It isn;t slated to build for a few days, but feel free to try it out.  It has the updated ck patches, with the 318 BFS dropped in. 

Merv, that sounds like a very tricky bug.  If you keep having it, I will ask ck about it.

[0] [https://launchpad.net/~chogydan/+archive/gnome-session](https://launchpad.net/~chogydan/+archive/gnome-session)

---

### Post by Anonymo on 2010-08-04
Is there a PPA with the Zen-kernel?  I understand this has or can have ck kernel + other improvements.

---

### Post by chronniff on 2010-08-04
merv, you aren't by chance using an ati video card with the latest fglrx driver are you?  I only ask because the last two versions of that driver have been giving me suspend and resume issues similar to what you described...sluggishness etc (especially anything that uses opengl which will slow down until it will eventually freeze up) For me that happens on any current kernel using my radeon 5770.

---

### Post by danbh on 2010-08-08
Hey guys, I just noticed the ck got ported to the 35 kernel, so I did some work today putting it into the ppa.  Looks like it is building ok!  So get it while it is hot.  For now, no meta package, which means that you will have to install it by manual putting in the version numbers.  I will start doing a meta package later on, after some testing.

---

### Post by NightwishFan on 2010-08-08
Thanks! I will test and get back to you.

---

### Post by f.zweig on 2010-08-12
Hi! Would it be possible to build 2.6.35 packages for Lucid, too? Thank you very much! :)

---

### Post by danbh on 2010-08-12
@f.zweig: I've just been running the maverick packages on Lucid as is.  Seems to be working fine.  Let me know if that doesnt work.

---

### Post by NightwishFan on 2010-08-13
Dan,

I tested the .35 kernel on Lucid and I notice no regressions. I have a lot to look forward to on Maverick, as the newer kernel supports changing the sound volume, touchpad configuration, etc. I also installed the 2.12 git Intel GPU drivers to go with it.

Plymouth works, in the next few days I will test using the Nvidia proprietary driver with it. Sound does not skip when the system is under heavy load. I tested using the program 'stress' in the repositories.

Edit: I notice in the config it the .35 generic uses 100hz, is that intentional? (Not that it matters, just curious)

---

### Post by danbh on 2010-08-14
I'll have to look into the 100hz thing, it should be 1000.  I'm afraid you guys know more about kernel configuration than I do.  In previous versions, I would get asked what frequency to configure the kernel, but this time I got no such questions.  I had assumed that the ck patches had improved, and that they were now pre-configuring everything to 1000HZ.

I was given this command to see: grep HZ /boot/config-$(uname -r)
and I seem to be at 1000HZ.  My uname -r= 2.6.35-14ck-generic and I'm on i386.  Can you describe further?

EDIT: nm, I think I found the error, for amd64 again.  I will apply a fix.

---

### Post by Temar09 on 2010-08-19
Just installed your kernel on Lucid. The responsiveness is amazing! This should be included in the standard kernel.

Thanks for your work.

EDIT:
One question: Does your kernel include all the patches of the normal Ubuntu kernel or is it a vanilla kernel + bfs?

---

### Post by danbh on 2010-08-20
it is Ubuntu + ck patchset, which includes bfs, and several other patches by ck

---

### Post by Temar09 on 2010-08-24
> **danbh said:**
> it is Ubuntu + ck patchset, which includes bfs, and several other patches by ck

Just noticed that there are new packages available with a 2.6.35 kernel. Does this kernel contain the [Linux Responsiveness Patches]("http://www.phoronix.com/scan.php?page=news_item&px=ODQ3OQ")?

Unfortunately I can't install the new kernel:

```

root@calcium:~> apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-ck-generic linux-ck-headers-generic linux-ck-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.


root@calcium:~> apt-get install linux-ck-generic linux-ck-headers-generic linux-ck-image-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  linux-ck-headers-generic: Depends: linux-ck-headers-2.6.35-16ck-generic but it is not installable
  linux-ck-image-generic: Depends: linux-ck-image-2.6.35-16ck-generic but it is not installable
E: Broken packages


root@calcium:~> apt-get install linux-ck-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  linux-ck-headers-generic: Depends: linux-ck-headers-2.6.35-16ck-generic but it is not installable
E: Broken packages


root@calcium:~> apt-get install linux-ck-headers-2.6.35-16ck-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-ck-headers-2.6.35-16ck-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-ck-headers-2.6.35-16ck-generic has no installation candidate

```

Is the headers-package not ready yet?

---

### Post by danbh on 2010-08-24
well, first off, I've uploaded the -17 kernel, and fixed a few issues.  I mistakenly left out a couple patches, and I believe that the 100HZ issue should be fixed.

With the meta package, I thought the versions looked wrong.  I don't know why it gave me the -16 when -17 was available.  I suspect that -17 was quote new or something.  I think eventually I'm going to have to start using git, to get more direct access to the source code.

You should still be able to install by putting in the version number directly: linux-ck-headers-2.6.35-17ck-generic linux-ck-image-2.6.35-17ck-generic

I just uploaded a new linux-meta, so it should be fixed.

---

### Post by tinyian on 2010-08-25
i am running x86_64 and having problems still...
```
Package linux-ck-headers-2.6.35-17ck-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package linux-ck-headers-2.6.35-17ck-generic has no installation candidate
```

Did I do something wrong?

---

### Post by Temar09 on 2010-08-25
> **tinyian said:**
> i am running x86_64 and having problems still...
```
Package linux-ck-headers-2.6.35-17ck-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package linux-ck-headers-2.6.35-17ck-generic has no installation candidate
```

Did I do something wrong?

No, it's the same for me. Somehow the package dependencies are messed up. I can't install nor upgrade either.

---

### Post by danbh on 2010-08-25
ah! I'm sorry.  I accidently released the maverick meta to lucid.

---

### Post by tinyian on 2010-08-29
i'm on a 64 bit (eh, well as much as I can be) system... and a little wary of using the maverick meta... Anyone have problems?

---

### Post by NightwishFan on 2010-10-07
Using the latest CK kernel on Maverick, running amazingly!!! I am installing a game, and compressing several files with not a hint of stutter! :)
```
top

top - 07:41:29 up  1:07,  5 users,  load average: 6.40, 6.29, 7.27
Tasks: 183 total,   7 running, 176 sleeping,   0 stopped,   0 zombie
Cpu(s): 64.4%us,  2.9%sy, 32.3%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.4%si,  0.0%st
Mem:   3056080k total,  3033828k used,    22252k free,    41504k buffers
Swap:  4096536k total,      620k used,  4095916k free,  1972712k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
18204 virgil     7   0 2602m  23m  10m R   88  0.8   0:56.64 set446.tmp         
18185 virgil     7   0  5632 2872  676 R   30  0.1   0:21.87 wineserver         
16201 virgil    15  10  105m  94m 1000 R   16  3.2   4:05.58 lzma               
15514 virgil    14  10  105m  94m 1000 R   15  3.2   6:41.92 lzma               
16194 virgil    16  10  105m  94m 1000 R   15  3.2   4:06.68 lzma               
16200 virgil    13  10  105m  94m 1004 R   15  3.2   4:05.52 lzma               
 1119 root       1   0  185m  37m  15m S    5  1.3   4:08.20 Xorg               
 2814 virgil     1   0  701m  57m  25m S    5  1.9   4:37.35 rhythmbox          
18151 root       1 -20     0    0    0 S    3  0.0   0:02.53 loop0              
 2790 virgil     1   0  309m  18m  11m S    3  0.6   0:22.52 gnome-terminal     
   33 root       1   0     0    0    0 S    2  0.0   0:09.15 kswapd0            
 2826 virgil     1   0  609m 109m  27m S    2  3.7   1:15.15 firefox-bin        
   57 root       4   0     0    0    0 S    0  0.0   0:05.86 kondemand/0        
18275 virgil     7   0 19276 1364  960 R    0  0.0   0:00.01 top                
    1 root       1   0 23852 1892 1272 S    0  0.1   0:00.40 init               
    2 root       1   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root       1   0     0    0    0 S    0  0.0   0:00.08 ksoftirqd/0        

```

---

### Post by Mystilleef on 2010-10-09
I'm getting the following errors when I try to install the wireless module. I'm on Lucid.


> sudo apt-get install linux-ck-backports-modules-wireless-lucid-generic
[sudo] password for lateef: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  linux-ck-backports-modules-wireless-lucid-generic: Depends: linux-ck-backports-modules-wireless-2.6.32-24ck-generic but it is not installable
E: Broken packages


---

### Post by NightwishFan on 2010-10-09
I believe all the meta packages like that are broken. Not sure why.

---

### Post by Mystilleef on 2010-10-09
I believe I need that meta package to get my wireless working. Without it I have no wireless.

---

### Post by NightwishFan on 2010-10-09
You would have to ask the maintainer. I am unsure how to get it working for me either. You might just have to stick to the normal kernels, or perhaps compile the drivers from source.

---

### Post by stlouisubntu on 2010-10-11
@danbh

Hey friend, thanks so much for packaging these.  All seems to work well for me running 64-bit lucid on my ASUS/AMD Quad-core 3.0 Ghz machine.  Again, many thanks as you have made the CK/BFS available to those whose capabilities are not yet to the "patch/compile" kernels level.  Thanks for sharing your efforts and talents.

However, one minor adjustment I am hoping you will consider making to your "headers" packages is to modify them so that they provide the "linux-headers" virtual package as this is a dependency of fglrx.  Otherwise when one installs fglrx it will unnecessarily pull in linux-headers-generic (while your ck headers package is already installed) because it thinks it needs to.  This is likely also an issue for the nvidia proprietary drivers, too (but this solution would solve both problems at the same time.)  It still seems to work fine with both headers packages installed but is just a bit sloppy and unnecessary to have them both (when the ck one is actually the only one being used.)

For reference:

[http://packages.ubuntu.com/lucid-updates/linux-headers](http://packages.ubuntu.com/lucid-updates/linux-headers)

[http://packages.ubuntu.com/lucid-updates/fglrx](http://packages.ubuntu.com/lucid-updates/fglrx)


Thanks so much. :)

---

### Post by lalop on 2010-10-14
It works!  Unfortunately, since I installed it (64 bit maverick), the default Fn + F5/F6 shotcuts for screen brightness stopped working, for the nonmodified kernel as well, although sound volume shotcuts still work.  Brightness shortcut still works on dual-booted linux mint.

Anyone know what's up with this?

---

### Post by getaceres on 2010-11-11
The Lucid package is outdated. The last generic one is 2.6.32-24 while the CK one is 2.6.32-24ck. That displaces the CK kernel from the first position in GRUB.

---

### Post by NightwishFan on 2010-11-11
You can edit /etc/default/grub to change the order of boot options (until the maintainer gets back to you). The first entry in grub is defined as "0", second is "1". Remember to run "sudo update-grub" after you edit this file.

Oh, to edit the file just run "gksudo gedit /etc/default/grub"

---

### Post by getaceres on 2010-11-11
I don't have any /etc/default/grub file. Should I create one? If so, what's the complete content?

---

### Post by NightwishFan on 2010-11-11
Are you using grub1? If so the file is in /boot/grub/menu.lst

---

### Post by getaceres on 2010-11-11
Thanks, it's a system upgraded from 8.04 to 10.04 so I suppose that grub was not updated in the process.

---

### Post by danbh on 2010-11-11
hey guys,
Just wanted to say that I can't fix some of these issues being posted, ie, the headers things, and the wireless-compat stuff.  I might be able to fix those things in the future, but I will have to change how I put together the package.

At the moment, I am just updating the maverick package with my current methods.

---

### Post by stlouisubntu on 2010-11-13
@danbh

Hey friend.  Thanks so much for your efforts on this.  I really appreciate you making the time.

However, are you aware of your build failures on linux-ck - 2.6.32-25ck.43~ppa3 for lucid on September 17, 2010?  This is preventing lucid users of your ppa from upgrading to this latest version.  We are still running linux-ck-2.6.32-24ck.39~ppa1

Would you consider rebuilding these (both i386 and amd64) until you achieve successful builds so we can upgrade and be current with the recent security updates?

Thanks again and thanks so much for your work on this.

I really appreciate your keeping lucid updated for this as many of us will keep lucid until probably at least July of 2012.

---

### Post by danbh on 2010-11-13
yeah, I am aware.  That was actually me trying to use a different packaging method, relying upon git.  I didn't know what that error was.  Maybe it was because .43 wasn't ready at the time, but I didn't understand why it was listed in the git tree if it wasn't ready.  I couldn't figure it out.

With that failure, and the patches getting harder to apply, I decided to abandon the lucid kernel for the time being.  At least until I get better with git.

I actually ran the maverick kernel on lucid for the latter half of the lucid cycle.  You may want to give that a try.

---

### Post by c-shadow on 2010-11-16
> **danbh said:**
> 

I actually ran the maverick kernel on lucid for the latter half of the lucid cycle.  You may want to give that a try.

Works like a charm.
Thanks

---

### Post by circuit_breaker on 2010-11-18
hey dan can you automate the builds so we don't have to bug you for newer builds against more recent kernel sources? Or share instructions?

2.6.35-23-generic is the current Maverick kernel and your latest ck patch compiled ver is 2.6.35-22ck-generic.

Not sure what changed between 22 & 23.

---

### Post by cdufour on 2010-11-18
For those who must stick to the Lucid's 2.6.32 kernel: applying CK's 2.6.32.24 patch ([http://ck.kolivas.org/patches/bfs/2.6.32/2.6.32.24-sched-bfs-357.patch](http://ck.kolivas.org/patches/bfs/2.6.32/2.6.32.24-sched-bfs-357.patch)) to Lucid 2.6.32-25 kernel source will result in compilation failure in kernel/fork.c.

CK's 2.6.32.24 patch must be further patched with (see attached patch):
--- 2.6.32.24-sched-bfs-357.patch.orig	2010-10-04 08:00:46.000000000 +0200
+++ 2.6.32.24-sched-bfs-357.patch	2010-11-18 11:15:50.000000000 +0100
@@ -7855,3 +7855,17 @@
  	return (task_nice(task) + 20) / 5;
  }
  
+Index: linux-2.6.32/kernel/fork.c
+===================================================================
+--- linux-2.6.32.orig/kernel/fork.c	2010-11-17 16:15:25.000000000 +0100
++++ linux-2.6.32/kernel/fork.c	2010-11-18 11:07:32.000000000 +0100
+@@ -1243,7 +1243,9 @@
+ 	 * parent's CPU). This avoids alot of nasty races.
+ 	 */
+ 	p->cpus_allowed = current->cpus_allowed;
++#ifndef CONFIG_SCHED_BFS
+ 	p->rt.nr_cpus_allowed = current->rt.nr_cpus_allowed;
++#endif
+ 	if (unlikely(!cpu_isset(task_cpu(p), p->cpus_allowed) ||
+ 			!cpu_online(task_cpu(p))))
+ 		set_task_cpu(p, smp_processor_id());

Compilation will then succeeds ;-)

---

### Post by TSJason on 2010-11-21
Has anyone else noticed a problem with usb keyboards? I find that I have to unplug and re-plug my ms natural keyboard with these kernels. It's like the usb hub doesn't perform a proper reset at boot?

---

### Post by notlofty on 2010-12-05
Sorry, it appears I may be a little slow. I'm trying to use your ppa but I am very new to linux and have no idea what I am doing. So I added your ppa and then tried sudo apt-get install a whole number of things and it always says the file isn't found. I'm assuming I'm just requesting the wrong package name. What exactly do I input?
Edit: Ah, I saw in my Ubuntu Software center that I can view your ppa and so I don't have to do anything in the terminal after adding your ppa. Now my confusion is that you have a great many files in the ppa and most of them look the same. I'm assuming that I need the ones for i386 so I'm going with that. Thank you :-)
My kernel is .26 and yours is only .24 but whatever. I'm sure the -ck patches do a lot more than whatever the other patches do. Thanks again!!!

---

### Post by Plombo on 2010-12-22
Any news on an updated -ck kernel with [BFS version 0.360]("http://ck-hack.blogspot.com/2010/12/bfs-version-0360.html")?

---

### Post by qr25de on 2010-12-23
Just wanted to say thank you for the PPA. WOrking great here on 10.10. Just installed, edited the GRUB file from the information you posted in the first post. Thanks again!

- Scott

---

### Post by qr25de on 2011-01-27
2.6.35-25 Kernel - Official Update Via Update Manager.

Dan, I am assuming you will be patching this one as well? Should I hold off updating and wait for your patch?

Thanks!

---

### Post by danbh on 2011-01-31
Hey folks,
So, the old packaging method that I was using stopped working actually, and I have had to switch over to a new method.  I had planned on making this switch eventually anyway.

Basically this means there will be a name change, so all the directions that have been posted will be incorrect.  

I am running it as I type this, so testers are welcome.  I will post more directions as I get things more sorted out.

---

### Post by NightwishFan on 2011-01-31
Ok, hope you get it sorted out. What is the word on using a newer BFS?

---

### Post by danbh on 2011-01-31
the new package has 363.  All the patches applied very cleanly.

---

### Post by NightwishFan on 2011-01-31
Oh, excellent? Still just using the Maverick kernel for Lucid I assume (sorry for 20 questions) :)

---

### Post by danbh on 2011-01-31
I'm not doing anything for lucid, atm.  Right now, I want to focus on staying more uptodate with ck, and getting a 2.6.37 kernel together.

---

### Post by fackamato on 2011-02-14
> **danbh said:**
> I'm not doing anything for lucid, atm.  Right now, I want to focus on staying more uptodate with ck, and getting a 2.6.37 kernel together.

How is 2.6.37 coming together? Could you please include the patch to fix the b44 kernel panic? Many Dell laptops have this chip for LAN and 2.6.37 is unusable without this patch. See [http://groups.google.com/group/linux.kernel/browse_thread/thread/184c7cd190ae7b5a?pli=1](http://groups.google.com/group/linux.kernel/browse_thread/thread/184c7cd190ae7b5a?pli=1) .

Thanks!

---

### Post by danbh on 2011-02-14
I put together a lucid package, it is named differently, linux-bfs-whatever.  There should be specific directions on my ppa.  Would someone test it for me?  This package only includes the bfs scheduler, and not the rest of the ck patches as those patches were getting hard to apply.  Please report back if it works ok for you.

---

### Post by danbh on 2011-02-14
hi fackamato, I'm not sure how I will put together a natty kernel right away.  I heard that Canonical is using 2.6.38 for natty, but that isn't released.  And ck will likely not release his patches for .38 until it is released.  Also, I'm not a kernel developer, so I don't pick and choose which patches get applied where.

---

### Post by NightwishFan on 2011-02-14
Darn, just installed Mav last night. I will test Lucid kernels in a VM later today.

---

### Post by fackamato on 2011-02-14
> **danbh said:**
> hi fackamato, I'm not sure how I will put together a natty kernel right away.  I heard that Canonical is using 2.6.38 for natty, but that isn't released.  And ck will likely not release his patches for .38 until it is released.  Also, I'm not a kernel developer, so I don't pick and choose which patches get applied where.

Natty? I'm on Maverick :) (but I get what you mean)

Is there a reason why Natty kernels wouldn't be OK for Maverick?

---

### Post by NightwishFan on 2011-02-14
The Lucid packages installed and ran with no problems using Virtualbox.

---

### Post by danbh on 2011-03-20
Quick update: The lucid packages built fine, but launchpad had an error copying the packages over.

On Maverick, there is a build failure with, AFAICT, is a generic error message.  It seems to be the BFS patch.  

:(

---

### Post by fackamato on 2011-03-20
> **danbh said:**
> Quick update: The lucid packages built fine, but launchpad had an error copying the packages over.

On Maverick, there is a build failure with, AFAICT, is a generic error message.  It seems to be the BFS patch.  

:(

Post the build output here?

---

### Post by danbh on 2011-03-20
[http://launchpadlibrarian.net/66840253/buildlog_ubuntu-maverick-i386.linux_2.6.35-28.49~ppa61_FAILEDTOBUILD.txt.gz](http://launchpadlibrarian.net/66840253/buildlog_ubuntu-maverick-i386.linux_2.6.35-28.49~ppa61_FAILEDTOBUILD.txt.gz)

---

### Post by danbh on 2011-03-20
Ah, I see what I was missing.  There is more than one error msg than just the last "make error 2" message.

---

### Post by danbh on 2011-03-25
ok, all errors resolved, enjoy!

---

### Post by danbh on 2011-04-02
Hey folks,
I've put the latest experimental ck patch as -ckexperimental into my ppa.  Is this kind of testing interesting to anyone?  If so, where is the best place to announce such builds?

---

### Post by HankB on 2011-04-22
Hi Dan,
Thanks for putting the effort into making this available.

I have a question about suitability for the ck kernel for my usage.

At present I am crunching the Rosetta DC (distributed computing) project on all four cores of an AMD Phenom CPU. I have recently added a GPU/CUDA project to the system and have found that it gets starved for CPU cycles (or perhaps delayed is a better description) by the compute bound Rosetta application. With Rosetta active on four cores, the GPU application uses 0-1% CPU and keeps the GPU at about 15% utilization. If I restrict Rosetta to three cores, the GPU application uses about 8% CPU and keeps the GPU at 90% or higher. (I suppose that the real reason is that the GPU app buffers insufficient data to accommodate scheduling delays when there are insufficient idle CPU cycless.) These utilization numbers do not change even if I renice the GPU app to -20. (Rosetta is already at nice 39.)

I switched to a Real Time kernel and that allows the GPU app to keep the utilization at 30-45% with 0-1% CPU cycles but the extra overhead for the RT scheduler reduces Rosetta throughput about 15%.

Do you have any idea if the ck kernel will improve this situation? I thought I'd ask before I try. Also if you have any further insight into this or can provide pointers to more information I would appreciate that. I'm not very familiar with scheduling policies and I don't even know if the scheduler in the stock kernel can be tuned. I did some searching on it and did not succeed in finding much information.

I'm running 10.04 64 bit desktop.

best,
hank

---

### Post by danbh on 2011-04-22
> **HankB said:**
> Do you have any idea if the ck kernel will improve this situation? I thought I'd ask before I try. 

I would say give it a try.  The bfs is geared towards desktop / low latency stuff, so maybe it would help.  Maybe the low latency stuff would help with getting the GPU program the cpu it needs.  

CK would know more than I would.  You should ask on his blog, and certainly post the results of any testing you do, there too.

FYI, there is some delay before I update to the latest BFS.  I will update when there is a ABI bump in the mainline kernel

---

### Post by HankB on 2011-04-22
> **danbh said:**
> I would say give it a try.
Thanks for the info. I did. Unfortunately those kernels seemed not to play well with the nVidia drivers. During boot the splash screen remained up perpetually. I could ssh into the box but the X server did not come up. I suppose nVidia does not test with other than stock kernels.

thanks,
hank

---

### Post by c-shadow on 2011-04-22
Check the Xorg logs.
I would rather say that nvidia drivers or xorg does not play well with the kernel :-)
On my lucid install I tried 2.6.32ck-generic-pae with nvidia 256.35 ant it worked fine. After 80+ days uptime with maverick kernel 2.6.35-22ck-generic-pae a couple of days ago switched to natty kernel 2.6.38-8-generic-pae-ck and nvidia 270.29. Old 256.35 does not work with 2.6.38. No problems so far.
Lucid's default xorg is quite buggy with dual, separate screens configuration so had to install this version:
```

X -version

X.Org X Server 1.8.1.902 (1.8.2 RC 2)
Release Date: 2010-06-21
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-xen i686 Ubuntu
Current Operating System: Linux witch 2.6.38-8-generic-pae-ck #41~ppa1-Ubuntu SMP Sun Apr 10 17:37:32 UTC 2011 i686
Kernel command line: root=UUID=2bc0a82e-e5d3-47fc-aa50-04c3b465f7a3 ro quiet splash 
Build Date: 21 June 2010  05:25:01AM
xorg-server 2:1.8.1.902+git20100621+server-1.8-branch.2ae159ba-0ubuntu0sarvatt~lucid (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.19.1
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.

```

---

### Post by HankB on 2011-04-24
> **c-shadow said:**
> Check the Xorg logs.
I would rather say that nvidia drivers or xorg does not play well with the kernel :-)
On my lucid install I tried 2.6.32ck-generic-pae with nvidia 256.35 ant it worked fine. After 80+ days uptime with maverick kernel 2.6.35-22ck-generic-pae a couple of days ago switched to natty kernel 2.6.38-8-generic-pae-ck and nvidia 270.29. Old 256.35 does not work with 2.6.38. No problems so far.
Lucid's default xorg is quite buggy with dual, separate screens configuration so had to install this version:
```

X -version

X.Org X Server 1.8.1.902 (1.8.2 RC 2)
Release Date: 2010-06-21
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-xen i686 Ubuntu
Current Operating System: Linux witch 2.6.38-8-generic-pae-ck #41~ppa1-Ubuntu SMP Sun Apr 10 17:37:32 UTC 2011 i686
Kernel command line: root=UUID=2bc0a82e-e5d3-47fc-aa50-04c3b465f7a3 ro quiet splash 
Build Date: 21 June 2010  05:25:01AM
xorg-server 2:1.8.1.902+git20100621+server-1.8-branch.2ae159ba-0ubuntu0sarvatt~lucid (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.19.1
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.

```

Thanks for the tip. How do I go about installing an older version of X? Is there a HOWTO you can point me to or is it easier than that?

thanks,
hank

---

### Post by c-shadow on 2011-04-24
> **HankB said:**
> Thanks for the tip. How do I go about installing an older version of X? Is there a HOWTO you can point me to or is it easier than that?

thanks,
hank

Which kernel version and nvidia drivers did you install?
Wouldn't recommend installing older version of X, tried once, didn't end well :-)
I installed newer version on my lucid because of problems. For that, just add X updates PPA and update packages. Don't do that unless really necessary. 
As for your problem it could be a couple of things:
1. ubuntu provided nouveau driver (in the kernel) interfering with nvidia proprietary. 
2. Something is wrong with your xorg.conf - check the logs already mentioned: ```
/var/log/Xorg*.log
```
3. nvidia kernel module did not build. In this case,  for nvidia driver to build automatically via DKMS you need kernel headers installed. Did you install it together with CK kernel image from PPA?
After a kernel installation DKMS should compile nvidia module and place it in a path something like this:
```
/lib/modules/<your kernel version>/updates/dkms/nvidia-current.ko
```
A log of that compile should be here:
```
/var/lib/dkms/nvidia-current/<your nvidia version>/<your kernel version>/i686/log
```
Check both paths and see if there is something like nvidia-current.ko. If thee is, the kernel module is built and your problem is somewhere in 1. or 2.
Or there is some point 4. I didn't encounter before :-)

---

### Post by HankB on 2011-04-25
> **c-shadow said:**
> Which kernel version and nvidia drivers did you install?
At present I'm running:
```
hbarta@olive:~$ uname -a
Linux olive 2.6.31-11-rt #154-Ubuntu SMP PREEMPT RT Wed Jun 9 13:40:34 UTC 2010 x86_64 GNU/Linux
```

Nvidia version is 260.19.29. X is 1.8.2.

> Wouldn't recommend installing older version of X, tried once, didn't end well :-)I misunderstood because the one you listed is older than what I'm running.

> ...
3. nvidia kernel module did not build. In this case,  for nvidia driver to build automatically via DKMS you need kernel headers installed. Did you install it together with CK kernel image from PPA?
After a kernel installation DKMS should compile nvidia module and place it in a path something like this:
```
/lib/modules/<your kernel version>/updates/dkms/nvidia-current.ko
```
A log of that compile should be here:
```
/var/lib/dkms/nvidia-current/<your nvidia version>/<your kernel version>/i686/log
```
There is no log for the kernels that do not start X so I suppose that is the issue.

When I installed, I 'apt-got' the generic package thinking it would pull in whatever is necessary through dependencies. So for example I have:
```
hbarta@olive:/var/lib/dkms/nvidia-current/260.19.29$ dpkg -l | grep preempt-bfs
ii  linux-image-2.6.32-30-preempt-bfs     2.6.32-30.59~ppa1                                                     Linux kernel image for version 2.6.32 on x86
ii  linux-image-preempt-bfs               2.6.32.30.36~ppa1                                                     Linux kernel image for Low Latency Servers.

```

I purged those packages and reinstalled with the kernel headers. This time the required module was built and X starts.

Thanks for the help with that.

I'm running it now and it looks like it provides the GPU task (SETI) more CPU cycles than the stock kernel but perhaps not as much as the RT kernel. That is not easy to determine at a glance since the GPU utilization with the SETI GPU task tends to jump around a lot in the first place. I will leave this running for long enough to see what throughput on both SETI GPU and Rosetta CPU looks like.

thanks,
hank

---

### Post by danbh on 2011-04-30
Hey Hank,
You may also want to take a look at some of the scheduling policies available to you:  [http://ck.wikia.com/wiki/SchedulingPolicies](http://ck.wikia.com/wiki/SchedulingPolicies)

I just noticed these!  Obviously, you can try SCHED_IDLEPRIO for the cpu bound processes. And _maybe_ SCHED_ISO for the gpu bound process?  In theory that process needs some realtime-ness since it is just pumping the gpu full of work.  It might have huge downsides to it though...

EDIT, FYI: the downside I was thinking of is that it could interrupt your other graphical apps.  I don't know

---

### Post by NightwishFan on 2011-04-30
sched_iso has the advantage of potentially having a task constantly run on a single cpu for best performance I believe. It also guarantees a time-slice with a hard upper limit to prevent starvation. Really cool stuff.

---

### Post by HankB on 2011-04-30
> **danbh said:**
> Hey Hank,
You may also want to take a look at some of the scheduling policies available to you:  [http://ck.wikia.com/wiki/SchedulingPolicies](http://ck.wikia.com/wiki/SchedulingPolicies)

Thank you! I will have to study and try those out. I suppose it seems particularly propitious since they use 'setiathome' in an example.

I wonder if there are similar tunable capabilities with the standard kernel as well.

thanks,
hank

---

### Post by NightwishFan on 2011-04-30
Use the program schedtool to find out more:
```
sudo apt-get install schedtool
```
```
man schedtool
```

The main gain of sched_iso and sched_idleprio is that you do not need to be root to change to them. Very useful.

Personally (even on BFS) I just use nice.
[https://secure.wikimedia.org/wikipedia/en/wiki/Nice_%28Unix%29](https://secure.wikimedia.org/wikipedia/en/wiki/Nice_%28Unix%29)

---

### Post by TazDevl on 2011-05-24
How do I get the latest build? Somehow after a apt-get update everything is up to date... Oh eh i'm running 10.10 :)

---

### Post by towheedm on 2011-06-30
Just came across this thread.  I only just built 2.6.39.1 and 3.0.0-rc5.  Is there a patch file available that I can use with these two kernels?

I'm on 10.10.

BTW:  Just setting the frequency to 1000Hz on these kernels have allowed me to run flash videos fullscreen without the usual red bars from the stock kernels.

Thanks.

---

### Post by a1212 on 2011-07-24
The AMD proprietary driver for Radeon 4xxx installed by Jockery seems not to be comfortable with Linux lid 2.6.38-10-generic-ck.
But I have decided throwing AMD driver away and keep ck kernel. Otherwise, I would throw Linux instead and go back to Windows.

The below is my complaining report:

I bought Mathematica 8 for Linux weeks ago, and got frustrated soon to the awful user experience when I just started playing around its tutorials and demonstrations(Before that I had tried several other distros and none of them can boot their live-cd successfully on my ancient machine: Acer Aspire M3202 with AMD athlonII 245, 3G ram, and MSI radeon 4670). After not too long time, I considered to send a message to Wolfram.com  ,asking the possibility of replacing the license with a Windows version one, instead of money-back and purchasing another license.
In the meantime, I wandered on internet to search any workaround and found this patchset.
After a whole day of trial and error, including tuning the kernel config, rebuilding the kernel from source, and finally the ppa:chogydan/ppa, I found no way to enter my desktop without the recovery mode unless no AMD Radeon HD 4xxx driver installed.

I wish very much that the scheduler can be integrated into the linux driver model. All one needs to do is just rmmod and insmod 
like normal device drivers. It's not only convenient and useful for both users and developers but also leading to more elegant design IMHO.

---

### Post by dentaku65 on 2011-07-30
Hi danbh,
what can I say?
Thank you!
Incredible speed here with laptop Amilo Centrino 2004! On Lucid.:D

---

### Post by Victor Ivanov on 2011-07-31
Lucid Lynx, ppa - all works well, real responsivness increase,  thank you

---

### Post by T2Small on 2011-08-18
Just installed these kernels for 10.10, and everything was looking great until I tried VirtualBox.  VirtualBox 3.2.x and 4.1.2 are both failing for me.  Any thoughts?

Parallel javac compiles do seem to scale to 8 cores better than CFS did.

---

### Post by danbh on 2011-08-18
any errors?

---

### Post by T2Small on 2011-08-19
> **danbh said:**
> any errors?

Sorry, forgot to mention the error.  I'm at home now and this laptop runs 11.04, but the error is similar to my work machine with 10.10.


[   94.728153] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[  100.706196] BUG: unable to handle kernel NULL pointer dereference at 0000000000000014
[  100.706202] IP: [<ffffffffa0e08092>] VBoxDrvLinuxCreate+0x32/0xd0 [vboxdrv]
[  100.706220] PGD 378df067 PUD 378c9067 PMD 0 
[  100.706224] Oops: 0000 [#1] SMP 
[  100.706227] last sysfs file: /sys/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/block/sda/dev
[  100.706230] CPU 1 
[  100.706231] Modules linked in: pci_stub vboxpci vboxnetadp vboxnetflt vboxdrv binfmt_misc kvm_intel kvm parport_pc ppdev rfcomm sco bnep l2cap snd_hda_codec_si3054 snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi nvidia(P) snd_seq_midi_event arc4 snd_seq tpm_infineon joydev iwlagn snd_timer snd_seq_device snd btusb asus_laptop iwlcore r852 sm_common bluetooth nand nand_ids nand_ecc tpm_tis lp tpm mtd video psmouse sparse_keymap soundcore snd_page_alloc tpm_bios mac80211 parport cfg80211 serio_raw firewire_ohci ahci sdhci_pci sdhci firewire_core crc_itu_t atl1 libahci
[  100.706276] 
[  100.706279] Pid: 2162, comm: VirtualBox Tainted: P            2.6.38-10-generic-ck #46~ppa1-Ubuntu ASUSTeK Computer Inc.         F3Sv                /F3Sv      
[  100.706285] RIP: 0010:[<ffffffffa0e08092>]  [<ffffffffa0e08092>] VBoxDrvLinuxCreate+0x32/0xd0 [vboxdrv]
[  100.706293] RSP: 0018:ffff88012a641be8  EFLAGS: 00010286
[  100.706295] RAX: 0000000000000000 RBX: ffff8801141140b0 RCX: ffffffffa0e35f60
[  100.706298] RDX: ffffffffa0e33338 RSI: ffff880037a2ca80 RDI: ffff880136bc5d40
[  100.706300] RBP: ffff88012a641c18 R08: 0000000000000000 R09: 0000000000000000
[  100.706302] R10: ffff88013f8123a0 R11: 0000000000000002 R12: 00000000ffffffff
[  100.706304] R13: ffff880037a2ca80 R14: ffffffffa0e33320 R15: 0000000000000000
[  100.706307] FS:  00007f0847098720(0000) GS:ffff8800bfd00000(0000) knlGS:0000000000000000
[  100.706310] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[  100.706312] CR2: 0000000000000014 CR3: 00000000378d6000 CR4: 00000000000006e0
[  100.706314] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  100.706316] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  100.706319] Process VirtualBox (pid: 2162, threadinfo ffff88012a640000, task ffff8801141140b0)
[  100.706321] Stack:
[  100.706322]  0000000000a00038 0000000000a00038 ffff88012a641c18 ffffffff8164d8e0
[  100.706327]  ffff880037a2ca80 ffff880136bc5d40 ffff88012a641c68 ffffffff8139bfe2
[  100.706331]  ffff88013702c600 0000000000000000 ffff880037a2ca90 0000000000000000
[  100.706335] Call Trace:
[  100.706341]  [<ffffffff8139bfe2>] misc_open+0x152/0x2b0
[  100.706345]  [<ffffffff8115b9da>] chrdev_open+0xda/0x1f0
[  100.706348]  [<ffffffff8115b900>] ? chrdev_open+0x0/0x1f0
[  100.706352]  [<ffffffff8115577e>] __dentry_open+0xce/0x2f0
[  100.706356]  [<ffffffff811619b3>] ? generic_permission+0x23/0xc0
[  100.706360]  [<ffffffff81156c71>] nameidata_to_filp+0x71/0x80
[  100.706363]  [<ffffffff81165e68>] finish_open+0xc8/0x1b0
[  100.706366]  [<ffffffff81165057>] ? do_path_lookup+0x87/0x160
[  100.706370]  [<ffffffff81166628>] do_filp_open+0x2c8/0x7c0
[  100.706374]  [<ffffffff8112c2a8>] ? anon_vma_chain_free+0x18/0x20
[  100.706377]  [<ffffffff8112e1d5>] ? unlink_anon_vmas+0x95/0x120
[  100.706380]  [<ffffffff81120836>] ? free_pgtables+0xd6/0x120
[  100.706384]  [<ffffffff81127543>] ? unmap_region+0x113/0x170
[  100.706387]  [<ffffffff812d93a7>] ? __strncpy_from_user+0x27/0x60
[  100.706391]  [<ffffffff81173947>] ? alloc_fd+0xf7/0x150
[  100.706394]  [<ffffffff81156cea>] do_sys_open+0x6a/0x150
[  100.706397]  [<ffffffff81156df0>] sys_open+0x20/0x30
[  100.706401]  [<ffffffff8100c002>] system_call_fastpath+0x16/0x1b
[  100.706403] Code: 30 48 89 5d e8 4c 89 65 f0 4c 89 6d f8 0f 1f 44 00 00 65 48 8b 1c 25 80 cc 00 00 48 8b 83 10 04 00 00 49 89 f5 41 bc ff ff ff ff <8b> 40 14 85 c0 74 17 44 89 e0 48 8b 5d e8 4c 8b 65 f0 4c 8b 6d 
[  100.706437] RIP  [<ffffffffa0e08092>] VBoxDrvLinuxCreate+0x32/0xd0 [vboxdrv]
[  100.706444]  RSP <ffff88012a641be8>
[  100.706446] CR2: 0000000000000014
[  100.706449] ---[ end trace 44ad988f09feae50 ]---

I do see references to bug fixes related to VirtualBox in the Linux-ck Package Changelog, but I don't know if they are related to this issue.

If I can get it to work in 11.04, I don't mind upgrading as it would be nice to have BFS/ck patches and VirtualBox.  Thanks for any help!

---

### Post by danbh on 2011-08-19
Those bug fixes are part of the regular Ubuntu kernel package.  My only guess is maybe you are trying to mix together 32bits with 64bits somewhere.  The guests and host must line up on that.  

You can also install the 11.04 kernel on 10.10 by changing your sources a little bit.  I have done that just as part of my testing.

---

### Post by idfred on 2011-08-19
Just installed packages from your ppa, system Ubuntu Natty x86, kernel 2.6.38-10-generic-pae-ck #46~ppa1-Ubuntu.
Application launching became faster, first experience seems to be really nice. Thank you!
But I confirm problems with virtualbox (version 4.1.2-73507~Ubuntu~natty).

---

### Post by T2Small on 2011-08-19
> **danbh said:**
> Those bug fixes are part of the regular Ubuntu kernel package.  My only guess is maybe you are trying to mix together 32bits with 64bits somewhere.  The guests and host must line up on that.  

You can also install the 11.04 kernel on 10.10 by changing your sources a little bit.  I have done that just as part of my testing.

In both cases the host VirtualBox is 64bit, as is my kernel.  The guest is 32bit Windows XP and it had been working well with the regular Ubuntu kernel.

I guess for now I'll just reboot to the regular Ubuntu kernel when I need VirtualBox.  It's a pain, but I'll live with it until I find a solution.

---

### Post by c-shadow on 2011-08-19
Maybe just a coincidence, but untila a couple of days ago I was running 32-bit lucid with 2.6.35 maverick PAE CK kernel. Worked great, no problems with virtualbox (up to version 4.10). 2.6.38 was giving me problems, a couple of guest machines were locking up quite often. All other programs seem to run fine on that 2.6.38. I'm stil in the proces of upgrading to 64-bit natty, will test vbox as soon as i install CK kernel.

---

### Post by danbh on 2011-08-20
I can confirm the vbox issues on 32 bit host attempting to boot a 32bit guest

---

### Post by c-shadow on 2011-08-21
No luck with 2.6.38 kernel and virtualbox 4.1.2
After a nasty lockup (host: natty 2.6.38-10-generic-ck, windows 7 x86 guest) today I installed Con's 2.6.39-ck1-3 kernel from here: [http://ck.kolivas.org/patches/Ubuntu%20Packages/](http://ck.kolivas.org/patches/Ubuntu%20Packages/)
No crashes since, all machines started up and rebooted fine :)
Tried the following guests: lucid x86 and x64, Windows XP and Windows 7 x86. Don't have any windows x64.
It would be interesting to see how Con's prebuilt 2.6.38 works with virtualbox, at the moment dont't have the time for testing.

---

### Post by danbh on 2011-08-24
I've tracked down the issue.  It was on my end.  A patch was not applying cleanly, and I failed to notice that.  I've since fixed the issue, which will be a part of the -11 upload.

---

### Post by idfred on 2011-08-29
Just updated to version 2.6.38.11.26~ppa1 of linux-image-generic-pae-ck package (from -10 version of same package). Issue with virtualbox is still here.
Also during update grub-probe hanged (no return, no cpu consumption, no disk activity for several minutes). When I switched to non-ck kernel on same system grub-probe went fine.

As I mentioned above, my system is Ubuntu Natty x86. Below you can find dmesg output related to vritualbox problem.
```

[   32.577855] vboxdrv: Found 2 processor cores.
[   32.577931] vboxdrv: fAsync=0 offMin=0x1d9 offMax=0xb2c
[   32.577976] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   32.577977] vboxdrv: Successfully loaded version 4.1.2 (interface 0x00190000).
[   32.845079] vboxpci: IOMMU not found (not registered)
[   34.301171] ip_tables: (C) 2000-2006 Netfilter Core Team
[   34.324116] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   40.496005] CE: hpet2 increased min_delta_ns to 7500 nsec
[   40.496014] CE: hpet2 increased min_delta_ns to 11250 nsec
[  208.811810] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[  214.677594] BUG: unable to handle kernel NULL pointer dereference at 00000028
[  214.677601] IP: [<f9172076>] VBoxDrvLinuxCreate+0x26/0xc0 [vboxdrv]
[  214.677618] *pdpt = 000000002d071001 *pde = 0000000000000000 
[  214.677623] Oops: 0000 [#1] SMP 
[  214.677627] last sysfs file: /sys/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/block/sda/sda1/stat
[  214.677632] Modules linked in: ipt_MASQUERADE iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack nf_defrag_ipv4 ip_tables x_tables binfmt_misc pci_stub vboxpci vboxnetadp vboxnetflt vboxdrv parport_pc ppdev vesafb snd_hda_codec_realtek nvidia(P) snd_hda_intel nfsd snd_hda_codec snd_hwdep exportfs snd_pcm nfs snd_seq_midi snd_rawmidi snd_seq_midi_event lockd snd_seq snd_timer snd_seq_device snd psmouse serio_raw coretemp fscache soundcore snd_page_alloc nfs_acl hp_wmi sparse_keymap lp tpm_infineon parport auth_rpcgss tpm_tis tpm tpm_bios sunrpc usbhid hid ahci libahci e1000e dm_raid45 xor
[  214.677695] 
[  214.677699] Pid: 5060, comm: VirtualBox Tainted: P            2.6.38-11-generic-pae-ck #48~ppa1-Ubuntu Hewlett-Packard HP Compaq 8000 Elite CMT PC/3647h
[  214.677708] EIP: 0060:[<f9172076>] EFLAGS: 00210292 CPU: 0
[  214.677720] EIP is at VBoxDrvLinuxCreate+0x26/0xc0 [vboxdrv]
[  214.677723] EAX: 00000014 EBX: ed09dc80 ECX: f9199260 EDX: ed0e66c0
[  214.677726] ESI: ffffffff EDI: 00000000 EBP: ed083de0 ESP: ed083dc4
[  214.677729]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[  214.677733] Process VirtualBox (pid: 5060, ti=ed082000 task=ed09dc80 task.ti=ed082000)
[  214.677736] Stack:
[  214.677738]  f74eb7a0 ed083de0 c1127ba6 ed083de0 f91991c0 c1563580 00000000 ed083e14
[  214.677746]  c132fbd9 ed083e14 c134204c c1127b70 ed083e2c 0000000a f919b660 f2f95950
[  214.677755]  ed0e66c0 00000000 c192d940 00000000 ed083e3c c1128395 ed0e66c0 f2f95950
[  214.677763] Call Trace:
[  214.677771]  [<c1127ba6>] ? cdev_get+0x26/0x90
[  214.677778]  [<c132fbd9>] misc_open+0x119/0x240
[  214.677782]  [<c134204c>] ? kobj_lookup+0xfc/0x180
[  214.677787]  [<c1127b70>] ? exact_match+0x0/0x10
[  214.677792]  [<c1128395>] chrdev_open+0xa5/0x1c0
[  214.677796]  [<c1122b91>] __dentry_open+0xc1/0x280
[  214.677801]  [<c1123efe>] nameidata_to_filp+0x6e/0x80
[  214.677805]  [<c11282f0>] ? chrdev_open+0x0/0x1c0
[  214.677810]  [<c113139f>] finish_open+0xaf/0x1a0
[  214.677814]  [<c1130c48>] ? do_path_lookup+0x68/0x120
[  214.677818]  [<c11319e7>] do_filp_open+0x207/0x6e0
[  214.677824]  [<c1123f66>] do_sys_open+0x56/0x120
[  214.677828]  [<c112405e>] sys_open+0x2e/0x40
[  214.677833]  [<c100ab5f>] sysenter_do_call+0x12/0x28
[  214.677835] Code: c4 08 5b 5d c3 55 89 e5 83 ec 1c 89 5d f4 89 75 f8 89 7d fc 3e 8d 74 26 00 be ff ff ff ff 64 8b 1d 2c 02 86 c1 8b 83 bc 02 00 00 <8b> 40 14 89 d7 85 c0 74 11 89 f0 8b 5d f4 8b 75 f8 8b 7d fc 89 
[  214.677886] EIP: [<f9172076>] VBoxDrvLinuxCreate+0x26/0xc0 [vboxdrv] SS:ESP 0068:ed083dc4
[  214.677901] CR2: 0000000000000028
[  214.677905] ---[ end trace f8cc2d13ec394f8d ]---

```

---

### Post by danbh on 2011-08-29
yeah, I see it too.  Sorry for saying it was fixed.  I think when I had built the kernel myself, it worked ok.  Unfortunately, I don't have the knowledge nor the time to look into this right now.

---

### Post by idfred on 2011-08-30
Another problem with this kernel package is openvpn. It hangs during connection procedure (tap mode) and could not be killed even with kill -9.

---

### Post by danbh on 2011-09-01
Well, I can somewhat confirm that the issue is with the kernel on launchpad.  I locally built the kernel using the same source code that I uploaded to launchpad, and the kernel is working fine with virtualbox.

---

### Post by dap.DarkneSS on 2011-09-07
Hello. Could you start patching of kernel to ubuntu 11.10?

---

### Post by dap.DarkneSS on 2011-09-10
Why i don't see bfq?
```
%cat /sys/block/sda/queue/scheduler
noop deadline [cfq]
```
I have -ck kernel:
```
%uname -r
2.6.38-11-generic-ck
```

---

### Post by NightwishFan on 2011-09-10
You are thinking of the Zen kernel. BFQ is a completely seperate patch and not maintained by Con Kolivas.

---

### Post by dap.DarkneSS on 2011-09-11
Thank you. I didn't know it.

---

### Post by NightwishFan on 2011-09-11
> **dap.DarkneSS said:**
> Thank you. I didn't know it.

No problems. BFQ is nice as well though.

---

### Post by danbh on 2011-09-30
Hey folks,
I'm leaning towards a mailing list.  I use gmail, and I really like conversation view.  Forums are poor for multiple conversations.  Whatever, the mailing list is here: [https://launchpad.net/~ck-patchset](https://launchpad.net/~ck-patchset)

Im also running out a fresh 3.0 kernel.  Im thinking of doing both a full ck and a simple BFS versions, to see if that changes the issue with virtualbox.

---

### Post by Faffin on 2012-01-05
I managed to patch CK 3.0.0 to the Ubuntu 10.10 source. You have to edit a file. Details at: [Creating Debian packages for Linux kernels >= 3.0.0 in Ubuntu]("http://mjanja.co.ke/#2011/10/creating-debian-packages-for-linux-kernels-3-0-0-in-ubuntu/"). Apart from that, everything is working fine from just following the Howto.

```
warren@midnight:~$ uname -r
3.0.9-ck1-ck1
warren@midnight:~$ 
```

I don't know why the source was 3.0.9, when 10.10 is at 3.0.14 though.

Followed [Howto: An easy way to enable CK patches]("http://ubuntuforums.org/showthread.php?t=1637004&page=4&highlight=con+kolivas").

I will probably join your launchpad group sometime.

---

### Post by danbh on 2012-01-05
Hey Faffin,
That's cool what you did.  Did you mean 11.10?  I tried running a 3.x kernel on 11.04, and it didn't really work out.

It has been awhile since I have updated the kernels.  I've gotten busy, plus I don't really want to upgrade to 11.10 (I don't like unity).  I just so happen to have gotten round to it again.  Lucid kernels will come in a bit, a few days later I'll do natty, and then a few days after that, I do one for oneiric.  

Anyway, welcome!

Also, for those interested, I got pretty stuck on that virtualbox bug.  I'm just gonna leave it for the time being.   :(

---

### Post by Faffin on 2012-01-06
Sorry I meant 11.10. At the moment I am running the 3.0.12 from your PPA on it. There is even a howto post about installing with it at [Linux versus Windows - bigadv folding results]("http://hardforum.com/showpost.php?p=1036935472&postcount=259"). Wish I had known about it sooner, would have saved about 4 hours it took making the .debs

Did you have problems with the headers in the 3.0.x kernels? What do you think of Alan's edit to that file (see link "Creating Debian packages for Linux kernels >= 3.0.0 in Ubuntu")? 

From reading Con's blog, and hanging in #ck, the 3.1.x will be interesting to try, but the 3.2.x just messes about with control groups, which bfs does not use anyway.

---

### Post by danbh on 2012-01-09
I am having issues with 3.0, and I am trying to sort it out.  The link you gave is dead, so I don't know what was there.  Looking at the ck-hacking website, it looks like folks are just using the simplest substitution.  I'm just going to go with them.  *shrugs*

---

### Post by c-shadow on 2012-01-09
Took me a while to find the correct link on the page:
[http://mjanja.co.ke/2011/10/creating-debian-packages-for-linux-kernels-3-0-0-in-ubuntu/](http://mjanja.co.ke/2011/10/creating-debian-packages-for-linux-kernels-3-0-0-in-ubuntu/)

Dan, any news on oneiric 3.0x packages?
I'd really like to try CK patched kernel on a HTPC built from oneiric minimal :)

---

### Post by danbh on 2012-01-09
tomorrow

---

### Post by idfred on 2012-01-12
> **danbh said:**
> Also, for those interested, I got pretty stuck on that virtualbox bug.  I'm just gonna leave it for the time being.   :(
Yesterday I updated to 2.6.38-13-generic-pae-ck #530~ppa1-Ubuntu on my x86 11.04 system. Virtualbox 4.1.8 works fine!

---

### Post by danbh on 2012-01-12
cool, hopefully that means it is fixed for all versions.  Thanks for the testing!

---

### Post by c-shadow on 2012-01-26
Anyone else having problem with ATI proprietary driver and 3.0.0-14-generic-ck (x86_64)? 
After kernel installation DKMS builds the fglrx module, but X doesn't start. There is some stacktrace in syslog right after fglrx module. That's on my AMD fusion based htpc with Radeon HD 6310 Graphics. Same version stock ubuntu kernel works fine.

---

### Post by ShareBuntu on 2012-03-27
Any idea if this is still going? Is the PPA still going too ([https://launchpad.net/~chogydan/+archive/ppa)?](https://launchpad.net/~chogydan/+archive/ppa)?)

---

### Post by Darxus on 2012-03-27
> **ShareBuntu said:**
> Any idea if this is still going? Is the PPA still going too ([https://launchpad.net/~chogydan/+archive/ppa)?](https://launchpad.net/~chogydan/+archive/ppa)?)

Yes, CK is still going:
[http://users.on.net/~ckolivas/kernel/](http://users.on.net/~ckolivas/kernel/)

The kernel 3.3.0 patches for BFS were updated 3 days ago:
[http://ck.kolivas.org/patches/bfs/3.3.0/](http://ck.kolivas.org/patches/bfs/3.3.0/)

Last update from that PPA is 2011-07-08, probably safe to assume it's dead.  It's frustrating to maintain this stuff when Ubuntu won't include it in the archives.

---

### Post by danbh on 2012-03-27
I'm still here.  I haven't pushed anything out since the last round of updates.

---

### Post by ShareBuntu on 2012-03-28
I know this is probably a lot to ask, but is there any chance of getting a little tutorial written to go from a vanilla Ubuntu 11.10 to completely patched kernel based on Kolivas's work?

---

### Post by idfred on 2012-03-29
> **ShareBuntu said:**
> I know this is probably a lot to ask, but is there any chance of getting a little tutorial written to go from a vanilla Ubuntu 11.10 to completely patched kernel based on Kolivas's work?Cool idea! I think such a guide would be appreciated.

---

### Post by danbh on 2012-03-29
I don't actually know off the top of my head.  But any "compile your own ubuntu kernel" guide would do.  Just apply the patches right after you get the source code.

---

### Post by ShareBuntu on 2012-03-29
> **danbh said:**
> I don't actually know off the top of my head.  But any "compile your own ubuntu kernel" guide would do.  Just apply the patches right after you get the source code.
Okay, so let's say we're going to patch the 3.3 kernel. Which of these patches should we apply? All of them? [http://ck.kolivas.org/patches/3.0/3.3/3.3-ck1/patches/](http://ck.kolivas.org/patches/3.0/3.3/3.3-ck1/patches/)

---

### Post by fackamato on 2012-03-30
> **ShareBuntu said:**
> Okay, so let's say we're going to patch the 3.3 kernel. Which of these patches should we apply? All of them? [http://ck.kolivas.org/patches/3.0/3.3/3.3-ck1/patches/](http://ck.kolivas.org/patches/3.0/3.3/3.3-ck1/patches/)

This one: [http://ck.kolivas.org/patches/3.0/3.3/3.3-ck1/patch-3.3-ck1.bz2](http://ck.kolivas.org/patches/3.0/3.3/3.3-ck1/patch-3.3-ck1.bz2)

However, you'll be running a vanilla kernel. I don't think there's 3.3x kernels for Ubuntu 11.10? Looks like Ubuntu 12.04 will get 3.2.whatever: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2.13-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2.13-precise/)

---

### Post by danbh on 2012-04-15
Hey folks.  I'm guessing that the need to compile one's own ck patched kernel was taken care of by me updating my ppa.  If that was the root issue, please just ask me for an update.  It is a pain trying to track kernel releases for Ubuntu releases that I am not running (I'm running natty btw).  So I will only check when I notice a kernel update for whatever release I'm running.

Also, from now on, can we move this discussion to this mailing list?: [https://launchpad.net/~ck-patchset](https://launchpad.net/~ck-patchset)

I feel this "thread" has grown unusefully long.  Thanks!

---

