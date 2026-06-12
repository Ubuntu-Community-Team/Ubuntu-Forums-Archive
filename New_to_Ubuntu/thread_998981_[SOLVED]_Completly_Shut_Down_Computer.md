---
title: "[SOLVED] Completly Shut Down Computer"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by Lewis Arthurton on 2008-12-01
I'm pretty new to Ubuntu but I'm seriously liking what I see 

I just have one query. when I shut down Ubuntu it goes through all the motions of shutting down and I can hear the hard disk power off but the screen and something else stays on (most properly power supply)

In windows (boo, hiss,) it automatically shut everything off

I was just wondering if it were possible to get Ubuntu to do this? 

Please Help 
Lewis Arthurton

oh by the way I'm using Ubuntu 8.10

---

### Post by philinux on 2008-12-01
Is this a pc with a bios pre 2000?

If so this will help.[U]
[http://ubuntuforums.org/showthread.php?t=809311&highlight=acpi+force](http://ubuntuforums.org/showthread.php?t=809311&highlight=acpi+force)
[/U]

---

### Post by Immolatus on 2008-12-01
what is the machine (hardware profile) it is very possible that a peripheral is causing a "hang". Maybe a printer, sound card....

---

### Post by mapes12 on 2008-12-01
> what is the machine (hardware profile) it is very possible that a peripheral is causing a "hang". Maybe a printer, sound card....In terminal type ```
sudo lshw
```and post the output here.

I had an old PIII machine that did the same thing but I never found a fix. Just had to hold the on/off button for a few seconds until it powered down.

---

### Post by 4Orbs on 2008-12-01
This has always worked for me (and other people), on several Ubuntu and Ubu-based installations.

First open the /etc/modules file as root in the text editor by entering in the terminal:
```
gksudo gedit /etc/modules
```
Then add this as the last line of the file:
```
apm power_off=1
```
Then save the file, close and reboot (important). Shutdown should work properly thereafter.

---

### Post by Lewis Arthurton on 2008-12-01
Thank you to everyone that spent the time to write in information to help me :)

But I must say thank you so much 4Orbs your suggestion worked and you were a great help :)

Thank you 
Lewis

---

### Post by 4Orbs on 2008-12-01
Happy Holidays

---

