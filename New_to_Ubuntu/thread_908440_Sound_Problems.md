---
title: "Sound Problems"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by Gonz_91 on 2008-09-02
Hi everyone!

I've recently set up a dual-boot in my laptop, between Ubuntu and Windoze Vista.

After a little learning, I started moving my music over to ubuntu. Then when I start listening... WTF? The sound's really low! So I put it a maximum, and it actually sounds normal, pretty much like my maximum volume in windows, a bit lower, but when I start turning down the volume, before reaching half, I can't hear a thing.

Any ideas?

---

### Post by ibuclaw on 2008-09-02
Are you sure that hardware, as well as software volumes are up to the max?

ie:
   the volume levels in totem and the volume level in the gnome panel.

Regards
Iain

---

### Post by MasterSander on 2008-09-02
yeah you should really check if everything is turned down equally, when I use my shortcut, it also turns down all the other volume bars.

---

### Post by knattlhuber on 2008-09-02
> **Gonz_91 said:**
> Hi everyone!

I've recently set up a dual-boot in my laptop, between Ubuntu and Windoze Vista.

After a little learning, I started moving my music over to ubuntu. Then when I start listening... WTF? The sound's really low! So I put it a maximum, and it actually sounds normal, pretty much like my maximum volume in windows, a bit lower, but when I start turning down the volume, before reaching half, I can't hear a thing.

Any ideas?

```
sudo apt-get update
sudo apt-get install gnome-alsamixer

```

Then start it from Applications > Sound&Video and crank up the sliders

---

### Post by Gonz_91 on 2008-09-02
> **tinivole said:**
> Are you sure that hardware, as well as software volumes are up to the max?

ie:
   the volume levels in totem and the volume level in the gnome panel.

Regards
Iain


Gnome panel? Where do I find that?


That alsamixer thing, it's the menu I get when I double-click the volume control icon sitting on the tray right? It's already at maximum...

---

### Post by knattlhuber on 2008-09-02
> **Gonz_91 said:**
> That alsamixer thing, it's the menu I get when I double-click the volume control icon sitting on the tray right? It's already at maximum...

No, that's different. Install as per above. The gnome-alsamixer has sliders for surround speakers. Once you crank them up, you'll be fine.

---

### Post by Gonz_91 on 2008-09-02
Installed the thing, put everything I could find at maximum.

Still the same :'(

---

### Post by knattlhuber on 2008-09-02
> **Gonz_91 said:**
> Installed the thing, put everything I could find at maximum.

Still the same :'(

That is really weird cos that fix worked for a lot of people using Hardy here in the forum. I'm really sorry.
Do you hear at least some sound or is it completely muted?
Are the devices in System > Prefs > Sound set to 'Autodetect'?
Have you tried changing the sound device by double-clicking the Volume icon and then File > Change Device ?

---

### Post by Gonz_91 on 2008-09-02
Yup, it's on autodetect, and yes, I tried changing the device.

I'm kinda lost, now. I'm basing my question on the fact that in Vista I listen to music comfortably at 6% volume, here I have to use like 70-80% to obtain the same result...

---

### Post by SwordRaven on 2008-09-04
I have noticed the same behaviour, whereas in windows I would normally have the volume sliders at 50% or lower with Ubuntu it seems like there is a complete cutoff at 50% so you have to have the sliders at 80%+ to actually hear what you're playing...

It's all very bizarre but not a problem if you have a speaker set with a volume control that sits on your desk. Not much comfort if you haven't though.

---

### Post by knattlhuber on 2008-09-04
Maybe this guide is helpful to you:

[http://ubuntuforums.org/showthread.php?t=843012]("http://ubuntuforums.org/showthread.php?t=843012")

---

### Post by AutomaticJack on 2008-09-07
I'm having sound issues with MY laptop installation as well (as in NO sound). Has anyone else had that problem? If so... how did it get fixed?

---

### Post by Mariane on 2008-09-10
I had the same problem.

I installed alsamixergui
sudo apt-get install alsamixergui

Then you launch alsamixergui by typing alsamixergui in a terminal

You can either use your mouse on it, or use the arrow keys. 
If some volumes are at minimum you have to use the arrow keys 
because there is nothing for your mouse to grab. 

Right and left arrow navigate between the possibilities
Up and down arrow adjust the sound

There are several possibilities, don't ask me what they all 
stand for. Some are for microphones and setting these up high 
suddenly makes your computer schriek. 

Test as you go along, or put a pillow on your head before 
testing... 

Mariane

---

### Post by santhust on 2008-09-13
oh yes i have found the volume levels inaudible in my laptop dell inspiron 1525. and  i have also tried the solution suggested in this reply: alsa mixer. but it hasn't worked. still the same sound level.

---

### Post by Mariane on 2008-09-14
There is a rather radical way to re-install or rebuild your drivers from scratch, including any configuration files which might be causing the problem: 

Re-install:
sudo apt-get --purge remove linux-sound-base 
sudo apt-get --purge remove alsa-utils
sudo apt-get --purge remove alsa-base 

sudo apt-get install linux-sound-base 
sudo apt-get install alsa-base 
sudo apt-get install alsa-utils

Re-build:
sudo apt-get install module-assistant
sudo module-assistant a-i alsa-source

But I would strongly advise you to wait until someone more qualified than I am tells you it's OK to try these commands. They worked for me but they might not work for you. And I'm perfectly incapable of telling you what to do if after using them you end up with no sound at all. 

Mariane

---

