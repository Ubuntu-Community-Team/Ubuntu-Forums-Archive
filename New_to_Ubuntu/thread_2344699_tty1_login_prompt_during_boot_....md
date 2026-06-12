---
title: "tty1 login prompt during boot ..."
date: 2016-11-27
forum: New to Ubuntu
---

### Post by michael351 on 2016-11-27
Why does Ubuntu post a TTY1 login prompt during boot sequence ? It doesn't last but for 10 seconds or so and then proceeds to load the X server and desktop login screen.
Just curious if I can have Ubuntu boot directly to my desktop and bypass this (and earlier messages).
thanks

---

### Post by Frogs Hair on 2016-11-28
You shouldn't be seeing TTY without using the keyboard prompt Ctrl + Alt + F1 . Can you tell us about your device specs, the Ubuntu release(upgrade or clean installation).

---

### Post by michael351 on 2016-11-29
I have the latest LTS (ubuntu 16.04.1) running on an Acer r3700. I did a clean installation onto a dual boot disk with an existing windows partition. I use Grub2 to launch Ubuntu.
TTY pops up during boot asking for login and lingers for bout 10 seconds. I tried using it to "log in", but it ignores my entry. 
Strange that it should do this.

(Is there a boot log I could pastebin or post which shows why/when it puts up TTY)? I don't know where to look for it.

---

### Post by Dennis N on 2016-11-29
I've occasionally seen that before. I could be wrong, but I don't think it a login prompt for your account, but a system message when user lightdm is logged into its session just before the log in screen. Normally, it should be hidden by the splash screen but that does not always work as expected.

from journalctl:

```
Nov 29 09:23:12 Kayleigh lightdm[978]: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
<removed some lines of output>
Nov 29 09:23:25 Kayleigh lightdm[1217]: pam_unix(lightdm:session): session opened for user dmn by (uid=0)
Nov 29 09:25:13 Kayleigh systemd[984]: pam_unix(systemd-user:session): session closed for user lightdm

```

During the lightdm session, I log in and my session opens (2nd line shown), and then lightdm session closes.

---

### Post by kingneutron on 2016-11-29
TTY1 should always be accessible by hitting Ctrl+Alt+F1 (in case something goes wrong with your X, or you just need to do something on the console without GUI. GNU Screen is invaluable for this.)

If the system is running off a slower hard drive, X session startup may be delayed a bit and TTY1 may seem unresponsive, however you should still be able to login at the text console with TTY2 (Ctrl+Alt+F2) if TTY1 is not accepting your login.

As long as the TTY1 prompt is eventually overridden by X Session startup, I'd say it was a cosmetic issue and not to worry about it. You might consider upgrading to a faster drive though.

---

### Post by michael351 on 2016-11-30
This all makes sense. The TTY1 prompt is overridden by the X session startup. I tried to "login" by typing my username and proceeded about one or two characters and it went away and the X session started. So it is a cosmetic issue.

This all started after I upgraded to Ubuntu 16.04.1 - but left a mess on my disk (the old Ubuntu is still there even though I did a clean install) taking up a new partition. That may be slowing the disk down? Not important enough to mess with now.

Thanks all.

---

