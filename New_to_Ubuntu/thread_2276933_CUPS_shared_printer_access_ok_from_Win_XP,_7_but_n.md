---
title: "CUPS shared printer access ok from Win XP, 7 but not from Windows 8"
date: 2015-05-05
forum: New to Ubuntu
---

### Post by James_Newton on 2015-05-05
I'm a 30 year veteran of the IT wars. ,o) 99% windows user and embedded systems programmer. Our "family" computer, an old Win7 machine, gave up the magic smoke the other week. This machine acted as a backup if anyones personal laptop went down, and was our print server for our bulletproof old Laserjet 2200. I decided it was time to try Ubuntu on an Dell PE T-310 server I was given. Got it installed, setup the printer, figured out how to share it, and was able to connect from all the other PC's in the house: one old windows XP machine that won't die as well as all our Windows 7 machines. But... my sons Windows 8 machine will NOT print to that printer. He /can/ print to a printer shared via the old XP machine.

I've followed the basic instructions of Add printer, "Not listed", Select shared printer by name, copied in the URL of the printer (which is 
[http://192.168.1.168:631/printers/HPLJ2200](http://192.168.1.168:631/printers/HPLJ2200)
if that matters) and then Next, it detects the printer and brings up the driver list. I select HP, then Laserjet 2200 PCL5, just like on the other machines, and it installs the printer. Everything looks great... until you try to print. Then it says "the que is in error" and the document just sits there. As far as I can see, the CUPS server isn't seeing any communication from the Windows 8 machine when it tries to print. 

Now, I CAN go to [http://192.168.1.168:631/printers/HPLJ2200]("http://192.168.0.168:631/printers/HPLJ2200") from the Windows 8 machine and click on all the links, etc... nothing wrong. There is no firewall issue; I tried turning off the AV program and Windows firewall entirely just to be sure.

I've seen a couple of other people post this same symptoms without resolution:
[http://askubuntu.com/questions/484825/printing-with-cups-in-windows-8](http://askubuntu.com/questions/484825/printing-with-cups-in-windows-8)
[http://superuser.com/questions/750725/windows-8-doesnt-want-to-print-via-ipp-although-it-detects-the-printer](http://superuser.com/questions/750725/windows-8-doesnt-want-to-print-via-ipp-although-it-detects-the-printer) (note, the 2200 is NOT a GDI printer)

Any suggestions for how to troubleshoot this? And please keep in mind: yes, I'm a total nube on Ubuntu, but I've been pushing bits since the '70's.

---

### Post by James_Newton on 2015-05-05
Just found this:
[http://superuser.com/questions/300986/ipp-printing-from-windows-7-ultimate](http://superuser.com/questions/300986/ipp-printing-from-windows-7-ultimate)
which has a couple of suggestions to try... which I will do as soon as my son (and his laptop) return.

---

