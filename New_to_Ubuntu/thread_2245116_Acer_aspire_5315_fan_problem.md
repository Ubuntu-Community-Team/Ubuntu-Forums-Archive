---
title: "Acer aspire 5315 fan problem"
date: 2014-09-21
forum: New to Ubuntu
---

### Post by p-oleksy on 2014-09-21
I have a 2 gb ram 80gb memory intel Celeron acer aspire 5315 with Ubuntu 12.04 and today I have come across a problem of the computer over heating and so I have come onto the forum and searched for the problem and I saw that many others have the same problem so I followed as I presumed the best solution which was this [http://ubuntuforums.org/showthread.php?t=1748521](http://ubuntuforums.org/showthread.php?t=1748521) I followed the steps but when it comes to starting the programme with terminal it say "cat: /sys/devices/platform/coretemp.*/temp1_input: no such file or directory" and it keeps repeating. can someone please tell me how to fix this or how to make the fan start working again. Thanks

---

### Post by overdrank on 2014-09-21
Hi and welcome, moved to New to Ubuntu

---

### Post by Vladlenin5000 on 2014-09-21
Have you updated the BIOS already? That should be the first thing to do...

---

### Post by p-oleksy on 2014-09-21
no I have not but I sure will try. could you link me to a forum page with steps to upgrading the BIOS. thanks :P im just starting to learn.

---

### Post by Vladlenin5000 on 2014-09-21
Updating BIOS is a computer specific procedure. Please check the instructions directly from the manufacturer.

---

### Post by raiden-san123 on 2014-09-21
[COLOR=#000000] change the sensors in /etc/thinkfan.conf to the following:

[/COLOR]sensor /sys/devices/platform/coretemp.0/temp1_input
sensor /sys/devices/platform/coretemp.0/temp2_input
sensor /sys/devices/platform/coretemp.0/temp3_input
sensor /sys/devices/virtual/hwmon/hwmon0/temp1_input[COLOR=#000000]

[/COLOR]

---

### Post by p-oleksy on 2014-09-21
what about do you want me to change? specifically please

---

### Post by raiden-san123 on 2014-09-21
[COLOR=#000000]*1. add kernel module 'coretemp' to /etc/modules*[/COLOR]
[COLOR=#000000]*2. load kernel module 'coretemp'*[/COLOR]
[COLOR=#000000]*3. add the following three sensor entries to /etc/thinkfan.conf just before the temperature levels:*[/COLOR]

[COLOR=#000000]*sensor /sys/devices/platform/coretemp.0/temp1_input*[/COLOR]
[COLOR=#000000]*sensor /sys/devices/platform/coretemp.2/temp1_input*[/COLOR]
[COLOR=#000000]*sensor /sys/devices/virtual/hwmon/hwmon0/temp1_input*[/COLOR]

---

### Post by green69 on 2014-12-19
Thank you so much raiden-san123!!!

Your solution worked for me using a acer aspire 5315 2GB RAM with an ubuntu 14.04.

So thanks to you I could recover my old 5315.

Cheers

---

### Post by green69 on 2014-12-19
No way! After a reboot the fan stopped working again and it seems there is no way to turn it on. Really these are the things that frustrate me a lot.

How this is possible?

---

### Post by green69 on 2014-12-22
I'm experiencing a very strange behavior. The solution seems to work ONLY after I suspend the machine and turn it on again. I can't understand why (but at least it works).

Anybody has an explanation for this?

Thanks in advance.

> **green69 said:**
> No way! After a reboot the fan stopped working again and it seems there is no way to turn it on. Really these are the things that frustrate me a lot.

How this is possible?

---

