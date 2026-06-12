---
title: "USB com port issue [ttyUSB*]"
date: 2010-04-23
forum: Programming Talk
---

### Post by rockom on 2010-04-23
Hello,

I'm having an issue with freeing up a ttyUSB port.  

I'm using a USB Com port cable to talk to a serial device.  When I plug it in, Ubuntu assigns is ttyUSB0.  When not communicating, If I unplug it, ttyUSB0 goes away.  Once I recognize I'm no longer connected, I need to close the port in my code.  If I fail to close the port, the resource is not freed.  When I plug the cable back in, Ubuntu assigns it ttyUSB1 because my app is still holding ttyUSB0 open.  So, If I can no longer see the port, I close it.  Once closed, when I plug the cable back in, Ubuntu assigns it ttyUSB0.  Very slick (I wish windows did this).

Now for my issue.  I have an instance where I'm sending data to my device via ttyUSB0.  I unplug the cable to create a lost connection.  ttyUSB0 no longer shows up in /dev. Now that I can no longer communicate, I close the port.  closing the port returns a -1 because the port does not exist.  I plug the cable back in.  I'm expecting to pick up ttyUSB0 however, Ubuntu assigns ttyUSB1.  I can't get ttyUSB0 back until I close my app.  As soon as I close my app, the next time I plug in a cable, it's assigned ttyUSB0.

This only happens mid stream while communicating.  If' I'm sitting idle, this does not happen.  Any ideas on how to get ttyUSB0 back without closing my app?

Thanks,
-Rocko

---

### Post by azagaros on 2010-04-24
My father found this problem on the Ubuntu platforms... he uses fedora...  

I don't know what is the exact cause we didn't look that far into it but it is associated to the Ubuntu platforms since 8.x.

---

### Post by sj1410 on 2011-06-02
has anybody found a solution to this problem

please share

---

### Post by rockom on 2011-06-06
I'm not having this issue anymore.

After I close my port, I use tcsetattr() to clear out the port settings (set to defaults).

Also, When changing port settings I was trying to open an open port....this was causing issues.    

-Rocko

---

