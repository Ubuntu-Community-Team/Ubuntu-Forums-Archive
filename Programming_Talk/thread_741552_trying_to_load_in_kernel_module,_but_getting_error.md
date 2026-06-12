---
title: "trying to load in kernel module, but getting error"
date: 2008-03-31
forum: Programming Talk
---

### Post by yaazz on 2008-03-31
I'm trying to follow this tutorial on kernel modules 
[http://www.freesoftwaremagazine.com/articles/drivers_linux?page=0%2C10](http://www.freesoftwaremagazine.com/articles/drivers_linux?page=0%2C10)

and have the module written, and the device wired up and ready, but when I try to  load in the module, I am getting an error 
insmod: error inserting 'parlelport-driver.ko': -1 Device or resource busy 


here is the full output

$ sudo mknod /dev/parlelport c 61 0
$ sudo chmod 666 /dev/parlelport 
$ sudo insmod parlelport-driver.ko
insmod: error inserting 'parlelport-driver.ko': -1 Device or resource busy 

does anyone see why this would be happening

---

### Post by Zugzwang on 2008-04-01
Hmm, I can't find the source of that kernel module on the page you mentioned. However, as a quick guess, did you follow the instructions on [this page]("http://www.freesoftwaremagazine.com/articles/drivers_linux?page=0%2C10"), i.e. did you remove all the other drivers for the parallel port beforehand?

---

