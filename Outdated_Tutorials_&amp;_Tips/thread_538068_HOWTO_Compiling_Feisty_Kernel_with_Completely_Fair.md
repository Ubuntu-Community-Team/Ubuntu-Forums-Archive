---
title: "HOWTO: Compiling Feisty Kernel with Completely Fair Scheduler (CFS)"
date: 2007-08-29
forum: Outdated Tutorials &amp; Tips
---

### Post by volsungs on 2007-08-29
Hi all,

There has been quite a bit of hype about potential 3D and desktop performance with the new Completely Fair Scheduler (CFS), which will be incorporated in kernel version 2.6.23. Word has it that CFS will not be added to Ubuntu Gutsy and some users have expressed disappointment about this decision ([http://ubuntuforums.org/showthread.php?t=533648&highlight=cfs](http://ubuntuforums.org/showthread.php?t=533648&highlight=cfs)). I wanted try out this scheduler on my Ubuntu Feisty box, but I didn't find much information on how to go about it. One recent post ([http://distrogue.blogspot.com/2007/08/life-on-bleeding-edge-linux-kernel-2623.html](http://distrogue.blogspot.com/2007/08/life-on-bleeding-edge-linux-kernel-2623.html)) describes how to upgrade to the 2.6.23-rc2 kernel for Ubuntu, but I had serious problems compiling the Nvidia video driver with that kernel and I just want the new scheduler, not all the other changes with 2.6.23 (it's still an unstable kernel, after all).

Fortunately, Ingo Molnar (CFS's developer) has released a patch file for the 2.6.20 tree. This is a brief HOWTO for compiling the CFS into the current stable Feisty kernel: 2.6.20-16.29. This guide assumes that you have installed and are running the aforementioned kernel (since I copy the config file from it below). If not, you'll need to apt-get install two packages: linux-image-2.6.20-16-generic linux-headers-2.6.20-16-generic. NOTE: I have compiled many kernels over the years (particularly on Gentoo), but it's possible that the instructions below may have inaccuracies and I welcome corrective feedback.

If you don't want to compile the kernel yourself (which is what is described below), you can download the .deb files that I built. These were compiled against the 2.6.20-16.29 source for Ubuntu Feisty, and the kernel configuration was the same as the current generic kernel (with kernel debugging turned off), so they should be as usable as the existing stock Feisty kernel.

DISCLAIMER: I accept no liability for the files provided below. They work great on my machine, but I haven't tested them on other computers.

[http://www.michaelhallquist.com/ubuntu-cfs/linux-image-2.6.20.16-ubuntu-cfs-v20.4_Custom_i386.deb](http://www.michaelhallquist.com/ubuntu-cfs/linux-image-2.6.20.16-ubuntu-cfs-v20.4_Custom_i386.deb)
[http://www.michaelhallquist.com/ubuntu-cfs/linux-headers-2.6.20.16-ubuntu-cfs-v20.4_Custom_i386.deb](http://www.michaelhallquist.com/ubuntu-cfs/linux-headers-2.6.20.16-ubuntu-cfs-v20.4_Custom_i386.deb)

To install these .debs, see step 10 below (basically you need to run: sudo dpkg -i <package>).

Thanks to tseliot for putting together a newbie's kernel compilation guide on Ubuntu ([http://ubuntuforums.org/showthread.php?t=56835](http://ubuntuforums.org/showthread.php?t=56835)). This guide is based largely on his documentation. Please read his guide before you jump into adding CFS to your kernel.

1) Prepare your box for kernel compilation. Follow the aforementioned guide up to the part where you have installed the necessary tools and have unpacked the kernel source. I skipped the xorg.conf modification from tseliot's guide above because I compiled the Nvidia module myself (see step 11 below). Tseliot's guide is a bit out of date, so you won't need gcc-3.4, and the latest source package is called linux-source-2.6.20. If you've done things correctly, you should now have the kernel source available at /usr/src/linux-source-2.6.20.

2) Obtain the patch from Ingo's site: [http://people.redhat.com/mingo/cfs-scheduler/older/sched-cfs-v2.6.20.16-v20.4.patch](http://people.redhat.com/mingo/cfs-scheduler/older/sched-cfs-v2.6.20.16-v20.4.patch)

(NOTE: there's a slightly newer v20.5 patch, but I haven't tested it and v20.4 is only a few days old)

3) Move the patch into the kernel source directory and run the patch against the source like so:

# sudo mv sched-cfs-v2.6.20.16-v20.4.patch /usr/src/linux-source-2.6.20
# cd /usr/src/linux-source-2.6.20
# sudo patch -p1 < sched-cfs-v2.6.20.16-v20.4.patch

4) You'll encounter two errors in the patch. The first is in the /usr/src/linux-source-2.6.20/Makefile and the second is  /usr/src/linux-source-2.6.20/kernel/sched.c. These occur because the patch was written for 2.6.20.16 vanilla sources, whereas I think the Ubuntu is a heavily patched 2.6.20.3. You can resolve these simple conflicts yourself (look at Makefile.rej and sched.c.rej) or just download the versions I fixed:

[http://www.michaelhallquist.com/ubuntu-cfs/sched.c](http://www.michaelhallquist.com/ubuntu-cfs/sched.c)
[http://www.michaelhallquist.com/ubuntu-cfs/Makefile](http://www.michaelhallquist.com/ubuntu-cfs/Makefile)

Replace the old versions with those.

5) Additionally, the 2.6.20 vanilla sources didn't include a definition for arch_enter_lazy_cpu, but the Ubuntu source does (in include/asm-i386/paravirt.h). Ingo's patch adds a null definition for arch_enter_lazy_cpu (assuming vanilla sources), which results in a duplicate definition. If you compile without fixing the duplication, I think it will work (you'll get lots of warnings), but I would instead just comment out line 118 of the post-patch file /usr/src/linux-source-2.6.20/include/linux/sched.h. This line is:

#define arch_enter_lazy_cpu_mode() do { } while (0)

Again, the corrected file can be pulled from:

[http://www.michaelhallquist.com/ubuntu-cfs/sched.h](http://www.michaelhallquist.com/ubuntu-cfs/sched.h)

6) Okay, now the source is in good shape to compile. Make sure the source is cleaned of object files and any old config files:

# cd /usr/src/linux-source-2.6.20
# sudo make-kpkg clean
# sudo rm .config .config.old

7) I didn't want to compile from scratch and wanted to stay close to the stock kernel, so I imported the 2.6.20-16-generic config like so:

# sudo cp /boot/config-2.6.20-16-generic /usr/src/linux-source-2.6.20/.config

8) By default, Ubuntu has kernel debugging turned on in the config, which makes the kernel and modules much bigger than they need to be (see also [https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)). So turn that off. Run sudo make menuconfig, go under "Kernel Hacking" and turn off "Kernel debugging." You can also alter your config while you're in there to turn off SMP, compile just for your architecture, and so on... but that's beyond the scope of this discussion. Or, you can get the config file I used from:

[http://www.michaelhallquist.com/ubuntu-cfs/config-2.6.20-ubuntu-cfs-v20.4](http://www.michaelhallquist.com/ubuntu-cfs/config-2.6.20-ubuntu-cfs-v20.4)

9) Okay, now we're ready to compile. Create the .debs for the image and headers following tseliot's guide:

# sudo make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers

(you can omit the --append-to-version portion if you like or change it to whatever suits you)

10) Once it compiles (it may take a while), there should be two debs in the /usr/src directory. Mine were called:

