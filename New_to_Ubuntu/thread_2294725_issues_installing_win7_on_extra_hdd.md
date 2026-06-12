---
title: "issues installing win7 on extra hdd"
date: 2015-09-12
forum: New to Ubuntu
---

### Post by eddyg on 2015-09-12
Hey guys I have 14.04 installed on my 120GB ssd for day to day + F@H and I love it 

I have 1TB and 500GB drives on this machine id like to install win7 on one of them for gaming. when i put my disk in and try to install windows i get error messages. 

Ive used Gparted to format and partition both drives to NTFS and still no luck? 

I understand this is a windows mostly related question but ive never had an issue till i put ubuntu on. Do they not play well together lol 

regards, 
eddy

---

### Post by Mark Phelps on 2015-09-12
Whenever you go to install Windows, you should have ONLY the target drive connected; otherwise, you risk getting boot loader information installed automatically to the wrong drive, which will be very difficult to fix.

Open a terminal and post the results of "fdisk -lu" (lowercase L, not a one) on the target windows drive.

---

### Post by QIII on 2015-09-12
And it might be helpful to let us know the exact errors you are getting.  "...getting errors..." is not particularly helpful.

---

### Post by yancek on 2015-09-12
You haven't indicated how these two drives are connected to your computer.  If they are usb, give it up because windows doesn't support installation to usb or IEEE 1394 ports.

---

