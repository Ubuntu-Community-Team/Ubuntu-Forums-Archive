---
title: "Dual monitors / memory use"
date: 2014-06-21
forum: New to Ubuntu
---

### Post by Andrew_L_Millspaug on 2014-06-21
Hi, Ubuntu Users, My name is Andrew Millspaugh and I'm new to ubuntu and just want to ask some question?

I was running windows 8.1 and I got a really bad virus, So I always wanted to try linux out, so here I am. anyways , I have 2 25" flat screen monitors, in windows 8 I used a dual monitors system and  I can drag folders or websties from one screen to the other, My question is how can I do that with ubuntu.

My other question is, where in ubuntu can I find where it shows how much ram I have. Thats It thats all I wanted to ask.
Thanks very much.

Andrew Millspaugh

---

### Post by oldos2er on 2014-06-21
What video card do you have?

In a terminal, run ```
free -m
``` or if you want detailed info use ```
cat /proc/meminfo
```

---

### Post by sandyd on 2014-06-21
Hi, and welcome to Ubuntu!

You can see how much RAM you have in the 'System Monitor'. You can find that by typing it in the Unity Dash (the button at the top-left of the screen).

In case it is not installed, you can install it from the software center.

---

### Post by JonPaul on 2014-06-21
If you are using Ubuntu from the dash start typing 'details' and it will tell you about memory/processor etc.

---

### Post by grahammechanical on 2014-06-21
Hi and welcome to the forums.

Open the Dash and search for System Monitor and the Resources tab should tell you how much memory (RAM) is in your system.

Regards.

---

### Post by LastDino on 2014-06-21
I don't know about first but second could be answered by simply opening settings and opening details which has gear like icon.

If you want more detailed info of entire system, you can also copypaste/type this in terminal
```
sudo lshw
```

---

### Post by Andrew_L_Millspaug on 2014-06-21
Hi, Thanks for welcomeing me :) My video card is Nvidia Geforce I have the drivers but its for windows, I dont know how to get it for ubuntu. I tryed to go to there site and do a auto detect but it keeps saying that I dont have java and I dont know where to get jave at. I went to there website and I dont know what linux to use sorry. Thanks for all your support.

---

### Post by LastDino on 2014-06-21
Simply go to settings>software & update manager>click on the tab ''additional drivers''> tick-mark if there is anything detected>apply changes. You don't need to download them separately and you definitely can't use Windows drivers on Ubuntu. Don't bother to install Java.

---

### Post by Andrew_L_Millspaug on 2014-06-21
Wow Thanks somuch  LastDino for your help I found it and its installing, Thanks agine. :)

---

### Post by gaxfax on 2014-06-21
**5 commands to check memory usage on Linux**
[http://www.binarytides.com/linux-command-check-memory-usage/](http://www.binarytides.com/linux-command-check-memory-usage/)

My other question is, where in ubuntu can I find where it shows how much ram I have. Thats It thats all I wanted to ask.
Thanks very much.

Andrew Millspaugh[/QUOTE]

---

### Post by cwmoser on 2014-06-21
I have dual monitors to give me a panoramic desktop and with Ubuntu's workspaces I set
my system for four unique desktops.  I use the nVidia GeForce 7300LE video card
and the "nvidia-current" drivers.  You need to install nvidia-settings to setup the drivers
for dual monitor -- i.e. from command prompt enter:  **sudo apt-get install nvidia-settings**

Carl

---

### Post by sandyd on 2014-06-21
> **gaxfax said:**
> **5 commands to check memory usage on Linux**
[http://www.binarytides.com/linux-command-check-memory-usage/](http://www.binarytides.com/linux-command-check-memory-usage/)

My other question is, where in ubuntu can I find where it shows how much ram I have. Thats It thats all I wanted to ask.
Thanks very much.

Andrew Millspaugh[/QUOTE]

You can find it in the system monitor, resources tab

---

