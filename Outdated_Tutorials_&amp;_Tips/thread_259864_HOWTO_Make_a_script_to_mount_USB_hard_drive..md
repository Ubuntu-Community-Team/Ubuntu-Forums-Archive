---
title: "HOWTO: Make a script to mount USB hard drive."
date: 2006-09-18
forum: Outdated Tutorials &amp; Tips
---

### Post by scott_ttocs46 on 2006-09-18
Recently, I put my external USB drive in the /etc/fstab file to automatically mount it on boot.

Recieved an error.

To make a long story short, there are a thousand ways to configure the fstab when probably only a handful are going to work for you.

So, to resolve my problem, I created a script to run on boot.

Step-by-step:

# sudo mkdir /mnt/sda1
# cd /etc/init.d/
# vim SCRIPTNAME

------------------------SCRIPT------------------------
#!/bin/sh
mount -t ext3 /dev/sda1 /mnt/sda1
------------------------SCRIPT------------------------

# chmod +x SCRIPTNAME
# update-rc.d SCRIPTNAME DEFAULTS

Now, reboot your system and it should work. (may have to edit script appropriately. i.e. filesystem, device name)


Hope this helps,
Scott

---

### Post by kidders on 2006-09-18
This script has the same effect as adding the following to your /etc/fstab:

```
/dev/sda1 /mnt/sda1 ext3 defaults 0 0
```

Of course, having more than one removable device plugged in at the same time may break both.

---

### Post by dgorchak on 2006-09-18
```
sudo apt-get install usbmount
```

I think it's more useful :)

---

### Post by scott_ttocs46 on 2006-09-18
For some reason those did not work for me.

---

### Post by dgorchak on 2006-09-18
Did you edit /etc/usbmount/usbmount.conf? By default it doesn't mount FAT USB drives

---

