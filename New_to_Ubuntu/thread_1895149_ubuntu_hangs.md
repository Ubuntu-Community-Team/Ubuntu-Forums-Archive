---
title: "ubuntu hangs"
date: 2011-12-14
forum: New to Ubuntu
---

### Post by crave-n on 2011-12-14
hi.... i'm a newbiw to ubuntu .
normally ubuntu runs fine on my system, but while installing software or while running multiple tabs in firefox ,ubuntu chruns up my cpu usage....
any suggestions???
:confused:

---

### Post by BC59 on 2011-12-14
Did you install the proprietary drivers for your Graphics card?

---

### Post by crave-n on 2011-12-14
do u mean the driver softwares from ubuntu ?

---

### Post by BC59 on 2011-12-14
Yes. To install them search **Joker** in the dash.

---

### Post by crave-n on 2011-12-14
sorry couldnt find anything called joker in the dash

---

### Post by BC59 on 2011-12-14
Sorry you have right. Check for Jockey and additional drivers.

---

### Post by crave-n on 2011-12-14
it says "no proprietary drivers are in use on this system"

---

### Post by BC59 on 2011-12-14
So there is no option to activate a driver?

---

### Post by crave-n on 2011-12-14
nope... the enable button cannot be selected...:(

---

### Post by BC59 on 2011-12-14
What type of driver might be installed according to the application? can you copy and paste it?

---

### Post by crave-n on 2011-12-14
the additional driver doesnt show me any application itself it just gives me a blank screen

---

### Post by crave-n on 2011-12-14
the additional driver doesnt show me any application at all it just gives me a blank screen

---

### Post by BC59 on 2011-12-14
Open a terminal with CTRL+ALT+T and paste this (with SHIFT+ALT+V) and run this:

```
lspci | grep VGA
```

Then copy and post the result.

---

### Post by crave-n on 2011-12-14
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)

---

### Post by Hylas de Niall on 2011-12-14
I'm going to watch this thread with interest, as the exact same thing is happening to my machine, and seems to be increasing in frequency as well.

---

### Post by BC59 on 2011-12-14
Looks like the Graphic Card is not causing the problem. Then you have to tweak Firefox. Look here and follow the instructions:

[http://warnet-nganjuk.blogspot.com/2011/02/to-fix-firefox-ubuntu-cpu-usage-100.html](http://warnet-nganjuk.blogspot.com/2011/02/to-fix-firefox-ubuntu-cpu-usage-100.html)

---

### Post by crave-n on 2011-12-14
thanks BC59.... :)

---

### Post by crave-n on 2011-12-14
it's not bad but  the cpu still flashes the processing light when i start the software center ....:)

---

### Post by BC59 on 2011-12-14
I don't know if this applies to your problem:

[http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html)

---

