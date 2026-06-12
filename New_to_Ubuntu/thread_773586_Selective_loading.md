---
title: "Selective loading ?"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Innernet on 2008-04-29
Hi all.
5.10 loaded fast. 7.04 too, about 20 seconds.  7.10 takes nearly a minute.
8.04 -I don't know yet-

In my little knowledge about operative systems, have a perception that at power-up, the memory gets loaded  with the items shown at
System > Administration > System monitor > Processes > View all processes.

Can someone teach me the reality, please ?

And feel like 80% I do not use in a typical session, besides have no clue what most they are for. I have deleted several oriental character sets which I will never use and never asked for them in the installation.  
How can I choose to load only the basics, and IF at any moment I use certain application, THEN the system will load it ?

Thanks.

---

### Post by spiderbatdad on 2008-04-29
removing --quiet splash from the kernel line in  /boot/grub/menu.lst may help you to see where the process is slowing down. And dmesg may offer suggestions for hardware detection

I went from a 5 minute boot to just over 30 secs. in 7.10 and 8.04 by setting boot parameters that work well in the kernel line. 

I have disabled a few starup programs...Bluetooth, Evolution, Tracker Applet, Tracker, Visual Assistance.

---

### Post by Innernet on 2008-04-29
Thanks for the hope.

As a beginner, cannot understand how to implement/do your suggestions.  Can you explain in detail as I do not know enough to navigate around and do those changes ?
Yes, I did delete bluetooth thingies too as I will never use those.

---

### Post by spiderbatdad on 2008-04-29
I've tried to explain here:
[http://spiderbatdad.wordpress.com/ubuntu-boot-problems/](http://spiderbatdad.wordpress.com/ubuntu-boot-problems/)
please let me know if it is helpful. If it isn't I can try to answer questions for you. Since your system boots, I suggest running dmesg in your terminal...Applications>>Accessories>>Terminal, and just read all the gobbly-gok...looking for suggestions like, "try using lapic."

---

