---
title: "I hate how slow Ubuntu 8.10 is."
date: 2008-11-16
forum: New to Ubuntu
---

### Post by Obero on 2008-11-16
So, this is my problem. I installed Ubuntu 8.10 a few days ago. It was a good install. After that, I went on here and got advice to install repositories, updates, and software to make the transition from Windows to Linux. It was good. But recently, I've found that Ubuntu's been a bit clunky, and ratty at times. I can't specifically nail the coffin on this, but this happens sometimes:

[LIST]
[*]The boot-up is good, fast, normal.
[*]Logging in is good, fast, normal as well.
[*]Then I start opening programs, and it takes a while. It's a crawl to open tabs, and open links at times. Internet stutters rather than being a smooth opening. It's not pleasant at times.
[*]When I close windows, or maximise and minimise them, I can see the black outline of it growing or shrinking. It's like a frame-by-frame of black borders.
[*]Videos and .gif images work but they pause and stutter every once in a while. I have always wait for them to load, and that takes like three to five minutes.
[*]I'm not using Compiz. I've tried desktop effects, but this always happens:

[IMG]http://i34.tinypic.com/2z7pjt1.png[/IMG]
[/LIST]

So, I figured this is probably something in my processes. I go and look, and everything seems kind of normal. It's almost always during Internet use, I should note. Is this not a regular Firefox percentage usage? 

Note: I don't have an image, but I also use Opera frequently (I even name it as my main Internet browser) and I've seen it's percentage usage jump from 6% to 33% at slow times.

Also Note: I've checked my networking, and it says Wired Network: Auto eth0, if that helps.

[IMG]http://i34.tinypic.com/zm17xc.png[/IMG]

Now I come to Ubuntu Forums for help. You guys haven't let me down *yet*, so I figure you guys can help. This is really my number one priority. Do you guys think I might have a virus, then? I haven't gone on any "bad" websites, and I've always known Ubuntu to be basically virus-free.

Here are some of my specs, if you guys need more, I'll be sure to output them from the *Terminal* or software or whatever.

```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Pentium(R) 4 CPU 2.40GHz
stepping	: 7
cpu MHz		: 2400.078
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid
bogomips	: 4800.15
clflush size	: 64
power management:
```
```
MemTotal:       351940 kB
```
```
Filename				Type		Size	Used	Priority
/dev/sda5                               partition	1028120	245260	-1
```

[IMG]http://i37.tinypic.com/2rm9njr.png[/IMG]

I've heard about graphic cards, video cards, drivers, etc. So I did some investigating, and it turns out I have *no* drivers? That's kind of wierd. Would I have to install such or...?

[IMG]http://i33.tinypic.com/20uelnm.png[/IMG]

 We're in a bit of a financial doubt right now, so I can't exactly spit out $90.00 for a new video card or anything like that? I've also heard that you there's some kind of 'restricted NVidia Drivers' update I'm supposed to do and I don't quite remember if I've done that.

Right now, it seems normal but again, it gets clunky then normal clucky then normal, it's irritatingly annoying. Please help, guys. Here's *System Monitor* -> *Resources*, if that helps too:

[IMG]http://i35.tinypic.com/25f7nde.png[/IMG]

Thanks in advance.

---

### Post by spiderbatdad on 2008-11-16
Your system appears to be short of the recommended minimum requirement for RAM...ie, 384...1GB would be better.

Also compiz.real maybe running. Try installing fusion-icon from synaptic and select metacity as your window manager or run --metacity replace &

---

### Post by oldos2er on 2008-11-16
What video card do you have? 

 To enable the Nvidia restricted driver, go to System, Administration, Hardware Drivers.

---

### Post by OutOfReach on 2008-11-16
I think your problem might be your memory. The minimuim is 384MB.
I suggest to either try a lighter alternative or upgrade your ram.

---

### Post by bonfire89 on 2008-11-16
I'm curious about the video card. I am experiencing similar problems as this person, and I believe it to be issues with my intel 940gml card/chipset/whatever (n00b here)

Hardy ran fine.

---

### Post by mirhciulica on 2008-11-16
It's all about RAM and video card. Maybe you don't have nvidia/ati or it hasn't detected it since you don't have any option for hardware driver.
Upgrading RAM would resolve your speed problems!

