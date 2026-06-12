---
title: "sd card doesnt automount when plugged in, but mounts if plugged in during boot up"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by thebestofall007 on 2008-05-13
i have a problem with an impact SD card _NOT_ automounting and showing an icon on the desktop if it _ISN'T_ plugged in when my machine boots up. however, if the card _is_ plugged in during boot up, it _DOES_ mount the way its supposed to (but requires root privileges to mount/unmount). the card is plugged into my acer 5610z laptop's built-in card reader.

what do I do or edit (fstab, etc) to correct this and make Ubuntu mount the card each time i plug it in, _regardless_ of whether I have the card plugged in at boot up or not and with proper permissions? 

i can run the sudo fdisk -l command and the device shows, but it has the problem mentioned above. i have checked the fstab and the device is listed.

---

### Post by andrewski on 2008-06-11
Can you post the contents of /etc/fstab and the output of `ls -l /media`? I'm wondering if there might be something amiss there.

---

### Post by thebestofall007 on 2008-08-25
> **andrewski said:**
> Can you post the contents of /etc/fstab and the output of `ls -l /media`? I'm wondering if there might be something amiss there.

here is the ls -l and /etc/fstab outputs. the mmcblk0p1 line is the device.

---

### Post by andrewski on 2008-08-25
Is that with the device mounted when booting, I'm assuming? What's it look like when it's not mounted?

---

### Post by thebestofall007 on 2008-09-01
same message on the ls -l and fstab as when the device is mounted.

---

### Post by aquamammal on 2008-09-05
I have the same problem~

Anyone got anything on this?

---

