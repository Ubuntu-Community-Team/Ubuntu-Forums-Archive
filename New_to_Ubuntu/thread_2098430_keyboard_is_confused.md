---
title: "keyboard is confused"
date: 2012-12-26
forum: New to Ubuntu
---

### Post by dragonlady on 2012-12-26
I have some keys that think they are something they aren't. My backslash key thinks it is less then greater then those keys are already assigned elsewhere. I have done some looking around in usr/share/x11/xkb/symbols. What file is the file my keyboard actually functions off of? I want to make sure i edit things correctly and in a way i won't lose information. PLease help

---

### Post by N00b-un-2 on 2012-12-26
what is the model of your keyboard?
This may be a simple case of the locale being incorrectly set.  Try ```
sudo dpkg-reconfigure console-data
```
and make sure it's set to your locale.

---

### Post by coldcritter64 on 2012-12-26
> **dragonlady said:**
> I have some keys that think they are something they aren't. My backslash key thinks it is less then greater then those keys are already assigned elsewhere. I have done some looking around in usr/share/x11/xkb/symbols. What file is the file my keyboard actually functions off of? I want to make sure i edit things correctly and in a way i won't lose information. PLease help
If you are one of the latest Unitys 12.04 or 12.10 look in system settings, available from the "power button" on the top unity panel.

There should be an icon for Keyboard, look there for a tab wih country keyboard layouts to do the changes "graphically". Changing to the correct keymap for your keyboard should fix your problem. Sorry I can't be more specific here, I'm on a tablet PC temporarily :).

---

### Post by dragonlady on 2012-12-26
I am using 12.10 I looked at the graphical english keyboards none matched mine. I have an asus g60.

I tried the terminal command this was what it came back with

dpkg-query: package 'console-data' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: console-data is not installed

---

### Post by audiomick on 2012-12-26
Just to be sure of things, what country are you in, and is the computer from that country? You seem to be trying to set up English as the system language. Is that the language of the country you are in and the country that the computer came from?

---

### Post by dragonlady on 2012-12-28
I live in america and its a computer from america. My backslash key is in a different spot then all other stabdard ubuntu keyboard options. Where it shows the return key as a big key taking up to lines. My backslash key is the key that exists on the top row and my enter key is one single key on one line of keys.

---

