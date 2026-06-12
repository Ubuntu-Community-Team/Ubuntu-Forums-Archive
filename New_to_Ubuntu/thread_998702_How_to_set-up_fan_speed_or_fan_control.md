---
title: "How to set-up fan speed or fan control?"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by manilaph on 2008-12-01
I am using a Compaq Presario V3000 with pure Ubuntu 8.10. 

I am not sure if my fan is working because there seems to be no sound or fan noise.

How do I know for sure if the fan is working?

How do I set-up or configure the fan controls?

Thank you.

---

### Post by fr.theo on 2008-12-01
your system bios should handle that Automatically, you should enter you bios and see if it is enabled and at what setting it is set at.

---

### Post by Hypo_Mix on 2008-12-01
linux uses less computing power that windows so it dosn't need to run the fan as fast, so it would be running quieter
(at least thats what i found)

---

### Post by manilaph on 2008-12-01
> **fr.theo said:**
> your system bios should handle that Automatically, you should enter you bios and see if it is enabled and at what setting it is set at.

hi.

i can't see the fan controls at BIOS at all. i've read over here at the forum that there are fan control packages.

what should i sudo apt-get?

---

### Post by fr.theo on 2008-12-01
try this site it may help:


[http://www.thinkwiki.org/wiki/ACPI_fan_control_script](http://www.thinkwiki.org/wiki/ACPI_fan_control_script)

or
[http://www.nvnews.net/vbulletin/showthread.php?t=100705](http://www.nvnews.net/vbulletin/showthread.php?t=100705) 

or

[http://ubuntuforums.org/showthread.php?t=315430](http://ubuntuforums.org/showthread.php?t=315430)

---

### Post by fr.theo on 2008-12-01
this thread does is not conserning your notebook but see if it can point you in the right direction, hope this helps, sorry if I am not much help to you.

P.S see if Compaq has a bios update, might help.


here is the thread: [http://ubuntuforums.org/showthread.php?t=539365&highlight=overheat](http://ubuntuforums.org/showthread.php?t=539365&highlight=overheat)

---

### Post by 3rdalbum on 2008-12-01
Your motherboard knows how fast to run the fans, and it will perform that function unless something in the operating system interferes with that.

My Acer Aspire One runs the fans slower in Ubuntu than it did in Linspire, with no overheating problems.

Trust your motherboard. If the fans are running slowly, that's because they can safely run slow.

---

### Post by manilaph on 2008-12-01
ok. i just hope that my fan is working. can't seem to hear anything at all. it is too quiet and that worries me. and i feel that it is hotter than normal.

there is no fan speed or fan configuration on my BIOS.

i tried the gkrellm but can't seem to get it detect the heat or fan speed.

---

### Post by gandaran on 2008-12-01
> How do I know for sure if the fan is working?

install lm-sensors (run **sudo sensors-detect** after install and reboot) and sensors-applet or xsensors
for the sensors applet, click add to panel, hardware sensors monitor, configure it to show cpu temp or fan speeds

---

### Post by levelup2 on 2008-12-01
Thanks for all your post

---

