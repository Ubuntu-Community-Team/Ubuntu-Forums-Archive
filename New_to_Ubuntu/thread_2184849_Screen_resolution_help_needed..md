---
title: "Screen resolution help needed."
date: 2013-10-30
forum: New to Ubuntu
---

### Post by Luc_Lacombe on 2013-10-30
Hello  On a new Ubuntu 12.04LTS install. Ihave a 1024x768 screen resolution while I have a 1680x1050 monitor.    I have Intel  integrated Q45/Q43 Chpiset graphic card and don't know if I need Intel drivers. Maybe but how???    Anyway... So I tried this Linux solution. Here :   [http://www.vxbus.com/software/linux/148-how-to-change-monitor-resolution-in-ubuntu-1204.html](http://www.vxbus.com/software/linux/148-how-to-change-monitor-resolution-in-ubuntu-1204.html)    Everything was coming OK up to Step5.    So I made step 6 and my 1680x1050 resolution was not retained after reboot.    I don't know what went wrong! I doN,t understand and I'm new to this.    Hey...I don't want to make things complicated ...I just want to have 1680x1050 opn my monitor. Someone to help, please?    Thanks!  Luc

---

### Post by fantab on 2013-10-30
Read the solution here: [http://ubuntuforums.org/showthread.php?t=1888642&p=11503588#post11503588](http://ubuntuforums.org/showthread.php?t=1888642&p=11503588#post11503588)
Tell us if it helps.

---

### Post by Luc_Lacombe on 2013-10-31
Hello Fantab

I used the link supplied in your post and found solution in your post #4.
I just replaced "HDMI2" by "VGA1" and thanks to you my resolution is now the right one!
Two questions remains.
1) After first reboot from my mod, it reported a DDCPROBE problem, it produced a report that I read with no very much meaning for me, I closed it and rebboted. Afterwards problem seemed to disappear as no other error message triggered. Am I on the right track?
2)Why didn't Ubuntu detected my monitor during install or reboot? Is it the reason for the preceding DDCPROBE error reported?

Thanks very much for your kind help, Fantab

Luc Lacombe

---

### Post by fantab on 2013-10-31
I am not sure. Intel's graphics are quite well supported in Linux. However there have been a few lemons with respect to opensource support. 
I have Intel G45/G43 graphics and they work great out of the box. Never had any issues.
The details of my Graphics:
```
$ **lspci**
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
```

Go to System Settings -> Details and see what Graphics its showing.
Also check the output of the command:
```
lspci
```

If you are looking for 'real' solution then check out [THIS THREAD]("http://ubuntuforums.org/showthread.php?t=1743535"). You can post your query there with as many details about your graphics as possible.

Good Luck.

---

