---
title: "Can Google Earth be installed on ubuntu 16.04 LTS?"
date: 2017-08-30
forum: New to Ubuntu
---

### Post by jack6128 on 2017-08-30
I downloaded and tried to install both 64 and 32 bit versions. My processor is 64 bit: Intel Core2 T7200. Ubuntu is 64 bit. I tried the 64 bit version of GE first. No luck. Tried 32 bit version. No luck. These are the two files I downloaded:

google-earth-pro-stable_current_amd64.deb
google-earth-pro-stable_current_i386.deb

When I click on either file, Ubuntu Software opens for 'google-earth-pro-stable,' with one button labelled 'Install'. I click on the button and 'Install' changes to 'Installing' for about two seconds and then reverts to 'Install'. Nothing installs.

Is there any hope?

Jack

---

### Post by &amp;KyT$0P# on 2017-08-30
What happens when you try to install it with GDebi?

If you don't have GDebi, run this command in Terminal to install it -
```
sudo apt-get install gdebi
```

---

### Post by jack6128 on 2017-08-30
Thanks. Installed gdebi. Googled how to use. It appears to be doing its job. Will report success or failure.

---

### Post by jack6128 on 2017-08-30
Success. Thank you.

---

### Post by mörgæs on 2017-08-31
Good, please use Thread Tools for marking the thread solved.

---

### Post by jack6128 on 2017-08-31
Thanks for the help. I will use Thread Tools for marking the thread solved in future. I got Google Earth to install, but I can't get passed the splash screen, and the actual earth portion is a very small rectangle in the upper left corner of the window. The area of the window that is usuall filled with earth is either the ubuntu desktop or whatever program was active when GE was launched. See attachment. Tried several uninstalls/reinstalls, including this: [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth) and this: [http://www.webupd8.org/2014/04/install-google-earth-in-ubuntu-1404.html](http://www.webupd8.org/2014/04/install-google-earth-in-ubuntu-1404.html). No luck.

The machine is a ThinkPad T60 with an Intel Core2 T7200 CPU, and "Gallium 0.4 on ATI RV515" graphics. Software Updater did not find any updates.

---

### Post by sed_faster on 2017-09-01
Hello,

I tried this tip on my:
```

OS: Ubuntu 17.04 zesty
 Kernel: x86_64 Linux 4.10.0-19-generic
 Uptime: 7h 44m
 Packages: 2065
 Shell: bash 4.4.7
 Resolution: 2944x1080
 DE: LXDE
 WM: OpenBox
 CPU: Intel Core i5-7500 CPU @ 3.8GHz
 GPU: Mesa DRI Intel(R) Kabylake GT2 
 RAM: 2019MiB / 7845MiB

```

and I have good results!

All time I need install a package .deb I should use program gdebi?
[B]
[UPDATE][/B]
Maybe I started talking early: [https://snag.gy/rAoK0S.jpg](https://snag.gy/rAoK0S.jpg) 
This image don't goo enough!

---

### Post by mc4man on 2017-09-03
> **Edgar_Oliveira said:**
> 

All time I need install a package .deb I should use program gdebi?

No need for gdebi in 16.04 & newer, just use apt, i.e. 
sudo apt install /path/to/the.deb

---

### Post by oldrocker99 on 2017-09-03
Ubuntu MATE has a welcome screen that installs Google Earth from a PPA, and other distros should look into allowing easy installation of selected programs.

---

