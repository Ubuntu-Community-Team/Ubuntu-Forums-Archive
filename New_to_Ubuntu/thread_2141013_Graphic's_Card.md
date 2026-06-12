---
title: "Graphic's Card"
date: 2013-05-01
forum: New to Ubuntu
---

### Post by GaaraOrDSand on 2013-05-01
Hello everyone, it's been a while..

I have a question, I've recently updated my graphic's card from a Nvidia 9500GT to a HD7950 Sapphire Dual-X 3GB

I've never had an AMD card before, I've always used Nvidia, and always installed nvidia-settings and all was well, however now I do not know if I'm just using generic drivers and how to install AMD graphic drivers if there are any available.

```
riddlebox@BrainSlug:~$ lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Tahiti PRO [Radeon HD 7950]
```

As I said, I don't know much about AMD but to me that looks like generic drivers, however the card is recognized.

Also please note that I just installed Xubuntu 13.04 just a few minutes ago so it's still a vanilla installation, therefore nothing was tweaked or fiddled with regarding graphic's drivers.

Thanks in advance.

---

### Post by 2F4U on 2013-05-01
If it is a fresh install, the system uses the open source ATI drivers. Did you check built-in hardware drivers application?

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by GaaraOrDSand on 2013-05-01
Wow! Thank you for the very quick reply.

I think I did manage to install the hardware drivers:

> riddlebox@BrainSlug:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7900 Series
OpenGL version string: 4.2.12217 Compatibility Profile Context 12.104

Also in Xubuntu when I go to Settings Manager from the menu on the top-left corner of the screen it shows AMD catalyst control center and AMD catalyst control center (administrative), it wasn't there before.

Does that mean I successfully managed to install the drivers? (Sorry for the noob question)

---

### Post by bogan on 2013-05-01
Hi!, **GaaraOrGSand,**

To check which driver is working, and if correctly for 3D: ```
:lspci -nnk | grep -iA3 vga
/usr/lib/nux/unity_support_test -p # if that does not run, then:
glxinfo | grep -i opengl
```

Chao!, **bogan.**

---

### Post by GaaraOrDSand on 2013-05-02
```
riddlebox@BrainSlug:~$ lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Tahiti PRO [Radeon HD 7950] [1002:679a]
	Subsystem: PC Partner Limited Device [174b:3000]
	Kernel driver in use: fglrx_pci
01:00.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI Tahiti XT HDMI Audio [Radeon HD 7970 Series] [1002:aaa0]

```

I don't know if I did the second line as I should've, however:

```
riddlebox@BrainSlug:~$ /usr/lib/nux/unity_support_test -p
bash: /usr/lib/nux/unity_support_test: No such file or directory

```

```
riddlebox@BrainSlug:~$ glxinfo | grep -i opengl
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7900 Series
OpenGL version string: 4.2.12217 Compatibility Profile Context 12.104
OpenGL shading language version string: 4.20
OpenGL extensions:

```

So.. In poor terms, is it ok?

---

### Post by Bashing-om on 2013-05-02
GaaraOrDSand; Hi !
The out put from the "unity_support_test" is odd.

