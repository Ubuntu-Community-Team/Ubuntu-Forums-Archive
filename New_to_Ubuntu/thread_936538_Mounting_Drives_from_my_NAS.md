---
title: "Mounting Drives from my NAS"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by LowMen on 2008-10-02
I hope I can explain this properly so someone understands.

Ok I have a thing about icons and my desktop, prefer nothing on it, and putting the recycle bin in the tray "**Thank you**" .

I am using Hardy Heron on my main system and would love to mount the 2 drives from my Linksys Nas but! I would prefer not to have them on my Desktop.  Is it possible to mount the drives in "My Computer" where my DVD drive is?  And also have them stay there when I reboot the system.

After pouring over the information to my question on the forum I either did not see the answer or it was answered and went swoosh over my head.

Thank you
LowMen

---

### Post by RealPSL on 2008-10-03
Disabling the drives from appearing on your desktop is not difficult. Run the following commands:
```

ALT+F2
gconf-editor
Navigate apps > nautilus < desktop
uncheck volumes visible 
File > Quit

```

This will remove the icons from the desktop. If the NAS drives behave like flash drives then they should appear under your computer as well.

---

### Post by Paqman on 2008-10-03
> **LowMen said:**
> 
I am using Hardy Heron on my main system and would love to mount the 2 drives from my Linksys Nas but! I would prefer not to have them on my Desktop.  Is it possible to mount the drives in "My Computer" where my DVD drive is?  And also have them stay there when I reboot the system.


Sure, the reason things show up on your desktop is because their mount point is within /media. If you pick somewhere else to mount them, they won't pop up.

Without knowing too much about your NAS, i'm assuming it's designed to serve files over a Windows network (the protocol is called SMB or CIFS) [This thread](http://ubuntuforums.org/showthread.php?t=288534) gives step-by-step instructions for setting up shares using CIFS.

If your NAS can use the Linux protocol NFS that would probably be better than CIFS, but most home NAS's won't.

---

### Post by LowMen on 2008-10-05
Thank you Both for the reply.

I will check out this information this evening after work and see how it goes.

LowMen

---

