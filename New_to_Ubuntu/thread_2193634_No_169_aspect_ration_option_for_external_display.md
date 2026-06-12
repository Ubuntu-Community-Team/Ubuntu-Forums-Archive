---
title: "No 16:9 aspect ration option for external display"
date: 2013-12-13
forum: New to Ubuntu
---

### Post by aaronnott on 2013-12-13
Greetings fellow Linux users,

Firstly I couldn't find a solution to my current problem, what I am seeking is a 16:9 aspect ratio setting for my Panasonic 32" TV which I have set up as an external monitor. I would prefer to use the mirror setting and have it as my main monitor, but it has currently only got the 1024 x 768 (4:3) setting available... would love to be able to get a 1280 x 800 (16:10) or 16:9 working.

Thank you in advance,

Aaron

---

### Post by DuckHook on 2013-12-13
Hi Aaron and welcome to Ubuntu and the forums.

Please provide much more info:

1. HW specs of computer. Sounds like a laptop. Is it? If so, is the native resolution of laptop monitor 1024x768, 1280x800 or higher? Make, model, CPU, amount of RAM, video chipset, amount of VRAM, is always useful.

2. Please post output of following commands wrapped in ```
 marks (the "#" button at top of *Adv Reply*) back to this thread. Accuracy is critical so it's best to copy and paste into a terminal:[CODE]sudo lshw -C processor -C video
``````
lspci -vnnk | grep -iA13 vga
``````
xrandr
``````
cat /etc/X11/xorg.conf
```...this above command may return nothing, which is also useful info. Then, would like you to download an app from the repositories, run it, and post results of:```
sudo apt-get install read-edid && sudo get-edid | parse-edid
```

3. What is the native resolution of your TV? I assume it's 1920x1080, but if it is 1280x720 or something else altogether, we need to know this info. How is it connected to your laptop? Directly, or through a receiver, or a KVM switch? Is it HDMI to HDMI, or through a DVI converter, or yet another method?

An answer to every question is important. Lots of homework here but it is all needed to understand what's going on with your system.

---

### Post by aaronnott on 2013-12-14
sudo lshw -C processor -C video 
results:

```
aaron@aaron-VGN-CS13G-Q:~$ sudo lshw -C processor -C video
[sudo] password for aaron: 
PCI (sysfs)  
  *-cpu                   
       description: CPU
       product: Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
       vendor: Intel Corp.
       physical id: 7
       bus info: cpu@0
       version: 6.15.13
       serial: 0000-06FD-0000-0000-0000-0000
       slot: N/A
       size: 1GHz
       capacity: 2166MHz
       width: 64 bits
       clock: 166MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm cpufreq
       configuration: id=1
     *-logicalcpu:0
          description: Logical CPU
          physical id: 1.1
          width: 64 bits
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 1.2
          width: 64 bits
          capabilities: logical
  *-display:0
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:46 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:60f0(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:d3400000-d34fffff

```

---

### Post by Bucky Ball on 2013-12-14
Have you installed and tweaked with arandr? It's in the repos.

---

### Post by aaronnott on 2013-12-14
Terminal code: lspci -vnnk | grep -iA13 vga
results:

```

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07) (prog-if 00 [VGA controller])
    Subsystem: Sony Corporation Device [104d:903f]
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 60f0 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915

00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
    Subsystem: Sony Corporation Device [104d:903f]
    Flags: bus master, fast devsel, latency 0
    Memory at d3400000 (64-bit, non-prefetchable) [size=1M]

```

---

### Post by aaronnott on 2013-12-14
Ahhh not yet, not sure where to access it?? Still going through the commands you sent. By the way thanks for your help, don't believe I mentioned that in my initial reply

---

### Post by aaronnott on 2013-12-14
```
Screen 0: minimum 320 x 200, current 2304 x 800, maximum 32767 x 32767
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1024x768+1280+32 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
DP1 disconnected (normal left inverted right x axis y axis)

```

---

### Post by aaronnott on 2013-12-14
Command "cat /etc/X11/xorg.conf" did indeed return no results... will run the app

---

