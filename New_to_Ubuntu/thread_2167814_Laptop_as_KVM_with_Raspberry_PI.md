---
title: "Laptop as KVM with Raspberry PI?"
date: 2013-08-15
forum: New to Ubuntu
---

### Post by ConcreteDonkey on 2013-08-15
I was wondering it would be possible my laptop as a KVM (without the M part) I don't have anything freely available like keyboards a such  this would be the perfect solution. Any help would be appreciated.

Thanks,

---

### Post by JRV on 2013-08-15
This will work to access the RPi from another computer if you don't have a network:

[http://learn.adafruit.com/adafruits-raspberry-pi-lesson-5-using-a-console-cable](http://learn.adafruit.com/adafruits-raspberry-pi-lesson-5-using-a-console-cable)

----------------------------------------------------------------------------------------------

If you have a network using ssh works. 

I usually log in with the command:```
ssh -X USERNAME@HOSTNAME
``` 
[http://learn.adafruit.com/adafruits-raspberry-pi-lesson-6-using-ssh](http://learn.adafruit.com/adafruits-raspberry-pi-lesson-6-using-ssh)

The -X (Capital X) allows you to run graphic programs

----------------------------------------------------------------------------------------------

[http://learn.adafruit.com/adafruit-raspberry-pi-lesson-7-remote-control-with-vnc](http://learn.adafruit.com/adafruit-raspberry-pi-lesson-7-remote-control-with-vnc)

This tutorial explains how to run the full graphic environment remotely.

---

