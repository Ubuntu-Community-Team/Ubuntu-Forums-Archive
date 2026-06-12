---
title: "Minecraft/Steam Games and OpenGL?"
date: 2015-02-07
forum: New to Ubuntu
---

### Post by leah4 on 2015-02-07
I just installed Ubuntu on my Acer Chromebook and have downloaded Steam and the Minecraft.jar file. I have tried to open a steam game and was warned about OpenGL and came across the same issue in Minecraft. I made it past the loading screen and clicked play when the launcher crashed. I've read through a few topics and found that NullPointerException: null means I don't have the proper OpenGL. I have yet to install one and I'm a bit lost as to where to start. Can OpenGL be installed from the Ubuntu Store?
Thanks!
Leah

---

### Post by Rob Sayer on 2015-02-07
OpenGL isn't somethink you just 'install'.

What's you cpu and RAM?  Are you using the Unity DE version?

Also video card ... paste this into terminal:

sudo lshw -C video

and post output here, embedded in [code] tags so we can read it.

---

### Post by leah4 on 2015-02-07
Pasting that code in the terminal yields:

[sudo: lshw: command not found]

I have Ubuntu 12.04 LTS
Memory: 1.8 GiB
Processor: Intel Celeron(R) 2955U @ 1.40GHz x 2
Graphics: Unknown
OS type: 64-bit
Disk 0 bytes

when attempting Steam I get the following error:

"OpenGL GLX context is not using direct rendering, which may cause performance problems.


For more information visit https://support.steampowered.com/kb_article.php?ref=9938-EYZB-7457."

It then proceeds to try and load but crashes.

---

### Post by newb85 on 2015-02-07
lshw ought to be installed in a normal Ubuntu installation.  You can add it with 
```
sudo apt-get install lshw
```

---

### Post by leah4 on 2015-02-07
Okay, I now have a response but copying the code from the terminal and pasting here doesn't seem to be working...

---

### Post by newb85 on 2015-02-07
The keyboard shortcut for copy in the terminal is Ctrl+Shift+C, not just Ctrl+C.  In Ubuntu, you should be able to highlight and drag-and-drop it, as well.

---

### Post by leah4 on 2015-02-07
Strange... Shortcuts don't seem to be working.

---

