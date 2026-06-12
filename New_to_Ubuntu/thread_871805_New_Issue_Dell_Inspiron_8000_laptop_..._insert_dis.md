---
title: "New Issue Dell Inspiron 8000 laptop ... insert disk 71% into alt 32 bit install"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by bytes on 2008-07-27
Error is 

[!!] Install the base system

Please insert the disk labeled: 'Unbuntu 8.04.1 _Hardy Heron_' Release I386 (20080701) in the drive '/cdrom/' and press enter. 

Media Change
Back--------------------------------------------------Continue

If I hit continue the message comes up again the same if I hit back. I'm stuck!

Help! 

Thanks

---

### Post by halitech on 2008-07-27
sounds like either a bad burn or an issue with your cd rom. Try rebooting and use the check disk option to confirm the disk is okay

---

### Post by bytes on 2008-07-27
The test was successful no problems. What should I do?

---

### Post by halitech on 2008-07-27
try running memcheck?

are you trying to load the Live CD or the alternate cd?

---

### Post by bytes on 2008-07-27
Its the  alt 32 bit CD as suggested earlier in another post.

---

### Post by bytes on 2008-07-28
Maybe I should try a different version of Linux? Anyone have any ideas why it will not install? 

Thanks

---

### Post by bumanie on 2008-07-28
> **bytes said:**
> Maybe I should try a different version of Linux? Anyone have any ideas why it will not install? 

Thanks

Hard to say definitively - depends on system specs and sometimes there can be some idiosyncratic hardware issues - very often the alternate cd will install when the live cd won't. What's your cpu and how much ram do you have?

---

### Post by bytes on 2008-07-28
My computer specs include

PIII 900 
256M ram
20 gig hdd 
8 x DVD drive 
Built in Actiontec 10/100M ethernet and Lucent WinModem 
Infrared 
32M Geforce 2 GO 
15" screen (1600x1200 resolution) 
Maestro 3 soundcard 
2 PCMCIA slot 
2 USB ports

---

### Post by bytes on 2008-07-28
The error requesting the CD happens at 73% of install exactly. It seems to work fine up until that point.

---

### Post by bumanie on 2008-07-28
> **bytes said:**
> My computer specs include

PIII 900 
256M ram
20 gig hdd 
8 x DVD drive 
Built in Actiontec 10/100M ethernet and Lucent WinModem 
Infrared 
32M Geforce 2 GO 
15" screen (1600x1200 resolution) 
Maestro 3 soundcard 
2 PCMCIA slot 
2 USB ports

You would be best using xubuntu, ubuntu needs 384mb ram - lack of ram is most likely the issue. Xubuntu needs 192mb ram for the install from the live cd, but will operate comfortably on 128mb ram.

---

