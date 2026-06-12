---
title: "Installed resolution is too big"
date: 2013-04-26
forum: New to Ubuntu
---

### Post by dedgar on 2013-04-26
I just installed Ubuntu 13.04. The screen resolution as installed is 2560X1600. That is so big I can't even see how to change to a smaller one when I try.
I need 1920X1080 at the most right now. 
How do I change the resolution if I can't see the settings, buttons, etc. on the page to do so?

---

### Post by DuckHook on 2013-04-26
Please provide the following info:

What is your video chip/card? Provide as much hardware info as you can.
Did you install proprietary drivers for it or are you running on the open source drivers?

1. If you can see your mouse pointer, right click to bring up an option menu.
2. Select "Change Desktop Background". We are not interested in the desktop background, but this is a way to get to the system settings app.
3. At top left, click on "All Settings"
4. Click "Displays"
5. Change "Resolution" to your choice. Hopefully, 1920x1080 shows. Otherwise, choose one that is at least small enough for you to see what you are doing.

Resolution should change right away with a dialogue box asking if you want to keep the new resolution. You must answer yes or else system will drop back to its old resolution after a few seconds. See if the new settings hold by doing a reboot.

---

### Post by dedgar on 2013-04-27
The motherboard is an ECS TIGT-I. GPU is Intel GMA 3150.
I have already tried the right click, etc., that you refered to.
The settings area and buttons are so far down to the bottom and right that I can't see them let alone click on anything.
All I see is the pic of a computer screen that would show the different changes to be made and part of the column of background screens. 
That's it.

---

### Post by dedgar on 2013-04-27
I know I can 'grab' the top of the page and drag it back and forth. But that doesn't get me to the buttons to change the resolution.
I haven't installed any drivers. I have only installed Ubuntu.

---

### Post by DuckHook on 2013-04-27
It is possible to move windows around on a desktop without the using the mouse at all.

1. <Alt>+<Space> will bring up the window menu.
2. <m> then selects the "move" option.
3. Arrow keys will then move the window around until you can see the buttons you want.
4. <Enter> will set the window into position and exit out of "move" mode.

See if you can get to the menu you need by using the above navigation process.

I am beginning to think that the problem isn't as simple as setting a new resolution, but let's start with an attempt at the simplest solution first.

Please also tell us your monitor's native resolution and how it is connected--VGA/HDMI/DVI/Displayport?

---

### Post by dedgar on 2013-04-28
Okay, was able to move the window around and there is nothing there for me to change the resolution.
The max/recommended/native/etc. resolution for the monitor I have is 1920X1080.
The motherboard only has VGA output.

---

### Post by dedgar on 2013-04-28
I think I need to install a video driver. I think the one I need is xf86-video-intel-2.21.3
How do I dl/install that driver? I can't even find how to open a terminal to do an 'apt-get'.
As an oh-by-the-way, the computer is now randomly freezing. I have to kill power and restart to get it back.
So more fun in the offing.
I may just say the heck with it and install 12.04 LTS instead to see how it goes.

---

### Post by DuckHook on 2013-04-29
Have looked into your graphics chip more closely. It appears to be a CPU/video combo chip coupled with an Atom CPU made for netbooks. Are you trying to install Ubuntu 13.04 on a netbook? Should have asked at the outset. Because if so, this just won't fly.

Starting at 12.10, Ubuntu is no longer designed to work on light hardware. The 3D eye-candy of Compiz will tax even older standalone video cards with dedicated VRAM to the max. Lightweight combo graphics chips do not stand a chance. This is why Ubuntu split into various flavours, with Lubuntu available for the lightest HW. It continues to be 2D, so small video chips won't wilt under pressure. Installing Ubuntu 12.04 will automatically force Unity into 2D mode for sub-threshold video HW, but you are still unlikely to enjoy the experience. Unity in Ubuntu 13.04 does not even have a 2D mode.

Please provide complete HW specs, or alternatively, if my guesses are correct, download Lubuntu as LiveUSB and give it a spin. If it suits your needs, then it is a far better flavour for HW with your specs and you will actually enjoy the computing experience rather than fighting with it.

