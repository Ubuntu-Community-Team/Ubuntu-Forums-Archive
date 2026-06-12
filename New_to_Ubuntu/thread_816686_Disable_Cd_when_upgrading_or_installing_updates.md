---
title: "Disable Cd when upgrading or installing updates"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by adrianp0918 on 2008-06-02
how would i be able to disable the CD check when i am doing a apt-get install update, it ask for me to insert the cd into the cd rom,

i dont have 24 / 7 access t the server as i am sometimes at a remote location,

it is at my house though so i can make the changes

---

### Post by SunnyRabbiera on 2008-06-02
actually it should not call for the CD unless something is needed.

---

### Post by Mister.Vash on 2008-06-02
See the following section from the wiki page on how to disable the cdrom as a source:

[https://help.ubuntu.com/community/Repositories/Ubuntu#head-7b4ba9c71df331383c85fa08d14bca91a24ce17a](https://help.ubuntu.com/community/Repositories/Ubuntu#head-7b4ba9c71df331383c85fa08d14bca91a24ce17a)

---

### Post by adrianp0918 on 2008-06-02
i am running this in command line server

---

### Post by cariboo on 2008-06-02
The easiest way is to open /etc/apt/sources.list in gedit and just put a hash mark in front of the line with the cd in it use in a terminal type:

```
sudo gedit /etc/apt/sources.list
```

This is just a short part of my sources.list

```
# deb cdrom:[Ubuntu 8.04 _intrepid Heron_ - Release amd64 (20080423)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
<----------------cut--------------->
```

as you can see the first line has a "#" in front of it, just add it, save your file, close gedit, and thats it your done.

JIm

---

### Post by Maestro23 on 2008-06-02
Check your /etc/apt/sources.list

If you have a line at the top like:

> #deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted


Make sure you comment it out (#).

---

### Post by adrianp0918 on 2008-06-02
Thank you so much i got it, and wow worked GREAT!! you guys rock

---

