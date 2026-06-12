---
title: "nautilus script to dpkg"
date: 2005-11-17
forum: Outdated Tutorials &amp; Tips
---

### Post by pomalin on 2005-11-17
Hello, this is my first nautilus script, and my first howto, if somebody now how to improve it let me know.

So just download the attached file, decompress it in ./gnome2/nautilus-scripts/ and make it executable .

And you will have a new script called dpkg.

Right on a something.deb file, scripts, dpkg, it will open a terminal, ask for password, and dpkg the file.
One thing I want to improve, but don't know how to :
Make the terminal persistent if the installation process failed.

edith: ok, I don't use no more gnome-terminal, because I don't know how to keep it open when the command is fnish, so i usr xterm with -hold argument, so now, the xterm stay open, when the command is finish, so you can so errors, or success.
I've updated the attached file.

---

### Post by pomalin on 2005-11-23
I've uploaded the new version of my nautilus script, modified by anbreizh (thanks to him) from the french ubuntu forum.
Now with this script you can install the .deb and the .rpm.
Follow the instructions of the first post ;)

---

### Post by linkunderscore on 2006-01-03
Very nice simple script, but this is one thing that is almost just as easy to type dpkg -i whatever.deb or alien -i whatever.rpm

---

### Post by Saiboogu on 2006-01-05
[QUOTE=linkunderscore]Very nice simple script, but this is one thing that is almost just as easy to type dpkg -i whatever.deb or alien -i whatever.rpm[/QUOTE]

I agree that dropping to a terminal to type it out is pretty simple, but I don't know how many times I've double clicked a .deb without thinking, and expected it to install. This is handy, thanks!

---