BTW, the driver you want to download should already be included on a standard Ubuntu install. However, it only works for i800 level chips or higher and will almost certainly refuse to load for your chip, as it was not designed to work with it.

---

### Post by Yellow Pasque on 2013-04-29
I think the system in question will run Unity okay since the GPU has good 3D acceleration. However, that discussion is kind of irrelevant here IMO. The 2560x1600 problem happened in my Xubuntu VM too..

> BTW, the driver you want to download should already be included on a standard Ubuntu install.
That's true.
> However, it only works for i800 level chips or higher and will almost certainly refuse to load for your chip, as it was not designed to work with it. 
That's false. The standard intel driver will work just fine for GMA3150 (think of it as i965 GPU if you have to). I think you're confusing it with those other terrible "Intel" GPU's that are coupled with Atom's (GMA 500/600, 3600/3650 a.k.a Poulsbo, Cedarview). Those are completely different GPU's that were actually designed by PowerVR. [http://en.wikipedia.org/wiki/Intel_GMA](http://en.wikipedia.org/wiki/Intel_GMA)

---

### Post by Yellow Pasque on 2013-04-29
Okay, now that we have ^that out of the way, I would suggest opening a terminal (Ctrl+Alt+T does that in Unity IIRC) and entering an xrandr command (you probably won't be able to see the terminal, so type carefully:
```
xrandr --addmode VGA1 1920x1080
```

---

### Post by dedgar on 2013-04-29
[TABLE="class: table_style2"]
[TR]
[TD="class: table_style2_l table2_frame1 table_padding table2_title_left, width: 150"]**CPU**
[/TD]
[TD="class: table_style2_l table2_frame2 table_padding content left_middle"]º Onboard Intel Dual Core Atom D510 processor
º DMI 667Mb/s
[/TD]
[/TR]
[TR]
[TD="class: table2_frame3 table_padding table2_title_left, width: 150"]**CHIPSET**[/TD]
[TD="class: table2_frame4 table_padding content left_middle"]º Intel[SUP]®[/SUP] NM10 Express
[/TD]
[/TR]
[TR]
[TD="class: table_style2_l table2_frame1 table_padding table2_title_left, width: 150"]**GRAPHICS**[/TD]
[TD="class: table_style2_l table2_frame2 table_padding content left_middle"]º Integrated Intel[SUP]®[/SUP] Graphics Media Accelerator 3150(GMA3150)
º Integrated DirectX 9 graphics processor
º Max DVMT Graphics Memory up to 384MB
[/TD]
[/TR]
[TR]
[TD="class: table2_frame3 table_padding table2_title_left, width: 150"]**MEMORY**[/TD]
[TD="class: table2_frame4 table_padding content left_middle"]º Single-channel DDR2 memory architecture
º 2 x 240-pin DDR2 DIMM socket support up to 4 GB
º Support DDR2 800/667 DDR2 SDRAM
[/TD]
[/TR]
[/TABLE]

Here's the important stuff about the motherboard/cpu/gpu.

---

### Post by dedgar on 2013-04-29
If I can open a terminal and force it to a screen resolution of 1920X1080, I think I should also be able to force that resolution when Ubuntu loads. Am I wrong in that?
I'm thinking of giving this one more day of attempts and then going with Lubuntu. If that doesn't work then I don't know where to go after that.

---

### Post by DuckHook on 2013-04-29
> **Temüjin said:**
> The standard intel driver will work just fine for GMA3150 (think of it as i965 GPU if you have to). I think you're confusing it with those other terrible "Intel" GPU's that are coupled with Atom's (GMA 500/600, 3600/3650 a.k.a Poulsbo, Cedarview).

Thanks for stepping in Temüjin. It's always nice to have conjecture replaced with real knowledge. I don't run anything with Intel GPUs so was extrapolating from info gleaned through Google and the Intel web site (which doesn't offer the chip detail that you just did).

@dedgar

Based on your system specs, Temüjin is correct: you should be able to run Ubuntu 13.04 just fine. Those are not lightweight specs. What threw me was the reference to an atom processor which just a couple of years ago would have automatically meant a Netbook. These days, there are *dual* atom processors addressing 4GB of RAM, etc, which yields a sort of hybrid-laptop or super-Netbook that breaks all of the old rules. Hard to keep up with progress.

I run Ubuntu 13.04 in a VM as well, and after Temüjin's post, have looked more carefully at the startup display. Sure enough, mine shows 2560 x 1600 as well. This is odd because I don't seem to get the ballooning effect that you have. My VM still starts up in 1024 x 768 mode, though Guest Additions allows me to adjust it to anything I want.

I suspect that it's a bug in 13.04 and may run across all flavours. If Temüjin's xrandr settings don't work, it may be easiest for you to revert to a stable 12.04 install and wait until 13.04 has had the bugs worked out of it. You may even like the stability or 12.04 over the long term and decide to stick with it.

---

### Post by dedgar on 2013-04-29
Tried the xrandr --admode vga1 1920x1080
I get the response of: cannot find output vga1

---

### Post by dedgar on 2013-04-29
I poked around some more and found System Details. That shows the Intel video driver as installed.
I think this now revolves around 'cannot find output vga1'.

---

### Post by DuckHook on 2013-04-29
May be just a few typos that need correcting: *addmode* instead of *admode*, and "VGA-1" instead of "vga1". In Linux, case matters. So, command would be:```
xrandr --addmode VGA-1 1920x1080
```It is usually best to copy and paste these commands to avoid typos. If you get an error that says you don't have proper privileges, you must execute command with "sudo".

VGA-1 may not exist on your system and it could be called something else. Do:```
xrandr -q
```...and post output back to this thread. If your system is a laptop (please clarify if it is), you will see two entries: one for your VGA external monitor, one for your built-in laptop LCD. You must note the exact name of the entry that says something like "VGA-1" and substitute this name verbatim for VGA-1 in the code above. The built-in laptop display might be "LVDS", "DFPx" or "DVI", or something else entirely, but it won't be VGA.

---

### Post by dedgar on 2013-04-29
Responce to the xrandr is:
Screen 0: minimum 320 x 200, current 640 x 480, maximum 32767 x 32767
LVDS1 connected 640x480+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x576       60.0 +
   640x480        59.9* 
VGA1 connected 640x480+0+0 (normal left inverted right x axis y axis) 598mm x 336mm
   1920x1080      60.0 +
   1280x1024      60.0  
   1440x900       59.9  
   1280x800       59.8  
   1152x864       75.0  
   1024x768       70.1     60.0  
   800x600        60.3     56.2  
   640x480        66.7     60.0* 
   720x400        70.1

---

### Post by DuckHook on 2013-04-29
Here is my interpretation of what is happening:

1. Your external device is properly called "VGA1". All caps but no hyphen.
2. Your system is properly seeing both your laptop monitor and your external monitor.
3. Your laptop monitor has a native resolution of 1024 x 576 (so it is a Netbook?) Please confirm this.
4. Your external monitor is sensed as possessing a native resolution of 1920 x 1080.
5. Your OS is trying to display an identical desktop on both monitors at the same time. You probably have both monitors set to "mirror" each other. This is impossible because both monitors are totally different, but the OS tries its best to attempt a logical compromise. Since the only resolution common to both monitors is 640 x 480, this is the resolution that the OS chooses to use.
6. However, since your external monitor is being sensed as 1920 x 1080, the OS has created a 640 x 480 window centred on the larger virtual desktop, and then ballooned it to fill the monitor.
7. The whole 2560 x 1600 resolution is a red herring. Your current problem has nothing to do with that issue.

Hopefully, Temüjin chimes in here because I am nowhere as familiar with Intel Chips as he. If you don't hear from him in time, then it is up to you whether and when you wish to try my solution:

1. You will have to navigate into the "Display" settings as per instructions in previous post.
2. Uncheck the "Mirror Displays" checkbox (in passing, you should note the warning: "may limit resolution options").
3. Click on the graphic representation for "laptop" and move the switch to "off" for this display. **Be sure you are addressing your internal Laptop display and not turning off your external display!**
4. Click on the graphic representation for your external display and make sure "resolution" drop down box is set to 1920 x 1080.
5. Click "Apply"
6. If your external monitor displays properly, agree to accept new configuration.

Hopefully, if my analysis is accurate, this should solve your display resolution issues.

I'm not reprimanding you by any means, but I can't help noting that we could have gotten here much earlier and with far less trouble if you had included much more detail about your system details and physical setup at the start. As it was, such critical details as it being a Netbook, set up as dual display, etc. only became evident from the output of the commands you were asked to run and not from any description.

In future, you will find that when asking for help on this forum or any other, it is much easier on yourself and on any respondent if you paint a complete picture of your hardware and software, and all of the peripherals and attachments you have, along with the steps you have already taken to get where you are. A really good primer when asking for help is [this]("http://ubuntuforums.org/showthread.php?t=1422475") sticky (at the top of the Beginner's forum).

As a final note: I still believe that you will prefer Lubuntu on your Netbook. If you find that Ubuntu is sluggish notwithstanding proper resolution, then I highly encourage you to give Lubuntu a whirl.

---

### Post by dedgar on 2013-04-30
This isn't a laptop nor a netbook. The ECS TIGHT-I motherboard is a Mini-ITX. There is only one output for video via the vga conn. There are no other video out connections on the motherboard. So I don't know how it could find a laptop AND a desktop output.
I'll try those operations tomorrow sometime. But if I remember correctly, the mirrored was already off. I'll check that. 
And I didn't set anything. What I'm seeing is what Ubuntu did on install. We are now trying to correct that.

---

### Post by DuckHook on 2013-04-30
Many apologies for jumping to conclusions. It's the limitations inherent in this form of communication, I suppose.

Okay, things look stranger and stranger.

By all means, pick up on this tomorrow. I will leave you some thoughts and things to try when you do.

 Could there be a hidden LVDS header on your mobo not connected but active all the same? I suppose such conjecture is academic as you just want to get the damned thing working.

1. Did you try out a LiveDVD/USB before installing? If so, how did the video look?
2. Are you willing to download 12.04 and see how a LiveCD runs? I have found that 12.04 is generally much stabler with HW than the newer versions which try to push the envelope.
3. You can try a higher-risk strategy to first disable the LVDS with:```
xrandr --output LVDS1 --off
```
4. Then force VGA into 1920x1080 mode with:```
xrandr --output VGA1 --mode 1920x1080
```
Or alternatively, skip #3 and do #4 first to see if it doesn't simply solve the problem.

---

### Post by dedgar on 2013-04-30
Don't worry about jumping to conclusions. I could have and should have been more precise. And, as you pointed out, listed my hardware and specs.

---

### Post by dedgar on 2013-04-30
It is now running on only one monitor and at 1920x1080 resolution.
Thanks DuckHook. Your xandr suggestions worked. 
BTW, I didn't see the mirrored display option checked when I looked.

Now how do I change this to Solved?

---

### Post by DuckHook on 2013-04-30
Glad it finally worked.

Mark thread solved:

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Since Linux/Ubuntu is a community effort, I was wondering if you would care to report this as a bug to launchpad? There may even be a number of open tickets there because I'm sure that you are not the only one who has run into this bug, in which case, you don't need to open a ticket, but just register that you have experienced the same bug.

---

### Post by wojeda on 2013-04-30
I have been following this thread even though it is not my actual problem per-se but similar. Duck-hook grabbed my attention back there when he speculated that the the res represented was the combination of the two devices put together.

My problem is with a new nvidia card I just got (GTX640), and my upgrade to 13.04. My x11vnc does not work any more. All I see is a huge screen and my desktop sits on a tiny corner. I can't even read the letters let alone control anything. I have tried scaling, forcing geometry, what not. Nothing seems to work.

I had the same thought, for some reason vnc clients (I have tried 4 different ones), see the desktop as huge and is not picking up the actual size of the main server display. By the way, one is a VGA the other is a 1080i TV over HDMI.

The lasterst nvidia drivers v304.88 seem to have the twinview/cloning broken to top it off, so all the TV displays the extension of the VGA and that is what I believe x11vnc is pickin up.

I want to try this xrandr thing as posted here see if it works. Then maybe I can add it to my x11vnc autostart.

---