1. What version of ubuntu are you running ?
2. What is the out put of terminal command:
```
ls -la /usr/lib/nux/unity_support_test
```
3. If your are running "unity" for your desk top, here is my output for comparison to what should be similar:
> sysop1@1204-a:~$ /usr/lib/nux/unity_support_test -p 
OpenGL vendor string:   X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI RV515
OpenGL version string:  2.1 Mesa 8.0.4

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
sysop1@1204-a:~$ 
[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by GaaraOrDSand on 2013-05-03
I'm running xubuntu, sorry I'm so used not to running unity even when I had ubuntu that I totally did not think that that command could possibly be related to Unity.

Please let me know if you need more info or you would like to know some terminal outputs.

EDIT: By the way, I'm running Xubuntu 13.04

---

### Post by BlinkinCat on 2013-05-03
> **Bashing-om said:**
> GaaraOrDSand; Hi !
The out put from the "unity_support_test" is odd.

1. What version of ubuntu are you running ?
2. What is the out put of terminal command:
```
ls -la /usr/lib/nux/unity_support_test
```
3. If your are running "unity" for your desk top, here is my output for comparison to what should be similar:[INDENT=2]
just try'n to help

[/INDENT]

Hi Bashing-om,

I don't think that Unity test command is working anymore - I tried it for a negative response.

All the best - :p


Edit - maybe it's because I'm running Xubuntu too ?

Sorry if I hijacked this thread - OP hasn't had his query answered yet. - :(

---

### Post by Bashing-om on 2013-05-03
GaaraOrDSand; Hey ..

xubuntu explains it all ( I should have looked closer, huh )//..

To your original questions:This is your card info:
> 
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Tahiti PRO [Radeon HD 7950] [1002:679a]
And this is the driver loaded:
> Kernel driver in use: fglrx_pci
This is my open source results:
> sysop1@1204-a:~$  glxinfo | grep -i opengl
OpenGL vendor string: X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI RV515
OpenGL version string: 2.1 Mesa 8.0.4
OpenGL shading language version string: 1.20
OpenGL extensions:
sysop1@1204-a:~$ 


Additional driver info from terminal command:
```
sudo lshw -C display
```

Are you presently experiencing any problems with the proprietary driver ?[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by GaaraOrDSand on 2013-05-04
Well, no I'm not experiencing "problems" so far with the graphic's card so far, I just wanna know if the drivers are installed correctly just to know if I'm using the graphic's card full potential, I spent EURO300 on this, I deserve to use it.. And also when I had the nvidia 9500GT on xubuntu 12.10 I used to play League of Legends with 40 FPS

Due to the new xubuntu release I formatted, and now with the new xubuntu and new graphics' card i'm getting 20 FPS in League of Legends, so I think something is not right, hence the thread on this forum.

Also, in regards to that code given in the previous post to this one: 

```
riddlebox@BrainSlug:~$ sudo lshw -C display
[sudo] password for riddlebox: 
  *-display               
       description: VGA compatible controller
       product: Tahiti PRO [Radeon HD 7950]
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:48 memory:e0000000-efffffff memory:f7c80000-f7cbffff ioport:b000(size=256) memory:f7cc0000-f7cdffff

```

---

### Post by Bashing-om on 2013-05-04
GaaraOrDSand; Good day to you.

Be aware I am far from an expert on graphics drivers. however, I am aware of a few things.
This is my thoughts -> that card should scream. To that end ->
1. What results from:
```
sudo aticonfig --initial
``` As you are running a proprietary driver.
2. What does AMD/ATI web site advise as to the proper driver to use in your instance:
 If you go to ATI:
[http://support.amd.com/us/Pages/AMDSupportHub.aspx](http://support.amd.com/us/Pages/AMDSupportHub.aspx)
And use "autodetect" when you are looking for a Linux Driver, what does it say about your chipset and any suggested driver?
Bear in mind --departing from ubuntu's repository is in my mind a means of last resort. Doing so places the maintenance of your system as your complete responsibility, being aware of what updates break the system and how to repair it.

I remain open to discussion.[INDENT=2]
best regards

[/INDENT]

---

### Post by GaaraOrDSand on 2013-05-06
I thought I already downloaded the graphics? I don't know this is getting really confusing now; this is the command you asked for:

```
riddlebox@BrainSlug:~$ sudo aticonfig --initial
[sudo] password for riddlebox: 
Found fglrx primary device section
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.fglrx-0
```

And here is a pic of what I think is the drivers I installed.

```
http://tinypic.com/r/1zhcw4/5
```

---

### Post by mastablasta on 2013-05-06
> **GaaraOrDSand said:**
> Well, no I'm not experiencing "problems" so far with the graphic's card so far, I just wanna know if the drivers are installed correctly just to know if I'm using the graphic's card full potential, I spent EURO300 on this, I deserve to use it.. And also when I had the nvidia 9500GT on xubuntu 12.10 I used to play League of Legends with 40 FPS

Due to the new xubuntu release I formatted, and now with the new xubuntu and new graphics' card i'm getting 20 FPS in League of Legends, so I think something is not right, hence the thread on this forum.


it seems like you installed the drivers ok.

AMD drivers are not always good in linux. for some cards they work well but for some they are crappy.

next you could try to get AMD beta drivers and install those manually.
it could also be that one of many LOL update made the FPS drop.
it could also be hte issue with Wine version in 13.04.

lately i am not sure what they did but i play it on winxp and after a couple of updates suddenly my FPS is little over 20. never had any lag before (well aside from net lag when servers were slow). anyxway just saiyng it's always an issue when you have these frequent updates for windows games under wine. it could be that somehting is not compatible between 13.04 wine version and LOL.

---

### Post by GaaraOrDSand on 2013-05-07
Thank you mastablasta, from what you are saying it sounds like it's not a problem I could resolve, maybe I should wait it out because I heard LOL on linux is in progress and finally we're gonna have a proper port, hopefully it won't be long.

---

