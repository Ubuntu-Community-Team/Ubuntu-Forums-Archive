---
title: "Rhythmbox importing library"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by tone33 on 2008-05-15
So I've got Ubuntu x64 running dual boot with Vista.  I can import my music library (mp3's) from a vista ntfs drive without issue, but every time I restart my machine I have to reimport - what's the skinny?

---

### Post by Dynamo_Joe on 2008-05-15
Hi tone33, 

Is your NTFS drive automatically mounted at boot-up in Ubnuntu? 

If not, then the behaviour is normal because Rhythmbox will assume that the drive does not exist all the time and will require re-import every time. 

Try mounting the NTFS drive first then open Rhythmbox and you will find that you do not need to re-import the folder(s) again.

---

### Post by tone33 on 2008-05-15
The drive shows up in the file browser on every boot - doesn't that mean it's being mounted?

---

### Post by Xiong Chiamiov on 2008-05-15
> **tone33 said:**
> The drive shows up in the file browser on every boot - doesn't that mean it's being mounted?
It depends on where it's showing up.  Ubuntu will automatically mount some drives when you double-click them in the media folder (or whatever it is in Gnome).  Could you please copy and paste the your fstab here?
```

gedit /etc/fstab

```
will open it up for easy viewing.

---

### Post by Dynamo_Joe on 2008-05-15
Hi tone33, 

The drive "showing up in the file browser" doesn't actually mean it is mounted ... usually it requires a "double-click" and another "click" before you can actually see the contents of the drive ... when you can "browse" the contents of the drive, then it is "mounted". 

Try "double-clicking" on the NTFS drive and then try accessing it. Once you can see the contents, then start Rhythmbox and you shouldn't need to re-import the folder(s) again. 

Hope this helps.

---

### Post by tone33 on 2008-05-15
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=791fa0ab-a395-407b-990e-16c37d50630f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=a6f2191a-db43-424f-99b4-dad41b88fd3d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0



you guys rock.  thanks for all the responses-i'm learning so much about linux already.  I can browse it easily once I double click on it..   Need to read up a little on this /etc/fstab file and figure out what it does..  looks like drive mounting instructions

---

