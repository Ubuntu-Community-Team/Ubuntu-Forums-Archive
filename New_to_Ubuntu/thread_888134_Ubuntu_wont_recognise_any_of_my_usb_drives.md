---
title: "Ubuntu wont recognise any of my usb drives"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by chaka53 on 2008-08-12
Good Morning

I installed the latest Ubuntu - love it but it won't recognise any of my usb  drives.

I have a Western Digital external drive and several usb flash drives.

I have plugged and unplugged,  booted without the drives and then inserted also booted with the drives.  No result

Any help would be appreciated.

:confused:

---

### Post by Pro-reason on 2008-08-12
OK, so they are not automounting.  That may be a problem with *hal*, the program that handles that.

Please plug in your devices, open a terminal, and enter this command:

```

sudo blkid

```
Copy the output and paste it here, between [noparse]```
...
```[/noparse] tags.

That will give us info on your drives.  We'll be able to see if Ubuntu recognises them or not.

It would also be a good idea to give us the output of the following command:

```
cat /etc/fstab
```

You might also want to refer to this [documentation]("https://help.ubuntu.com/community/MountDevicesTroubleshooting").

---

### Post by xe1ufo on 2008-08-21
I had my external Western Digital 230-Gig hard drive working fine under Ubuntu 7.10. Then I upgraded to 8.10 and no matter what, I cannot mount it when connected to the USB port. 

BUT: The drive also has a FireWire port. I plugged in the FireWire cable made to go from the video camera to the laptop, and it worked instantly. It is also much faster then USB.

---

