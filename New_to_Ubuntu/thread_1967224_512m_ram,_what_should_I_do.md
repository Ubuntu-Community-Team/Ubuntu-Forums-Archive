---
title: "512m ram, what should I do?"
date: 2012-04-27
forum: New to Ubuntu
---

### Post by jamesbeat on 2012-04-27
I have just been given a Dell Dimension 4300.

This is great, because I also just got an LCD TV, and I wanted a pc to connect up to it.

My needs are very basic, as I have other machines for doing my more demanding stuff. All I intend to use this computer for is:

Basic web browsing, a little youtube etc.
Watching movies that I have stored on the local hard drive
(Most important) Skype, so my mom, who's back home in the UK can at least sort of watch her grand daughter growing up.

I've always used Ubuntu, but I just checked, and it seems that I don't have enough memory. The specs of this machine are:

1.6Ghz Pentium 4
512Mb ram
160Gb HDD

As you can see, the specs are not all that bad, and I know I can get something to work well on this machine.
The problem is that Ubuntu requires a minimum 1Gb ram, and this Dell cannot handle anything above 512Mb.

I want to do this without spending any money whatsoever.

I'd like to hear some opinions from people with more experience :)

---

### Post by Rodney9 on 2012-04-27
Try L[COLOR="Blue"]ubuntu[/COLOR]

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by Penguinnerd on 2012-04-27
Yes. The other "lightweight" option is Xubuntu, but it's really not as light at Lubuntu. If Lubuntu will do everything you need it to do, that's the way to go.

If that isn't fast enough for you, you could also try plain 'ol Debian with LXDE. It would be marginally faster, but somewhat more technical.

---

### Post by jamesbeat on 2012-04-27
Thanks for the suggestions, I've already tried xubuntu (on a different machine, trying to find an alternative to Gnome 2/unity) and, although it is very basic, I think I could get used to it.
Never even heard of lubuntu, but I'll give that a go too.

Forgive me if I sound like a noob, but will these behave the same as ubuntu apart from the desktop environment?
For instance, could I install ubuntu restricted extras, or are things like this specific to the distro?
I notice that kubuntu has its own restricted extras package for instance, so obviously there's a reason for that.

---

### Post by cryptotheslow on 2012-04-28
First and foremost - breathe. Don't run around like a headless chicken installing distribution after distribution seeking one that works for you.

STOP - and think.

What are your priorities?

You stated:[I]
Basic web browsing, a little youtube etc.
Watching movies that I have stored on the local hard drive
(Most important) Skype, so my mom, who's back home in the UK can at least sort of watch her grand daughter growing up.[/I]

Now to put those in your stated order of priority:
*1. (Most important) Skype, so my mom, who's back home in the UK can at least sort of watch her grand daughter growing up.*

No point going beyond 1. really. The most important thing is to get something installed that can cope with Skype video.

With 512MB RAM - you are not going to be able to run Ubuntu 12.04 in any meaningful way.

If the priority is video skype we need to know what are using for graphics (what graphics card or what video chipset) and what webcam you want to use.

---

### Post by Miljet on 2012-04-28
A lot of the default programs are the light-weight cousins of the ones you are used to in Ubuntu. For example, Leafpad instead of Gedit, Abiword and Gnumeric instead of OpenOffice, and so forth. For the most part, other than the names, you will notice little notice. And if you really prefer a program you are used to, you can always install it.

I actually find that I prefer the simpler versions. I can even remember when you could get an entire word processor (including mail-merge) on a 360kb floppy disk.

---

### Post by mferarri on 2012-04-28
how about debian (squeeze release)?