linux-image-2.6.20.16-ubuntu-cfs-v20.4_2.6.20.16-ubuntu-cfs-v20.4-10.00.Custom_i386.deb
linux-headers-2.6.20.16-ubuntu-cfs-v20.4_2.6.20.16-ubuntu-cfs-v20.4-10.00.Custom_i386.deb

Whatever yours are called, install the debs with: 

# sudo dpkg -i linux-image-<name here>.deb
# sudo dpkg -i linux-headers-<name here>.deb

11) (FOR NVIDIA CARD BINARY DRIVER USERS ONLY) Now, with luck, the new kernel and headers are installed. But wait! I run an Nvidia graphics card and I need a module compiled against the new kernel (If you reboot before you make the module, X windows will not start, which may be uncomfortable for those not used to a command line interface). I have no clue about ATI, so you're on your own if you have an ATI card. You'll need the nvidia-kernel-source package installed. This will give you the /usr/src/nvidia-kernel-source.tar.gz archive. Extract that and compile a module against the new kernel like so:

# cd /usr/src
# sudo tar xf nvidia-kernel-source.tar.gz
# cd modules/nvidia-kernel/nv
# SYSSRC=/usr/src/linux-headers-2.6.20.16-ubuntu-cfs-v20.4/ make module install

Note that the SYSSRC argument above must be set to wherever your kernel source headers were installed from step 10. Now, the new module should be installed in the proper /lib/modules directory. If you do get stranded at a CLI without the driver, login, then type:

