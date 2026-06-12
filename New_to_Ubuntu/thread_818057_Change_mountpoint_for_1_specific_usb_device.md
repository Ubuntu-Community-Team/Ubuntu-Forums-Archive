---
title: "Change mountpoint for 1 specific usb device"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Europegirl on 2008-06-04
... after it won't mount anymore due to an error in the latest mountpoint.

This is problably the most stupid thread ever, but anyway, I'll give this a try. 

When I changed the mountpoint for a specific usb device, just by right-clicking on the mounted device on the desktop, I did something wrong. I don't know what, but when I plug in that device now, it will not mount anymore. Maybe because of some error in the new location name or something. But because the device won't mount, I don't know how to change the mountpoint to default.

What can I do?

---

### Post by kpkeerthi on 2008-06-04
Did you try to change the mountpoint by right-clicking the mounted device? When specifying mount point in the device properties, there should be no slash. If you want it mounted at /media/MyUSBDisk, you only need to enter MyUSBDisk in the device properties from right-click menu. See [https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/107668](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/107668) for a fix.

Alternatively, you may change the [device label]("https://help.ubuntu.com/community/RenameUSBDrive") to something unique & meaninful. Unplug & plug it back in.

---

### Post by Europegirl on 2008-06-04
I think my explanation was a little confusing, I'm sorry for that.. so I will try to explain it again. :) 

> **kpkeerthi said:**
> Did you try to change the mountpoint by right-clicking the mounted device?
Well, yes, that's how I changed it.

> When specifying mount point in the device properties, there should be no slash.
Maybe that's why there is an error now, because I did use a slash.. :$

So because of the error, my usb-stick will not mount. So I can't right-click on the mounted usb volume on my desktop.
Is there another way to change the mountpoint of that specific usb stick, without the obligation to mount it first?

---

### Post by kpkeerthi on 2008-06-04
There is a link to the fix in my earlier post.

---

### Post by Europegirl on 2008-06-04
You're right, I'm sorry. The problem mentioned in the link you gave me is exactly what I meant.

I found something that seems to be a good explanation, but I don't understand the last part:
> 
In my /media directory existed:
/CDback
/CDback_
/CDback__
/Mint
/Mint_
/Mint__

In my drive, I have two partitions. I would like to see them always mount to /CDback and /Mint.

Be careful here. I did a quick "gksudo thunar" (or gksudo nautilus), and erased ONLY those mount directories which were related to my drive. you dont want to erase your standard hard drive's mounting point, or your CD-ROM etc etc etc (sda,hda,cdrom,cdrom0,etc). Many a folk will likely scold me for even mentioning doing this. a sudo rm MOUNT-DIRECTORY would suffice for each sloppy underscored directory as well. return to gconf-editor and remove the text from the 'value' field.

exit, plug back in...BAM! brilliant.
Thanks in advance.

---

### Post by kpkeerthi on 2008-06-04
Can you post the output of below command?
```
ls /media
```

---

### Post by Europegirl on 2008-06-04
That'll be:

cdrom  cdrom0

---

### Post by kpkeerthi on 2008-06-04
You don't have to be concerned about the below as you don't seem to have the ghost folders mentioned.
> 
In my /media directory existed:
/CDback
/CDback_
/CDback__
/Mint
/Mint_
/Mint__

In my drive, I have two partitions. I would like to see them always mount to /CDback and /Mint.

Be careful here. I did a quick "gksudo thunar" (or gksudo nautilus), and erased ONLY those mount directories which were related to my drive. you dont want to erase your standard hard drive's mounting point, or your CD-ROM etc etc etc (sda,hda,cdrom,cdrom0,etc). Many a folk will likely scold me for even mentioning doing this. a sudo rm MOUNT-DIRECTORY would suffice for each sloppy underscored directory as well. return to gconf-editor and remove the text from the 'value' field.

exit, plug back in...BAM! brilliant.


---

### Post by Europegirl on 2008-06-04
Ok, it's done. :)

Thanks a lot!

---

