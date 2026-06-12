---
title: "Forced mount my usb drive, lost power and can't re-mount"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by Xzinum on 2008-07-21
Hi guys, 

I mounted a USB disk using the -o force command since i previously hadn't use Safely remove device in windows. Everything was working great, the drive was automounting and all that. Overnight, we lost power and i quickly shutdown my pc to avoid any damage to my data. It was 3am, and i did not unmount my drive prior to shutting down. Now i can't access my drive in either ubuntu or windows. In WinXP, the drive does not appear but the safely remove disk is there but i cannot terminate it since it says that the drive is in use.

How do i get my drive functionning again? I am aware that i may have corrupted or lost data, but i want to give it a try just to see.

---

### Post by Potatoj316 on 2008-07-21
When you shut down your computer was it through the shutdown button where everything goes down nicely or was it through a power removal?  If you used shutdown to turn your computer off it should auto unmount your drive.  Maybe you could try ```
sudo umount /media/disk
``` Im dont really expect that to work though, but its worth a try.

---

### Post by bumanie on 2008-07-21
If you are not worried about the data and assuming the drive won't mount in ubuntu, but is recognized > sudo apt-get install gpartedThen go to System --> Administration --> Partition editor and active the editor. Try reformatting it. Most usb pendrives are formatted to FAT16. No guarantees, but it maight work. If ubuntu does not recognizr it at all - things will be harder.

---

### Post by Xzinum on 2008-07-21
It shutdown nicely, I had time to shut it down when my ups was beeping.

Now the problem is that it shows up on my desktop, but i can't access it. It's "auto-mounted" but not mounted in /media

I do want to try to keep the data that's on the drive. But i also understand that if there is no other way i'll have to format it.

I get this error

A security policy place in prevents this sender from sending this message to this recipient, see message bus 
configuration file (rejected message had interface "org.freedesktop.Hal.Device.Volume" member "Mount" error name "(unset)"
destination "org.freedesktop.Hal")

---

### Post by bumanie on 2008-07-21
That is saying that the Hardware Allocation Layer can't do anything with it. Try to unmount it (right click, unmount on drop box) then try as above suggestion.

---

### Post by Potatoj316 on 2008-07-21
That sounds like it might not be mounted, if that is the case try 
```
sudo mount /dev/sdb1 /media/disk
```

you might have to change the sdb1 part around, maybe hdb1, sba1, hda1, usb.  Im not too familiar with mounting usb flash drives, it works for usb hard drives

---

