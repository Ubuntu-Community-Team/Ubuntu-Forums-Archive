---
title: "cheese"
date: 2011-10-21
forum: New to Ubuntu
---

### Post by rburkartjo on 2011-10-21
does anyone have a fix for the program cheese. i just noticed that this webcam program is no longer working.

---

### Post by no2498 on 2011-10-21
you may try this in a terminal
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese

---

### Post by rburkartjo on 2011-10-21
no tks didnt work. also know program wont load in my linux mint partition and found that is a bug that has been reportetd but not fix.

---

### Post by dFlyer on 2011-10-21
It's working here, have you tried uninstalling and reinstalling?

---

### Post by rburkartjo on 2011-10-21
df gave that a shot didnt work. would have been a good fix if worked. oh well bug report just have to wait and see if future updates fix

---

### Post by no2498 on 2011-10-22
look in your system's startup programs see if cheese or skype is set to auto start at start if yes turn them off
then restart the computer

---

### Post by dunbrokin on 2011-10-22
I have the same problem.....cheese worked in 10.10 but has been very problematical since then....

---

### Post by rburkartjo on 2011-10-23
dun glad it is not just me. hope some updates fix it soon.

---

### Post by rburkartjo on 2011-10-23
just got a fix. at least it works on my end. i still have cheese installed but it fails to load. i just installed camorama webcam viewer from the software center. if i run the program my webcam works. go figure. thought i would share and hope it works for others.

---

### Post by Sch_030 on 2011-12-03
I had the same problem with Cheese Webcam w/ Logiitech Portable Webcam.  (Cheese Webcam worked fine w/ the same hardware and Fedora 14 -- no idea what's different). Camorama install worked great.

---

### Post by ubudog on 2011-12-03
Do you have any webcam programs that start automatically on boot?  Like video4linux or anything?

---

### Post by TedinOz on 2012-02-17
> **Sch_030 said:**
> I had the same problem with Cheese Webcam w/ Logiitech Portable Webcam.  (Cheese Webcam worked fine w/ the same hardware and Fedora 14 -- no idea what's different). Camorama install worked great.

A recent Partial Upgrade took out Cheese for me and although still in USC, wouldn't install due to unresolved dependencies. In Synaptic I tried to re-install dependencies to find that further important software would be un-installed so I gave up. Just installed Camorama and it works just fine although no video recording. I couldn't find any bug reports for the cheese problem so far but will keep searching. Any further info will be most welcome.

---

