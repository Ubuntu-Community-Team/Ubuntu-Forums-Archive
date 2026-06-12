---
title: "Can't install HP C6280 drivers"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by Gobbie on 2008-09-01
Hi,  

I'm trying to install the drivers for my HP C6280. I've downloaded HPLIP 2.8.7 but it won't run. Any guidance would be great! I'm running Ubuntu 7.10

I'm still pretty new to Ubuntu so go easy please!


owen@owens-desktop:~$ sudo sh hplip-2.8.7.run
[sudo] password for owen:
sh: Can't open hplip-2.8.7.run
owen@owens-desktop:~$ sh hplip-2.8.7.run
sh: Can't open hplip-2.8.7.run
owen@owens-desktop:~$


I saw something about chmodding the file but i've got no idea what that means!

I've put this in the terminal as suggested somewhere.......... sudo aptitude install hplip
It installed something. No idea what though!

I also tried following this, from another post.......
1. open Printing - System - Administration - Printing
2. Click New printer
3. Select AppSocket/HP Jet Direct
a. Enter the IP address where it says Hostname, leave the port at 9100
Click Forward
4. Select HP in the list of printers in the database and click forward
5. Find Photosmart c6180 and select it and click forward
6. fill in printer name, location and readable name and click apply.

All ok until it asked for my password on localhost. I don't know of any password other than my login which I tried. What else could it be?

Please help!

---

### Post by bumanie on 2008-09-01
You first have to change directory to your desktop, then run the sh .run file
owen@owens-desktop:~$> cd ~/Desktop
owen@owens-desktop~$> sudo sh hplip-2.8.7.run

---

### Post by Gobbie on 2008-09-01
> **bumanie said:**
> You first have to change directory to your desktop, then run the sh .run file
owen@owens-desktop:~$
owen@owens-desktop~$

OK, thanks.  I thought I was at the desktop but I struggle with the terminal stuff.  I'll try that and let you know how I get on.

---

### Post by bumanie on 2008-09-01
Be aware it will take about 20 or so minutes. It's not fast, but has never failed for me yet - although I will mention, if a HP printer is plugged in during installation, it automatically is installed - great feature.

---

