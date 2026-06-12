---
title: "[SOLVED] Fresh 7.10 Install - Couple of Things ?"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by KevinD_Atl on 2008-05-24
[FONT="Tahoma"]Fresh install of 7.10 on Acer Aspire 5315 laptop.  Everything but the sound, wi-fi, and visual effects didn't work out of the box.  I did get the wi-fi and sound to work, but I can wait on the visual desktop.  Here are a few things that I'm hitting, more annoyances than anything

**1) Wi-Fi -** I can go to Wi-Fi Radar and see the wireless networks in my range, but how do I connect to them? I can't even get to a point to enter a WEP/WPA. I try network manger from terminal, and command not found.

**2) Passwords -** I used sudo passwd and entered what I wanted, but the pop-up for admin password is still the same as the login for my normal user. I want one password for the root/sudo and one for the user. I thought there was a conf file, but couldn't find it.

**3) Toolbar -** Every reboot the taskbar(not the one with Applications) keeps going all the way to the bottom. I can go to properties and change it from Top then back to Bottom and it's fine. 

**4)Updating / Repo's -** Maybe I'm paranoid but I didn't get any available updates.  Maybe the ISO I just download was already updated?  I've rem'd out the universal and the other rep's, but no updates are availabe...

**5) Touchpad -** Maybe I'm shaking but it makes spuradic jumps and then locks for a few seconds. I've rem'd out the SymapticTouchpad in the conf file[/FONT]

:guitar:

---

### Post by Sarah L on 2008-05-24
1) networkmanager is a very handy tool, but might not be installed by default. Try ```
sudo apt-get install network-manager-gnome
```

2) The first user you create after an installation is an adminstrator. This means that you're capable of running commands as root by using sudo and typing in the password for the admin account. If you do not want to be able to use sudo by typing in your user password, then create a non-admin user.

3) I use KDE, so I'm not familiar enough with gnome to help you with gnome panels.

4) Have you enabled all of the repositories? Also, do you have a working network connection? The package manager queries the repository servers for updates.

5) Make sure there are no other input devices (such as plug in mice) that are competing with the touchpad.

---