---

### Post by Obero on 2008-11-16
How would I go about doing this 'lightweight' option? Would that mean not using Ubuntu at all, or...? Upgrading my RAM would be kind of difficult because of my, again, aforementioned financial strain right now.

Also, how do I figure out my video card? What *Terminal* input do I need to get that information?

---

### Post by Mardoct909 on 2008-11-16
"Desktop effects could not be enabled."

Probably means.

"Graphics hardware sucks. Get something better... Or maybe you need drivers for what you have, hmm?"

A lighter option would be Xubuntu or Fluxbuntu. Both are less demanding desktop environments.

---

### Post by kernelhaxor on 2008-11-16
> **Obero said:**
> 

Also, how do I figure out my video card? What *Terminal* input do I need to get that information?

To list all PCI devices, type this in a terminal: 
```

lspci
```

I would suggest trying Xubuntu .. it is Ubuntu but with Xfce desktop environment instead of Gnome

---

### Post by bonfire89 on 2008-11-16
for me it's definitely driver issues



me@meezcomp:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

Would you like to know more? (Y/n) y 

 The vesa driver is not capable of running Compiz, you need to install the
 proper driver for your graphics card. 



I will be plugging away at fixing this and will post back.

---

### Post by Obero on 2008-11-16
> **kernelhaxor said:**
> To list all PCI devices, type this in a terminal: 
```

lspci
```

I would suggest trying Xubuntu .. it is Ubuntu but with Xfce desktop environment instead of Gnome

Alright, so what's your advice after reading this:

```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 651 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

```

---

### Post by Elfy on 2008-11-16
Run ```
lspci
``` to find out what gpu you have.

You can install xubuntu from the desktop

```
sudo aptitude install xubuntu-desktop
```
Once installed it will be available at the login window from Sessions

You could try fluxbox

```
sudo aptitude install fluxbox fluxconf
```

Again access from Sessions on login window

---

### Post by flsantos on 2008-11-16
@ obero your graphic card is a SIS, there is no way you could use compiz.
About the speed, try another window manager, like xfce (xubuntu) or *box.

---

### Post by OutOfReach on 2008-11-16
> **Obero said:**
> How would I go about doing this 'lightweight' option? Would that mean not using Ubuntu at all, or...? Upgrading my RAM would be kind of difficult because of my, again, aforementioned financial strain right now.

Also, how do I figure out my video card? What *Terminal* input do I need to get that information?

Installing a lighter desktop enviroment/window manager such as Xfce, Fluxbox, Openbox, etc... Would reduce memory usage significantly

Of course there's always the option of switching to a lightweight distro.

---

### Post by SonicSteve on 2008-11-16
Sorry to jump in here, but I've tried Ubuntu on systems that have the SIS video chipsets. I'm lumping all SIS video chipsets together because I've never had much sucess with any of them when it comes to desktop effects. 

Your system is using;
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

---

### Post by Obero on 2008-11-16
Alright, the general consensus seems to be to use a lightweight desktop environment. Does that mean I'd have to install all my updates, repositories, software, etc. again because that would be a pain in the butt.

I've heard of something called Envy, to install drivers. Would that help me in my situation?

---

### Post by Mardoct909 on 2008-11-16
No. It's all more or less compatible between any of the desktop environments. Your software and their level of patchedness will be retained... But you might need to fetch some updates for Xfce, but that's no biggie. It'd also be a good idea to remove gnome afterwards for the extra space.

Envy is awesome, but only works with ATI and Nvidia. I also believe that it was said the card simply wasn't good enough to render for compiz-fusion... So no. Sorry.

---

### Post by Obero on 2008-11-16
> **Mardoct909 said:**
> No. It's all more or less compatible between any of the desktop environments. Your software and their level of patchedness will be retained... But you might need to fetch some updates for Xfce, but that's no biggie. It'd also be a good idea to remove gnome afterwards for the extra space.

Envy is awesome, but only works with ATI and Nvidia. I also believe that it was said the card simply wasn't good enough to render for compiz-fusion... So no. Sorry.

