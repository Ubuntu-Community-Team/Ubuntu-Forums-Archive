---
title: "Enable Num Lock at Boot"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by hal8000 on 2008-05-29
I'd like to enable Num Lock (i.e. numeric keypad LED lights and numeric keypad active) at boot time.

I'm running Hardy 8.04, keyboard is BTC9000 set to BTC9000 in xorg.conf.

Numlockx is installed via synaptic, I have also created a user .xinitrc in my home directory

cat ~/.xinitc
!#/bin/bash
numlockx &

file permissions are 755 and if numlock is off and I execute
~/.xinitrc

the .xinitrc file does enable num lock.

Why isn't my .xinitrc loaded at boot?
Thanks in advance

---

### Post by ricardisimo on 2008-05-29
I'm having the same problem in Kubuntu Hardy. I thought it was something in the /boot/grub/menu.lst file, but nothing there looks pertinent.

---

### Post by unutbu on 2008-05-29
Unfortunately, if you use the gnome desktop, you lose the ability to put startup commands in ~/.xinitrc (and also ~/.Xclients). Instead, I think you have to click System>Preferences>Sessions and add your command there.

I suppose you could just add .xinitrc to the Startup Programs list...

If you'd like `numlockx &` to run at bootup, you could add the command to /etc/rc.local; just put it above the exit 0 line.

---

### Post by Forlong on 2008-05-30
You can also add
```
if [ -x numlockx ]; then
  numlockx on
fi
``` to **/etc/gdm/Init/Default**

---

### Post by ricardisimo on 2008-07-05
I'm assuming these are Ubuntu-specific solutions, since I don't have that file to modify on my KDE system. There must be a simple solution, built right into Kubuntu, or no?

---

### Post by Sef on 2008-07-05
To enable numlock at boot in Hardy Heron, I just made sure it was on when I logout the first time.

---

### Post by ricardisimo on 2008-07-05
Oops! This is a tad embarrassing... From [https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock) --->
Quote:
Enabling NumLock in KDE (as used in Kubuntu)
From the K Menu, launch System Settings and click on Keyboard (Edgy users: K Menu -> System Settings -> Keyboard and Mouse -> Keyboard). You can see in the middle section the options for "NumLock on KDE Startup", where you can choose to Turn On, Turn Off, or Leave Unchanged. Select "Turn On" to turn NumLock on at startup.
Many thanks to the kind folks in the IRC Ubuntu channels.

---

### Post by Butthead on 2008-07-05
If only it was that easy on some systems though...:rolleyes:

---

### Post by derixc on 2008-07-06
> **ricardisimo said:**
> Oops! This is a tad embarrassing... From [https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock) --->
Quote:
Enabling NumLock in KDE (as used in Kubuntu)
From the K Menu, launch System Settings and click on Keyboard (Edgy users: K Menu -> System Settings -> Keyboard and Mouse -> Keyboard). You can see in the middle section the options for "NumLock on KDE Startup", where you can choose to Turn On, Turn Off, or Leave Unchanged. Select "Turn On" to turn NumLock on at startup.
Many thanks to the kind folks in the IRC Ubuntu channels.

Thanks ricardisimo, this one surely helps me a lot :)

---

### Post by ricardisimo on 2008-07-09
A little problem here, by the way: Num Lock is indeed activated at startup now, but the keyboard light does not come on, which is a bit disconcerting. In fact, if I hit <Num Lock> the light comes on, but then Num Lock is actually disabled, so it's in reverse now. Odd. I'd call it a bug, myself, but I don't know if it's worth reporting. Any opinions? Should I file a bug report?

---

### Post by MC707 on 2009-09-16
> **ricardisimo said:**
> A little problem here, by the way: Num Lock is indeed activated at startup now, but the keyboard light does not come on, which is a bit disconcerting. In fact, if I hit <Num Lock> the light comes on, but then Num Lock is actually disabled, so it's in reverse now. Odd. I'd call it a bug, myself, but I don't know if it's worth reporting. Any opinions? Should I file a bug report?

I answer a little late, but it IS indeed a bug. I mean, the light should be on when it is *active*, don't you think??:lolflag:

---

