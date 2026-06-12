---
title: "Problem with system program"
date: 2013-05-18
forum: New to Ubuntu
---

### Post by korporalbenjamin on 2013-05-18
After every start of my Firefox Internet browser I get this message:

"Recognition of network service disabled. Your network has a .local domaine. This is not recommended and is not compatible with AVAHI recognition of network services. Service has been disabled."

The message has arisen some time ago when with the assistance from a local Ubuntu forum I replaced a driver program for the printer to rectify a problem with unstable printing. The operation was successful as the printer is now running perfect, but in connection with the replacement I probably have made some mistakes, which I will now ask for help to get corrected, because I cannot myself figure out what is behind the said message.

For information I shall mention that my computer uses a processor named Intel Pentium (R) Dual CPU E2180@2.00HZX2, OS type 32 bit, and I use Mozilla Firefox 21.0 with Ubuntu LTS 12.041 which is continuosly updated.

The problem does not seem to affect the functionality of my computer, but I read the message as a warning that something is wrong, and I would like to have the matter clarified. How do I solve the problem?

---

### Post by MoebusNet on 2013-05-18
I haven't had to use this, but it looks like this has been used to fix this issue:

[http://smallbusiness.chron.com/resolving-local-ubuntu-38861.html](http://smallbusiness.chron.com/resolving-local-ubuntu-38861.html)

according to:

[http://ubuntuforums.org/showthread.php?t=1978822](http://ubuntuforums.org/showthread.php?t=1978822)

Keep track of everything you do you so you can put it back to original. Even better, make a copy of any file you intend to make changes to and give it a different name (ie original_filename.txt saved as original_filename_backup.txt). Then you can always put things back as they were if it doesn't work out. Hope this helps!

---

### Post by Cheesehead on 2013-05-18
It's usually an incompatibility between Samba networking and Avahi service discovery.
Samba network services can include network drives, printers, etc.
Avahi is a different way to broadcast and discover such services.
Do you run know if your run services on your LAN? Discoverable services?

---

### Post by grahammechanical on 2013-05-18
I get that message when Ubuntu connects to the router before the router has made its connection to the ISP. It is not usually a problem as I have just one machine. Is this a network printer?

---

