---
title: "Ubuntu Haywire Edition - details here!"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by adamogardner on 2008-09-13
this is (in a round-a-bout way) a triple posting. My appologies for breaking there but rules but malfunctions prevented me from accessing this room for quite some time so I posted in purple ponies for some redirection.  But now I've made it somehow and am taking this opportunity to spin a new thread.

My resolution and compiz went haywire upon returning from a short trip into a freshly made user acccount.  It was the first alternate user account I ever made and did so for the sake of experience.  right now my resolution is fuzzy and big, and althoough the cube is set and all the effects, nothing works.  What happened  how can I fix please?

---

### Post by starcannon on 2008-09-13
Lets first get some diagnostics:

```
glxinfo | grep direct
```

and lets see what video card you have:

```
sudo lshw -C video
```

GL and have fun

---

### Post by adamogardner on 2008-09-13
here is the information we require.  If it is not to much to ask would you please explain some about how we are accomplishing this?  I am a student and this is a golden opportunity to learn.  

adamogardner@CRONUS:~$ glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
adamogardner@CRONUS:~$ sudo lshw -C video
sudo: unable to resolve host CRONUS
[sudo] password for adamogardner: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: GeForce 8400M GS
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
adamogardner@CRONUS:~$

---

### Post by adamogardner on 2008-09-13
i should note that in trying something new  I opened this session in GNOME rather than the default x-somethingoranother

---

### Post by starcannon on 2008-09-13
You have absolutely know 3d capability at the moment, and getting some very nasty errors on that glxinfo.

I would suggest reinstalling vid card drivers first.

{System>Administration>Hardware Drivers}

---

### Post by adamogardner on 2008-09-13
you were correct in that my nvidia card was unchecked and not in use.  I checked the box and restarted the computer.  I just rechecked and the card is now in use and the box is checked however nothing has changed.  resolution is funny but the resolution settings dialog now offers other option whereas before it offered only the one it was set at.  None of the new ones are 1024 x 780 which is what my resolution is.  Over to you.

---

### Post by starcannon on 2008-09-13
```
sudo apt-get install nvidia-settings
```

after its installed:

Alt-F2

```
gksu nvidia-settings
```

Make your changes using that widget, and I think you'll be golden... if not, post back, the 8400m gs is definitely a viable card, we have one in my wifes HP dv2600 it works like a dream with lots of compiz effects enabled.

---

### Post by adamogardner on 2008-09-13
> **starcannon said:**
> ```
sudo apt-get install nvidia-settings
```

after its installed:

Alt-F2

```
gksu nvidia-settings
```

Make your changes using that widget, and I think you'll be golden... if not, post back, the 8400m gs is definitely a viable card, we have one in my wifes HP dv2600 it works like a dream with lots of compiz effects enabled.

I have the widget:  how does it work and exactly how do I not screw this up?

---

### Post by adamogardner on 2008-09-13
i see where it says the number of my pixels./  it is incorrect.  how do I edit that?

i don't think this works

---

### Post by starcannon on 2008-09-13
Click on the:
{X Server Display Settings}

Click on the:
{Resolution:} Drop Down Menu

Either choose "Auto" or the Resolution you prefer, ten click "Apply", if you don't like what you see, click "Cancel" on the pop up dialog, if you can't see anything at all, then do nothing and in 15 seconds it will auto revert back to your starting resolution.


Be sure to click "Detect Displays" as well it can be handy for letting it set up the timings for you.

Once you have it just right then click "Save to X Configuration".

This tool is an official Nvidia Tool, and it does indeed work, I use it for all of my Nvidia Carded Computers (6 of them, no 2 with same series in it lol, and growing).

GL

---

### Post by adamogardner on 2008-09-13
now it says this: 
 adamogardner@CRONUS:~$ glxinfo | grep direct
direct rendering: Yes
adamogardner@CRONUS:~$ 

of course I don't know what I'm doing but trying to help out.

---

### Post by starcannon on 2008-09-13
Thats good, and means the driver is working, use the 
```
gksu nvidia-settings
```
command that I gave earlier, and the follow up mini guide on how to use the utility, it works fine, and is an official configuration utility from Nvidia themselves. I use it regularly and find it to be very good.

---

### Post by adamogardner on 2008-09-13
> **starcannon said:**
> Thats good, and means the driver is working, use the 
```
gksu nvidia-settings
```
command that I gave earlier, and the follow up mini guide on how to use the utility, it works fine, and is an official configuration utility from Nvidia themselves. I use it regularly and find it to be very good.

what mini guide?  f1 offers no help  there is no way to change settings for the resolution.  all the help button does is tell me what my settings mean.

---

### Post by starcannon on 2008-09-13
> **adamogardner said:**
> what mini guide?  f1 offers no help  there is no way to change settings for the resolution.  all the help button does is tell me what my settings mean.
This is the mini guide here:
[http://ubuntuforums.org/showpost.php?p=5784876&postcount=10](http://ubuntuforums.org/showpost.php?p=5784876&postcount=10)

GL, if that doesn't work keep posting, there are multiple ways to skin this cat.

---

### Post by adamogardner on 2008-09-13
ok  while you were posting I was searching for resolution in gconf=editor i don't know why Iand came up with this:

---

### Post by adamogardner on 2008-09-13
i did exactly that,  placed on auto, hit apply, restart, same thing

---

### Post by starcannon on 2008-09-14
Not sure whats happening there, PM me with a good time to meet, and if you like I could Remote Assist and take a peek at whats happening and see if I can help you sort it out that way.

Hang in there, you've got a great vid card, and it does work splendidly.

---

### Post by adamogardner on 2008-09-14
i fixed the resolution in recovery mode by selecting the xserver option.  now whats the deal with my compiz settings?  I still don't have the cube. also no wobbly windows or anything, even thoough the dialog box exists and myu options are checked.

---

