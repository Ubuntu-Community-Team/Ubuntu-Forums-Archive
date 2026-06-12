---
title: "Need to set fan speed to max on T400 running 11.10 (and very hot!)"
date: 2012-02-01
forum: New to Ubuntu
---

### Post by ntrgc89 on 2012-02-01
I've tried doing some research on how to do this, but I've only found a lot of broken links and outdated advice. I've seen the thinkwiki pages and others on the subject, which suggest modifying /etc/modprobe.d/thinkpad-acpi.conf, but this file doesn't exist on my system.

I've found a file in /proc/acpi/ibm called 'fan' which contains the following text:

> 
status:		enabled
speed:		2996
level:		auto


And I've noticed that the speed changes every time I launch the text file. Is there some way to modify this file to be able to set fan speed to max? If you have any suggestions, please put them in newbie format, thank you!

---

### Post by ntrgc89 on 2012-02-02
I've found this website: [http://29a.ch/2011/10/14/review%3a-ubuntu-linux-on-thinkpad-x1](http://29a.ch/2011/10/14/review%3a-ubuntu-linux-on-thinkpad-x1)

And followed his advice to modify my thinkfan.conf - I set all levels to 7, but I don't think the fan is running any faster (I can barely hear it). Any advice??

---

### Post by kazztan0325 on 2012-02-02
Hi ntrgc89,

I'm sorry I don't know the way to modify the files to be able to set fan speed to max.

By the way, why don't you try to install a package called **'thinkfan'** with Synaptic Package Manager or Ubuntu Software Center?

I have installed the package **'thinkfan'** on my ThinkPad X200s, and it seems to work well for control of fan speed.

---

### Post by olwe on 2012-03-11
I've installed thinkfan (U11.10/Thinkpad t61). I made the file /etc/modprobe.d/thinkfan.conf with the line "options thinkpad_acpi fan_control=1" in it. I run it from the command line, and it seems to be working. Okay, how to I have it auto-start automatically at start up? I made an entry in the GUI "Startup Applications Preference," (command: /usr/sbin/thinkfan) but it doesn't seem to start it. Should I put the executable in a bash script and run that?

---

### Post by 2F4U on 2012-03-11
Maybe this thread helps:

[http://ubuntuforums.org/showthread.php?t=1749186](http://ubuntuforums.org/showthread.php?t=1749186)

---