OK, it's kind of unfortunate but if the slowness of this environment is annoying and I don't think anything can compensate it. So what desktop environment are you recommending? And how would I go about doing it? What major changes would happen? What would I lack and what would I gain?

---

### Post by sirjoebob on 2008-11-16
I would recommend a lighter window manager or lighter distro. Xubuntu should run MUCH better on that computer. You MAY even be able to get desktop effects working with it.

---

### Post by Mardoct909 on 2008-11-16
I believe the package is called "xubuntu" or "xubuntu-core" or somesuch. I don't have synaptic on this computer to check with.

Install it, logout, change the session type to Xubuntu or Xfce, make it the default if it asks and go ahead.

The difference is everything looks a little different, but it's largely the same thing with a lot of the crap cut out and less eyecandy so it requires less space and resources.

What I've told you doesn't remove Gnome, so you can change the session type back to gnome if you want to, so this is all benign.

---

### Post by Obero on 2008-11-16
> **sirjoebob said:**
> I would recommend a lighter window manager or lighter distro. Xubuntu should run MUCH better on that computer. You MAY even be able to get desktop effects working with it.

Wouldn't that mean a completely new installation though? Is there a way to do it but not that I have to install repositories, updates, software, etc.?

---

### Post by sirjoebob on 2008-11-16
The package is xubuntu-desktop

---

### Post by Mardoct909 on 2008-11-16
See my post.

---

### Post by markharding557 on 2008-11-16
your memory seems unusualy low for a p4 ,performance will improve dramaticaly with more,i note from your specs post it is swapping heavily and not much free memory remains.
your video chip won't run compiz but should be ok otherwise(i have ubuntu on an old p3,512ram,32mb video works ok)

---

### Post by Kenth Soderstrom on 2008-11-16
I've started my installation of 8.10 as well and I'm really experiencing the lack of correct drivers.

Kenth Söderström

---

### Post by Mardoct909 on 2008-11-16
This isn't about a lack of drivers, it's about a lack of hardware. His computer isn't up to scratch for the regular Gnome desktop, so we're helping him get a less intense one.

---

### Post by Obero on 2008-11-16
> **Mardoct909 said:**
> I believe the package is called "xubuntu" or "xubuntu-core" or somesuch. I don't have synaptic on this computer to check with.

Install it, logout, change the session type to Xubuntu or Xfce, make it the default if it asks and go ahead.

The difference is everything looks a little different, but it's largely the same thing with a lot of the crap cut out and less eyecandy so it requires less space and resources.

What I've told you doesn't remove Gnome, so you can change the session type back to gnome if you want to, so this is all benign.

How do you change the session type?

And one of them is called 'xubuntu-desktop' which is probably the one you mean?

---

### Post by Sealbhach on 2008-11-16
At the login screen, there is an option to Select Session, so you pick Xfce Session from the list.

If you want to use Gnome, you select Gnome Session. Xfce is lighter on resources, that's why it's been recommended.


.

---

### Post by Obero on 2008-11-16
> **Sealbhach said:**
> At the login screen, there is an option to Select Session, so you pick Xfce Session from the list.

If you want to use Gnome, you select Gnome Session. Xfce is lighter on resources, that's why it's been recommended.


.

Okay, so I'm on xubuntu now. It doesn't seem all that different but it does seem faster. So how do I go back to Ubuntu? By going through Gnome?

---

### Post by Tom--d on 2008-11-16
> **Obero said:**
> Okay, so I'm on xubuntu now. It doesn't seem all that different but it does seem faster. So how do I go back to Ubuntu? By going through Gnome?

Gnome is the DE for Ubuntu
Xfce is the DE for Xubuntu
KDE is the DE for Kubuntu

These are the 3 main ones. There are others like *box

---

### Post by Sealbhach on 2008-11-16
> **Obero said:**
> Okay, so I'm on xubuntu now. It doesn't seem all that different but it does seem faster. So how do I go back to Ubuntu? By going through Gnome?

If you log out, you can select the Gnome session when you log in again.


.

---

### Post by Scunizi on 2008-11-16
I'm suprised nobody has mentioned this yet.. sometimes the system doesn't pickup the type of card you have.  I've seen it happen with SiS on several occations.  You might try typing this into a terminal.

