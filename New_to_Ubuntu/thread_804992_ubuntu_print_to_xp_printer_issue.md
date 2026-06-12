---
title: "ubuntu print to xp printer issue"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by mblack3 on 2008-05-23
it doesnt work
i have both vista and and ubuntu on my labtop and i can print to our desktop at home in vista but ubuntu craps out on me. I know that the printer is shared and when i am in ubuntu i go to printer and all that and click on windows printer via samba in new printer but when i click verify, it says that the print share is not accessible
any help people
thanks a lot and God bless

---

### Post by plucky on 2008-05-23
Hope this link helps [https://help.ubuntu.com/community/WindowsXPPrinter](https://help.ubuntu.com/community/WindowsXPPrinter)

Never tried it as my printer is on an Ubuntu machine.

Good Luck

---

### Post by Bartender on 2008-05-24
I can confirm the directions in the link work.  At least they did for me.  Have been getting nowhere for two days (not experienced with networking issues) trying to send a print job to my Dad's wireless HP Photosmart C6180 from the Vista side of our Acer laptop.  Have tried to satisfy basic networking rules (same workgroup name, that sort of thing).
About to give up.  Figured no way would I be able to make it work in Linux.
But I closed out of Vista, started Ubuntu 8.04, and found this thread.
Followed the first set of directions in the link.  After a few minutes of fumbling around, the HP printer spit out a test page sent wireless from 8.04.  So, Ubuntu 1, Vista 0!
The C6180 is seen by the Netgear wireless router, and is hardwired to his XP PC via the USB connection.  Because of the path that Ubuntu saw, I'm not sure whether the print job went thru the XP PC, then via the USB cable, or from the Netgear router to the printer, but the directions did work here...

EDIT: Read this post 
[http://ubuntuforums.org/showthread.php?t=452121&highlight=c6180](http://ubuntuforums.org/showthread.php?t=452121&highlight=c6180)

The thread is old so 8.04 works more automagically than described.  The point is, with Dad's XP PC turned off HPLIP found the printer and sent it a test page via the Netgear router.  I love it when Ubuntu does something faster and easier than Windows!!

---

