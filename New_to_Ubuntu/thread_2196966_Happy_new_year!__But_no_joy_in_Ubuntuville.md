---
title: "Happy new year!  But no joy in Ubuntuville"
date: 2014-01-01
forum: New to Ubuntu
---

### Post by lile001 on 2014-01-01
Today I was working away on a Libreoffice document when the computer crashed.  Screen became very sluggish, eventually things froze, mouse unresponsive, and so on, so I hit BOB (The Big Off Button).  

Rebooting, Linux ( ubuntu 12.04) take a long time to boot, and eventually ends up at a linux command prompt instead of a graphical screen.  

Here are things I have tried:



1.  It's a dual-boot machine. Can boot into Windows normally
2.  installed smartmontools, because that was the first helpful idea I ran across while surfing for solutions. 
3. sudo smartctl -i /dev/sda  says SMART is available and enabled
4. run short test   sudo smartctl -t short /dev/sdb1 
5.  No errors found
Run long test sudo smartctl -t long /dev/sdb1 Estimated time 255 minutes = 5:45 PM.  aborted test.  I may come back to this later.
6. Reboot into GRUB recovery mode, run "fsck Check All File Systems".  Did not see any results, returned to recovery mode screen.  I do not know how to use this utility so do not know if that is bad or good. 
7. Try FailSafeGraphic Mode from recovery mode menu.  Failed with error message "no screens found", returns to recovery mode menu

I have a theory that, since Windows boots normally, that this may be a hard drive error, since if it was a memory error it might affect both OSs.  This theory might be wrong as well, but I have been trying to check for hard drive problems. 

I don't have the foggiest Idea what I am doing, having never encountered this sort of problem, so don't expect me to know anything at all.  I have tried these things because I found them when surfing for a solution, not really understanding what is the best thing to try first.  

Can someone give me any pointers as to how to proceed?

---

### Post by sudodus on 2014-01-01
I suggest that you make a USB boot drive (or use one that you have already) with Ubuntu or some repair operating system, or something in between, for example Knoppix. Boot from that and try to repair the partition, where Ubuntu resides

```
sudo e2fsck -cf /dev/sdxy
```

where x is the drive letter (a for the first drive), and y is the partition number (maybe 5 if Ubuntu is installed into the first logical partition of an MSDOS partition table). If you see a massive number of errors, you can interrupt the repair session and try to save what can be saved with ***ddrescue*** before you try anything else. The tutorial (and info page) of ddrescue are very good.

[https://www.gnu.org/software/ddrescue/manual/ddrescue_manual.html](https://www.gnu.org/software/ddrescue/manual/ddrescue_manual.html)

---

