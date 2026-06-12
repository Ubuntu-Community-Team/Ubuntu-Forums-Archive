---
title: "Unable to Mount the Volume..."
date: 2008-11-01
forum: New to Ubuntu
---

### Post by kvanbev1087 on 2008-11-01
I'm sorry to be so repetitive, I've seen this question around the forums, but I am trying to figure this all out, but I'm so new that I have no idea what I'm doing lol

I wanted to back up my files.  It is not recognizing the external hard drive where I'd like to put them.  I am running 8.10, and when I put in the external hard drive I get an "cannot mount volume" error.

When I click "Details" it describes how to force it via "mount -t ntfs-eg/dev/sdb1/media/Queens -o force" but when I do that it just goes to the help for mount.  I then tried the fstab apprach, but I am not seeing the external drive.  When I view my computer, though, I do see the drive.

Any ideas?

---

### Post by kansasnoob on 2008-11-01
Try installing pmount:

```
sudo apt-get install pmount
```

Usbmount works in a similar manner. From the description at synaptic:

> USBmount is intended as a lightweight solution which is independent of
a desktop environment. Users which would like an icon to appear when an
USB device is plugged in should use the pmount and hal packages
instead.

If the drive is formatted NTFS you may also find either ntfs-config or ntfsprogs useful.

---

### Post by kvanbev1087 on 2008-11-01
Alright, I installed that, but now what happens?  It still won't recognize it.  I'm not sure what that did.  Sorry, I am clueless!

---

### Post by taurus on 2008-11-01
What model/brand is that external USB drive?  Can you post the output of this command from a terminal after you've plugged in the drive to a USB port?

```
dmesg | tail
```

---

### Post by kvanbev1087 on 2008-11-01
I was able to run that code and this is what came up:

[ 5055.399298] sd 8:0:0:0: [sdb] Write Protect is off
[ 5055.399322] sd 8:0:0:0: [sdb] Mode Sense: 27 00 00 00
[ 5055.399331] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 5055.409255] sd 8:0:0:0: [sdb] 58633344 512-byte hardware sectors (30020 MB)
[ 5055.433205] sd 8:0:0:0: [sdb] Write Protect is off
[ 5055.433233] sd 8:0:0:0: [sdb] Mode Sense: 27 00 00 00
[ 5055.433242] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 5055.434754]  sdb: sdb1
[ 5055.493548] sd 8:0:0:0: [sdb] Attached SCSI disk
[ 5055.493966] sd 8:0:0:0: Attached scsi generic sg2 type 0

---

### Post by taurus on 2008-11-01
What happens if you run

```
sudo mkdir /media/Queen
sudo mount -t ntfs-3g /dev/sdb1 /media/Queen
df -h
```

---

### Post by kvanbev1087 on 2008-11-01
I get this:

Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/Queens -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/Queens ntfs-3g force 0 0

That is the same error I get when I try to click the external hard drive from computer.

---

### Post by kvanbev1087 on 2008-11-01
Note: I ran the second option where I updated fstab and the rebooted, and I got a new error:

Unable to Mount Volume
You are not privileged to mount the volume 'Queens'

---

### Post by taurus on 2008-11-01
Looks like you didn't "unmount" your USB harddrive cleanly the last time you used it.  Therefore, it's a good idea to boot into Windows, plug in the external harddrive, then unmount it from the icon in the bottom right corner (next to the clock).  Don't just unplug it if you want to remove it.  Unmount it first, even in Windows, before unplugging it.  Otherwise, you need to use the force option to mount it in Ubuntu.

```
mount -t ntfs-3g /dev/sdb1 /media/Queens -o force
```

---

### Post by kvanbev1087 on 2008-11-01
That worked! Thank you so much :)

---

