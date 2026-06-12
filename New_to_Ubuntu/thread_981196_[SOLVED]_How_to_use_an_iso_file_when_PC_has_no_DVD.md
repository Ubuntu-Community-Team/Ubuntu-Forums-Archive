---
title: "[SOLVED] How to use an iso file when PC has no DVD reader?"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by resander on 2008-11-13
I want to try to install VC++ 2008 =VC2008 via Wine. The VC2008 iso is free from Microsoft and I have it on a DVD, on a USB memory stick and on the desktop. Instructions at MS download site says simply insert the DVD created into the computer and double-click the setup.hta file. 

My PC has a CD drive and cannot read DVDs. 

Is there some way I can make Ubuntu 'see' the setup.hta file by accessing the iso file on the desktop. 

P.S.
Clicking the iso file on the memory stick shows a Readme text file that says the iso contains a filing system in UDF format.

---

### Post by SuperSonic4 on 2008-11-13
I know you can mount a fake cd drive, ie using hard drive space and tricking the PC into thinking it is a DVD drive but I don't know how in ubuntu

---

### Post by pennacook on 2008-11-13
should be able to just mount it as a loop device
```
mount -o loop /<path>/<iso file> /<directory>
```

---

### Post by resander on 2008-11-15
Thanks for your responses...

Mounting is necessary, but not sufficient. Ubuntu must also be able to read the UDF filesystem in the iso image, which contains two parts an 'iso' part and an UDF part.

I have seen posts mentioning that earlier versions of Ubuntu cannot read UDF. Is there a way to make Ubuntu 8.10 'see' and let me access the UDF in iso images?

---

### Post by blackened on 2008-11-15
```
mount -t udf -o loop **/path/to/iso.iso /mount/path**
```

---

### Post by nhasian on 2008-11-15
or if you dont want to be bothered with the command line and like to stick to a gui you can use gmount.

```
sudo apt-get install gmount-iso
```

---

### Post by resander on 2008-11-15
blackkened:
Thanks, I can now access the UDF format files and directories in the iso/udf image.

nhasian:
Thanks, useful to know there is GUI version of mount. It is actually available via Synaptic manager searching for gmountiso. However, it supports iso only, not iso/udf.

---

### Post by binbash on 2008-11-15
[http://www.getdeb.net/app/AcetoneISO](http://www.getdeb.net/app/AcetoneISO)

---

### Post by blackened on 2008-11-15
No sweat, the thanks button is your friend. You should probably mark this thread as solved as well.

---

### Post by resander on 2008-11-15
Thanks, acetoneiso2 also mounts iso images. I have downloaded it and found it supports iso only not iso/udf.

---

