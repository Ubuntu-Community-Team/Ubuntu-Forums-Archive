---
title: "CPU Speed/Power lvl?"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by jenova_skill on 2008-06-22
Im new to linux..... I have everything working that i need so far.... only 1 problem plauges me...... ajusting the computer operating speed or power to save battery life..... I have 2 toshiba laptops and u can lower the CPU speed Or something to that effect when Using apps that don't require alot of cpu speed ( like browsing ) or something....
USing this while running on battery I nearly double the battery life........
I played with the options on the power saving options on ubuntu... however i don't see ne options for the computing speeds.   

Please let me know if they already have this somewhere or if im able to do this already.......   I might not be wording it right but im sure u got the just of it.

---

### Post by Flying caveman on 2008-06-22
[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)

hope reading that helps.

powernowd or cpufreq are the names of the programs that do that.  

I think i had to add the line p4-clockmod to my /etc/modules to get mine to work. 

sorry, i can't be of more help.

you might just have to run```
sudo dpkg-reconfigure gnome-applets
```

---

### Post by Mikecore on 2008-06-22
your laptop will auto adjust the cpu speed as needed and when it doesn't need alot of speed it will slow down. 

but if you must set it manually try this this will let you set the speed manually just make sure to add the cpu speed applet to your task bar

```

sudo dpkg-reconfigure gnome-applets

```

---

### Post by sdennie on 2008-06-22
If you are using a fairly modern CPU, pegging it to the minimum speed to "save power" will actually do the opposite.  Letting the CPU go between minimum and maximum power on demand is much more efficient.  Google for "intel race to idle" for more information on why this is true.

---

### Post by m_l17 on 2008-06-22
Follow this guide :[http://technowizah.com/2007/01/debian-how-to-cpu-frequency-management.html]("http://technowizah.com/2007/01/debian-how-to-cpu-frequency-management.html")

It does say for Debian but works for Ubuntu since it's Debian based distro.

---

