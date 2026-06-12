---
title: "Linux Compatible Thermometers"
date: 2006-06-28
forum: Other OS Talk
---

### Post by gushy on 2006-06-28
Anyone know of linux compatible thermometers?  I want to monitor the room temp where I keep my server and ideally I'd like to do it from a thermometer plugged into a USB port or Serial port.

---

### Post by Keith_Beef on 2006-06-28
I got a Voltcraft VC304 four channel thermometer. This has a "3.5mm stereo jack format" (to quote the manual) RS232 connector.

collar == GND
middle == RX
tip == TX

[http://www.usinglinux.org/misc/voltcraft304.html](http://www.usinglinux.org/misc/voltcraft304.html)
[http://groups.google.com/group/comp.os.linux.misc/browse_thread/thread/bf982d45bc45c9/74c92ae97fca2462?lnk=st&q=Voltcraft+304+linux&rnum=1&hl=en#74c92ae97fca2462](http://groups.google.com/group/comp.os.linux.misc/browse_thread/thread/bf982d45bc45c9/74c92ae97fca2462?lnk=st&q=Voltcraft+304+linux&rnum=1&hl=en#74c92ae97fca2462)


Beef.

---

### Post by gushy on 2006-06-28
I'll have a look for that, thanks.

---

### Post by Keith_Beef on 2006-06-28
[QUOTE=gushy]I'll have a look for that, thanks.[/QUOTE]

I never got mine working properly, but your post has re-awakened my interest.

I can't find the cable that I made up, but I managed to track down and compile the code that Bernd Luevelsmeyer wrote in 2004.

[http://ftp.heitec.net/pub/distfiles/voltcraft304-1.0.tar.gz](http://ftp.heitec.net/pub/distfiles/voltcraft304-1.0.tar.gz)

It was written for BSD, but seems to compile for Ununtu 6.06.

I'm not sure how to make the node /dev/thermometer though. It's been a long time since I did this, and can't remember the major and minor numbers I used.

Beef.

---

