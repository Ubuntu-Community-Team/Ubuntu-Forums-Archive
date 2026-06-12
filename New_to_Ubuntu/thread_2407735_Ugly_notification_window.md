---
title: "Ugly notification window"
date: 2018-12-08
forum: New to Ubuntu
---

### Post by angisky on 2018-12-08
I installed i3 a while back to mess with it and I ditched it to go back to Unity (I know what you're thinking) but now my notifications all come up as those ugly little square boxes with a terrible hard to read font. I just want the old ones back.

BTW I'm running Ubuntu 16.04.

---

### Post by Frogs Hair on 2018-12-08
You could try the following and logout and in.

```
sudo apt install --reinstall notify-osd
```

---

### Post by angisky on 2018-12-08
> **Frogs Hair said:**
> You could try the following and logout and in.

```
sudo apt install --reinstall notify-osd
```
 That didn't work. I'm gonna start looking through config files.

---

### Post by Frogs Hair on 2018-12-08
Try these as well to remove any I3 leftovers and reinstall the ubuntu-desktop.

```
sudo apt autoremove 
``` ```
sudo apt install --reinstall ubuntu-desktop
```

---

### Post by oldos2er on 2018-12-08
I believe ```
sudo apt remove dunst
``` will work.

---

### Post by angisky on 2018-12-09
> **oldos2er said:**
> I believe ```
sudo apt remove dunst
``` will work.
 That didn't work unfortunately. I did some research and other people have had similar problems switching to different desktop environments. They should make it so in the future each environment uses it's own config files instead of changing the ones that are used by other environments.

I'm just gonna leave it as is for now. Maybe I'll reinstall Ubuntu on this laptop. I might actually use 16.04 until the end of it's support cycle because it's stable and fast on this laptop.

---

### Post by pauljw on 2018-12-10
You know, I see this sort of thing a lot lately.  There's no reason to remove one DE to use another.  A DE is just software, install it and select it at boot time.  I have several DE's installed on my 16.04 Ubuntu.  I prefer xfce4, but I can logout and select Unity and login with no issues.  I also have Mate and a couple others that I don't recall right now, but the point is that you can install as many DE's as you wish and switch between them rather easily.  I find it's when you think you have to remove them that you get in trouble because there can be bits that are shared that get removed leaving another DE without a needed bit.

---

### Post by freemedia2018 on 2018-12-10
> **pauljw said:**
> There's no reason to remove one DE to use another.

Other than possibly saving space and not leaving things installed that you don't want. Still if there's any confusion your advice to leave the old DE installed isn't a bad idea. 

No matter how many libraries are installed, there are only so many ELF binaries to call them. So unless you're using a weird DE that could be run by env python, simply removing the executable attribute (or moving the binary to a disable-bin folder) should be enough to stop these things from running unexpectedly.

Which for the average "I don't want to know how it works" user, is probably better than mucking around tweaking packages.

The one other situation where uninstalling is better-- when you're worried than the next update will bring back the program you disabled via one of these other methods. That's when uninstalling is the only way (short of chattr or removing the network capabilities?) to be sure.

---

### Post by oldos2er on 2018-12-10
Did you reset Ubuntu's notifications too? Might need to.

---

### Post by Ars_Ivci on 2018-12-10
Having an empty partition of 10 GB and installing it with a different user name is also handy if you like to try new distributions.

---

### Post by again? on 2018-12-10
> **angisky said:**
> That didn't work unfortunately. I did some research and other people have had similar problems switching to different desktop environments. They should make it so in the future each environment uses it's own config files instead of changing the ones that are used by other environments.

I'm just gonna leave it as is for now. Maybe I'll reinstall Ubuntu on this laptop. I might actually use 16.04 until the end of it's support cycle because it's stable and fast on this laptop.
Did you log out. 
The dunst daemon will continue to run after removal, until logout.
You may even need to restart to revert to the default notifications.

---

