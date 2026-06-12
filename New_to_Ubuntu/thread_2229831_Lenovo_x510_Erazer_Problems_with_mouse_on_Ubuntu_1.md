---
title: "Lenovo x510 Erazer: Problems with mouse on Ubuntu 14.04"
date: 2014-06-15
forum: New to Ubuntu
---

### Post by koru7 on 2014-06-15
Hello, I recently installed Ubuntu 14.04 on my Lenovo x510 Erazer (Dual-Boot with Ubuntu 14.04)  I'm now having problems when I boot it up and when I go onto the desktop.  The problem is that whether or not I have a mouse plugged in, Ubuntu assumes I already have one plugged in and it's stuck in the top right corner clicking things randomly.  If I plug in my mouse (no matter what mouse)  it just spazzes out and tries to go back to the top right.  I'm thinking it's a driver issue... Please help.

---

### Post by oskaripisterantala on 2015-01-03
I'm having the same problem with the same Lenovo model. There's further discussion in this thread (but sadly not a solution yet): [http://ubuntuforums.org/showthread.php?t=2235704](http://ubuntuforums.org/showthread.php?t=2235704)

---

### Post by mörgæs on 2015-01-03
How does it work in a live boot of 14.10?

---

### Post by oskaripisterantala on 2015-01-03
It's the same thing with 14.10, unfortunately. Cursor snaps back in the corner if I try to move it and clicks randomly, whether a mouse is connected or not.

---

### Post by mörgæs on 2015-01-04
If it's also the case for 15.04 (development) it would be good if you could report the bug.

---

### Post by oskaripisterantala on 2015-01-04
Thanks, I'll give 15.04 a try next then.

I've never reported a bug before, so I'm not sure if I can do that properly. 

I read (here: [http://help.ubuntu.com/community/ReportingBugs](http://help.ubuntu.com/community/ReportingBugs)) that you are supposed to do it in Ubuntu via the Apport application. The mouse doesn't work, so using the GUI can be tricky.

I also haven't installed Ubuntu yet and tried it only from live USB to see if it works on this computer. Can I file a bug when using the live USB or should it be an installed version?

---

### Post by mörgæs on 2015-01-04
Thanks. If you are unsure about how to proceed you could ask in the [development forum]("http://ubuntuforums.org/forumdisplay.php?f=427") (or I could move thread if you want).

---

### Post by murlock on 2015-05-11
Hi,

I've same issue (15.04 and 14.04 LTS) with same computer and I can't find opened tickets at launchpad.

I've found that a mouse is detected on isa0060/serio1 (and /dev/input show two mice)
```

$ dmesg | grep -E 'mouse|mice'
[    0.485839] mousedev: PS/2 mouse device common for all mice
[    0.672781] psmouse serio1: Failed to reset mouse on isa0060/serio1
[    7.312566] psmouse serio1: Failed to deactivate mouse on isa0060/serio1
[    7.411902] psmouse serio1: Failed to enable mouse on isa0060/serio1
[    8.476262] psmouse serio1: Failed to enable mouse on isa0060/serio1

```

---

### Post by 4levels on 2015-06-17
Hi all,

I have exactly the same issue for months now and it's driving me completely nuts!
I've tried Fedora 21, 22, Ubuntu 14, 15, ubuntu-gnome, ubuntu-mate, Debian 8 and all these render the same buggy behavior both in the live environment and the fully installed versions, exactly as described here: mouse jumping to the top edge, right edge, eventually ending up in the top-right corner and clicking around like it's completely mad.  For a short period of time right after startup this behaviour doesn't appear, it seems to randomly start after maximum a couple of minutes.
I've tried to change the surface the mouse is on, but even when changing to a different mouse or keyboard this doesn't seem to help.  Even removing the mouse doesn't change a thing!  I tried [FONT=Courier New]rmmod psmouse[/FONT] option but psmouse is no longer a module but built in [FONT=Courier New]rmmod: ERROR: Module psmouse is builtin[/FONT].

I've tried almost all psmouse boot line parameters like psmouse.proto and still didn't succeed.  Even when using a rdesktop client I can see the mouse jumping around but at least the connecting machine doesn't, still this is completely unsatisfying.  Currently I disabled the graphical runlevel target completely, I'd rather have a working commandline instead of a tripping mouse on the login screen.

At some point (as I felt like loosing my mind over this) I even removed the built-in wireless card, it seemed related to my cellphone being near but both mouse and keyboard are cable connected through USB.  There is no bluetooth device available in my machine so that rules out any other possible interference issues.  Still, interference doesn't even make sense on cable connected devices.

I've changed my monitor's cables from display port to DVI but still the same, I've tried all ports on the AMD Radeon card, to no avail either.
 
This has by far been my most frustrating experience ever and I've been using Linux for more than 15 years as a developer.

I'm addressing Lenovo atm, awaiting their reply.  I did get a terrible experience trying to register my desktop as well, the ThinkAdvantage software fails miserably and their support website keeps redirecting me to the country selection page..  
I struggled a lot trying to get rid of the RAID-0 striped disk array as I don't like the idea all my data being lost if one of the 2 disks fails.  I still had a 64Gb SSD disk around from my laptop which I want to use for windows.  Another 128Gb SSD disk is for Linux.  I ended up destroying the raid in the bios and had to reinstall windows using a vanilla disk.  

Because of all this, I'm starting to believe that this device is somehow cursed!  I'm very glad I found this thread, at least I'm not losing my mind as other people are having this mouse issue too.  I'm still going to try not using both keyboard and mouse, but that's really a shame as both devices work flawlessly under windows.

I hope to be able to provide a solution for this, I keep my fingers crossed!

Kind regards,

Erik aka 4levels

I just tried with a completely different mouse and keyboard and the problem is exactly the same!  This rules out any driver / hardware issue related to the specific Lenovo Gaming mouse MS-172 or the Lenovo Black Silk gaming keyboard..  
I'm currently testing OpenSUSE and Arch Linux, after that Gentoo is up, maybe I find more info when configuring the latter..

Still no answer from Lenovo Support..

---

### Post by mörgæs on 2015-06-21
It's always a good idea to try the latest Buntu which now is 15.10 (in development) in a live boot. 
Any improvement here?

---

### Post by 4levels on 2015-06-22
I'll get on with that tonight..
Yesterday I tested OpenSUSE 13.2 with no difference: either with the Lenovo Gaming peripherals or the Cherry keyboard and plain old optical mouse, or even without mouse at all, the cursor keeps jumping to the top right corner and clicking on it's own.  I'm starting to chase Lenovo support for this.  To me it starts to seem that this issue might go really deep as so many different distro's seem to be affected.. *sigh*

Still no luck, the live environment of ubuntu-gnome-15.04 shows the same erratic mouse behaviour, in short, unusable.
I'm trying the default ubuntu with unity next.. after that, Arch is on.

I'll keep you posted here

I finally got through to Lenovo support.  They officially don't support Linux, but only when I kept on explaining my experiences about this frustrating mouse issue and how my previous experiences with Linux on Lenovo have always been great, the agent told me to switch off the computer, remove the power cable and vga cables, wait 10 seconds and push the power button repeatedly to drain all remaining current and try again.

I couldn't believe that this would do anything but.. here the **mouse issue disappeared**!!

I couldn't stop thanking the agent, I hope this works for other people too!

Now I'm going to try with the Erazer mouse and keyboard, fingers crossed!

This "fix" seems to work as well with the Lenovo Black gaming keyboard and mouse.  Although occasional re-emerging, by simple repeating the process of draining all power from the computer, the issue disappears again.  I do start to think it could be related to the keyboard: I'm guessing the backlight feature can drain quite some power when fully lit and it seems to help to use the button on the top right of the numpad to disable the backlight during the boot sequence.  I did try plugging them into the blue USB3 ports at the rear as I expect USB3 to provide more power, but this doesn't seem to make a difference.  This might just be coincidence but somehow it works better if I disable the backlight during boot.

Can anyone confirm this "fix" also works on their end?

---

### Post by william90 on 2015-11-04
I created an account so that I can post my experience with the Erazer X510 which has been irrespective of distro, I have experienced the mouse issue on Fedora and Suse as well.

The reason am posting this is so that other Linux users might find it useful

On the versions of these two distros the psmouse is a built in kernel module, what worked for me was doing the following steps

1. removing the noveau rpms
2. disabling nouveau on the kernel boot line and setting the psmouse.proto to bare on /etc/default/grub

GRUB_CMDLINE_LINUX="rd.driver.blacklist=nouveau psmouse.proto=bare"

3. create a new grub.cfg file

grub2-mkconfig > /boot/grub2/grub.cfg

4. reboot

5. download the Nvidia GeForce GTX 760 from [http://www.geforce.com/drivers](http://www.geforce.com/drivers), this is the current file NVIDIA-Linux-x86_64-352.55.run compile and install

before doing that you will need the compiler tools and kernel-dev and headers
sudo dnf groupinstall 'Development Tools' -y && sudo dnf install kernel-devel kernel-headers

This is what worked for me and an happy with the results.

---

### Post by 4levels on 2015-11-05
Hi,

thanks for the update on the psmouse module and your feedback.  At my end, the issue keeps coming back after a while so I'm still plagued with this on a daily basis.
I do however have the Erazer with an ATI setup, so I'm not sure if the same procedure (remove default ATI drivers in favour of the proprietary one) will make a difference but it's definitely worth a try!

I'll keep you updated here..

---

### Post by Lars_Henrik_rn on 2015-11-09
Hi

I am on Debian. I have had the same problem on Debian, Archlinux but not on gentoo. I am using a wonderfulll X510 with radeon and 32 GB ram

I have found out that there is a problem with the psmouse driver. If you do not use trackpad a simple

modprobe -r psmouse

did the trick. You can off course make this change permanent by adding a psmouse.conf in /etc/modprobe.d with the following content:

# Do not load the 'psmouse' module on boot. 
blacklist psmouse

Have a nice day

---

### Post by d.hypercube on 2016-03-07
Exactly the same problem here on a Lenovo Yoga 2 13. I cannot find a pattern, this sometimes shows up after 2 minutes or 20 but it DOES show up.

My Lenovo support experience has been pretty abominable every time I reached out so, other than the fact I would never ever wish a Lenovo on my worst enemy, I know pretty much nothing about my problem.

Note it is always one of the right corners for me, never the left ones.

Ubuntu version: 14.04, tried 15.10 also but still the same.
Has anybody found a solution?

---

