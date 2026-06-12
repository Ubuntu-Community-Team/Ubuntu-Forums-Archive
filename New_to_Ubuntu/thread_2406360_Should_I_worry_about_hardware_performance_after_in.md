---
title: "Should I worry about hardware performance after installing Ubuntu ?"
date: 2018-11-19
forum: New to Ubuntu
---

### Post by automate-stuff on 2018-11-19
Will I have to set the CPU to performance mode ? How about the GPU, Wireless and SSD ?


By default, what are these set to after a clean installation ? performance or power saving ?


Many Thanks

---

### Post by oldos2er on 2018-11-19
It's difficult to say since you don't tell us any hardware you're using. If you can provide that info it would help.

---

### Post by automate-stuff on 2018-11-19
Crucial mx500 SSD, Intel Centrino Advanced-N 6205, Intel HD 4000 iGPU, Intel i5-3320M

---

### Post by automate-stuff on 2018-11-19
Ok ... after some reading I realized I can change the CPU pstate using the command below: 

sudo cpupower frequency-set -g powersave/performance/ondemand/userspace/conservative/schedutil ...

How about GPU, Wireless and SSD ?

---

### Post by oldrocker99 on 2018-11-19
The open-source Intel drivers, from Intel itself, do not, AFAIK, allow optimizing adjustments. The only thing you need to do for an SSD is to trim it using a script. Here's a good way:[http://ubuntuhandbook.org/index.php/2013/12/enable-trim-ssd-better-performance/](http://ubuntuhandbook.org/index.php/2013/12/enable-trim-ssd-better-performance/)

---

### Post by Tadaen_Sylvermane on 2018-11-20
I have similar hardware except I have a mobile i7 in my laptop. I don't notice any problems with power saving or the like. I haven't changed many default system settings so it seems to have good defaults. Using 18.04.

---

### Post by HermanAB on 2018-11-22
It is all automatic.  Don't worry about it.

If you really want high performance, then don't use Ubuntu.  Change the desktop to XFCE or LXDE instead.

---

