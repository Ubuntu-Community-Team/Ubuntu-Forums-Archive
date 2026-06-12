---
title: "Running a wireless ubuntu box in HardyH"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by tubulamax on 2008-05-26
Hi All,

I'm very new to Linux/Ubuntu, but i'm forcing myself away from XP/Vista to learn a new skill.

I want to run a ubuntu box, on an old htpc, in a cuboard out the way. I don't have a wired connection to it, so i've put in a netgear WG311T card and this is working fine, and connects to my WPA wifi network fine.

The problem i'm having is that with a screen and keyboard attached, everything is fine, but i want to put the box in a cupboard without this. Everytime i reboot, or turn the pc on, it asks for a keyring password before it connects to the wifi connection. This is a pain, as it means if i reboot the box, it is no longer contactable. 

I'm using the latest version of Ubuntu, 8.something, (hardy Heron) and i've had a look at libpam-keyring, which, even though i've followed many guides on these forums and other sites, it still does not unlock the keyring at startup and allow the box to connect to my router, to then allow me to connect remotely to it.

I'm not sure what other information i should supply for you, as i say, i'm very new to this, but any help with this would be great.

Thanks in advance,

Max

---

### Post by quelx on 2008-05-26
So you have done this?

[http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/](http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/)

and enable automatic login for **gdm**

[http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_066.html](http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_066.html)

---

### Post by tubulamax on 2008-05-26
Hi there,

Yes, i've tried the first of the 2 links, and i couldn't find libpam-keyring, only libpam-gnome-keyring, which i installed as it instructed. This didn't work, so then i found another how-to and actually compiled the libpam-keyring myself, and again, this still hasn't worked.

On the second link, it seems a bit out of date, as it doesn't really reflect what i'm seeing in Hardy heron.

At present, i have HH logging in under my username, so it gets to the desktop, but then the first thing i see if the keyring prompt, asking for my keyring password. This is the same as my user password as instructed in the howto.

Here is the info in the gdm:-

#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session required        pam_limits.so
@include common-session
session optional        pam_gnome_keyring.so auto_start
@include common-password
auth optional pam_keyring.so try_first_pass
session optional pam_keyring.so

Is this right?

Thanks,

Max

---

### Post by quelx on 2008-05-26
A quick search of the forums revealed

[http://ubuntuforums.org/showthread.php?t=805602&highlight=hardy+autologin](http://ubuntuforums.org/showthread.php?t=805602&highlight=hardy+autologin)
[http://ubuntuforums.org/showthread.php?t=768370&highlight=hardy+autologin](http://ubuntuforums.org/showthread.php?t=768370&highlight=hardy+autologin)
[http://ubuntuforums.org/showthread.php?t=805618&highlight=hardy+keyring](http://ubuntuforums.org/showthread.php?t=805618&highlight=hardy+keyring)

---

### Post by tubulamax on 2008-05-26
Right, i've read all those, and i thought i'd fixed it! I set the keyring password to blank, and all was looking rosey! I could restart with my mouse, keyboard and monitor plugged in, leave a ping running from another pc, and it would reboot and come back to the desktop, and auto connect to my AP. Great i thought! Even if it's a little unsecure, it does the trick. So i then unplugged the keyboard and mouse and monitor, and now it won't work!

Scratch that, think i've figured it out! It looks like there was a prompt on screen for low graphics mode, which i've now selected and i think that is finally working!

Thanks for all your help.

Max

---