# sudo apt-get remove nvidia-glx
# sudo apt-get install nvidia-glx
# sudo /etc/init.d/gdm restart

This should get the driver up and running for you.

12) Reboot the computer and choose the new CFS-based kernel (should have cfs-v20.4 at the end)! The new kernel worked great for me and I've had no problems. I haven't observed drastic responsiveness improvements over the old scheduler, but I haven't really put the kernel through its paces, either. You can verify that CFS is running by looking in the /proc/sys/kernel directory. If you have CFS running, you'll see something like this:

# ls /proc/sys/kernel

sched_batch_wakeup_granularity_ns  sched_features    sched_min_granularity_ns  sched_stat_granularity_ns
sched_child_runs_first             sched_latency_ns  sched_runtime_limit_ns    sched_wakeup_granularity_ns

All those sched parameters are for CFS. I don't know what tweaking them would do, so I'd leave it at the default for now.

I hope this guide proves useful to others interested in trying out the new Completely Fair Scheduler!

- Michael

---

### Post by volsungs on 2007-09-05
Several people have expressed interest in compiling CFS into the 2.6.22 branch, which is currently being tested for Ubuntu Gutsy Gibbon. The following information updates the above HOWTO by patching a 2.6.22 kernel with CFS.

For those who prefer to use precompiled packages, rather than compiling their own, I have provided .deb files for the 2.6.22-cfs kernel here. These were compiled against the 2.6.22.4 source for Ubuntu Gutsy, and the kernel configuration was the same as the Gutsy generic kernel (with kernel debugging turned off), so they should be as usable as the existing stock Gutsy kernel.

DISCLAIMER: I accept no liability for the files provided below. They work great on my machine, but I haven't tested them on other computers.

[http://www.michaelhallquist.com/ubuntu-cfs/2.6.22/linux-headers-2.6.22.4-cfs-v20.5.deb](http://www.michaelhallquist.com/ubuntu-cfs/2.6.22/linux-headers-2.6.22.4-cfs-v20.5.deb)
[http://www.michaelhallquist.com/ubuntu-cfs/2.6.22/linux-image-2.6.22.4-cfs-v20.5.deb](http://www.michaelhallquist.com/ubuntu-cfs/2.6.22/linux-image-2.6.22.4-cfs-v20.5.deb)


1) Obtain the latest 2.6.22 kernel source

# sudo gedit /etc/apt/sources.list

Insert the following line at the bottom and save the file:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted

Then run:

# sudo apt-get update
# sudo apt-get install linux-source-2.6.22
# cd /usr/src
# tar xf linux-source-2.6.22.tar.bz2

2) Remove the Gutsy packages from your deb sources (i.e., get rid of the line you inserted above)

# sudo gedit /etc/apt/sources.list
# sudo apt-get update

NOTE: It's important to remove the gutsy sources. Otherwise, you'll get notifications to update many packages and you'll end up running Gutsy, which is not yet ready for prime time.

