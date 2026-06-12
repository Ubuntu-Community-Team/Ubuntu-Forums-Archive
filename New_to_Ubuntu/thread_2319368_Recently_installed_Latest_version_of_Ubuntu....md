---
title: "Recently installed Latest version of Ubuntu..."
date: 2016-04-03
forum: New to Ubuntu
---

### Post by armon2 on 2016-04-03
Hi, I just got Ubuntu for my laptop. An envy notebook with i 7 processor and 16 gb of ram. Very good pc, however, when i open more than5 or 6 tabs in mozilla I sometimes get a lag, and its hard to close the tabs without it freezing up. Also, at one point I couldn't type smoothly, it would be really laggy. I had to completely quit out of mozilla. Then reopen it for it to go back to normal. Why is it so bugg/laggy??? I haven't done anything challenging on my pc yet...

---

### Post by deadflowr on 2016-04-03
What does latest refer to?
And what is the gpu in use?

---

### Post by armon2 on 2016-04-03
14.04.4 and I am not sure. How do I figure out my GPU usage?? (i am a real noob)

Also, as a sidenote...Theres like virtually no files in my .wine  I tried to find my directory for world of warcraft and theres no sign of it anywhere...I cant find wow.exe even when i press cntrl H to show hidden files

---

### Post by yancek on 2016-04-03
What is the "latest" you are referring to?  If you mean 16.04, it hasn't reached final release point as is still beta.  If you installed it then you have volunteered to test it for Canonical/Ubuntu and you should be notifying them of the problems you are having so they are aware and can make changes needed before final release.  I've never used any beta releases but there must be some process to notify the developers.

---

### Post by deadflowr on 2016-04-03
If you can open up a terminal (press ctrl + alt + T)
And post the output from:
```
lspci | grep VGA
```
Or more nuanced:
```
sudo lshw -C display
```
Note the second command requires a password ala the sudo command.
The password field will be invisible, so do not worry about it not showing what you type.

---

### Post by armon2 on 2016-04-03
Trying to show you a screenshot of it using imagemagic, but that wont launch...I feel like either im completely inept or something isnt right with my ubuntu.

---

### Post by deadflowr on 2016-04-03
> **armon2 said:**
> Trying to show you a screenshot of it using imagemagic, but that wont launch...I feel like either im completely inept or something isnt right with my ubuntu.
Could you simply copy the output from the terminal and paste it in the thread?
(Or are you trying to work through the issues via a second PC?)

---

### Post by armon2 on 2016-04-03
sure here you go, but do you know why imagemagick isnt working either... I just reinstalled it on the terminal and whenever I try and open the app it just doesnt open.... 
 
Here you go  
  
 
*-display               
       description: VGA compatible controller
       product: Broadwell-U Integrated Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:c2000000-c2ffffff memory:d0000000-dfffffff ioport:5000(size=64)
  *-display UNCLAIMED
       description: 3D controller
       product: GM108M [GeForce 940M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:c3000000-c3ffffff memory:b0000000-bfffffff memory:c0000000-c1ffffff ioport:3000(size=128)

---

### Post by armon2 on 2016-04-03
I am beginning to wonder if I should reinstall ubuntu =/ I cant find my files for world of warcraft in the .wine section, theres really not much there either. It is very strange to me. I may be just a complete noob. But believe me, im trying hard to figure it out through online research ATM 
 
 
Well i fixed finding imagemagick...I just typed in display imagemagick on the command line lmao..but sitll no wow directory files

---

### Post by grahammechanical on 2016-04-03
I no longer have wine installed so I cannot check this as a fact, but I do not think that .wine is where wine stores the Windows .exe files that we install through wine. If you open the Dash and type wine in the "Search your computer" panel you should see 3 or 4 wine utilities. I think that one of them is called C:/Drive. Anyway, there is a wine utility that looks and works like Windows Explorer and you can use that to browse through that old familiar Windows file structure that wine uses.

By the way, if applications are crashing when loading it indicates that something is mightily wrong with the OS.

Regards

---

### Post by Geoffrey_Arndt on 2016-04-03
Just a few questions:

>  Did you install the nVidia drivers?
>  Do you watch a lot of video using Flash?
>  What Browser are you running?  Chrome or Firefox or other?
>  Do you have straight-up Wine installed, or did you get the more user friendly front-end "Play-on-Linux" . . ?

The slow down/semi-freeze state you're describing is more typically caused by improper Flash design or rendering due to a number of factors - often the side-content (spam ads) etc. of certain malformed html/js sites.

If you're doing a lot of video, perhaps Chrome would work out better, as it has the latest Flash vs Firefox in Linux which does not (without tweaks).

PS:   I use Firefox, but have set the Flash plugin to require permission to run.

---