### Post by aaronnott on 2013-12-14
```
sudo apt-get install read-edid && sudo get-edid | parse-edid
[sudo] password for aaron: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  read-edid
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 12.2 kB of archives.
After this operation, 81.9 kB of additional disk space will be used.
Get:1 http://nz.archive.ubuntu.com/ubuntu/ raring/universe read-edid i386 2.0.0-3.1 [12.2 kB]
Fetched 12.2 kB in 5s (2,255 B/s)       
Selecting previously unselected package read-edid.
(Reading database ... 190722 files and directories currently installed.)
Unpacking read-edid (from .../read-edid_2.0.0-3.1_i386.deb) ...
Processing triggers for man-db ...
Setting up read-edid (2.0.0-3.1) ...
parse-edid: parse-edid version 2.0.0
get-edid: get-edid version 2.0.0

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
    Function supported
    Call successful

    VBE version 300
    VBE string at 0x11100 "Intel(r)Cantiga Graphics Chip Accelerated VGA BIOS"

VBE/DDC service about to be called
    Report DDC capabilities

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
    Function supported
    Call successful

    Monitor and video card combination does not support DDC1 transfers
    Monitor and video card combination supports DDC2 transfers
    0 seconds per 128 byte EDID block transfer
    Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
    Read EDID

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
    Function supported
    Call failed

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged
parse-edid: IO error reading EDID

```

---

### Post by aaronnott on 2013-12-14
The TV is a 32" Panasonic Viera Link, running a resolution of 1366 x 768, it's connected to my Sony Vaio laptop via a standard VGA cable, my laptop was built prior to HDMI.. hope that helps

---

### Post by DuckHook on 2013-12-14
Getting late where I am and about to morph back into a pumpkin. Sorry to bail on you tonight but won't be any use to you unless I can actually think straight.

Summary of your problem is as follows:

For some reason&#8212;could be the VGA cable, could be your TV&#8212;your laptop cannot read the info that is usually passed from monitor to video driver that contains resolution capabilities. This info is called EDID. It could be that the EDID chip is only built into your TV's HDMI interface (this was done on some older HDTVs) so although it exists, you can't get the info through the VGA port. Frankly, dunno. But it isn't being read at any rate. If it were, your video chip would read the TV resolution and automatically use it.

Summary of next steps:

Will have to define an xrandr setting that conforms to your TV, then add it to your list of usable resolutions, then create an xorg.conf file, then configure that to send output to TV.

Too much for what's left of my brain cells tonight, so unless a guru steps in, will have to wait till tomorrow. Hope you understand.

DuckHook

---

### Post by aaronnott on 2013-12-14
No problem at all DuckHook, I appreciate the help you have given me thus far, you're making sense of it all in my head too... rest up, and thanks again ;)

---

### Post by Bucky Ball on 2013-12-14
> **Bucky Ball said:**
> Have you installed and tweaked with arandr? It's in the repos.

?

---

### Post by DuckHook on 2013-12-14
> **Bucky Ball said:**
> Have you installed and tweaked with arandr?Hi Bucky Ball,

Trust everything is splendid down under. Re: *arandr*—not sure that it would work in OP's case absent EDID from the balky TV connection. First EDID call worked (likely LVDS1) but second failed (almost certainly VGA1), so *arandr* would have nothing to work on. At least, I don't know how to make it work. If you do know, would really appreciate the education, as it is certainly much easier for all concerned than what follows.> **aaronnott said:**
> ...making sense of it all in my head too...@Aaron:

Before embarking on following complexity, please check your VGA cable. Is it missing any pins? Some cables, especially old ones, tried to skimp by eliminating strands/pins that served no purpose back before EDID became a standard. But EDID uses those missing pin-outs to pass its info to your card. If a complete VGA cable passes the EDID info properly so that it is auto-recognized by your system, then this is far better than the witchcraft that follows.

