---
title: "Flash drive permissions changed by, Windows(?)"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by Buntu Bunny on 2012-08-01
I recently lost my PCI ethernet card due to a lightening strike. Ordered a new one, and attempted to update the driver via the provided CD. For some reason I couldn't access the CD on my home machine, though I had no problem with other CDs. I took it to the library to copy the files onto a flash drive. No problem there, but now the flash drive is read-only on Ubuntu. I tried to change permissions but I get a wait signal which goes on ... well, probably forever but I closed it out after 15 or 20 minutes of waiting and no change. On the library computer (XP Pro) I can write to that same flash drive, delete files, etc. On Ubuntu I can only view files. 

Is it possible Windows changed permissions? This had never happened before and I used the USB stick back and forth all the time. Any suggestions on how to fix it?

---

### Post by Buntu Bunny on 2012-08-02
Ideas anybody? Maybe not, *sigh*. Good thing flash drives are cheap.

---

### Post by oldfred on 2012-08-02
I have not copied something from a CD with Windows for ages, but because the CD was read only, I remember having to reset any file from a CD back to read/write in Windows.

---

### Post by Buntu Bunny on 2012-08-02
OldFred, thanks. Actually it's all the files on the flash drive that are now read only, in fact I can't copy anything to it at all. Trying to change permissions didn't seem to work. Is there another way to reset it?

---

### Post by Paqman on 2012-08-02
> **Buntu Bunny said:**
> Trying to change permissions didn't seem to work. Is there another way to reset it?

Most Flash drives are FAT32 and as such don't accept Linux permissions. If it really does stubbornly refuse to play ball you could copy all the data off, format it then copy the data back. That's bound to sort it, but it wouldn't explain how you got into this position in the first place.

---

### Post by robtygart on 2012-08-02
Try using gparted to re-format the drive, if its just a storage drive that you swap between Win and Linux I usually keep it as FAT32, if you want it to allow Linux permissions go with ext3 or ext4.

---

### Post by oldfred on 2012-08-02
If you use this can you read the files? Then it still is a permission issue.

gksu nautilus

Just do not do anything else with above command as you then have the capability to accidentally delete important system files or cause other havoc with system. Just use with care.

---

### Post by Buntu Bunny on 2012-08-03
Thank you! I will definitely try these when I get home (currently having to work on a library computer), will report results and hopefully mark this thread SOLVED!

---

### Post by Buntu Bunny on 2012-08-11
> **oldfred said:**
> If you use this can you read the files? Then it still is a permission issue.

gksu nautilus

Just do not do anything else with above command as you then have the capability to accidentally delete important system files or cause other havoc with system. Just use with care.

Finally able to get back to this after delays in getting my computer and problems installing Ubuntu 12.04. Not too sure what's too old for an old thread, but I was still interested in working on this.

This was the output

```
leigh@leigh-CM1740:~$ gksu nautilus
Initializing nautilus-gdu extension
Shutting down nautilus-gdu extension
Error: Couldn't open file '/media/5EDE-3773/cs_en.pdf': Permission denied.
Error loading document: Error opening file: Permission denied
Error: Couldn't open file '/media/5EDE-3773/en_dtg.pdf': Permission denied.
Error loading document: Error opening file: Permission denied
Error: Couldn't open file '/media/5EDE-3773/manualpart04.pdf': Permission denied.
Error loading document: Error opening file: Permission denied
javaldx: Could not find a Java Runtime Environment! 
Please ensure that a JVM and the package libreoffice-java-common
is installed.
If it is already installed then try removing ~/.libreoffice/3/user/config/javasettings_Linux_*.xml
Warning: failed to read path from javaldx

```

I installed JRE and libreoffice-java-common. Too many options for JVM; didn't know which to choose. 

I can now open the files and edit, but must save to a new place. Cannot save to the usb stick. Everything still works on Windows however.

---

