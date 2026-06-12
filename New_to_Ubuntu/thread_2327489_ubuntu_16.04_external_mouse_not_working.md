---
title: "ubuntu 16.04 external mouse not working"
date: 2016-06-11
forum: New to Ubuntu
---

### Post by blade4 on 2016-06-11
Hello all, 

I recently installed Ubuntu 16.04 on my MSI GT70 laptop and now whenever I log into unity, the external mouse stops working. I've narrowed it down to unity specifically cuz I don't have this problem with i3. 

A roundabout solution I'm using right now is : 

```
sudo rmmod usbhid

sudo modprobe usbhid 
``` 

But having to do this every time I log in is a pain. Any tips on a more permanent solution ? I've already tried adding usbhid in /etc/modules and it didn't help. 

Cheers !

---

### Post by X-RED_Tech on 2016-06-11
Reconnecting doesn't work?

---

### Post by blade4 on 2016-06-11
> Reconnecting doesn't work?   Actully reconnecting brings the problem back .. I have to reenter the commands if I reconnect the mouse.

---

### Post by X-RED_Tech on 2016-06-12
This [laptop]("https://www.msi.com/Laptop/GT70-2OD.html#hero-overview")? With the discrete nvidia graphics? If so it may or may not be related with the video drivers. Have you installed the recommended nvidia proprietary drivers (version)?

---

