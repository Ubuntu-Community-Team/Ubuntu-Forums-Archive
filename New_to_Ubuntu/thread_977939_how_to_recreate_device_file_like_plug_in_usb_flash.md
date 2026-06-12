---
title: "how to recreate device file like plug in usb flash drive"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by say2sky on 2008-11-10
We all know when plug in USB flash drive into USB port, OS will create device file such as /dev/sdb and /dev/sdbx for each partition. 

I sync my system onto usb flash drive when it is plug in and it succeed.

Now I hope to go one step further to use cron to automatically this process.

My question is:

How I can recreate device file for usb flash drive just like we plug it into usb port.  

I think perhaps there is a daemon to be run again but I don't know. Any suggestion are greatly appreciated.

---

### Post by Carl Hamlin on 2008-11-10
> **say2sky said:**
> We all know when plug in USB flash drive into USB port, OS will create device file such as /dev/sdb and /dev/sdbx for each partition. 

I sync my system onto usb flash drive when it is plug in and it succeed.

Now I hope to go one step further to use cron to automatically this process.

My question is:

How I can recreate device file for usb flash drive just like we plug it into usb port.  

I think perhaps there is a daemon to be run again but I don't know. Any suggestion are greatly appreciated.

I'm not entirely sure I understand what you're wanting to do. There me be a language barrier issue here, but it sounds like you're wanting to create a mounted device instance without actually mounting a device. Is this correct?

---

### Post by MasterSander on 2008-11-10
Dunno about your problem, but always syncing a flash drive isn't that great, cause unlike a hard drive, flash memory can't be written on forever.

---

### Post by say2sky on 2008-11-10
> **Carl Hamlin said:**
> I'm not entirely sure I understand what you're wanting to do. There me be a language barrier issue here, but it sounds like you're wanting to create a mounted device instance without actually mounting a device. Is this correct?

I add this code to file /etc/udev/rules.d/60-persistent-storage.rules

```

KERNEL=="sdb1",  ATTRS{vendor}=="xxx", ATTRS{model}=="xxx", RUN+="xxx.sh", GOTO="persistent_storage_end"

```

so each time I plug in my usb flash drive, xxx.sh script will run and do the sync I want. 

now my question is 
how I can do this through cron at any time I want not just the time I plug in usb flash drive.

---

### Post by say2sky on 2008-11-12
anyone know how to use command line to emulate the action of pluging usb drive to recreate device file?

---

