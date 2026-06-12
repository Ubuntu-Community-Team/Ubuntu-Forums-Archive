---
title: "grub not working"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by oliwood2 on 2008-07-26
heres the story..
i booted from a live disk and i installed ubuntu on a usb memory stick on a machine running windows and now when i try to boot i just get error 21 :(

---

### Post by boblemur on 2008-07-26
is that a windows error a ubuntu error or a grub error? what happens exactly??

and did you just install ubuntu normaly as though you would onto a hard drive?? or did you use the peddrive linux guide?

---

### Post by Thingymebob on 2008-07-27
Error 21 is a grub error, It means can't find disk.
Your usb stick will need to be in and accessible by the machine at boot.
I would recommend you follow one of these guides
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent")
[https://help.ubuntu.com/community/BootFromUSB]("https://help.ubuntu.com/community/BootFromUSB")

---

### Post by kansasnoob on 2008-07-27
Can you still boot with the USB memory stick plugged in?

I'll bet you wiped out the Win MBR.

Is this XP or Vista?

EDIT: No worry .............. it can be fixed!

---

### Post by oliwood2 on 2008-07-27
i installed it like i would on a harddrive with the live cd
and it doesnt help having the usb memory stick plugged in while booting
EDIT: the problem was that it installed grub on the harddrive instead of the usb memory stick
and btw im using vista

---

### Post by kansasnoob on 2008-07-27
You need to restore Vista's MBR. Do you have a Vista recovery/installation disc?

---

### Post by kansasnoob on 2008-07-27
The following explains quite well how to restore Vista's MBR if you do have the Vista DVD/CD set:

[http://www.winvistatips.com/fix-mbr-a116.php](http://www.winvistatips.com/fix-mbr-a116.php)

If you don't have the install media, it's available in a download.

I'm looking for the link. It's buried in my junk somewhere.

---

### Post by kansasnoob on 2008-07-27
This is what I was looking for:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by oliwood2 on 2008-07-27
Thank you so much!!
works now >D but as you can see my keyboard doesnt but thats for another time btw how does the thank system work?

---