3) Obtain the CFS patch for 2.6.22 tree: [http://people.redhat.com/mingo/cfs-scheduler/sched-cfs-v2.6.22.5-v20.5.patch](http://people.redhat.com/mingo/cfs-scheduler/sched-cfs-v2.6.22.5-v20.5.patch)

4) Move the patch into the source tree and perform the patch:

# sudo mv sched-cfs-v2.6.22.5-v20.5.patch /usr/src/linux-source-2.6.22
# cd /usr/src/linux-source-2.6.22
# sudo patch -p1 < sched-cfs-v2.6.22.5-v20.5.patch

5) Two rejections will occur: the first is /usr/src/linux-source-2.6.22/Makefile and the second is /usr/src/linux-source-2.6.22/arch/sparc64/kernel/smp.c. You can resolve these yourself or download the fixed files here:

[http://www.michaelhallquist.com/ubuntu-cfs/2.6.22/Makefile](http://www.michaelhallquist.com/ubuntu-cfs/2.6.22/Makefile)
[http://www.michaelhallquist.com/ubuntu-cfs/2.6.22/smp.c](http://www.michaelhallquist.com/ubuntu-cfs/2.6.22/smp.c)

Replace the old versions with those files.

6) Obtain the proper 2.6.22 config file from my site. I used the config from Gutsy's default 2.6.22-generic kernel. As in the previous guide, kernel debugging was turned off.

[http://www.michaelhallquist.com/ubuntu-cfs/2.6.22/config-2.6.22-ubuntu-cfs-v20.5](http://www.michaelhallquist.com/ubuntu-cfs/2.6.22/config-2.6.22-ubuntu-cfs-v20.5)

Move the file into place:

# sudo mv config-2.6.22-ubuntu-cfs-v20.5 /usr/src/linux-source-2.6.22/.config

7) Follow steps 9 and 10 from the previous guide to compile the kernel. Of course, make sure to type in the commands for 2.6.22, not 2.6.20. If all goes well, the 2.6.22 kernel with CFS should be up and running!

As for Nvidia drivers for the 2.6.22 kernel, I had the best luck downloading and running the latest package directly from Nvidia. 

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Check out this thread for more driver details. [http://ubuntuforums.org/showthread.php?p=2587126](http://ubuntuforums.org/showthread.php?p=2587126)

That's it for the 2.6.22 kernel.

- Michael

---

### Post by Prosthetic Head on 2007-09-05
Absolutly amazing!! my old hardware (thinkpad 600e - PII 366) feels so much more responive, menus open smoothly, firefox can still scroll while somthing else is eating the cpu, mp3 and ogg dosn't skip when somthing hits the cpu any more, its just superb :)
I wish this could make it i to GG, I was sceptical before, but now i've tryed it on this old hardware i'm convinved this is a special cas and should be seriously consiered for GG. 
As a (poor) fix for this maby somone with the know-how will post up an unofficial repository with the  patched kerneal kept up to date, the same way others have for compiz, etc in the past?

Thanks for makin it easy for me to try this, i'm liking what i see!

---

### Post by Nigmah on 2007-09-06
haven't had the time yet to do the problem solving i normally  do but
i managed to get to step 4b on the gutsy install and it couldn't find the directory.
So i used both debs and i now have about 4 different kernel boot options cfs 22-10 22-15 and 22-16. i've tried installing nvidia drivers on cfs and 22-10 and it hasn't worked, but i'll post back after i tried some more stuff, i just cant right now.

---

### Post by vassalle on 2007-09-06
Hi, tried to install using the debs you provided. Manage to install the header and image but I got stuck when I tried to install the header for my nvidia driver at the SYSSRC part. I got the error below:
```

vassalle@vassalle-desktop:/usr/src/modules/nvidia-kernel/nv$ SYSSRC=/usr/src/linux-headers-2.6.22.4-cfs-v20.5/ make module install
./conftest.sh: 946: cannot create conftest6297.c: Permission denied

The C compiler 'cc' does not appear to be able to
create executables.  Please make sure you have 
your Linux distribution's gcc and libc development
packages installed.

*** Failed CC sanity check. Bailing out! ***

make: *** [select_makefile] Error 1
```

I've installed the required tools as per tselliot's howto. What else am i missing?

Thanks.

---

### Post by volsungs on 2007-09-06
```

vassalle@vassalle-desktop:/usr/src/modules/nvidia-kernel/nv$ SYSSRC=/usr/src/linux-headers-2.6.22.4-cfs-v20.5/ make module install
./conftest.sh: 946: cannot create conftest6297.c: Permission denied

The C compiler 'cc' does not appear to be able to
create executables.  Please make sure you have 
your Linux distribution's gcc and libc development
packages installed.

*** Failed CC sanity check. Bailing out! ***

make: *** [select_makefile] Error 1
```


Hi Vassalle,

Make sure you run the command with sudo, like so:

# SYSSRC=/usr/src/linux-headers-2.6.22.4-cfs-v20.5 sudo  make module install

With the 2.6.22 kernel, I had really good luck with the installer from Nvidia. Download the installer from here: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html). Then run it with:

sudo sh NVIDIA-package-name.run

Give those two things a try -- I think one or the other should get you a working Nvidia module.

---

### Post by vassalle on 2007-09-06
Will try with Sudo later.

Anyway, I have already installed my Nvidia driver using the installer from Nvidia and it's working perfectly on the stock gutsy kernel (w/out the CFS). Just need to sort out the SYSSRC problem. 

Thanks for your effort. Very much appreciate it, even more so when I can run a CFS patched kernel! :p

---

### Post by Nigmah on 2007-09-06
got the driver working on cfs(with more than a couple errors but everything went fine)
Though my problem is its now like i've zoomed out all the text is smaller, as well a pictures, its very annoying.

edit: well the problems seems fixed after an amd x.org update in update manager and a subsequent reinstall of the driver.

---

### Post by volsungs on 2007-09-08
> **vassalle said:**
> Will try with Sudo later.

Anyway, I have already installed my Nvidia driver using the installer from Nvidia and it's working perfectly on the stock gutsy kernel (w/out the CFS). Just need to sort out the SYSSRC problem. 

Thanks for your effort. Very much appreciate it, even more so when I can run a CFS patched kernel! :p

Hi Vassalle,

If you've gotten the Nvidia module working on the stock Gutsy kernel, all you need to do is boot up using the new CFS kernel, wait for gdm to bomb out, log in at the command line, and run the Nvidia installer like so:

sudo sh NVIDIA-packagenamehere.run

That will compile the module and insert it into the kernel. Then type:

sudo /etc/init.d/gdm restart

And you should have the module up and running for the CFS kernel. Basically, even though you used the installer for the stock kernel, it only compiled for that kernel (in the appropriate /lib/modules folder), but not for the new CFS kernel. Anyway, give that a try.

---

### Post by CnlPepper on 2007-09-13
Just tried the 2.6.20 kernel, works fantastically. The audio output from last.fm radio no longer skips, adobe acroread no longer causes my machine to crawl when it (inevitably) screws up etc... Thanks! :)

