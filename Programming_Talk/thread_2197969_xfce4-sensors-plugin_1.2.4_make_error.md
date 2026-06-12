---
title: "xfce4-sensors-plugin 1.2.4 make error"
date: 2014-01-06
forum: Programming Talk
---

### Post by mattdawolf on 2014-01-06
I removed the repo package and am attempting to install from source so NVIDIA gpu temps will be recognized. Any solutions?


hddtemp.c: In function 'initialize_hddtemp':
hddtemp.c:417:5: error: 'p_uname' undeclared (first use in this function)
     p_uname = (struct utsname *) malloc (sizeof(struct utsname));
     ^
hddtemp.c:417:5: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [libxfce4sensors_la-hddtemp.lo] Error 1
make[2]: Leaving directory `/home/mattdawolf/Desktop/xfce4-sensors-plugin-1.2.4/lib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mattdawolf/Desktop/xfce4-sensors-plugin-1.2.4'
make: *** [all] Error 2

---

### Post by Toz on 2014-01-06
*Moving to the **Programming** subforum.*

Hello and welcome to the forums. 

What version of X/Ubuntu are you using?
Did you download the package from [http://goodies.xfce.org/projects/panel-plugins/xfce4-sensors-plugin]("http://goodies.xfce.org/projects/panel-plugins/xfce4-sensors-plugin")?
Did you patch the code in any way?

On my Xubuntu 13.10 install, with the following dependencies installed:
```
sudo apt-get install build-essential intltool libgtk2.0-dev libxfce4ui-1-dev xfce4-panel-dev
```
...then running:
```
./configure
make
```
...the code built properly.

---

### Post by mattdawolf on 2014-01-06
I'm running 14.04 and I got the tarball from that link. After installing all of those packages and doing make again, I still get the same error.

---

### Post by Toz on 2014-01-06
I just threw together a Xubuntu 14.04 install (daily image) and the build worked for me. Can you try a:
```
make clean
```
...before running make?

You might also want to re-download the package and try again with a fresh package (in case there was some corruption in the previous one).

---

