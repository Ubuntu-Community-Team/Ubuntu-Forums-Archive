---
title: "usb stopped working after  update"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by sully53 on 2008-06-24
I have a problem with usb system bus. 
I am new to Linux. I decided to give Ubuntu a try.

After a fruitless attempt at trying to get my Fd7000 Belkin pci card to work.  I decided to buy an edimax usb wireless card

When I plugged the edimax it worked out of the box.

I then upgraded the system once I was online and now my usb has stopped working.The card activity light flashes at boot then doesn't mount. Any Usb device will not work. 

Any ideas

---

### Post by Yuki_Nagato on 2008-06-24
Try

```
sudo mount -a
```

This mounts all of the devices mentioned in your "fstab" file to be mounted to your OS.  It might not work though, so we might have to delve deeper.

I used the command

```
man mount
```

to find that out.

---

