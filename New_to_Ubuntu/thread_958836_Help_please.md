---
title: "Help please"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by welder663 on 2008-10-25
I have an HP pavillion dv71027ca,vista premiam 64 bit,ok I had it installed once,seemed to work fine,I uninstalled to try kubuntu,nothing worked,so i uninstalled that.Now I have installed ubunto again.This time my wireless network is not recognized.I have tried everything I think.I cannot connect to the wireless.Now I have security enabled my linksys 802-11n,could that be the problem,man i need help.

---

### Post by ciscosurfer on 2008-10-25
The forums have many threads regarding wireless issues that may already have an answer for you.

---

### Post by lifestream on 2008-10-25
To sum it up, install wicd:

sudo apt-get install wicd

then run

sudo /etc/init.d/wicd start

If the wicd icon doesnt show up on your system tray, run wicd-client


wicd works just great with secured wireless.
Best of luck, hope this helps!

---

