---
title: "[SOLVED] The best course of action to take..."
date: 2008-06-18
forum: New to Ubuntu
---

### Post by UnWarierMage224 on 2008-06-18
Hi folks, 

I currently have a dualboot system with both ubuntu and windows XP. I'd like some way to be able to access my existing windows partition from within ubuntu, or run windows apps within ubuntu. 

Now, before I get the crap flamed out of me, let me tell you that 
1. I have tried to use WINE. I don't like it. 
2. I have tried the tutorial that bodhi_zazen posted in the forums. It worked, but windows ran very, very slowly - basically unusable. 

The reason I want to run windows is because there are a couple apps I run which WINE does not support, or Ubuntu does not have an equivalent I like (photoshop, digsby, SuperC, PowerDVD - yes, I know about VLC in Ubuntu, but DVD playback is very choppy for me. I like PowerDVD.)

Following questions: 

1. If I follow bodhi's tutorial again, is there a way to increase the responsiveness of windows?

2. Is it better to install windows as a virtual machine within linux? Could I, because I have an Acronis image backup of my windows install, install windows within the linux VM (VMWare server, or equivalent) and then recover my windows installation? I ask this because I've tweaked my windows installation quite heavily and I don't want to have to go through and redo all the tweaks. 

3. What about following this: [http://macrolinz.com/macrolinz/index.php/2006/01/09/physcial-to-virtual/](http://macrolinz.com/macrolinz/index.php/2006/01/09/physcial-to-virtual/) ?

4. Or, is it best to leave the dual boot?

Thanks, 

-'Mage

---

### Post by lisati on 2008-06-18
PowerDVD does have some nice features: occasionally I've burned DVDs where the sound doesn't work on a regular DVD player, but is playable with PowerDVD.

The NTFS-3G tool might be useful for accessing your Windows partitions through Ubuntu - and don't forget to check the "places"->"computer" menu option.

As for alternatives to wine, I recently heard of "playonlinux" but haven't checked it out yet.

---

### Post by sdowney717 on 2008-06-18
install virtualbox 
then install windows inside virtualbox

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by tjwoosta on 2008-06-18
if WINE doesnt do it for you then i would reccomend a virtual windows install

if that doesnt work for you then i recomend just dual booting (its what i do, that way i can still play pc games and use my media center connectivity with xbox on windows)

you can acess files on your windows partiton from ubuntu no problem by simply mounting the ntfs partition

and with windows you can downlaod an ext3 compatibility driver that allows you to access your ubuntu files in windows

as for using windows apps there really is no substitute for a full on dual boot

windows apps will always run best on windows, its just the way it is

---

### Post by UnWarierMage224 on 2008-06-18
Thanks to everyone for the suggestions. 

At this point, I will do as tjwoosta says and keep the 2X boot. 

-'Mage

---

