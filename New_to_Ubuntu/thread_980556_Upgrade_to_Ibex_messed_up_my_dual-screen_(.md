---
title: "Upgrade to Ibex messed up my dual-screen :("
date: 2008-11-12
forum: New to Ubuntu
---

### Post by spectrevk on 2008-11-12
So, for a while now I've had Hardy set up to use two screens, one of which is my LCD Television. I had them as separate X screens, which meant that windows couldn't be moved from one screen to the other, and programs which could only have one instance, like Firefox, could only run on one screen at a time. This was fine, since I just watched video files on the TV screen.

Then I upgraded to Ibex. :(

Now I'm unable to open up nautilus windows on the second screen. If I go to the places menu on that screen and try to open anything, the file manager opens up on the other screen, which makes no sense. Mind you, I can open up VLC player on the TV screen just fine, but not nautilus. What gives?

---

### Post by spectrevk on 2008-11-13
bumping, in the hopes that someone knows how to fix this. I checked the prefs for nautilus, found nothing. :(

---

### Post by spectrevk on 2008-11-13
bump

---

### Post by spectrevk on 2008-11-13
bumping again. Is this the wrong forum for this?

---

### Post by spectrevk on 2008-11-14
Hmm...I don't usually have this much trouble tracking down a problem like this. Nobody else had this kind of issue?

---

### Post by spectrevk on 2008-11-22
bump

---

### Post by MunkyJunky on 2008-11-22
I have the same setup, for watching films on my tv, and get the same issue. I can open totem on my tv, and open films in there, but i cant open nautilus. Maybe its an issue with the new version of Gnome? 

What graphics card/drivers are you on? I'm running Nvidia geforce 6600LE with recommended drivers.

---

### Post by Bastes on 2008-11-26
Bump also here.

---

### Post by spectrevk on 2008-12-20
> **MunkyJunky said:**
> I have the same setup, for watching films on my tv, and get the same issue. I can open totem on my tv, and open films in there, but i cant open nautilus. Maybe its an issue with the new version of Gnome? 

What graphics card/drivers are you on? I'm running Nvidia geforce 6600LE with recommended drivers.

I'm pretty sure it's a GNOME issue. I'm using an old GeForce FX 5600/5700 (the box said 5700, it detects as a 5600 in BIOS). Nobody seems to know anything about it, so I just rolled myself back to Hardy Heron and that seems to fix the problem.

---

### Post by Gone fishing on 2008-12-20
I watch films on my TV but I use the NVIDIA X Server Settings and use Twin view. Which I set up using the NVIDIA tool.

I then start the film and then drag it onto the TV screen.

Edit: added screenshot (the film is on the TV)

---

### Post by spectrevk on 2008-12-20
I was using the nvidia-settings tool to set up separate X screens. The problem with Dual View is that it screws up my wallpapers by spanning them across both screens.

That said, there is a workaround in Ibex. If you create a blank folder on the desktop of the second screen, you can access the file manager on the second screen normally, and be able to open files there.

---

### Post by lonelypauly on 2008-12-26
I'm having problems with dual view in Ibex as well.  I have 2 indentical monitors though.  First problem is saving the config in the nvidia glx settings...for some reason it wont let me save the xorg.conf, so everytime i reboot the computer, im back to only one screen being active.  Second problem is that one a few occasions the screen single monitor would blink like crazy just after log in.  It would blink very fast and the system would become unresponsive, I have to reset the computer.  Its not the hardware because XP is on the same machine and it works just fine.  Is there a problem with the Nvidia drivers?  My video card is an NVIDIA 9800 GT.

---

### Post by moredhel on 2008-12-26
> **lonelypauly said:**
> I'm having problems with dual view in Ibex as well.  I have 2 indentical monitors though.  First problem is saving the config in the nvidia glx settings...for some reason it wont let me save the xorg.conf, so everytime i reboot the computer, im back to only one screen being active.  Second problem is that one a few occasions the screen single monitor would blink like crazy just after log in.  It would blink very fast and the system would become unresponsive, I have to reset the computer.  Its not the hardware because XP is on the same machine and it works just fine.  Is there a problem with the Nvidia drivers?  My video card is an NVIDIA 9800 GT.

Make sure you edit your xorg using sudo. Sorry i don't know about the other problems though

---

### Post by lonelypauly on 2008-12-26
Yeah, im aware of that, and I am sure that is why.  There just is no option to save as sudo in the Nvidia setup when launching it from the taskbar.  I guess it doesn't make sense to me how you can open up the Nvidia settings from the preferences menu but not be able to make any changes because after pressing "apply changes" it tells you that its unable to do so...unless I was doing something wrong.  Any ideas on that?  

Thanks

---

### Post by moredhel on 2008-12-26
try typing gksudo nvidia-settings into terminal :)

---

### Post by spectrevk on 2008-12-27
sudo nvidia-settings works as well. It doesn't matter though, since nothing in nvidia-settings actually fixes the problem. If you try to open folders from the panel, it will open them on the main screen only. Hell, I've even had problems opening folders that are ON the screen's desktop; it still opens them in the "main" screen. It's ridiculous.

---

