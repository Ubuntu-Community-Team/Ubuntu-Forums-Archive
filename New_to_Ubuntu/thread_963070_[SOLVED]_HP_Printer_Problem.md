---
title: "[SOLVED] HP Printer Problem"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2008-10-29
Hey, what's up?
I just got a new printer to replace my old printer that no longer works. The replacement is now an "HP F4235 All-in-One".
I installed it on Windows Vista and, predictably, it had a problem (a "Spooler SubSystem App" problem that both refuses to die and still stumps the Vista Forums today, to be exact). So, I tried on Ubuntu. Unfortunately, it does not quite have the right driver. The closes one available now is HP F4100. Is this enough?

What would you advise?

Thanks for your time.

Take care,
RedStarYellowSun

---

### Post by scradock on 2008-10-29
> **RedStarYellowSun said:**
> Hey, what's up?
I just got a new printer to replace my old printer that no longer works. The replacement is now an "HP F4235 All-in-One".

....... I tried on Ubuntu. Unfortunately, it does not quite have the right driver. The closes one available now is HP F4100. Is this enough?

What would you advise?

Thanks for your time.

Take care,
RedStarYellowSun

Try the driver it suggests - if it works, you're in business. If not, call HP and complain about the lack of Linux drivers for their products and ask if they want to give you your money back.

---

### Post by oldsoundguy on 2008-10-29
You can also try installing the HPLIP toolbox from synaptic.

---

### Post by bumanie on 2008-10-30
Go the Hp linux site and download the self extracting installer - there are instructions on the HP site - the installer works well. I have a HP F4185 all-in-one - have installed it via this metod in the past. If you ever reinstall if the printer is plugged in and turned on, it will install automatically.[ Go here ]("http://hplipopensource.com/hplip-web/gethplip.html")for HP self extracting installer. You will find install instructions also

---

### Post by RedStarYellowSun on 2008-10-30
> **bumanie said:**
> Go the Hp linux site and download the self extracting installer - there are instructions on the HP site - the installer works well. I have a HP F4185 all-in-one - have installed it via this metod in the past. If you ever reinstall if the printer is plugged in and turned on, it will install automatically.[ Go here ]("http://hplipopensource.com/hplip-web/gethplip.html")for HP self extracting installer. You will find install instructions also

Thanks for the advice. I went to the website and downloaded the file. I, turned on my printer and plugged it into my computer.
Unfortunately, the computer does not seem to know how to run the program. What do I do?

Thanks for your time.

Take care,
RedStarYellowSun

PS: Long live Ubuntu 8.10!

---

### Post by bumanie on 2008-10-31
Follow the instructions. Open terminal > cd ~/DesktopAssuming you have downloaded the file to your desktop, then > sh hplip-2.8.8.44.run and it should install. It asks a couple of simple questions and takes 20-30 minutes to install.

---

### Post by RedStarYellowSun on 2008-11-01
Thank you VERY much for your help!
It is now installed and my printer now works, thanks to you.

Take care,
RedStarYellowSun

---