Assuming that doesn't work, or no other VGA cable, then these are the next steps, all done through terminal. Again, accuracy is critical, so cut and paste:```
cvt 1366 768 60
```...this queries your card and basically asks it "give me the settings I would need if I want to set a resolution of 1366x768 at 60 Hz". Output will look something like:```
$ cvt 1366 768 60
# 1366x768 59.86 Hz (CVT 0.48M3) hsync: 65.35 kHz; pclk: 72.25 MHz
Modeline "1366x768_60.00"   72.25  1366 1372 1398 1400  768 769 771 800 -hsync +vsync
```...yours will be different—it depends on the card. There are two important items: first is the number after "hsync"—in the example: 65.35, which may be needed if we have to define an xorg.conf file. Second are all the numbers after "Modeline"—in the example: 72.25  1366 1372 1398 1400  768 769 771 800. Copy and paste *your* results to a text file. Again, accuracy is super critical so copy and paste if you can. Otherwise, doublecheck carefully if you copy by hand. Next, we define a new mode with:```
xrandr --newmode "1366x768" 72.25  1366 1372 1398 1400  768 769 771 800 -hsync +vsync
```...where you replace the string of numbers after "1366x768" with the output that resulted from your own *cvt* command. Then, we add the new mode to make it available:```
xrandr --addmode VGA1 1366x768
```Now, you can use arandr which will give you a GUI to choose 1366x766 resolution for VGA1 (which is your TV output), or you can finish things off using the command line with:```
xrandr --output VGA1 --mode 1366x768 --rate 60
```If all went well, you should see a flicker and now have proper resolution on your TV. These changes may not be persistent in that they don't survive a reboot. If so, then we will have to further monkey around by creating and configuring an xorg.conf, but let's not anticipate problems until they arise.

Obviously a simple change in VGA cable, if it works, is far preferable to all of these commands. But there you are if you need it. Let us know how it goes.

---

### Post by mpxxuk on 2013-12-14
I had a similar problem with a laptop connected to a TV which I knew only supported 1366x768

Here's what I did:

1.  Find out the mode for the desired display using cvt.  See example below.[INDENT]   $ cvt 1920 1080 60
      1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
      Modeline "1920x1080_60.00" 173.00 1920 2048 2248 2576 1080 1083 1088 1120 -hsync +vsync

(This is only an example).

 [/INDENT]
Then I created a script based on the modeline for the desired resolution

#! /bin/bash

xrandr --newmode "1368x768_60.00"  85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
xrandr --addmode VGA1 1368x768_60.00
xrandr --output VGA1 --mode 1368x768_60.00
# reset
xrandr --auto
# turn off laptop screen
xrandr --output LVDS1 --off

# 1366x768 screen on:
xrandr --output VGA1 --mode 1366x766


I have turned this into an executable script, and only have to click it once when I boot to switch off the laptop screen and start the TV.  It works!

---

### Post by DuckHook on 2013-12-14
It's always good to see members jumping in to help. However, yours are the same instructions that I already gave, except that you assume that modelines are universal whereas they actually change from video chipset to chipset. In other words, your settings likely won't work in OP's equipment. With video, it's important to generalize our advice so that it is broadly applicable rather than assume that what worked on one system will work on all. Also, OP wanted mirrored monitors, though he may wish to reconsider this since his monitors are different resolutions. If the methodology that I laid out works for OP, then the settings unique to his system can be permanently configured into his xorg.conf such that he won't need to invoke a script at all. But let's cross that bridge later.

And it is still best to look into the VGA cable first. Simple solutions always trump complex ones and especially so in this case where this whole kludge would have to be recreated should OP decide to do a pristine install when upgrading (13.10 will only be supported for another 7 months).

---

### Post by aaronnott on 2013-12-14
Good day to you all, thanks a lot for all the input thus far :)

Firstly, I followed the procedure outlined by Duckhook and it did indeed solve the aspect ratio issue (there seems to be no problem with the VGA cable by the way)... but the new configuration did not survive a reboot as you suspected DuckHook, upon restarting the computer I recieved the following message:
[B]
Could not apply the stored configuration for monitors[/B]

could not assign CRTCs to outputs:
Trying modes for CRTC 63
CRTC 63: trying mode 1280x800@60Hz with output at 1280x800@60Hz (pass 0)
    none of the selected modes were compatible with the possible modes:
Trying modes for CRTC 63
CRTC 63: trying mode 1024x768@60Hz with output at 1368x768@60Hz (pass 0)
CRTC 63: trying mode 800x600@60Hz with output at 1368x768@60Hz (pass 0)
CRTC 63: trying mode 800x600@56Hz with output at 1368x768@60Hz (pass 0)
CRTC 63: trying mode 848x480@60Hz with output at 1368x768@60Hz (pass 0)
CRTC 63: trying mode 640x480@60Hz with output at 1368x768@60Hz (pass 0)
CRTC 63: trying mode 1024x768@60Hz with output at 1368x768@60Hz (pass 1)
CRTC 63: trying mode 800x600@60Hz with output at 1368x768@60Hz (pass 1)
CRTC 63: trying mode 800x600@56Hz with output at 1368x768@60Hz (pass 1)
CRTC 63: trying mode 848x480@60Hz with output at 1368x768@60Hz (pass 1)
CRTC 63: trying mode 640x480@60Hz with output at 1368x768@60Hz (pass 1)
Trying modes for CRTC 64
CRTC 64: trying mode 1024x768@60Hz with output at 1368x768@60Hz (pass 0)
CRTC 64: trying mode 800x600@60Hz with output at 1368x768@60Hz (pass 0)
CRTC 64: trying mode 800x600@56Hz with output at 1368x768@60Hz (pass 0)
CRTC 64: trying mode 848x480@60Hz with output at 1368x768@60Hz (pass 0)
CRTC 64: trying mode 640x480@60Hz with output at 1368x768@60Hz (pass 0)
CRTC 64: trying mode 1024x768@60Hz with output at 1368x768@60Hz (pass 1)
CRTC 64: trying mode 800x600@60Hz with output at 1368x768@60Hz (pass 1)
CRTC 64: trying mode 800x600@56Hz with output at 1368x768@60Hz (pass 1)
CRTC 64: trying mode 848x480@60Hz with output at 1368x768@60Hz (pass 1)
CRTC 64: trying mode 640x480@60Hz with output at 1368x768@60Hz (pass 1)

CRTC 63: trying mode 1024x768@60Hz with output at 1280x800@60Hz (pass 0)
CRTC 63: trying mode 800x600@60Hz with output at 1280x800@60Hz (pass 0)
CRTC 63: trying mode 800x600@56Hz with output at 1280x800@60Hz (pass 0)
CRTC 63: trying mode 640x480@60Hz with output at 1280x800@60Hz (pass 0)
CRTC 63: trying mode 1280x800@60Hz with output at 1280x800@60Hz (pass 1)
    none of the selected modes were compatible with the possible modes:
Trying modes for CRTC 63
CRTC 63: trying mode 1024x768@60Hz with output at 1368x768@60Hz (pass 0)
CRTC 63: trying mode 800x600@60Hz with output at 1368x768@60Hz (pass 0)
CRTC 63: trying mode 800x600@56Hz with output at 1368x768@60Hz (pass 0)
CRTC 63: trying mode 848x480@60Hz with output at 1368x768@60Hz (pass 0)
CRTC 63: trying mode 640x480@60Hz with output at 1368x768@60Hz (pass 0)
CRTC 63: trying mode 1024x768@60Hz with output at 1368x768@60Hz (pass 1)
CRTC 63: trying mode 800x600@60Hz with output at 1368x768@60Hz (pass 1)

---

### Post by DuckHook on 2013-12-14
Time to generate your xorg.conf.

This next step takes you out of the comfort zone of the GUI. You won't have access to a browser either, so you may wish to print out the instructions before proceeding. The issue is that you cannot generate an xorg.conf while X is actually running. So you will have to switch into a console, stop X, generate the xorg.conf, and start X again. These are the steps:

Switch to a console by pressing <Ctrl>+<Alt>+<F1> (or <F2>, <F3>...<F6>). Stop lightdm with:```
sudo service lightdm stop
```Generate an xorg.conf with:```
sudo Xorg -configure
```...which creates a file called xorg.conf.new in your /home directory. The rest of your changes can be done in the GUI environment, so just reboot with:```
sudo reboot
```Once you're back in the regular Ubuntu environment, open xorg.conf.new with *gedit* and post all contents of the file back to this thread. Please enclose your output in [CODE] tags (using the "#" button at the top of the Adv Reply box) for easier reading.

---

### Post by mpxxuk on 2013-12-14
A serious case of not fully reading the thread -itis! (My apologies) However I did want to suggest the idea of just creating a desktop script: I tried endlessly to get the desired configuration during boot up and in the end I gave up and just created the executable script, and it works for me-  In just one click of the mouse after boot, everything is configured as I want it.

However, the instructions you have given here for xorg.conf are very clear, and one day when I have an hour or two to spare I will have a go at it.  As a beginner, I am finding that the level of configurability of Linux is infinite, and limited only by one's lack of expertise!

I did find that using two monitors is problematic if the vertical resolutions are different, so I gave up and just switch off the laptop screen when I want to use it through my TV.

---

### Post by aaronnott on 2013-12-14
> **DuckHook said:**
> Time to generate your xorg.conf.

This next step takes you out of the comfort zone of the GUI. You won't have access to a browser either, so you may wish to print out the instructions before proceeding. The issue is that you cannot generate an xorg.conf while X is actually running. So you will have to switch into a console, stop X, generate the xorg.conf, and start X again. These are the steps:

Switch to a console by pressing <Ctrl>+<Alt>+<F1> (or <F2>, <F3>...<F6>). Stop lightdm with:```
sudo service lightdm stop
```Generate an xorg.conf with:```
sudo Xorg -configure
```...which creates a file called xorg.conf.new in your /home directory. The rest of your changes can be done in the GUI environment, so just reboot with:```
sudo reboot
```Once you're back in the regular Ubuntu environment, open xorg.conf.new with *gedit* and post all contents of the file back to this thread. Please enclose your output in [CODE] tags (using the "#" button at the top of the Adv Reply box) for easier reading.

Great, thanks again, unfortunately I won't be near a printer until tomorrow.. so will have to have another go tomorrow night when I arrive home from work. I will also note that in mirror mode it still renders both screens at 4:3 aspect ratio... obviously mirror mode only requires the external monitor to be in the correct ratio. Thanks again, you have been a great help so far  ;)

---

### Post by DuckHook on 2013-12-14
No problem, and apologies not remotely necessary. That's what we do around here... throw ideas against the wall and see what sticks. Your script is a good idea and sometimes the best solution is the path of least resistance. There's a way to automate your script though so that it invokes automatically at login, and there's an even easier hidden config file called .xsession on your /home directory that is designed to do exactly what you wrote your script to do, so you are thinking along the right lines. But the "best" way for general use is through xorg.conf because it will work for all users on a multiuser system, though some people actually don't want this behaviour because, for example, they want a completely different resolution/output scheme when they boot up as XBMC.

At any rate, if interested, I suggest that we wait for Aaron to send us his output. Once we have it, the principles in getting xorg.conf configured properly can be generalized and applied to most other configurations.

Two monitors tend to be problematic only if they are running on two different video cards. Again, once Aaron is up to speed, it will be natural to address that on this thread too.

Cheers!

---

### Post by JKyleOKC on 2013-12-14
> **DuckHook said:**
> The issue is that you cannot generate an xorg.conf while X is actually running. So you will have to switch into a console, stop X, generate the xorg.conf, and start X again.I understand completely what you're doing here -- great work, BTW! However I think there's a much simpler way for the OP to get xorg.conf created without having to go into the unfamiliar territory of the Terminal editors: First, create a file named "xorg.conf.txt" in the home directory, using gedit, mousepad, or any other text editor. This can be done in the familiar surroundings of the GUI. Once the file is created and saved, just one quick command in terminal is needed:```
sudo cp ./xorg.conf.txt /etc/X11/xorg.conf
```Even though I've been using command lines for almost 50 years, starting on time-shared mainframes in 1965, I still use this approach when creating new system files since it gives me a chance to proofread the result before putting it any place that it can actually affect my system's operation!

I'll be quiet now; you're doing a great job and this thread ought to become a sticky since resolution problems are so common.

---

### Post by DuckHook on 2013-12-14
Hi Jim! Great to hear from you again and happy you could drop in. Hope it's way warmer where you are than it is up here.

Actually, your suggested methodology was also my initial thought. I agree that it's always better to avoid the console with new users than to meddle with it. However, in this case, I judged it to be worthwhile because a system-generated xorg.conf may come fully pre-stocked with the OP's system specs like drivers/monitors/etc. Well... if we're lucky, that is... If the config script chokes reading the chipset, etc, we may just end up with a generic xorg.conf so convoluted that we may as well start from scratch, but that's okay too. This just gives us a fighting chance to cut down on some of the grunt work.

The other saving grace is that not much can go wrong on this console maneuver because we really aren't changing any critical files yet. If Aaron loses his way, all he has to do is:```
sudo reboot
```...and he's back to the comfortable GUI—no harm, no foul.

It *would* be useful if there was a way of generating a preconfigured xorg.conf file without having to leave X, but I don't know how to do that. Both NVidia-settings and AMD Catalyst will generate an xorg.conf without even having to log out, so it's clearly possible, but the OP has an Intel chipset and I don't know of any Intel settings manager that will do the same. If others out there know of a method, I for one would love to learn it. This console stuff is one of the reasons that new users often feel Linux to be so intimidating and any way to bypass it will be instantly adopted by me.

---

### Post by aaronnott on 2013-12-17
Hey team, good to see lots of help coming through here, much appreciated... but I am so new to this operating system that I need this following sentence explained in slightly more detail: 
"Once you're back in the regular Ubuntu environment, open xorg.conf.new with *gedit* and post all contents of the file back to this thread."
Basically, what is "xorg.conf.new ....and what is "gedit" ...sorry to be such a novice!

---

### Post by DuckHook on 2013-12-17
*gedit* is the actual technical name of the "text editor" that is bundled with every default Ubuntu installation. You access it through the dash, or you can do <Alt>+<F2> and then launch it by typing:```
gedit
```

"xorg.conf.new" is the file that was/will-be created from the steps given in post #18. As already explained in that post, once created, it will be in your /home directory. By opening *gedit* you can navigate to your /home directory and open it. In Linux, the /home directory is short form for the directory that actually is /home/aaron, so I may have confused you with an incomplete reference.

Again, will not be responding further until proper night's rest.

---

### Post by aaronnott on 2013-12-18
Great thanks, I opened up a 'console' and got as far as it asking me for login? I have password but I have no idea what my login is, don't recall setting up a login as such? Does it have anything to do with the user account under 'administrator'?? .... okay, ignore this post, results coming shortly

---

### Post by aaronnott on 2013-12-18
Okay here's the 'xorg.conf.new file':

```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen1"
    Screen      3  "Screen3" RightOf "Screen2"
    Screen      4  "Screen4" RightOf "Screen3"
    Screen      5  "Screen5" RightOf "Screen4"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor2"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor3"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor4"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor5"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "Backlight"              # <str>
        #Option     "DRI"                    # <str>
        #Option     "ColorKey"               # <i>
        #Option     "VideoKey"               # <i>
        #Option     "Tiling"                 # [<bool>]
        #Option     "LinearFramebuffer"      # [<bool>]
        #Option     "SwapbuffersWait"        # [<bool>]
        #Option     "TripleBuffer"           # [<bool>]
        #Option     "XvPreferOverlay"        # [<bool>]
        #Option     "HotPlug"                # [<bool>]
        #Option     "RelaxedFencing"         # [<bool>]
        #Option     "XvMC"                   # [<bool>]
        #Option     "ZaphodHeads"            # <str>
        #Option     "TearFree"               # [<bool>]
        #Option     "PerCrtcPixmaps"         # [<bool>]
        #Option     "FallbackDebug"          # [<bool>]
        #Option     "DebugFlushBatches"      # [<bool>]
        #Option     "DebugFlushCaches"       # [<bool>]
        #Option     "DebugWait"              # [<bool>]
        #Option     "BufferCache"            # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "Backlight"              # <str>
        #Option     "DRI"                    # <str>
        #Option     "ColorKey"               # <i>
        #Option     "VideoKey"               # <i>
        #Option     "Tiling"                 # [<bool>]
        #Option     "LinearFramebuffer"      # [<bool>]
        #Option     "SwapbuffersWait"        # [<bool>]
        #Option     "TripleBuffer"           # [<bool>]
        #Option     "XvPreferOverlay"        # [<bool>]
        #Option     "HotPlug"                # [<bool>]
        #Option     "RelaxedFencing"         # [<bool>]
        #Option     "XvMC"                   # [<bool>]
        #Option     "ZaphodHeads"            # <str>
        #Option     "TearFree"               # [<bool>]
        #Option     "PerCrtcPixmaps"         # [<bool>]
        #Option     "FallbackDebug"          # [<bool>]
        #Option     "DebugFlushBatches"      # [<bool>]
        #Option     "DebugFlushCaches"       # [<bool>]
        #Option     "DebugWait"              # [<bool>]
        #Option     "BufferCache"            # [<bool>]
    Identifier  "Card1"
    Driver      "intel"
    BusID       "PCI:0:2:1"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "kmsdev"                 # <str>
        #Option     "ShadowFB"               # [<bool>]
    Identifier  "Card2"
    Driver      "modesetting"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "kmsdev"                 # <str>
        #Option     "ShadowFB"               # [<bool>]
    Identifier  "Card3"
    Driver      "modesetting"
    BusID       "PCI:0:2:1"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # <str>
        #Option     "fbdev"                  # <str>
        #Option     "debug"                  # [<bool>]
    Identifier  "Card4"
    Driver      "fbdev"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "DefaultRefresh"         # [<bool>]
        #Option     "ModeSetClearScreen"     # [<bool>]
    Identifier  "Card5"
    Driver      "vesa"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen2"
    Device     "Card2"
    Monitor    "Monitor2"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen3"
    Device     "Card3"
    Monitor    "Monitor3"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen4"
    Device     "Card4"
    Monitor    "Monitor4"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen5"
    Device     "Card5"
    Monitor    "Monitor5"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

