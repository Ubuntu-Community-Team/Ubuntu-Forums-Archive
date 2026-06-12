---
title: "[SOLVED] Application folder locations"
date: 2008-05-19
forum: Programming Talk
---

### Post by af20001 on 2008-05-19
Hi,

Is there a standard for file locations in an application installed by end users?

I am writing a python app (pyGTK) that uses a number of sound and image files. While I'm currently developing the application, the folders are in a couple of sub-folders (1 for sounds, 1 for images) in my Dev folder, which I've hardcoded the location of.

What happens when the app gets packaged up? Where would/should the sound/images folders end up? How should I code the application to look for the location of these folders?

Any help appreciated.

---

### Post by didac on 2008-05-19
In linux folder names are standard -- more or less. Check:

[HTML]http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html[/HTML]

for information.

Applications users install in their system usually go to the hierarchy beginning in /usr/local. bin and sbin for executables, etc for configuration files, lib for libraries, share for all the rest. Open your /usr/share or /usr/share/local to see how other programs do it. /dev should be left for devices, like hard disks, modems, sound cards, etc

---

### Post by af20001 on 2008-05-19
Thanks, that was a useful link.

Also looks like I can use os.getcwd to return the location of the current working folder, so I should be able to build the full location from there.

---