Only one nitpick, I couldn't get the framebuffer to work eg vga=0x318 kernel boot option fails.

---

### Post by fishcake007 on 2007-09-14
Impressive stuff!  I would recommend this as a must for all those like myself who's hardware is getting a bit old. It speeds things up considerably over the stock kernel! Well I guess I can hold off buying a new pc for a bit longer! 

I'm running a Celeron 600 and I notice a considerable difference in performance!

---

### Post by xat_ on 2007-09-14
In case of failure/unsatisfaction how would one fall back?

---

### Post by CnlPepper on 2007-09-14
xat_ if you find it doesn't work or you have problems with it them just select the previous kernel version in the grub menu when booting, everything will work as normal then.

---

### Post by SonicSteve on 2007-09-15
Hi Guys,
I'm wondering what happens if I don't edit the xorg.conf before trying to compile a new kernel?
I want to patch my current feisty kernel with UDF support from sourceforge.net

---

### Post by mthakur2006 on 2007-09-16
hi,
i have run into problems with the cfs kernel and i need ur help,please.
i can't compile because the tseliot guide refers to ubuntuguide.org and it is down atm. so, i can't enable the extra repos to download the software needed e.g. linux tree etc.
when i install the debs, i have no connection to the net when i reboot.
please help.
thanks.

