---
title: "Errors while compiling sound card driver"
date: 2012-10-01
forum: New to Ubuntu
---

### Post by the butler on 2012-10-01
Hi, I'm super noobtastic when it comes to linux/ubuntu so hopefully my error is obvious. I'm trying to install my sound card (Fatality Titanium XFi Pro) and I'm having...issues...:mad:

A walk through of everything I've done, sorry if it's a lot of superfluous information. 

1. Obtained opensource driver file from:
[http://opensource.creative.com/soundcard.html](http://opensource.creative.com/soundcard.html)
2. Read the readme file. Instructions are as follows:
> In terminal,

1) Goto source directory
2) Execute make command as root
   make
   make install
3. Seemed pretty simple so followed the directions (and here is where stuff just starts going wrong):
```
the_butler@the-beast:~/Documents/Sound Card drivers/XFiDrv_Linux_Public_US_1.00$ sudo make
[sudo] password for the_butler: 
make -C /lib/modules/3.2.0-31-generic/build M=/home/the_butler/Documents/Sound Card drivers/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-31-generic'
make[1]: *** No rule to make target `Card'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-31-generic'
make: *** [all] Error 2

```
4. I get that error every time. Following is a list of things I have done to try and solve it:
  1. Tried running it after sudo su (out of superstition): same result
  2. Re-installed the Linux headers file (several times...): same result
  3. Re-installed the build essential file: same result
  4. Purged, removed and re-installed dkms: same result
  5. Made edits to the driver file according to an forum post ([http://ubuntuforums.org/showthread.php?t=1550809):](http://ubuntuforums.org/showthread.php?t=1550809):) same result
  6. Scoured the Ubuntu forums for hours (I don't want to re-post an already solved problem, I couldn't find much else that seemed to relate. Doesn't mean it isn't on the site but to the best of my ability I can't find it.)
  7. Ritually sacrificed half a dozen cute and fuzzy animals to the terminal gods: same result

I don't think there is any problem with the makefile itself as i JUST compiled my wireless device drivers a couple minutes prior to beginning this driver. However, I simply don't see what else it could possibly be. That said I've probably a total of less than 24 hours behind the console in ubuntu so...

---

### Post by the butler on 2012-10-01
I always do things the hard way...apparently Ubuntu automatically installed the dang thing already.

---

