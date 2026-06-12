---
title: "Access files on an Ext4 formatted drive from Windows?"
date: 2013-04-16
forum: New to Ubuntu
---

### Post by Opiatool on 2013-04-16
Hello Ubuntu users!
 
I had a secondary computer that I used for streaming videos to my TV that had an install of Ubuntu on a main SSD drive with a lot of videos  on a backup data drive.  The computer had been functioning for about a year without issue until the SSD crashed last week and wouldn't boot and isn't seen in BIOS.   I  received a RMA number from Crucial and sent the drive back to them to get a replacement.
 
The data drive had been formatted as EXT4 and I'm trying to access and transfer files from it while I await the replacement SSD and can get Ubuntu reinstalled but I can't seem to access the drive from my Windows gaming machine.
 
I had tried hooking the drive in the windows machine and using EXT2FSD to access the drive but I couldn't see the data driveafter installing the driver.  I then tried launching Ubuntu from a thumb drive thinking I could transfer files from the drive to a backup but now I receive an error stating that I don't own the drive.
 
Any ideas on how I can get my data? I am kind of worried that when I install the new SSD with Ubuntu on it I will receive the same error message since it will be a fresh install of Ubuntu.

---

### Post by papibe on 2013-04-16
> **Opiatool said:**
>  I then tried launching Ubuntu from a thumb drive thinking I could transfer files from the drive to a backup but now I receive an error stating that I don't own the drive.
That is what I've done in the past.

How did you get that error?
Did you mount the drive by clicking on Nautilus, or did you use 'mount' from command line?
Is the disk encrypted?

Regards.

---

### Post by Opiatool on 2013-04-16
If you can forgive a crappy cellphone picture of the error: [http://imgur.com/fmzNZ3Z](http://imgur.com/fmzNZ3Z)

I am able to view the drive in disk utility and can mount it there. That's was the only way i really knew how to mount the drive for the temporary boot of ubuntu to see it.

---

### Post by papibe on 2013-04-16
Launch the file manager (Nautilus) using gksudo:
```
gksudo  nautilus /path/where/Falcon1_is_mounted 
```
Regards.

---

### Post by Opiatool on 2013-04-16
Awesome! I still wasn't able to do a simple copy/paste from the drive but I was able to utilize the Send To command from the menu.

Thank you for your help! If you're ever in Chicago I'll buy you a drink

---

### Post by papibe on 2013-04-16
:)

---