---

### Post by newb85 on 2013-12-18
Prior to HDMI probably means the laptop itself isn't widescreen.   You can't mirror displays if they're different ratios without distorting one of them.   Are you sure you want to mirror them?

---

### Post by aaronnott on 2013-12-18
> **newb85 said:**
> Prior to HDMI probably means the laptop itself isn't widescreen.   You can't mirror displays if they're different ratios without distorting one of them.   Are you sure you want to mirror them?

The laptop is not that old dude ...It's a Sony Vaio, one model prior to HDMI, resolution '1280 x 800 (16:10)' ;)

---

### Post by Bucky Ball on 2013-12-18
> **aaronnott said:**
> The laptop is not that old dude ...It's a Sony Vaio, one model prior to HDMI, resolution '1280 x 800 (16:10)' ;)

Either way, still different ratios so same applies.

---

### Post by DuckHook on 2013-12-18
We are almost there.

The xorg.conf.new file that you generated may look arcane and convoluted, but it actually contains mostly superfluous stuff that we can delete. Before doing so, it is important to understand the role that xorg.conf plays in your GUI.

Starting around Ubuntu 9.10 or so, X actually stopped using an xorg.conf file. X settings were split up into a number of different files deeper within the /etc/X11 tree. This is why you were unable to find an xorg.conf file in your post #8. However, if an xorg.conf file is created manually, then any of the settings within xorg.conf will override the external X settings, and xorg.conf takes precedence. This means that by creating an xorg.conf we are at liberty to define only the settings that we want and leave alone any other settings that are already working.

