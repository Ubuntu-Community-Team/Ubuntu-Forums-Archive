---
title: "[SOLVED] usb disk drive causes permissions problem"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-10-20
**Yesterday**

I have a new Sabrent external usb 2.0 hard drive enclosure. The drive is an 80 gig WD. It had some Microsoft code on it. Probably xp. The drive was a gift, so I don't know for sure.

I installed the drive with jumper at 'master' per the Sabrent manual. I plugged the drive in to the usb and then powered it up. The device did not get a Desktop (/home/mark/Desktop) icon. I found it in Places/Computer. It could not be mounted. I d/l's GParted, formatted (without specifying Disk Label) for Pri. Part and ext3. Rebooted. Drive icon shows on desktop but cannot be written to. Permission for it and two memory sticks now say "The permissions of xxxxxx could not be determined". I opened gksudo nautilus and changed the permissions of the 80 gig. Rebooted. Still says "not be determined".

Did more fooling around by setting jumper as Cable Select (CS). Reformatted under GParted as ext. part and ext2. Didn't work except that I could copy a file during that session but upon rebooting the drive was inaccessable.

Device is usb 2.0 and plugged into 2.0 port

**TODAY**

relevant outputs:

lsusb does not show the device

gnome file mgr. shows the device, giving it the name usb in /media and I can read & write to it. Yikes!

How can I get an icon for this device on the desktop?

---

### Post by Mark_in_Hollywood on 2008-10-21
I believe that this problem was caused by setting the jumper on the drive to Master. It went back to an icon appearing on the /home/mark/Desktop when I set the jumper to cable select.

---

