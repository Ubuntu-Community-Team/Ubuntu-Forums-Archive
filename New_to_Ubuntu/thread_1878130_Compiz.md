---
title: "Compiz?"
date: 2011-11-09
forum: New to Ubuntu
---

### Post by llmunro on 2011-11-09
Hi forum!

I upgraded to 11.10 from 11.04 via the upgrade manager and all seems to be working as it should, with the exception of Compiz.  It doesn't do *anything*, no matter what options I select or deselect. It had worked beautifully in 11.04, so I'm confused as to why it won't work now. Is there any way to get it working in 11.10 or should I leave well enough alone?

Thanks to all.

Best,
Lisa

---

### Post by Silent Warrior on 2011-11-09
I'm pretty sure Unity uses quite a bit of Compiz in full 3D - I hesitate to call it a gigantic Compiz plug-in, but that might serve as a mediocre explanation. What exactly do you mean when you say it doesn't do anything? What are you trying to do? In what utility?

---

### Post by Mark Phelps on 2011-11-09
My own advice is to leave well enough alone, at least, from the standpoint of NOT touching Compiz Configuration Settings Manager (ccsm).  All I did was OPEN that, and it trashed my desktop, forcing me to remove packages, do some clean up, and reinstall packages.

It needs more work before it can be trusted to NOT break stuff in 11.10.

---

### Post by bluexrider on 2011-11-09
Isn't there a Unity checkbox in Compiz that is suppose to enable the comparability?

---

### Post by mc4man on 2011-11-09
> **llmunro said:**
> Hi forum!

I upgraded to 11.10 from 11.04 via the upgrade manager and all seems to be working as it should, with the exception of Compiz.  It doesn't do *anything*, no matter what options I select or deselect. It had worked beautifully in 11.04, so I'm confused as to why it won't work now. Is there any way to get it working in 11.10 or should I leave well enough alone?

Thanks to all.

Best,
Lisa

It's possible you are actually in a unity-2d session instead of a Ubuntu (unity-3d) session

Many ways to tell - this will tell you in an obvious manner
 ```
ps aux |grep unity |grep -v grep
```
If you see unity-2d listings then either you choose unity-2d from the login or there is a 3d support issue
==================================================================
ccsm is fairly safe to use, though never click on "Preferences". Doing so will immediately switch you from the "unity" profile to the "default" profile where the unity plugin is not enabled & some other differences.
Many of the posted methods to recover from that, while they will produce a 'working' unity-3d session are incorrect & overwrought

---

### Post by llmunro on 2011-11-09
Hi, thanks to all for the replies!

The computer works fine with 11.10, but I miss the desktop effects I could achieve with Compiz and 11.04 (wobbly windows, etc.).  I can open CCSM without breaking anything, but checking/unchecking various options produces no results.

So....

```

```lisa@lisa-Samsung:~$ ps aux |grep unity |grep -v grep
lisa      1823  0.6  1.6 461840 65960 ?        Sl   16:36   0:01 unity-2d-launcher
lisa      1824  0.6  1.2 187452 49020 ?        Sl   16:36   0:01 unity-2d-panel
lisa      1936  1.0  0.4 138232 16360 ?        Sl   16:37   0:02 /usr/lib/unity/unity-panel-service
lisa      2346  7.4  1.8 260684 74336 ?        Sl   16:41   0:01 /usr/bin/unity-2d-places
lisa      2366  3.5  0.1  52000  7392 ?        Sl   16:41   0:00 /usr/lib/unity-lens-applications/unity-applications-daemon
lisa      2368  0.3  0.1  61032  4128 ?        Sl   16:41   0:00 /usr/lib/unity-lens-files/unity-files-daemon
lisa      2370  1.0  0.1  62136  6080 ?        Sl   16:41   0:00 /usr/lib/unity-lens-music/unity-music-daemon
lisa      2398  0.1  0.0  58892  2580 ?        Sl   16:41   0:00 /usr/lib/unity-lens-music/unity-musicstore-daemon


So it appears that I am using a 2-D session?  How does one switch to the 3-D version?  I confess that the numerous changes to Ubuntu since 11.04 have left me mighty confused.

Thanks to all.  
Best,
Lisa

---

### Post by grahammechanical on 2011-11-09
Wobbly windows works for me in 11.10. Whereas, in 11.04 it would remove the top panel.

I have not tried any of the other effects but if checking and unchecking the options does not produce any results, then count yourself lucky. From some posts on this forum there are those that have problems.

As for getting Unity 3D at the login screen or greeter click on the cog icon (I think) and select Ubuntu. That is Unity 3D. If the option to select Ubuntu is not there then in Ubuntu 2D run Additional Drivers to activate a proprietary driver (if available) so the 3D will work.

Regards.

---

### Post by mc4man on 2011-11-09
To add to above - if when selecting "Ubuntu" at the login screen you end up back in unity-2d then run this command  & post
```

/usr/lib/nux/unity_support_test -p

```

---

### Post by llmunro on 2011-11-09
Hi, thanks for the suggestions!

I verified that "Ubuntu" (plain, old, vanilla Ubuntu!) was selected at the login screen, but I didn't seem to be ending up with Unity 3D upon log in.

Here's the results :

/usr/lib/nux/unity_support_test -p

lisa@lisa-Samsung:~$ /usr/lib/nux/unity_support_test -p
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Segmentation fault


What does this mean?  What now?

Best to all and thanks for the help!

Lisa

---