Our intent is to edit your newly created xorg.conf.new, change its name to xorg.conf and move it into the /etc/X11 directory so that the next time you boot up, you will be using its customized settings. So:

1. Since your keyboard and mouse are working, we can delete anything having to do with input devices like keyboards and mice,
2. We can delete all extraneous drivers,
3. We can delete all extraneous card interfaces that are not connected to anything,
4. We can delete all extraneous monitors,
5. We don't need to define a BusID since the system is clearly already outputting to both monitors, so we can delete this,
6. We can clean up the display options so that they are compact and more readable.

Subtracting all the unnecessary stuff, we end up with a skeletal, clean, not-yet-usable xorg.conf but one ready for us to populate, that looks like this:```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
    Identifier  "Card0"
    Driver      "intel"
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
EndSection
```

First things first. We no longer need the former xorg.conf.new that was created. It has done it's job, we now have our template, and its continued presence will only confuse us. Let's get rid of it with:```
rm ~/xorg.conf.new
```Then Let's open *gedit* and create a new document. Save it as *xorg.conf*. Remember which directory you save it to. I strongly recommend saving it to your /home/aaron directory. Now to populate it with the settings specific to you. These can be taken from your prior efforts in post #3 to #10. I will leave it as an exercise for the reader to compare what that output was and where it is going in the following xorg.conf:```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "0-VGA1"
    VendorName   "Panasonic"
    ModelName    "Viera"
    Modeline     "1366x768" xxx  1366 xxxx xxxx xxxx   768 xxx xxx xxx   -HSync +Vsync
    Option       "PreferredMode" "1366x768"
    Option       "TargetRefresh" "60"
    Option       "Position" "0 0"