sudo dpkg-reconfigure -phigh xserver-xorg

This has and should reconfigure your video picking up the video card type and apply the appropriate driver.. disclaimer - your mileage may vary..

---

### Post by halitech on 2008-11-17
I thought with 8.04 and 8.10 you could run
```
sudo xfix
``` instead to set up the video?

---

### Post by Elfy on 2008-11-18
I thought same - in fact I'm under the impression that the old method no longer dealt with video.

---

### Post by chuckyp on 2008-11-18
Yeap he can just run:

```

sudo xfix

```

Installing proper video drivers rather than using vesa would help a bit. You can find out your specific model of video card by using
 ```

$ lspci

```

---

### Post by starcannon on 2008-11-18
> 01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display AdapterI am sorry to say you will get no, zilch, zero, nada, 3d performance out of that video gpu.
You will have to either buy a new video card (I recommend an Nvidia 6600gt or 6800ultra for an agp machine), or convince SiS to build a decent closed source driver for linux, or convince SiS to Open their drivers up so the Linux/gnu community can build one themselves (either way your gonna wait a long time).

get 1 to 2 gb of ram in there too if you can.

GL sorry for your gpu :(

P.S. the best way to install Xubuntu is cleanly, download the Xubuntu liveCD from [http://www.xubuntu.org/](http://www.xubuntu.org/)
Be sure to make a separate /home partition to make mistakes easier to recover from.

---

### Post by edschofield on 2008-11-18
I can confirm that Ubuntu 8.10 is _much_ slower on my 2.4 GHz P4 than either Ubuntu 7.10 or 8.04. Unlike the original poster, I have 1 GB of RAM, and the machine is definitely not swapping. But X is so slow that switching among virtual desktops or windows often takes 5-10 seconds. Top shows that even moving the mouse around the screen causes X to use 10-20% of the CPU. When there are several windows on the screen, moving the mouse around causes X CPU usage to jump to 40-80% and stay there until I stop moving the mouse. [Update: this is with "focus follows mouse". Without focus-follows-mouse, X uses only 20-30% of CPU when moving the mouse around with multiple windows on the screen. Could this be a metacity bug?]

I have an integrated Intel 845G graphics chip. X seems to be recognizing my graphics hardware fine; glxinfo shows that direct rendering is enabled. The following are the errors and warnings from /var/log/Xorg.0.log when X is started without a config file:

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.0.0
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "intel"
...
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 0.0.2
    ABI class: X.Org Video Driver, version 4.1
(EE) open /dev/fb0: No such file or directory
...
(WW) intel(0): Bad V_BIOS checksum
...
(WW) intel(0): Register 0x70024 (PIPEASTAT) changed from 0x80000203 to 0x00000000
(WW) intel(0): PIPEASTAT before: status: FIFO_UNDERRUN VSYNC_INT_STATUS VBLANK_INT_STATUS OREG_UPDATE_STATUS
(WW) intel(0): PIPEASTAT after: status:
...
(==) intel(0): VideoRam: 131072 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(WW) intel(0): Failed to allocate texture space.
(II) intel(0): Tiled allocation failed.
(II) intel(0): Attempting memory allocation with untiled buffers.
(II) intel(0): Untiled allocation successful.

I'll file a bug report and ask the X developers ...

We have 20 of these machines. (Just for reference, X is much more bearable under older versions of Ubuntu and Fedora, and screen redraws with this hardware are very snappy indeed under Windows XP.)

---

### Post by egalvan on 2008-11-18
Regarding RAM...

If your machine uses DDR2, then the upgrade can be dirt-cheap.

A pair of used 256meg sticks should run less than ten dollars.

A pair of used 512meg sticks should not be much more.

A Mom&Pop-type computer repair shop is a good source for used RAM.

A computer club can also give good "shopping" results.

Remember, a bunch of Vista users have been franticly upgrading their RAM.
512meg and 1gig is considered obsolete in the Vista camp.

But DDR is climbing in price.
And DDR3 still hasn't dropped much.
DDR2 is the sweet-spot.

Good luck.

---

### Post by Keen101 on 2008-11-18
RAM is cheap these day's.

upgrade to at least 512mb or maybe more. That should really help.

Otherwise you could install hardy, which is slightly faster.... but only slightly.

---

### Post by halitech on 2008-11-18
if you like the basic way Ubuntu works, you could try pure Debian which works *much* better on low ram systems

[http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

---

### Post by tilen2009 on 2009-01-06
Hi everyone!

Please don't be mad because I stole this topic.
I also have similar problems with Ubuntu 8.10 on my HP laptop. Specs are: AMD 64-bit processor, ATI x1250 graphics card, 2 GB of ram and 120 GB hard disk.
Installation went fine, but everything else is to damn slow.
When I open a window or want to open a program, I must wait at least 20 to 30 seconds.

Does anyone have an idea how could I solve the problem, or would it be better if I installed ultimate edition 2.0, would there be any difference?

Thanks a lot guys!!!

---

### Post by Scunizi on 2009-01-06
I have found that the perception of speed is due in large part to the video drivers.  I can only speak to the nvidia drivers and my last 2 nvidia cards.  I had a 6600 gt agp card that just screamed with whatever nvidia driver was available in the last two distributions (173?).  After a motherboard failure and a rebuild I had an onboard 8200 which ran like molassas on the 173 & 177 driver.  After installing the 180.x driver the system was much faster.  Acceptable but not close enough yet to my old 6600.  For me it's just a waiting game for nvidia to catch up with their linux driver support.

---

### Post by rasdamaan on 2009-01-16
Hey everyone, being a new guy around here I
guess I'm buying the first round of drinks.
What are y'all drinking?

Anyways, I'm in the same boat with the slow
OS situation and have come to the conclusion
that 8.10 is not the OS I want on my mosheen.
So instead of getting more ram or a new video
card, I plan on reverting to 8.04 because it
worked well with my current hardware configuration.

I don't really want to reformat and reinstall the
OS from scratch.  Is there a simple way to
reinstall Hardy without doing reformat?

[img]http://img118.exs.cx/img118/7837/d0kcheers.gif[/img]

---

### Post by 73ckn797 on 2009-01-17
Generally agree with previous postings. Memory and no video acceleration via drivers. Xubuntu may be your best option. Other option is to get memory up to 1 Gig and video running with proper drivers or update video card to at least 256mb capacity. Nvidia probably best chipset to use.

---

### Post by rasdamaan on 2009-01-18
BTT.

Any idea if it's possible to reverse upgrade from 8.10 to 8.04?

[img]http://img118.exs.cx/img118/7837/d0kcheers.gif[/img]

---

### Post by ready4thebreak on 2009-01-18
It sucks to hear what you're going through. Be I will say what you're going through sounds really strange to me. I've run Ubuntu on worse computers than your's with slower processors(same RAM and 512 on one). Old Neoware Server computers and slimline Compaq's. Ubuntu ran great with the different Gnome themes and everything. No special graphic cards, all integrated, so I am a bit surprised that you're having so much issues. 

The main difference in my experience though is that I was using 8.04, which I know was a LTS and recommended for businesses. I would try to downgrade to it and give it a shot. You should be able to do it rather simply. And if not you may just have to reinstall. And that wouldn't be terrible. I will admit that as a fairly new Ubuntu user myself, GET USED TO STARTING FROM STRATCH AND REINSTALLING. It's happened a few times to me but once I truly began to understand how Ubuntu works I haven't had to reinstall but, it will happen. lol. 

Hope all gets worked out. I will look on the downgrade option for you, but I am a bit busy at the moment, so someone else may beat me to the chase.

---

### Post by eilios on 2009-01-18
I can buy 2 gigs of ram for 50 dollars, it increases your speed by SO much. Before I couldn't even run flash games, now I can run anything.

---

### Post by ready4thebreak on 2009-01-18
You're saying that but you're not sure what type of RAM this person has. If they have older DDR(or older) RAM, then upgrading won't be that cheap.

---

### Post by rasdamaan on 2009-01-18
It's a PITA to have to reformat the HD but I guess I'll have to bite the bullet.

Thanks.

[img]http://img118.exs.cx/img118/7837/d0kcheers.gif[/img]

---

### Post by tomitzel on 2009-01-22
deleted

---

