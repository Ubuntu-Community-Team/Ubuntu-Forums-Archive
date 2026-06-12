---
title: "Update libusb"
date: 2012-06-28
forum: New to Ubuntu
---

### Post by d4bs on 2012-06-28
Hi
i am using 10.4.4 LTS (2.6.32)

I currently have libusb 0.1-4 installed but need to update to a newer version, is this possible? 
I have tried using 'apt-get' but it doesnt update anything new.

Any help would be appreciated.

Regards

---

### Post by jmfal on 2012-06-28
Welcome to Ubuntu

Try this in a terminal

```
 sudo apt-get update     
```

Then 

```
sudo apt-get upgrade   
```

This will upgrade all the apps/packages that you have installed.

---

### Post by Curtis6767 on 2012-06-28
> **d4bs said:**
> Hi
i am using 10.4.4 LTS (2.6.32)

I currently have libusb 0.1-4 installed but need to update to a newer version, is this possible? 
I have tried using 'apt-get' but it doesnt update anything new.

Any help would be appreciated.

Regards

Version 0.1-4 2:0.1.12-20 is showing in the Software Center in 12.04. If you use Synaptic, you should be able to find your version and then check for updates.

And there's this: [http://www.linux-usb.org/](http://www.linux-usb.org/)

---

### Post by d4bs on 2012-06-28
Sorry, i should have said im using the server edition so need to do everything through putty on my Windows7 pc.

I have found this: [http://downloads.sourceforge.net/project…b-1.0.9.tar.bz2](http://downloads.sourceforge.net/project…b-1.0.9.tar.bz2)

But im having MAJOR trouble installing it. Can someone please tell how its done? My head is spinning searching google :redface:

---

### Post by cortman on 2012-06-28
> **d4bs said:**
> Sorry, i should have said im using the server edition so need to do everything through putty on my Windows7 pc.

I have found this: [http://downloads.sourceforge.net/project…b-1.0.9.tar.bz2](http://downloads.sourceforge.net/project…b-1.0.9.tar.bz2)

But im having MAJOR trouble installing it. Can someone please tell how its done? My head is spinning searching google :redface:

Did you first try jimfal's suggestion?
I would strongly recommend that you NOT install it manually from a tarball.

---

### Post by d4bs on 2012-06-28
> **cortman said:**
> Did you first try jimfal's suggestion?
I would strongly recommend that you NOT install it manually from a tarball.

Yes and it has updated things, but libusb is still 1.0.4 

thanks

---

### Post by d4bs on 2012-06-28
If anyone else could help me, i would appreciate it.

---

### Post by cortman on 2012-06-28
Please post the full link to the site rather than "....." in the middle, and I'll download it and see what needs to be done.

---

### Post by d4bs on 2012-06-29
> **cortman said:**
> Please post the full link to the site rather than "....." in the middle, and I'll download it and see what needs to be done.

I'm very grateful, thank you. Clicking this link starts the d/l. I wasn't sure if live links were permissible here.

[http://sourceforge.net/projects/libusb/files/libusb-1.0/libusb-1.0.9/libusb-1.0.9.tar.bz2/download?use_mirror=switch](http://sourceforge.net/projects/libusb/files/libusb-1.0/libusb-1.0.9/libusb-1.0.9.tar.bz2/download?use_mirror=switch)

---

### Post by d4bs on 2012-07-01
I managed to find a tutorial.

Thanks anyway.

---