it can run gnome2 ([http://www.debian.org/releases/stable/i386/ch03s04.html.en]("http://www.debian.org/releases/stable/i386/ch03s04.html.en")) and it can also run skype ([http://wiki.debian.org/skype]("http://wiki.debian.org/skype")), i've used it and i think it's really great. (just my opinion). hope it goes well for you.

---

### Post by 3rdalbum on 2012-04-28
To answer your question, Lubuntu is simply Ubuntu with a different desktop and a different set of preinstalled programs. Anything you can install on Ubuntu can also be installed on Lubuntu, including Ubuntu-restricted-extras. You can even install the Unity desktop on Lubuntu, but it would use as much memory as regular Ubuntu.

---

### Post by Anuovis on 2012-04-28
Like others said, Xubuntu or Lubuntu would probably do the job. 

If you are up for an adventure, you could take a look at Bodhi Linux, I only tried a live session but it is designed with very weak machines in mind. It seems to be a derivative of Ubuntu but the graphical environment is very different from all Ubuntu flavors. Might take time to get used to.

[http://www.bodhilinux.com/system.php](http://www.bodhilinux.com/system.php)

---

### Post by Cheesemill on 2012-04-28
Another distro you could check out is #! (Crunchbang Linux).
[http://crunchbanglinux.org/](http://crunchbanglinux.org/)

It's based on Debian + Openbox and it's the OS I always go for on low spec machines.

---

### Post by jamesbeat on 2012-04-28
Thanks guys, this is really helping with the learning curve.
I tried bodhi, but the machine wouldn't read the disk. The disk works fine in all three other computers in the house, so I'm suspecting the dust and cat hair filled cd drive.
I'll either clean it or temporarily install another drive in it and try again.
I hadn't heard of crunchbang, but that looks like another good candidate.

@cryptotheslow:
yes, you're right about the headless chicken thing, I could easily drive myself nuts! I'll try about four livecds from the suggestions and pick one.

Webcam/skype is most definitely #1 priority.
To the list of priorities, I would also like to add that it should be an ubuntu derivative, so I can use the repos.
I'm not a total noob (been using ubuntu since 2006) but I want this machine to be as painless as possible.
I don't want to have to spend hours fighting it to make it work.

I'll check to see what the graphics card is later (I'm at work right now).
The webcam is some generic thing with a vimicro chipset.
It is plug and play with cheese on my ubuntu setup (10.04lts) but it doesn't initialize with skype for some reason.
I think I can get it working though, I just haven't tried in earnest yet.

What about using an older, less demanding ubuntu? 
Would one of the LTS versions do the trick?

---

### Post by Penguinnerd on 2012-04-28
If you're thinking about using an earlier release, I would discourage it.

10.04 has one more year of support, and after that you'll have to find something else. That's my situation right now.

Using an unsupported version is simply not an option. There are too many well-documented security holes that were not discovered back when they had support.

I would stick to recent releases. Even a short term (18 month) release has more time left than 10.04 at this point.

10.04 was and still is fantastic, but if it's your only option, you're just delaying the inevitable for another year. (And that's coming from me, an avid Gnome 2 supporter!)

I think you'll find that Lubuntu is adjustable enough to satisfy you, and it can probably run fast enough for you as well.

Keep in mind though, that it will be faster on a hard drive than when you test it on a live CD. CDs are slow.

---

### Post by jamesbeat on 2012-04-28
Hmm, I thought support for 10.04 was for three years, which would mean I'm ok for about a year. 
I'm afraid I'm living the nomadic life of those who cannot live with unity or gnome2, so 10.04LTS is what I'm using on all of my machines at the moment.
I just checked, and was delighted to discover that 10.04 will work fine on 512mb (I thought memory requiremebt was higher), but now you've worried me...

---

### Post by Anuovis on 2012-04-29
> **jamesbeat said:**
> I tried bodhi, but the machine wouldn't read the disk.
You could use USB instead, I find them more convenient than disks. Unless that laptop is ancient and doesn't have a slot.


> **jamesbeat said:**
> To the list of priorities, I would also like to add that it should be an ubuntu derivative, so I can use the repos.
In that case, Bodhi might not be for you. Again, I haven't used it beyond the live session but they are using their own sort of software center and I don't think you can use deb files to install new software. It differs from Ubuntu in many ways so maybe it's better to stick to Lubuntu or Xubuntu if you don't want to tinker with new environments.

I also feel you are making this into a bigger problem than it really is. Choices sometimes grow on us like that... :)

1) You need webcam and Skype
2) You would like to use something from Ubuntu family
Simply go with Lubuntu or Xubuntu. Huge chance it would work well. And you will have the same familiar system under the desktop environment.
 
If you ever want to experiment with different distros, you can try them later.

I used to run Ubuntus up to 11.04 with only 512 MB of RAM and it was bearable but I advice you to leave Ubuntu alone and go with lighter versions. It's unlikely to be a smooth ride, even with 10.04.

---

### Post by souravc83 on 2012-04-29
I would try crunchbang too. Very promising distro.

---

### Post by Peripheral Visionary on 2012-04-29
My old hand-me-down Dell has 512 of RAM and it runs Xubu 10.04 beautifully. It *also* runs Xubunu 12.04 beautifully. In fact 12.04 is even a little faster than 10.04.

I have experienced no discernible difference in speed or performance between Lubuntu and Xubuntu at all. It's pro'bly measurable with some kind of device, but it has not affected the "user experience" for me, except that Xubu has more features than Lubu.

Rest easy. Your 512 of RAM is enough for 3 more years!

---

### Post by jamesbeat on 2012-04-30
Ok, I tried lubuntu and xubuntu, and this is what happened:

lubuntu: a complete non-starter. When trying to install, the text was *tiny*.
I have the machine hooked up to my 40" lcd tv, but even though the screen is big, the text is so small that it's impossible to read, like a couple of mm in height.
I tried to fumble and guess my way through, but it was impossible.
I tried throwing in some other livecd's that I had, and the same problem occurred with bodhi and kde.

Xubuntu: installed ok, but it's a little slow. I could have coped with the speed, but unfortunately video is extremely choppy to the point of being unusable.
Webcam was the worst for choppy display, unless I reduced the size of the window to about 2" on a side, which kinda defeats the object of this project.

I monitored cpu and memory usage while performing various tasks, but neither went over about 60%, so I'm suspecting the graphics card.
Graphics card is an ATI Rage 128 which,  judging by the specs shouldn't be as bad as it is.

What could this be? Wrong drivers?

I'm leaning more towards lubuntu (I tried the livecd on another machine) but it is completely unusable unless I can figure out that tiny font problem, and even if I do manage to install it, will the video be just as choppy as it is with xubuntu?

So what should I do?
Install better drivers for the graphics card?
Buy a different graphics card?
Try an even lighter distro like puppy?
Have a tantrum and throw it out of a window?


Edit: I should add that I do not have access to a different monitor, so I can't temporarily hook it up to one to fix the font problem.
Seems like everyone has laptops nowadays :(

---

### Post by Penguinnerd on 2012-04-30
As for the tiny text in the installer, I believe there's some way to specify a boot option and force it to use a lower screen resolution. That should make the text bigger so you can get through the installer.

I've never had to do that in Ubuntu though, so I'm not sure how. Perhaps someone else knows?


I'm not sure what to do about the choppy video problem. It could very well be the drivers, but you usually get a notification that better drivers are available if that's the case. 
You can probably go to settings >>>> Additional drivers for a start. See what it says there, and try checking for better drivers. (I'm pretty sure there's a button for that)

---

### Post by jamesbeat on 2012-04-30
There wasmention of  a boot option in the help section of the installer.
It was 'vga=771'.
unfortunately, the help section said to press f6 twice to enter it, or something similar, but that didn't work.
I tried adding it to the boot parameters that were already there, but it didn't do anything. I'm not sure if I did it correctly though...

---

### Post by arpanaut on 2012-05-01
Sometimes LCD-TV's are difficult to configure especially with borderline graphic chips.
Do you have a "normal" monitor of some type to try the install with then hook-up the tv and see what you could get going?

A shot in the dark?

---

### Post by Penguinnerd on 2012-05-01
> **arpanaut said:**
> 
Do you have a "normal" monitor of some type to try the install with then hook-up the tv and see what you could get going?

See this: 

> **jamesbeat said:**
> 
Edit: I should add that I do not have access to a different monitor, so I can't temporarily hook it up to one to fix the font problem.
Seems like everyone has laptops nowadays :(

---

### Post by jamesbeat on 2012-05-01
No, as I said, I don't have access to a different monitor. Everyone I know seems to have laptops. To be honest, this is the first desktop I've had for a while.
I've had some measure of success by using guesswork to enlarge the fonts while running lubuntu from the CD.
This seems to have carried over to the install, which I'm doing as I type....

---

### Post by SemiExpert on 2012-05-01
I'd suggest Ubuntu 10.04.4, since Gnome 2.32 takes far less memory than the current alternatives.  The only real problem is that support ends in April of 2013, so you've got less than a year left.  If you want to experiment with a rolling release, try the latest version of Linux Mint Debian Edition or LMDE.  Mate 1.2, the fork of Gnome 2.x, is a very lightweight and full featured desktop, and the current version of LMDE is the best version of Mint so far - and this is coming from someone who doesn't like Mint.  I can't really recommend Lubuntu and Xubuntu, since neither is especially lightweight, but both are fairly limited in comparison to Mate 1.2/Gnome 2.x.  So the real choice is between 10.04.4 and LMDE, depending on your comfort level.

---

### Post by Sidewinder1 on 2012-05-01
+1 on all of the 10.04 suggestions. Also remember that in April 2013, Lucid won't go "POOF", and disappear/stop working. There will just be no more security updates for it; you could continue to use it. I have a very close friend who is still using Hardy.
Initially you said that you wished to spend 0$, then, if I recall, something about an additional expenditure. You may wish to consider a video card upgrade for some add'l video ram, for Skype since it's your number 1 priority.
Best of luck as it sounds like a pretty neat project. :-)

HTH, Side

---

### Post by kurt18947 on 2012-05-01
I was reading this thread and thinking a cheap Nvidia graphics card might provide the most 'bang for the buck'.  According to 

[http://support.dell.com/support/edocs/systems/dim4300/specs.htm](http://support.dell.com/support/edocs/systems/dim4300/specs.htm)

your machine doesn't have a PCI-E slot.  Instead it has PCI & AGP.  90% of video cards available today are PCI-E. There are PCI video cards available but I don't know how capable or how cheap.  AGP has been obsolete for quite some time so finding recent vintage  supported AGP video cards may make hens' teeth seem plentiful.

---

### Post by kurt18947 on 2012-05-01
duplicate -- please delete

---

### Post by Cheesemill on 2012-05-01
Have you tried Crunchbang yet as a few of us suggested earlier?
You might not have the graphics problems that you've been having with all of the *buntu derivatives.
 
[http://crunchbanglinux.org/](http://crunchbanglinux.org/)

---

### Post by jamesbeat on 2012-05-01
Man, I just got lubuntu installed, and the choppy video is still there :(

I tried installing ubuntu 10.04, but it just hung. Tried the alternate install disk andit got further then hung again.

Downloading crunchbang now...

---

### Post by LillyDragon on 2012-05-01
Have you tried running an OpenGL-based game on Ubuntu to at least test for hardware acceleration, by chance? If the performance is terrible even in Open Arena, it has to be your graphics drivers, which isn't going to translate well for video recording/playback either. Youtube on the other hand should be fine since the Flash runtime chokes the life out of your CPU more than anything, so no hardware acceleration is necessary, but still not as important as getting the webcam to cooperate.

tl;dr, I might as well chime in and suggest you get a better card, any card, as long as it's not ATI; don't even worry about a RAM upgrade. At least with Intel chipsets I don't have any choppiness in playing mid-end games or HD videos.

> **cryptotheslow said:**
> With 512MB RAM - you are not going to be able to run Ubuntu 12.04 in any meaningful way.

My desktop is still fine on just that and I don't have any trouble with GIMP, Amarok, Firefox, and several instances of Kolourpaint running at the same time. More RAM would be nice for the heavier sessions, and save my system from actually resorting to the swap partition, but I'll upgrade it when I have no other alternative, even if DDR2 RAM is dirt cheap nowadays. :P

---

### Post by jamesbeat on 2012-05-01
That's interesting. Youtube is actually the choppiest!
I tried playing an avi and that worked ok, but the webcam is choppy unless I shrink the window a great deal, and youtube is awful.
On youtube, the video takes ages to display (counter going, but takes several seconds for picture to start, then choppiness).
I tried both firefoxand chromium, figuring chromium is lighter, but it's still the same.

So ATI graphics cards are notoriously bad?
Should I buy an old non-ATI card on ebay or something?

---

### Post by lykwydchykyn on 2012-05-01
ATI is a mixed bag; did you install the proprietary driver?  It usually helps (though depends on the card).

You have to keep in mind, those cards were designed to drive a desktop monitor at 4:3 resolution, 40" monitors (I'm assuming at 1080p?) were not in the designs.  The higher the resolution, the more pixels have to be processed.  

If you haven't installed the proprietary driver, though, open the drivers tool and give it a shot.  It might help you out a bit.

---

### Post by jamesbeat on 2012-05-01
I tried playing with the resolution, and it was just the same in 640x480, although I don't know if that is a valid way of testing it.

I managed to get ubuntu 10.04 working, but youtube and webcam are both still choppy.
Videos files work great, even feature length movies in fullscreen are working perfectly.

No drivers show up in the hardware drivers section. I don't know if this means that there aren't any or if I need to do it in a different way?

---

### Post by lykwydchykyn on 2012-05-01
Ah, I guess the proprietary driver doesn't support the Rage 128.  I don't think you're bound to get good performance out of it.  Is there any onboard video, or is the card the only thing?

Can you post the contents of /var/log/Xorg.0.log?

---

### Post by jamesbeat on 2012-05-01
No integrated graphics.
I looked in software center, and it appears that there is a driver for the Rage 128 family, and it is installed.

I just tried the webcam, and it is working ok in Cheese (not in Skype, but I've always had that problem with this webcam)

So, webcam is ok, video files are ok, youtube is still unusable. I notice that it even stalls when I move the mouse!

On the whole, while I wouldn't call it snappy, ubuntu 10.04 seems to be working well enough to be usable, apart from the youtube problem.


EDIT: I installed Chromium and, while it is still too choppy to be useful, youtube is running much better than it was on Firefox.

Here's the Xorg.0.log:

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
Current Operating System: Linux beatbox 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:13:04 UTC 2012 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-38-generic root=UUID=75fc3a4c-3ef0-4e23-894c-62c955e53ea3 ro quiet splash
Build Date: 20 October 2011  03:05:54PM
xorg-server 2:1.7.6-2ubuntu7.10 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue May  1 14:29:13 2012
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 1002:5446:1002:0408 ATI Technologies Inc Rage 128 Pro Ultra TF rev 0, Mem @ 0xf8000000/67108864, 0xff9fc000/16384, I/O @ 0x0000ec00/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched ati as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 6.13.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "r128"
(II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
(II) Module r128: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 6.8.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.4.1
	ABI class: X.Org Video Driver, version 6.0
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
	ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
	ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
	ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
	ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
	ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
	ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
	ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
	ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
	ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
	ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
(II) R128(0): PCI bus 1 card 0 func 0
(II) R128(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) R128(0): Depth 24, (--) framebuffer bpp 32
(II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) R128(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.1.0
	ABI class: X.Org Video Driver, version 6.0
(II) R128(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) R128(0): RGB weight 888
(II) R128(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Video Driver, version 6.0
(II) R128(0): initializing int10
(II) R128(0): Primary V_BIOS segment is: 0xc000
(--) R128(0): Chipset: "ATI Rage 128 Pro ULTRA TF (AGP)" (ChipID = 0x5446)
(--) R128(0): Linear framebuffer at 0xf8000000
(--) R128(0): MMIO registers at 0xff9fc000
(--) R128(0): VideoRAM: 16384 kByte (128-bit SDR SGRAM 1:1)
(**) R128(0): Using external CRT for display
(II) R128(0): Primary Display == Type 3
(WW) R128(0): Can't determine panel dimensions, and none specified.
	Disabling programming of FP registers.
(II) R128(0): PLL parameters: rf=2950 rd=65 min=12500 max=35000; xclk=13000
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Video Driver, version 6.0
(II) R128(0): VESA BIOS detected
(II) R128(0): VESA VBE Version 2.0
(II) R128(0): VESA VBE Total Mem: 16384 kB
(II) R128(0): VESA VBE OEM: ATI RAGE128
(II) R128(0): VESA VBE OEM Software Rev: 1.0
(II) R128(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) R128(0): VESA VBE OEM Product: R128
(II) R128(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) R128(0): VESA VBE DDC supported
(II) R128(0): VESA VBE DDC Level 2
(II) R128(0): VESA VBE DDC transfer in appr. 2 sec.
(II) R128(0): VESA VBE DDC read successfully
(II) R128(0): Manufacturer: TSB  Model: 205  Serial#: 16843009
(II) R128(0): Year: 2012  Week: 1
(II) R128(0): EDID Version: 1.3
(II) R128(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) R128(0): Sync:  Separate
(II) R128(0): Max Image Size [cm]: horiz.: 160  vert.: 90
(II) R128(0): Gamma: 2.20
(II) R128(0): DPMS capabilities: Off; RGB/Color Display
(II) R128(0): First detailed timing is preferred mode
(II) R128(0): redX: 0.640 redY: 0.335   greenX: 0.285 greenY: 0.605
(II) R128(0): blueX: 0.150 blueY: 0.060   whiteX: 0.280 whiteY: 0.290
(II) R128(0): Supported established timings:
(II) R128(0): 640x480@60Hz
(II) R128(0): 800x600@60Hz
(II) R128(0): 1024x768@60Hz
(II) R128(0): Manufacturer's mask: 0
(II) R128(0): Supported standard timings:
(II) R128(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) R128(0): #1: hsize: 1360  vsize 765  refresh: 60  vid: 49291
(II) R128(0): Supported detailed timing:
(II) R128(0): clock: 85.5 MHz   Image Size:  1600 x 900 mm
(II) R128(0): h_active: 1360  h_sync: 1424  h_sync_end 1536 h_blank_end 1792 h_border: 0
(II) R128(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 795 v_border: 0
(II) R128(0): Monitor name: TOSHIBA-TV
(II) R128(0): Ranges: V min: 59 V max: 61 Hz, H min: 31 H max: 64 kHz, PixClock max 110 MHz
(II) R128(0): Serial No: 000000000
(II) R128(0): EDID (in hex):
(II) R128(0): 	00ffffffffffff005262050201010101
(II) R128(0): 	0116010308a05a782af09da355499b26
(II) R128(0): 	0f474a21080081808bc0010101010101
(II) R128(0): 	010101010101662150b051001b304070
(II) R128(0): 	360040846300001e000000fc00544f53
(II) R128(0): 	484942412d54560a2020000000fd003b
(II) R128(0): 	3d1f400b000a202020202020000000ff
(II) R128(0): 	003030303030303030300a20202000a1
(II) R128(0): EDID vendor "TSB", prod id 517
(II) R128(0): Using EDID range info for horizontal sync
(II) R128(0): Using EDID range info for vertical refresh
(II) R128(0): Printing DDC gathered Modelines:
(II) R128(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
(II) R128(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) R128(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) R128(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) R128(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) R128(0): Modeline "1366x768"x59.8   84.75  1366 1432 1568 1776  768 770 780 798 -hsync +vsync (47.7 kHz)
(==) R128(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) R128(0): I2C bus "DDC" initialized.
(II) R128(0): I2C device "DDC:ddc2" registered at address 0xA0.
(EE) R128(0): No DFP detected
(II) R128(0): <default monitor>: Using hsync range of 31.00-64.00 kHz
(II) R128(0): <default monitor>: Using vrefresh range of 59.00-61.00 Hz
(II) R128(0): <default monitor>: Using maximum pixel clock of 110.00 MHz
(II) R128(0): Estimated virtual size for aspect ratio 1.7778 is 1360x768
(II) R128(0): Clock range:  12.50 to 350.00 MHz
(II) R128(0): Not using default mode "640x350" (vrefresh out of range)
(II) R128(0): Not using default mode "320x175" (vrefresh out of range)
(II) R128(0): Not using default mode "640x400" (vrefresh out of range)
(II) R128(0): Not using default mode "320x200" (vrefresh out of range)
(II) R128(0): Not using default mode "720x400" (vrefresh out of range)
(II) R128(0): Not using default mode "360x200" (vrefresh out of range)
(II) R128(0): Not using default mode "640x480" (vrefresh out of range)
(II) R128(0): Not using default mode "320x240" (vrefresh out of range)
(II) R128(0): Not using default mode "640x480" (vrefresh out of range)
(II) R128(0): Not using default mode "320x240" (vrefresh out of range)
(II) R128(0): Not using default mode "640x480" (vrefresh out of range)
(II) R128(0): Not using default mode "320x240" (vrefresh out of range)
(II) R128(0): Not using default mode "800x600" (vrefresh out of range)
(II) R128(0): Not using default mode "400x300" (vrefresh out of range)
(II) R128(0): Not using default mode "800x600" (vrefresh out of range)
(II) R128(0): Not using default mode "400x300" (vrefresh out of range)
(II) R128(0): Not using default mode "800x600" (vrefresh out of range)
(II) R128(0): Not using default mode "400x300" (vrefresh out of range)
(II) R128(0): Not using default mode "800x600" (vrefresh out of range)
(II) R128(0): Not using default mode "400x300" (vrefresh out of range)
(II) R128(0): Not using default mode "1024x768" (vrefresh out of range)
(II) R128(0): Not using default mode "512x384" (vrefresh out of range)
(II) R128(0): Not using default mode "1024x768" (vrefresh out of range)
(II) R128(0): Not using default mode "512x384" (vrefresh out of range)
(II) R128(0): Not using default mode "1024x768" (vrefresh out of range)
(II) R128(0): Not using default mode "512x384" (vrefresh out of range)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "512x384" (hsync out of range)
(II) R128(0): Not using default mode "1152x864" (height too large for virtual size)
(II) R128(0): Not using default mode "576x432" (hsync out of range)
(II) R128(0): Not using default mode "1280x960" (height too large for virtual size)
(II) R128(0): Not using default mode "1280x960" (height too large for virtual size)
(II) R128(0): Not using default mode "640x480" (hsync out of range)
(II) R128(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) R128(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) R128(0): Not using default mode "640x512" (hsync out of range)
(II) R128(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) R128(0): Not using default mode "640x512" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) R128(0): Not using default mode "896x672" (hsync out of range)
(II) R128(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) R128(0): Not using default mode "896x672" (hsync out of range)
(II) R128(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) R128(0): Not using default mode "928x696" (hsync out of range)
(II) R128(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) R128(0): Not using default mode "928x696" (hsync out of range)
(II) R128(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(II) R128(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(II) R128(0): Not using default mode "832x624" (vrefresh out of range)
(II) R128(0): Not using default mode "416x312" (vrefresh out of range)
(II) R128(0): Not using default mode "1152x864" (height too large for virtual size)
(II) R128(0): Not using default mode "1152x864" (height too large for virtual size)
(II) R128(0): Not using default mode "576x432" (vrefresh out of range)
(II) R128(0): Not using default mode "1152x864" (height too large for virtual size)
(II) R128(0): Not using default mode "576x432" (hsync out of range)
(II) R128(0): Not using default mode "1152x864" (height too large for virtual size)
(II) R128(0): Not using default mode "576x432" (hsync out of range)
(II) R128(0): Not using default mode "1152x864" (height too large for virtual size)
(II) R128(0): Not using default mode "576x432" (hsync out of range)
(II) R128(0): Not using default mode "1152x864" (height too large for virtual size)
(II) R128(0): Not using default mode "576x432" (hsync out of range)
(II) R128(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) R128(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "700x525" (hsync out of range)
(II) R128(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "700x525" (hsync out of range)
(II) R128(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "700x525" (hsync out of range)
(II) R128(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "700x525" (hsync out of range)
(II) R128(0): Not using default mode "1440x900" (width too large for virtual size)
(II) R128(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) R128(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "840x525" (hsync out of range)
(II) R128(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "840x525" (hsync out of range)
(II) R128(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "840x525" (hsync out of range)
(II) R128(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "840x525" (hsync out of range)
(II) R128(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "840x525" (hsync out of range)
(II) R128(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) R128(0): Not using default mode "960x540" (hsync out of range)
(II) R128(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "960x600" (hsync out of range)
(II) R128(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(II) R128(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using driver mode "1280x1024" (height too large for virtual size)
(II) R128(0): Not using driver mode "1366x768" (width too large for virtual size)
(--) R128(0): Virtual size is 1360x768 (pitch 1360)
(**) R128(0): *Driver mode "1360x768": 85.5 MHz, 47.7 kHz, 60.0 Hz
(II) R128(0): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
(**) R128(0): *Default mode "1360x768": 84.8 MHz, 47.7 kHz, 59.8 Hz
(II) R128(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(**) R128(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) R128(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) R128(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) R128(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) R128(0): *Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) R128(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) R128(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) R128(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) R128(0): *Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "640x512"x60.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz)
(**) R128(0): *Default mode "720x450": 53.2 MHz, 55.9 kHz, 59.9 Hz (D)
(II) R128(0): Modeline "720x450"x59.9   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz)
(**) R128(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) R128(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) R128(0): *Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "640x480"x60.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz)
(**) R128(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) R128(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) R128(0): *Default mode "680x384": 36.0 MHz, 47.4 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz)
(**) R128(0): *Default mode "680x384": 42.4 MHz, 47.7 kHz, 59.8 Hz (D)
(II) R128(0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz)
(**) R128(0): *Default mode "576x432": 40.8 MHz, 53.7 kHz, 60.1 Hz (D)
(II) R128(0): Modeline "576x432"x60.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz)
(**) R128(0): *Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
(**) R128(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) R128(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) R128(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) R128(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(**) R128(0): Display dimensions: (1600, 900) mm
(**) R128(0): DPI set to (21, 21)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.2.1
	ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/lib/xorg/modules/libshadowfb.so
(II) Module shadowfb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) R128(0): Page flipping disabled
(!!) R128(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] loaded kernel module for "r128" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) R128(0): [drm] Using the DRM lock SAREA also for drawables.
(II) R128(0): [drm] framebuffer handle = 0xf8000000
(II) R128(0): [drm] added 1 reserved context for kernel
(II) R128(0): X context handle = 0x1
(II) R128(0): [drm] installed DRM signal handler
(II) R128(0): [agp] Mode 0x1f000211 [AGP 0x8086/0x1a30; Card 0x1002/0x5446]
(II) R128(0): [agp] 8192 kB allocated with handle 0x00000001
(II) R128(0): [agp] ring handle = 0xf0000000
(II) R128(0): [agp] Ring mapped at 0xb64f4000
(II) R128(0): [agp] ring read ptr handle = 0xf0101000
(II) R128(0): [agp] Ring read ptr mapped at 0xb7756000
(II) R128(0): [agp] vertex/indirect buffers handle = 0xf0102000
(II) R128(0): [agp] Vertex/indirect buffers mapped at 0xb62f4000
(II) R128(0): [agp] AGP texture map handle = 0xf0302000
(II) R128(0): [agp] AGP Texture map mapped at 0xb5e14000
(II) R128(0): [drm] register handle = 0xff9fc000
(II) R128(0): [dri] Visual configs initialized
(II) R128(0): CCE in BM mode
(II) R128(0): Using 8 MB AGP aperture
(II) R128(0): Using 1 MB for the ring buffer
(II) R128(0): Using 2 MB for vertex/indirect buffers
(II) R128(0): Using 5 MB for AGP textures
(II) R128(0): Memory manager initialized to (0,0) (1360,3084)
(II) R128(0): Reserved area from (0,768) to (1360,770)
(II) R128(0): Largest offscreen area available: 1360 x 2314
(II) R128(0): Reserved back buffer from (0,770) to (1360,1538)
(II) R128(0): Reserved depth buffer from (0,1538) to (1360,2307)
(II) R128(0): Reserved depth span from (0,2306) offset 0xbf6a80
(II) R128(0): Reserved 0 kb for textures at offset 0xffff00
(II) R128(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Dashed Lines
	Setting up tile and stipple cache:
		32 128x128 slots
		7 256x256 slots
(II) R128(0): Acceleration enabled
(==) R128(0): Backing store disabled
(==) R128(0): Silken mouse enabled
(II) R128(0): Using hardware cursor (scanline 9228)
(II) R128(0): Largest offscreen area available: 1360 x 775
(==) R128(0): DPMS enabled
(II) R128(0): [DRI] installation complete
(II) R128(0): [drm] Added 128 16384 byte vertex/indirect buffers
(II) R128(0): [drm] Mapped 128 vertex/indirect buffers
(II) R128(0): [drm] dma control initialized, using IRQ 16
(II) R128(0): Direct rendering enabled
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: drmOpenMinor returns 12
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: Loaded and initialized /usr/lib/dri/r128_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) XKB: reuse xkmfile /var/lib/xkb/server-0C76CA335E924C2441A31FBFED02D59A89874CA6.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device ImExPS/2 Generic Explorer Mouse (/dev/input/event4)
(**) ImExPS/2 Generic Explorer Mouse: Applying InputClass "evdev pointer catchall"
(**) ImExPS/2 Generic Explorer Mouse: always reports core events
(**) ImExPS/2 Generic Explorer Mouse: Device: "/dev/input/event4"
(II) ImExPS/2 Generic Explorer Mouse: Found 9 mouse buttons
(II) ImExPS/2 Generic Explorer Mouse: Found scroll wheel(s)
(II) ImExPS/2 Generic Explorer Mouse: Found relative axes
(II) ImExPS/2 Generic Explorer Mouse: Found x and y relative axes
(II) ImExPS/2 Generic Explorer Mouse: Configuring as mouse
(**) ImExPS/2 Generic Explorer Mouse: YAxisMapping: buttons 4 and 5
(**) ImExPS/2 Generic Explorer Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImExPS/2 Generic Explorer Mouse" (type: MOUSE)
(II) ImExPS/2 Generic Explorer Mouse: initialized for relative axes.
(II) config/udev: Adding input device ImExPS/2 Generic Explorer Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
```

---

### Post by *^kyfds( on 2012-05-01
Oddly enough I'm running on pretty much the same specs as you on 12.04, and it seems to be stable enough for what i use it for.

I'd probably just go for 12.04 as it's an LTS.

no fannying around with upgrading when support ends.

---

### Post by jamesbeat on 2012-05-01
> **Thehumorouscheese said:**
> Oddly enough I'm running on pretty much the same specs as you on 12.04, and it seems to be stable enough for what i use it for.

I'd probably just go for 12.04 as it's an LTS.

no fannying around with upgrading when support ends.


12.04 is working ok with 512mb ram?!
What graphics card do you have?

---

### Post by LillyDragon on 2012-05-01
It works okay on half a GB, usually taking up 300+ megabytes on idle in my experience, even with Xfce. (Might just be from Gnome or KDE libraries loaded in the background.) Still less memory usage than on the Windows Vista install I removed recently, ha!

> **jamesbeat said:**
> So ATI graphics cards are notoriously bad?
Should I buy an old non-ATI card on ebay or something?

lykwydchykyn summed it up nicely. The cards do work great for games on Windows, so they're hardly a bad vendor, but official support isn't quite as good on the 'nix like it is with nVidia, unfortunately. :(

---

### Post by lykwydchykyn on 2012-05-01
> **jamesbeat said:**
> 
Here's the Xorg.0.log:


The log reveals that you're using the r128 driver, and that it's loading DRI and GLX.  So, sadly, this is probably the best performance you're gonna get from this card.  You could possibly tinker around with xorg.conf options, but that's a big hairy mess and unlikely to give you any better performance.


If you get a new card, I'd look for an Nvidia card that's supported by the current Nvidia driver (my experiences with the legacy driver models are pretty negative).  If you look up the nvidia-current package in the repositories, there's a list of supported cards in the description.

A newer ATI card might do just as well also, if it has fglrx driver support.  I'm not really a video card guru, but I've had more reliable experiences with Nvidia and Intel than ATI.

---

### Post by pqwoerituytrueiwoq on 2012-05-01
flash requirements
> [LIST]
[*]**2.33GHz or faster x86-compatible processor, or Intel Atom 1.6GHz or faster processor for netbooks**
[*]Red Hat® Enterprise Linux (RHEL) 5.6 or later (32-bit  and 64-bit), openSUSE® 11.3 or later (32-bit and 64-bit), Ubuntu 10.04  or later (32-bit and 64-bit)
[*]Mozilla Firefox 4.0 or Google Chrome
[*]512MB of RAM; 128MB of graphics memory
[/LIST]
Good luck with YouTube

for that machine i would use Puppy Linux on it

---

### Post by jamesbeat on 2012-05-01
How likely is it that the video card is the problem?
Is there a way of confirming that it is in fact the video card that's slowing things down?
I don't mind spending a little on this project as long as it ends up doing what I need it to, but I don't want to start buying things on the offchance.

---

### Post by lykwydchykyn on 2012-05-01
> **jamesbeat said:**
> How likely is it that the video card is the problem?
Is there a way of confirming that it is in fact the video card that's slowing things down?

Well, other than borrowing a video card and swapping it out, I don't know any way for sure; but if the processor isn't pegging out while watching flash, that's a compelling indicator.

> 
I don't mind spending a little on this project as long as it ends up doing what I need it to, but I don't want to start buying things on the offchance.

I know I've used flash on machines with under 2.33GHz processors.  At least within the last couple years.  

Do you know the video RAM specs on the Rage card?  It can't be more than 64 Mb, I think the Rages were mostly 32 Mb cards (the 128 refers to the GPU design, not the VRAM amount).  

Just a thought -- you could try disabling hardware acceleration in flash.  Just open a page with flash, right-click the flash window, select "settings", and un-check "enable hardware acceleration".  That might actually help it perform better if the graphics card is bad.

---

### Post by jamesbeat on 2012-05-01
I routinely use an old laptop to watch youtube videos and it has a 1.4Ghz processor (celeron I think)

My progress so far is that I have Ubuntu 10.04 installed and working great, my webacm is set up and working perfectly with Skype (after a lot of hair-pulling) and also working at full speed, even in fullscreen.
Video files play flawlessly, again even in fullscreen.
All I need now is for flash to work properly and my project is complete!

I'll try disabling hardware acceleration and report back...

---

### Post by jamesbeat on 2012-05-01
I tried disabling harware acceleration, and it worked to an extent :)
youtube is not perfect, but is definitely watchable now, thanks.

I just made two skype calls to test it out.
The first call was so choppy as to be unusable.
The second call (to the same person) was much better, but still not perfect.
I'm suspecting that the problem was their end, but I won't know for sure until I try calling someone else, but unfortunately they're all asleep because they are in the UK...

---

### Post by jamesbeat on 2012-05-02
Ok, the machine is definitely too slow for skype with this setup :(
I called my sister, and it was unusable; video was a non starter, and audio was horrible.

I used another machine to check, and it worked fine, same internet connection etc.

I monitored the usage of the cpu, memory etc, and it seems that the processor is just too slow.
The memory was only at about 50% during a video call, but the processor just couldn't cope. As soon as I started a call, processor usage shot up to 100% and stayed there.

This guy:
[http://thewichitacomputerguy.com/blog/maximum-cpu-processor-upgrade-dell-dimension-4300](http://thewichitacomputerguy.com/blog/maximum-cpu-processor-upgrade-dell-dimension-4300)
says that you can upgrade the processor in this machine to a P4 2.8Ghz.
I found the exact processor he's talking about on an auction site for $9.99 shipped.
Should I pull the trigger?

One thing that's holding me back is attempting to upgrade the bios.
Apparently I need to do it via a floppy. Does a bootable cd work for this type of thing?

---

### Post by jamesbeat on 2012-05-02
After a bit of research, I decided to take the plunge.
I have a 2.6Ghz processor on the way.
The $10 one was marginally faster at 2.8Ghz, but ships from China, so I decided to pay an extra $3 and take a drop in performance of 200Mhz and buy one from the states, which will arrive a lot sooner.

As an extremely happy side effect of this research, I also discovered that, although Dell's specs say that this machine maxes out at 512Mb memory, it can in fact take 1024Mb!
According to a Dell insider, this was the original published spec, but they reduced it to 512Mb because of a bug in Windows that caused problems with with that much ram!

So soon, I will be the proud owner of a 2.6Ghz, 1024Mb powerhouse ;)
Should only cost me $30 or so in total, and will be capable of everything I need it for.

Thanks for the help guys :)

---

