---
title: "My media HD"
date: 2015-03-18
forum: New to Ubuntu
---

### Post by hmiersch on 2015-03-18
I keep my media files on an external HD that was formatted under OSX. Problem is, it is journaled which i think is why Ubuntu sees that HD as a read-only file system. So I went to the apple store and they told me I couldn't turn journaling off, I'd have to reformat the HD. So the question is, how do I format a HD without journaling? Disk utility gives me several options for OSX format, but they are all journaled. I don't want to use ms-dos or exfat formats. So how do I format that HD?
Can I format it under Ubuntu in a format that OSX can access?

---

### Post by dino99 on 2015-03-18
i doubt that journaling and 'read only' can be linked; it's fully different. If you have rights on that 'data' then its up to you to set it 'read only' or not.

googling around 'ubuntu osx data share' is a start point
[http://lifehacker.com/5702815/the-complete-guide-to-sharing-your-data-across-multiple-operating-systems](http://lifehacker.com/5702815/the-complete-guide-to-sharing-your-data-across-multiple-operating-systems)

---

### Post by sandyd on 2015-03-18
Journaling must be turned off if you want to mount it as read/write. Ubuntu can't handle journaled HFS+

1. [Turn off journaling (Direct Apple Support Document)]("https://support.apple.com/en-us/ht2355")
2. Unmount it
3. Install the hfsprogs package
```
sudo apt-get install hfsprogs
```
4. Use ```
sudo fdisk -l
``` to determine partition (/dev/sdxy)
5. Create mount point
```

mkdir ~/macmount
```
6. Mount it, replacing /dev/sdxy with partition from step 4
```
sudo mount -t hfsplus -o force,rw /dev/sdxy ~/macmount
```

Side note; Above is for HFS+ Journaled Volumes.

---

### Post by hmiersch on 2015-03-19
> **sandyd said:**
> Journaling must be turned off 

The "genius" at the apple store told me that journaling couldn't be turned off, but thanks to this forum I now know that was a lie. Oh well, one more reason to give apple the finger. 

But yeah, I've managed to get my new HD formatted without journaling, and I can access it from both OSX and Ubuntu. Now it's time to copy all the files over and then turn off journaling on the existing media HD. I want to copy the files first in case something goes wrong...

---

