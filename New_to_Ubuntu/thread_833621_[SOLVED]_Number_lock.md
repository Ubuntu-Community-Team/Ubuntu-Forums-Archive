---
title: "[SOLVED] Number lock"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by gettinoriginal on 2008-06-18
did a search, but cannot find this specific one.
I am dual booting with Ubuntu/XP.  My bios are set for numlock on and I have no problem when booting into XP, but when I boot into Ubuntu, my numlock is alway off.  Is there a setting for making Ubuntu boot with numlock on ??  This is not a major issue, just a hassle always having to remember to turn it on to log in.  Thank you

---

### Post by sdowney717 on 2008-06-18
numlockx in synaptic

[http://www.mike-devlin.com/linux/README-numlockx.htm](http://www.mike-devlin.com/linux/README-numlockx.htm)

you just need to install it, not compile or anything. The website gives some more info.
and it looks like you have to edit a line in a file

[http://ubuntulog.wordpress.com/2007/08/11/turning-on-num-lock-on-ubuntu-start/](http://ubuntulog.wordpress.com/2007/08/11/turning-on-num-lock-on-ubuntu-start/)

also I found this
run gconf-editor from terminal

check the check box in gconf-editor:
/desktop/gnome/peripherals/keyboard/remember_numlock_state

---

### Post by gettinoriginal on 2008-06-19
Thank you very much for your response, I did find that numlock is installed, and is turned on, but it doesnt work on my keyboard, so it must be my keyboard.  :(

---

### Post by Butthead on 2008-06-19
Doesn't seem to work with my keyboard neither. :(

You wouldn't happen to be running **Kubuntu 64 bit Hardy**, would you? :confused:

---

