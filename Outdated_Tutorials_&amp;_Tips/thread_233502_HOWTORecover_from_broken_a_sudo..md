---
title: "HOWTO:Recover from broken a sudo."
date: 2006-08-10
forum: Outdated Tutorials &amp; Tips
---

### Post by Bigglez on 2006-08-10
This is based on Kubuntu 6.06, I hope it's standard for all *ubuntu releases.

_**The Problem**_
You suddenly find that your password is not accepted by sudo anymore. For example, you start Adept (or Synaptic) and it refuses your password.
[COLOR="Red"]**Don't panic!**[/COLOR]

_**The Situation**_
What has happened is that your user name is no longer in the 'admin' group.
*(This can happen by accident, especially if you are new to the command line and you make a mistake with the 'usermod' command -- like I did :rolleyes: )*

_**The Solution**_
[LIST=1]
[*]Restart your computer.
[*]When you see the word "**GRUB**" at the bottom of the screen, press the **Esc** (escape) key quickly! This will allow you to choose what kind of Linux to start.
[*]Choose the Kernel you want by moving up and down with the arrow keys, but make sure it says 'Recovery Mode' alongside it. Hit Enter.
[*]Your machine now boots into a text mode prompt. Don't worry about it. When it gets to the prompt, type the following command:
*Make sure you replace [COLOR="SeaGreen"]username[/COLOR] with your actual username - get it exactly right.*
```
addgroup [COLOR="SeaGreen"]username[/COLOR] admin
```
[*]Now restart your machine by the following command:```
reboot
```
(On restart, you *might* have to go into GRUB again (by pressing Escape) and choose your ordinary kernel, not the recovery mode one.)
[/LIST]

**_The End_**
I hope this helps out. Please feel free to correct this guide if I made a mistake - I have done it from scribbled notes and memory.

-- keywords to help searches --
lost password sudo not working cannot login no root admin group problem Adept Synaptic accept Accept log   in won't allow
--

---

### Post by mlind on 2006-08-10
> **Bigglez said:**
> 
_**The Problem**_
You suddenly find that your password is not accepted by sudo anymore. For example, you start Adept (or Synaptic) and it refuses your password.
[COLOR="Red"]**Don't panic!**[/COLOR]


lol :mrgreen: 
I would have probably written "Slap yourself ten times moron!"


For people like myself who have set *alternative=false* in /boot/grub/menu.lst which removes recovery option(s) from GRUB menu,
you can achieve same behaviour by appending **1** or **single** as kernel parameter before booting.

This is info should be useful for many people, thanks.

---