### Post by anewguy on 2011-11-09
Here's what I've run into with desktop effects and 11.10:

- nothing says 2d so I assume I'm in 3D

- the output from that last command shows 3D

- installed compiz settings manager

- tried the cube - it disables some other option that includes big desktop, which in turns disables Unity, so that's no good

- tried wobbly Windows - nothing

It really was that simple before.


Admittedly the only thing I used desktop effects for was to tease my Windows die-hard friends, but I still had used it up until 11.10.  This was one of the things I never could get working and why I went back to 10.10 for a while.  I finally gave up, installed 11.10 again and just decided that for some reason there are some things that it would appear are slowly being taken away.  Eye candy is one thing, but I thought some people actually got some kind of use from desktop effects.

That's been my experience, for what it's worth.

Dave ;)

---

### Post by mc4man on 2011-11-09
Post this to show display adapter info
```
sudo lshw -C display
```

---

### Post by llmunro on 2011-11-09
Hi,

Here's what I get:

lisa@lisa-Samsung:~$ sudo lshw -C display
[sudo] password for lisa: 
  *-display UNCLAIMED     
       description: 3D controller
       product: GT218 [GeForce 310M]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:bc000000-bcffffff memory:c0000000-cfffffff memory:be000000-bfffffff ioport:2000(size=128) memory:bd000000-bd07ffff
  *-display
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:fc000000-fc3fffff memory:e0000000-efffffff ioport:1800(size=8)
lisa@lisa-Samsung:~$ 



I confess I'm not sure what any of this means! ;)

Best,
Lisa

---

### Post by llmunro on 2011-11-11
So it seems there's some sort of problem with my computer and Unity 3-D and also with GNOME, as every time I log in, it appears that I'm using the fallback version of either of these.  How would I know if my computer is capable of running either of these?

Thanks much.
Best,
Lisa

---

### Post by mc4man on 2011-11-11
Lisa - 
I've never had a machine with 2 display adapters, nor any with intel so likely can't provide any more of value.

You either have a desktop with intergrated intel graphics & a nvidia card or a laptop with some sort of hybrid or 'optimus' adapter. (I'm guessing  laptop..

So maybe post what what you have, it's likely others with the same or similar can help you. (make & model if possible

What's happening is you are using the intel 915 adapter without drivers supporting 3d , that's why you keep getting the 2d fallbacks
(whether intel 915 can do 3d I have no clue

If you can switch to the nvidia adapter then you should be ok, I can't tell you how to do that for sure. 

Is nvidia-current installed or showing as available in "Additional Drivers" (in unity-2d click on the "Dash Home" icon, type in add, it'll show up.

---

### Post by llmunro on 2011-11-11
Hi,

Thanks for the response.

The laptop in question is a Samsung Q430.  I think it does have some sort of graphics switching thing, but I've always used the Intel driver with Ubuntu without problems.
Here is a link to the specs: [http://www.samsung.com/us/computer/laptops/NP-Q430-JU01US-specs](http://www.samsung.com/us/computer/laptops/NP-Q430-JU01US-specs)

Ironically, when I was using 11.04, I actually had to REMOVE the nvidia driver, as it was causing all sorts of problems and left me unable to enable desktop effects.

nvidia-current appears to be installed when I look in synaptic, although "Additional Drivers" brings up a box that simply tells me that no proprietary drivers are in use, without any options to find/enable other drivers.

So I assume that this means that my laptop is only capable of running the fallback?

Thanks much.
Best,
Lisa

---

### Post by mc4man on 2011-11-11
> nvidia-current appears to be installed when I look in synaptic,
I hate advising on what I don't know but you may want to try completely  removing nvidia-current & restarting

Though before doing so I'd probably take a look in /etc/X11 for an xorg.conf
If there was one & it mentioned nvidia then best to rename 
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

What you could do if possible that may prove informative is boot to a live 11.10 session using a cd or usb. It would be interesting what you got there. (intel or nvidia with nouveau, 2d, 3d or possibly nothing

Or just wait for more possible solutions....

---

### Post by vasa1 on 2011-11-11
> **Mark Phelps said:**
> My own advice is to leave well enough alone, at least, from the standpoint of NOT touching Compiz Configuration Settings Manager (ccsm).  All I did was OPEN that, and it trashed my desktop, forcing me to remove packages, do some clean up, and reinstall packages.

It needs more work before it can be trusted to NOT break stuff in 11.10.

Has that happened on more than one computer? I've noticed that you've posted this observation in several threads.

I have just the one PC running 11.10 and have installed CCSM [after a bit of deliberation]("http://ubuntuforums.org/showthread.php?t=1867501") because I read about it breaking things. Merely installing it has not caused a problem for me. I also used the Unity plug-in to tweak a couple of minor things. And I still don't have a problem. I'm not ever going to go for the "special" effects, though.

I should also point out that my system is minimally "tweaked".

---

### Post by Miljet on 2011-11-11
> nvidia-current appears to be installed when I look in synaptic
Have you tried uninstalling the nvidia-current driver? I have read in several places that just installing the nvidia drivers causes problems, whether or not it is actually in use.

---

### Post by llmunro on 2011-11-14
Well, that was easy!

I decided to try Miljet and mc4man's advice and remove nvidia-current from Synaptic.  If that didn't work, I was prepared to go back to 11.04.

So, I removed it and restarted.

Presto!  I've got all desktop effects back: wobbly windows, transparent menus, etc!

Thanks to all who offered ideas!  :)

Best to all,
Lisa

---