EDIT: ubuntuguide.org is up now but i can;t find linux-tree so i can't start compiling and the .debs don't work....help, please. thanks.

---

### Post by Zorael on 2007-09-16
I installed it through the .deb packages, but when I reboot it fails to initialize my Intel PRO/Wireless 3945 card.

```
zorael@azrael:~$ dmesg | grep ipw3945
[   23.982654] cs: IO port probe 0xa00-0xaff:<6>ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   23.982979] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   23.983642] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   24.009893] ipw3945: ipw3945.ucode load failed: Reason -2
[   24.010016] ipw3945: Could not read microcode: -2
[   24.011793] ipw3945: probe of 0000:07:00.0 failed with error -2
```

Is this something I could easily resolve by compiling it myself? Or would I have to compile the driver? I've had some major setbacks in that area already, and I don't want to have to reinstall again just to restore the standard driver. :>

---

### Post by mthakur2006 on 2007-09-18
> **mthakur2006 said:**
> hi,
i have run into problems with the cfs kernel and i need ur help,please.
i can't compile because the tseliot guide refers to ubuntuguide.org and it is down atm. so, i can't enable the extra repos to download the software needed e.g. linux tree etc.
when i install the debs, i have no connection to the net when i reboot.
please help.
thanks.

EDIT: ubuntuguide.org is up now but i can;t find linux-tree so i can't start compiling and the .debs don't work....help, please. thanks.

okay never mind, ive started compiling, lets see how it goes and i will keep you all posted. thanks.

---

### Post by hardyn on 2007-09-18
removed

(seemed to have jumped into the middle of a thread... i should refresh before posting)

---

### Post by Anthon berg on 2007-09-18
I'm probably mistaken, but it seems that CFS makes Gnome load in a ... snap! Good stuff.

I'm using the latest CFS.

---

### Post by mthakur2006 on 2007-09-18
not going so well for me, gnome doesn't load in a snap, i have noticed no speed increase and worst of all, i have lost my wireless internet and the boot time has gone up from 27 to 43 seconds.....

---

### Post by mthakur2006 on 2007-09-22
> **mthakur2006 said:**
> not going so well for me, gnome doesn't load in a snap, i have noticed no speed increase and worst of all, i have lost my wireless internet and the boot time has gone up from 27 to 43 seconds.....

well i have got it working finally but i am yet to notice any speed increase :|

---

### Post by volsungs on 2007-09-24
> **Zorael said:**
> I installed it through the .deb packages, but when I reboot it fails to initialize my Intel PRO/Wireless 3945 card.

```
zorael@azrael:~$ dmesg | grep ipw3945
[   23.982654] cs: IO port probe 0xa00-0xaff:<6>ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   23.982979] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   23.983642] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   24.009893] ipw3945: ipw3945.ucode load failed: Reason -2
[   24.010016] ipw3945: Could not read microcode: -2
[   24.011793] ipw3945: probe of 0000:07:00.0 failed with error -2
```

Is this something I could easily resolve by compiling it myself? Or would I have to compile the driver? I've had some major setbacks in that area already, and I don't want to have to reinstall again just to restore the standard driver. :>

Hi Zorael,

Check out this post on compiling a custom kernel. There is a section on compiling the IP3945 drivers from source, which I believe you'll need to do to get wireless working with the CFS kernel. It looks straightforward to recompile the driver, but let us know if you have a problem with it, as I know others have had similar problems and would benefit from your experience.

