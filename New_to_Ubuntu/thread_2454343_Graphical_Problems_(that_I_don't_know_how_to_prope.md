---
title: "Graphical Problems (that I don't know how to properly describe)"
date: 2020-11-27
forum: New to Ubuntu
---

### Post by jerryjrowe on 2020-11-27
EDIT TO SAVE TIME FOR PEOPLE:
The name for the craziness we are seeing:  visual artifacts 
It is probably a problem in the video card, likely caused by the driver.


ORIGINAL POST:

I've spent a few hours looking for problems that match mine.
I haven't found a match, so I am posting here.

On occasion, and without warning, my system will seem to crash, and produce purple glitchy visuals like you can see in the attached photos.  (Sadly, screenshots do not work when this problem happens.  If necessary I can try to figure out how to take better pictures, but I figure that those who are knowledgeable will recognize this even with the poor picture quality.)  I cannot find a correlation between the number or kind of programs that are open and when the problem takes place.  It might be hours after turning on my system or only a few minutes.  

The system seems to still detect input, but nothing seems to work. (Keystroke commands don't do anything, but you can see that the system can tell that you're moving the mouse or typing.)

Sometimes, after several seconds, it will crash to a login screen.  
Other times, the system does not seem to recover.

I am not even sure how to describe what is happening.  It isn't screen tearing, although I do sometimes see screen tearing as this graphics-related problem begins to happen (for the first half second or so).

Can anyone help me figure out what is happening, or what to do about it?

---

### Post by CelticWarrior on 2020-11-27
Welcome.

All you describe and show points to hardware failure. Graphics and/or motherboard (likely "and") is defective.

---

### Post by jerryjrowe on 2020-11-27
Oh no.   These are new components.  Thank you for the quick reply.  Is it possible that I just screwed up installation, rather than that they are broken?

---

### Post by CatKiller on 2020-11-27
From your description (can't see the attachments on my phone) it sounds like corruption of the contents of your video memory. It could be caused by a driver doing something that it shouldn't, or by failing hardware.

---

### Post by jerryjrowe on 2020-11-27
Thank you, @CatKiller.

I am using the pre-installed AMD graphics driver.  

Also...I do recall now that everything seemed to be going smoothly until I tried to install a game ("League of Legends", using Lutris). I thought I removed all the changes that were made, but...The problems persist.  
Any idea how I could tell if it is the hardware, or just a driver, or something else?

I am quite sad about the idea of all this brand new hardware failing, and am very appreciative of your help.

---

### Post by jerryjrowe on 2020-11-27
I posted in "New To Ubuntu" with [my problem]("https://ubuntuforums.org/showthread.php?t=2454343"), and within minutes multiple people suggested that it may be hardware failure that is causing my graphical problem.

I am not certain how to verify this, though.

Is there a utility for ascertaining the functionality of a motherboard and / or graphics card?  I don't know where to start, and any help would be appreciated. (These are new components -- less than a month old -- so I certainly hope this is just a driver issue.)

---

### Post by QIII on 2020-11-27
Random, intermittent failures like this are often associated with thermal faults.

Is this a laptop or a desktop?  Is this an APU or a card on the motherboard?  Are your fans working? Any vents blocked?  If a laptop. are you sure it has adequate space underneath and is not sitting on a soft surface and pressing down to cover the vent?

If a driver is not working, the problem conditions will almost always exist from GUI startup and won't go away.

---

### Post by DuckHook on 2020-11-27
> **jerryjrowe said:**
> I posted in "New To Ubuntu" with [my problem]("https://ubuntuforums.org/showthread.php?t=2454343"), and within minutes multiple people suggested that it may be hardware failure that is causing my graphical problem.

I am not certain how to verify this, though.

Is there a utility for ascertaining the functionality of a motherboard and / or graphics card?  I don't know where to start, and any help would be appreciated. (These are new components -- less than a month old -- so I certainly hope this is just a driver issue.)

There is no Swiss Army Knife type of utility. The usual practice is to boot into a LiveUSB for an easy comparison. If the LiveUSB works without problems, then the problem is not hardware.

I note that you have started a separate thread in the Hardware subforum because you are asking a question specifically about HW. This is appropriate. But if the LiveUSB test shows that the problem is not HW, then please post all further questions back in your first thread so as not to confuse helpers and dilute community effort.

---

### Post by jerryjrowe on 2020-11-27
@QIII:

This is a desktop.  
The fans are working on both the CPU and GPU.
None of the vents are blocked.  

I had been using Psensor to monitor the temperature, but...I just realized that this is only showing the CPU.  (It has never gone above 60; usually it's hovering around 35-40.)

It may be that the GPU has been overheating, then?

---

### Post by Yellow Pasque on 2020-11-27
Those are good CPU temps (assuming the 60C was under heavy load).

What kind of GPU is it?
```
glxinfo -B
```

---

### Post by jerryjrowe on 2020-11-27
Thanks!  If I can rule out hardware, I will make sure to mark this as "resolved."

---

### Post by QIII on 2020-11-27
We can't say without a reading, otherwise it's a guess.

I don't know what psensor reports, but lm-sensors reports the temperature from my AMD GPU on *amdgpu-pci-4700*.  That should be the same sensor if psensors reports it.  If you have an APU, you may not have a separate sensor for CPU and GPU.

---

### Post by DuckHook on 2020-11-27
> **jerryjrowe said:**
> Thanks!  If I can rule out hardware, I will make sure to mark this as "resolved."
I note that other forum members have responded to your first thread. In this case, I think it will be more fruitful for you if I merge the two threads together. Therefore, there's no need for you to take further action on this thread.

---

### Post by jerryjrowe on 2020-11-27
@Yellow Pasque:  Here's what I get from that command:

```
name of display: :0
display: :0  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: X.Org (0x1002)
    Device: Radeon RX 570 Series (POLARIS10, DRM 3.35.0, 5.4.0-54-generic, LLVM 10.0.0) (0x67df)
    Version: 20.0.8
    Accelerated: yes
    Video memory: 8192MB
    Unified memory: no
    Preferred profile: core (0x1)
    Max core profile version: 4.6
    Max compat profile version: 4.6
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.2
Memory info (GL_ATI_meminfo):
    VBO free memory - total: 7808 MB, largest block: 7808 MB
    VBO free aux. memory - total: 8161 MB, largest block: 8161 MB
    Texture free memory - total: 7808 MB, largest block: 7808 MB
    Texture free aux. memory - total: 8161 MB, largest block: 8161 MB
    Renderbuffer free memory - total: 7808 MB, largest block: 7808 MB
    Renderbuffer free aux. memory - total: 8161 MB, largest block: 8161 MB
Memory info (GL_NVX_gpu_memory_info):
    Dedicated video memory: 8192 MB
    Total available memory: 16384 MB
    Currently available dedicated video memory: 7808 MB
OpenGL vendor string: X.Org
OpenGL renderer string: Radeon RX 570 Series (POLARIS10, DRM 3.35.0, 5.4.0-54-generic, LLVM 10.0.0)
OpenGL core profile version string: 4.6 (Core Profile) Mesa 20.0.8
OpenGL core profile shading language version string: 4.60
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile

OpenGL version string: 4.6 (Compatibility Profile) Mesa 20.0.8
OpenGL shading language version string: 4.60
OpenGL context flags: (none)
OpenGL profile mask: compatibility profile

OpenGL ES profile version string: OpenGL ES 3.2 Mesa 20.0.8
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20

```

---

### Post by jerryjrowe on 2020-11-27
@QIII:

I just installed "System Profiler and Benchmark" from the Ubuntu Software panel.

It's showing the GPU hovering around 40-45 for all the things I am doing.

So the good news is, I do have a sensor.  Bad news, the culprit is not yet obvious.

---

### Post by QIII on 2020-11-27
Is it a card and are you absolutely sure it is securely and fully seated in the slot?

Have to checked all the cables, including power from the PSU and output cable(s) from the back of the card to the monitor(s)?  Have you switched cables to check it that may be the failure?

---

### Post by jerryjrowe on 2020-11-27
It is definitely a card.

Regarding the cables / seating...
I will start testing cables now. (Which will likely take some time!)

---

### Post by jerryjrowe on 2020-11-27
@QIII:

I checked the cables from the computer to the monitors. (I have 2 identical monitors.)
It seemed that my headset cable was able to pull (ever so slightly) on the DisplayPort, and I think this was why it was doing the 'catastrophic failure' purple fuzzy glitching thing.
I unplugged and re-plugged just in case.

Because this seemed like an obvious possible culprit, I wanted to test before fiddling with the interior wires, and here's what happened:

I opened Discord, Firefox (with YouTube), and ran Godot, where I am struggling to make a game. :)
The temperatures on everything never got close to 60.  (One core was at 50; the other ones were at 35-40, and the GPU was at 40.)

Within a couple of minutes, there was a freeze + screen tearing for 2-3 seconds, and I found myself at a login screen.
This is better than it was before, because it wasn't doing the purple haze thing.

I am about to dive into the interior wires to make sure, but...I thought I should mention this data point.

I also have to say, this is BY FAR the best technical support community I have ever found for anything.
I would distribute high-fives / hugs / thumbs-up as desired to all involved in this thread.

---

### Post by jerryjrowe on 2020-11-27
@QIII:

I checked the internal cables & the seating of the card.

The card is firmly in there, and the cables seem to be as well.  (This is the first computer that I, myself, have assembled, so I may be wrong in my assessment.)

After closing the case & starting back up, I did the same "stress test" I did before, and...no problems as of yet. :)

It may have just been a cable that was getting nudged (by another cable: my headset).  Here's hoping!!

I will keep this thread open a couple of more days; if nothing else happens, I will report that the issue is resolved.  Of course, if problems persist, I will come back and mention that as well.

Thanks to everyone who participated, especially M. QIII!   (Is there a way to give honor / reputation / &c?  You deserve it!)

---

### Post by QIII on 2020-11-27
Don't assume that I deserve any commendations just yet.  :)  While I am convinced that I am a genius (of course!), I'm not (of course!).

If there is a thermal/electrical fault, you may still have it happen again.  It doesn't take much, however, for a cable or card to be ever so slightly out of place.  Often just the jiggle of checking is enough to correct that.  We'll see.

---

### Post by jerryjrowe on 2020-11-30
I'm back!  With more data!

Using the live CD (really a USB drive), I boot and everything works fine while using it.  So well that I am unable to make the problem happen while using it.  
Thus, as per @DuckHook, it may be possible to rule out the hardware.  (Although, while in the LiveCD mode, only one monitor is on.)

I only seem to get the problem after a while of using Godot.

Also...The sensors never go above 50C on any core or the GPU.  However, the problem seems far less frequent than it was before.
Also, input is no longer visible, and the freezes are total---no longer does it kick me to a login screen.
But if YouTube is playing, it continues to play audio, even though you can't see anything on the frozen purple haze screen.

I fear I may have to just do a clean install, but....I'd like to try to avoid that if I can.  Would anyone else have any ideas?

---

### Post by Jocklad on 2020-12-02
I have a similar problem. Brand new amd ryzen build less than two months ago.

This is not confined to Ubuntu I cannot get any Linux distro to install with workable graphics.

And its not a hardware problem Windows 10 pro runs perfect.

Have been trying for weeks to install ubuntu 20.04 lts. Its a no go on amd/radeon.

---

### Post by jerryjrowe on 2020-12-02
@JockLad -- this might help you; I've been fiddling with it for a day now.

[https://github.com/linuxhw/hw-probe](https://github.com/linuxhw/hw-probe)

hw-probe looks at everything on your system and generates a link so that you can share it someplace (like here) with ease.

It uploads stuff about your hardware, but nothing that can link it back to you.  If you have any problems with your hardware, it will let you know and offer new drivers &c.

My personal problem I'm still puzzling through.  I am currently thinking it is 100% to do with Godot, but I am not yet certain.

---

### Post by Jocklad on 2020-12-02
Thanks @[COLOR=#000000]Jerryjrowe Will have a look at that.[/COLOR]

---

### Post by rsteinmetz70112 on 2020-12-04
Just to chime in here. Since this seems to have started with a software install and you haven't found anything wrong with the hardware nor in a live session. 

I had a similar problem, but it was related to specific software - Firefox which would suddenly create a corrupt screen and lock the keyboard and mouse.  
It turned out to be a X11 issue with the graphics driver and a mismatch with the driver version. You might want to run the commands below in a terminal window:
```
sudo apt autoremove
sudo apt autoclean
sudo apt update
sudo ubuntu-drivers devices
```

That last command should list the drivers available and show you the one Ubuntu thinks is best.
You can then install the recommended driver with:
```
sudo ubuntu-drivers install 
```
or
```
sudo apt install <driver package name>
```

Of course I could be wrong.

---

### Post by jerryjrowe on 2020-12-04
I think it may be the drivers, too -- on a clean install of Ubuntu 20.04, it will still happen. 

And I can *make* it happen by letting the screen turn off from inactivity and then try to turn it back on.  So...reproduce-able!  Yay!  The less random this thing is, the better.

Also, I discovered that the name of this effect is "visual artifacts."  
The AskUbuntu forum lets you search with tags, and I found these, if it helps anyone. I am still researching.

[https://askubuntu.com/questions/tagged/visual-artifacts](https://askubuntu.com/questions/tagged/visual-artifacts)

---

### Post by rsteinmetz70112 on 2020-12-04
You might want to look at this article.
[https://linuxconfig.org/amd-radeon-ubuntu-20-04-driver-installation](https://linuxconfig.org/amd-radeon-ubuntu-20-04-driver-installation)

---

