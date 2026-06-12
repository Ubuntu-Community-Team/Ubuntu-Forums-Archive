---
title: "Mouse-Generated Visual Artifacts on Desktop"
date: 2020-05-13
forum: New to Ubuntu
---

### Post by cdef on 2020-05-13
Hi all,

I recently installed Ubuntu 20.04 on my Dell Laptop and have noticed weird rectangular visual artifacts when moving my mouse on my desktop. I've had a bit of experience using CentOS as a workstation at my university. I'm comfortable in the shell and can do some scripting in bash, but I've never set up a full Linux desktop on anything bigger than a Raspberry Pi and know very little about how to manage things like graphics and hardware for myself. 

Here's a picture of what I'm dealing with (so sorry it's a phone picture I'll explain):
[ATTACH=CONFIG]285857[/ATTACH]

Continuously moving the mouse generates the artifacts.
There are a few things which remove the artifacts:
- leaving the mouse still for a moment 
- clicking
- key presses
- screen shots/recordings

The last one is the reason I had to take this image my phone, as taking screenshots, even on a delayed timer, would clear the artifacts as well.
Here's my set up, let me know if there's any other info I should include!
Ubuntu Version: Ubuntu 20.04 LTS
GNOME Version: 3.36.1
Memory: 16 GB
Processor: Intel® Core™ i7-8550U CPU @ 1.80GHz × 8 
Graphics: Mesa Intel® UHD Graphics 620 (KBL GT2)
Resolution: 1920 x 1080
Refresh Rate: 60.03 Hz

If anyone has any ideas as to what's happening, please let me know.
Thanks so much! :)

---

### Post by sdsurfer on 2020-05-14
I have recently seen this in a difference environment. I am using an old VGA monitor due to the current work from home situation (long story) and my only way to connect it to the System76 lappie as a second monitor is through a Dell 6000 Universal dock. Immediately on setup (install dock drivers, etc.) I saw this aberration. It would also "hiccup" - the problem would come and go. Fortunately all that was required was a restart. It was somehow related to the way the dock interfaces with the mini USB.

The clue to be derived from this is it is related to graphics hardware or software. Lots of threads on how to collect information on that (which would be helpful to others here,) but a fairly hidden location for graphics configuration is in Software & Updates in the additional drivers tab. In a terminal execute one of the variations of the lshw command, I think the most simple is probably sudo lshw -class display, there are others. Then look at additional drivers, see if anything comes up, and if it seems like it's the correct driver for your hardware. Keep digging. :-D

---

