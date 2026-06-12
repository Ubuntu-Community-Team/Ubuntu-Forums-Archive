---
title: "ubuntu minimal install help"
date: 2012-05-19
forum: New to Ubuntu
---

### Post by tropic on 2012-05-19
Tried to install Lubuntu but failed during installation

**What I've done until now:**

Installed ubuntu 12.04 mini iso.

***referred these pages:***
[Help.ubuntu.com]("http://help.ubuntu.com/community/Installation/LowMemorySystems")

[Psychocats.net]("http://www.psychocats.net/ubuntu/minimal")

**Did these things:**

sudo apt-get install xorg

startx

sudo apt-get update

      "      clean ( but nothing happened)

sudo apt-get install lxde

         "           synaptic

**Doubts/problems**:
1)
Do I need this xorg thing? I couldnt find what it's really used for, the help.ubuntu page linked to above says its needed for a graphical environment. How is this different from lxde, openbox etc which it says are windowmanagers. Is xorg something like gnome or unity ?

Also,there are many programs/files starting with "x" like xbiff xcalc xedit (and manymore) which are cluttering the "others" section in the start menu.And also do i need xterm,uxterm etc when I've got Lxterminal ? 

2)I need to get other apps/features in Lubuntu
  (

3)Need to get my sound to work,need codecs like that for mp3 and some video files

4)After I booted it up this time I couldn't mount my other partitions (created when win xp was installed). It said "error" "authentication required". (this had never happened before)


treat me as an absolute beginner :)

---

### Post by jtarin on 2012-05-19
Why are you doing a minimal install? You can do a base install and have everything you need to get started then you can eliminate what you don't need.
Yes, you need xorg if you want any kind of desktop at all,without you will have only a black screen with white text.....a terminal if you will.

---

### Post by mastablasta on 2012-05-19
> **jtarin said:**
> Why are you doing a minimal install? You can do a base install and have everything you need to get started then you can eliminate what you don't need.
.
because it failed.

to the OP you can try alternate install disk (same as original but with text based installer).

1. yes xorg is mandatory for any desktop environment/widnows manager.

2. instead of installing only lxde, you can install lubuntu-desktop

```
sudo apt-get install lubuntu-desktop
```3. for codecs, flash etc. install restricted extras package
```

sudo apt-get install lubuntu-restricted-extras
```

or if you already installed lubutnu desktop then find it in software center and install it.

---

### Post by tropic on 2012-05-19
Thanks for the quick response.

If I were to install lubuntu desktop would I need to uninstall the lxde package that I already have ?

---

### Post by jtarin on 2012-05-19
> **tropic said:**
> Thanks for the quick response.

If I were to install lubuntu desktop would I need to uninstall the lxde package that I already have ?
Only if you didn't want it. It would be installed with Lubuntu anyway.

---

### Post by bodhi.zazen on 2012-05-19
> **tropic said:**
> Thanks for the quick response.

If I were to install lubuntu desktop would I need to uninstall the lxde package that I already have ?

No, the lxde package is part of lubuntu-desktop. lubuntu-desktop is a metapackage.

[https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

---

### Post by tropic on 2012-05-19
Ohk thanks everyone. Installed lubuntu-desktop , everything's a lot more organised now.:p

---

### Post by killer62491 on 2012-06-09
question, could one do the same with ubuntu-desktop? my minimal install is in a similar state as the OP's on initial boot. thanks in advance
<::ALPHA::HECTOR::SIERRA::>

---

### Post by bodhi.zazen on 2012-06-09
> **killer62491 said:**
> question, could one do the same with ubuntu-desktop? my minimal install is in a similar state as the OP's on initial boot. thanks in advance
<::ALPHA::HECTOR::SIERRA::>

yes, you can install any of the *-desktops

---

### Post by mastablasta on 2012-06-10
you can also try usign alternate install disk first. alternate install uses text based installer. which is not as preety looking as graphical but still very simple to use.

---

