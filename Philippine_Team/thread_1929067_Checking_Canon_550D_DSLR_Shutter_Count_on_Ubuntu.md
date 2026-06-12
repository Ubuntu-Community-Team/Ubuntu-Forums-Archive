---
title: "Checking Canon 550D DSLR Shutter Count on Ubuntu"
date: 2012-02-21
forum: Philippine Team
---

### Post by ragadanga63 on 2012-02-21
Getting a Canon 550DSLR's shutter count is a real pain.  It turns out Linux has the best solution- gphoto2.

First install gphoto2 and libgphoto2-2 using sudo apt-get or Synaptic.

Once installed, connect the DSLR.  Unmount it.

Fire up the Terminal and type the following command:  

gphoto2 --get-config /main/status/shuttercounter

Press Enter and voila!  

It can also be used for other DSLR's as well, though it couldn't determine the shuttercount when I tried it on a Nikon D3000.

---

### Post by tech-hero on 2012-02-21
wow. thanks for the info sir.

---

### Post by gamels on 2012-03-24
Is this for the Canon camera only or pwede bah yung Nikon??

---

### Post by ragadanga63 on 2012-04-09
A list of supported Cameras:

[http://gphoto.org/proj/libgphoto2/support.php](http://gphoto.org/proj/libgphoto2/support.php)

You may refer to the same site for the commands.

---