EndSection

Section "Monitor"
    Identifier   "0-LVDS1"
    VendorName   "Sony"
    ModelName    "Vaio"
    Option       "PreferredMode" "1280x800"
    Option       "TargetRefresh" "60"
    Option       "Position" "1366 0"
EndSection

Section "Device"
    Identifier  "Intel Mobile 4 Graphics"
    Driver      "intel"
    Option    "Monitor-VGA1"  "0-VGA1"
    Option    "Monitor-LVDS1" "0-LVDS1"
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
    Subsection "Display"
        Viewport   0 0
        Virtual   2646 800
        Depth     24
    EndSubSection
EndSection
```**IMPORTANT** You cannot just start using these settings as your xorg.conf. You must also exchange the modeline information that you generated using the cvt command in post #14. I asked you to copy that information down at the time and it is the same info that must be used to replace the "xxxx xxxx..." placeholders in my above template. Accuracy when dealing with config files is extremely important. One typo will wreck a config file. I do not have the same setup as yours so was not able to test it out.

Once you've copied my contents into an empty file using *gedit*, saved it to your /home/aaron directory as "xorg.conf", filled in the modeline information carefully, and doublechecked your work, do:```
sudo mv ~/xorg.conf /etc/X11/
```Before rebooting, it is important that you know how to switch to a console (just like you did to generate the xorg.conf.new file) in case the new xorg.conf file borks your GUI and you have to fix it using the console. You must be comfortable with this procedure before rebooting.

Should the new xorg.conf actually hang your GUI after reboot, just <Ctrl>+<Alt>+<F1> to a console, and rename it to something harmless with:```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.old
``````
sudo reboot
```... and you should be back to your current state.

**ALERT** Like others here have already pointed out, you must seriously reconsider trying to mirror these displays. They have incompatible resolutions and will only display at the highest resolution that is common to both displays, which would appear to be 1024x768. I have taken the liberty of setting your display up side-by-side: with the TV as the "left" display and your laptop monitor as the "right" one. If you do not like this setup, we will either have to tweak the xorg.conf further, or delete those references from xorg.conf altogether and allow something like *display manager* or *arandr* to configure the displays to your liking.

Reboot and tell us if it works.

---

### Post by aaronnott on 2013-12-20
Just checking in to let ya know that I haven't had a chance to implement the changes yet... and to also let you know that my laptop display is always left of the Panasonic display .... hate to say it, but when I boot up with windows (it's a duel boot machine still, unfortunately, hence why I am here), I get about 8 different resolution options for Panasonic in extended mode, and when I mirror displays they both appear in 1024x768 ..the basic reason for mirroring is because in some cases I have stashed the laptop under my desk and used the panasonic as the main display

---