[http://ubuntuforums.org/showthread.php?t=475886](http://ubuntuforums.org/showthread.php?t=475886)

---

### Post by nowshining on 2007-10-05
i'll try this out myself after Gutsy is released :)

---

### Post by andrew01 on 2007-10-10
Sorry if it isn't a good place for ask for this, but i will try,

I downloaded new kernel 2.6.23  form kernel.org (i have custom kernels since 2.6.20) and i tried to enable a CFS scheduler but I can't find suitable option in config. Could someone tell me how to enable it?

Many thanks in advance.
Best Regards
Andrew

---

### Post by Trueno22 on 2007-10-12
how do you make the restricted modules for this??? installed cfs fine but wireless doesn't work neither does my sound.

---

### Post by shae on 2007-10-14
> **andrew01 said:**
> Sorry if it isn't a good place for ask for this, but i will try,

I downloaded new kernel 2.6.23  form kernel.org (i have custom kernels since 2.6.20) and i tried to enable a CFS scheduler but I can't find suitable option in config. Could someone tell me how to enable it?

Many thanks in advance.
Best Regards
Andrew

You do not have to change the value at all.  CFS is the default option IIRC.

---

### Post by nowshining on 2007-10-15
> **shae said:**
> You do not have to change the value at all.  CFS is the default option IIRC.

if anyone is wondering the kernel 2.6.23.1 is stable from kernel.org

"The latest stable version of the Linux kernel is:  	2.6.23.1"

---

### Post by mendieta on 2007-11-11
Thank you so much, Michael! 

I am running your "2.6.22.4-cfs-v20.5" binaries just fine (I only had to install the NVIDIA driver as per your instructions, from NVIDIA's site).

I do notice better multitasking. For instance, I can run many different web browsers at the time, and jump around more smoothly than with the regular Gutsy kernel.  Also, running the NJam game with many processes opened in the background usually has large gaps where the game is just frozen for a second or two. With the cfs patch, I do get interruptions, but they last a fraction of a second, never too disruptive.

This is a kind of low end machine: a three years old AMD Athlon XP 2400+ (OC'ed to 2600+), with 768 Mb Ram, of course single processor. 

Again, thank you so much for taking the time. Linux is all about freedom to play, tweak, discover ... and **own your computer**. :-)

Cheers! Keep it up!

---

### Post by charlieg on 2007-11-24
Sadly the 2.6.22 kernel guide gave me a non-booting kernel.  I'll try one of the later releases.

---

### Post by mendieta on 2007-11-24
Guys, in a related note, I am running the **real-time** kernel for Gutsy. Anyone else doing it ? It seems to give more responsiveness (because it tends to limit latencies). 

There is some discussion here: [https://wiki.ubuntu.com/RealTime/Hardy](https://wiki.ubuntu.com/RealTime/Hardy)
They mention CFS. It's not clear how the RT patch will interact with the new scheduler. I think it's gonna be sweet :)

Anyway, if anyone is interested in trying this, just install the meta-package **[COLOR="Blue"]linux-rt[/COLOR]**.

Cheers!

---

### Post by runesvend on 2008-04-12
Hello

I just tried installing the CFS-kernel and it seemed to go fine. I compiled it without errors, booted into the new kernel and I was greeted with a low resolution screen saying something about Ubuntu not being able to configure my screen properly (because the nVidia driver isn't installed I suspect).

I then downloaded the run-file from nVidia's site for my GeForce 6 series, changed the runlevel to 3 with "telinit 3", closed down X Server with "/etc/init.d/gdm stop" and ran the run-script.

The nVidia-installer said that "No precompiled kernel interface was found to match your kernel" and I answered "No" when it asked if it should search for such a thing online. It then went on to compile this interface, which it did, and then it said it had "finished successfully". I restarted my computer and I was greeted the exact same way as before; a low resolution picture saying something is wrong with my screen configuration.

When trying to enter System>Administration>Restricted Drivers Manager i get a message saying:

> You need to install the package

linux-restricted-modules-2.6.22.9-cfs-v24.1-cfs

for this program to work.

What can I do to make it work?

---

