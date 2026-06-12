---
title: "Slow boot"
date: 2012-02-13
forum: New to Ubuntu
---

### Post by DaveMcC on 2012-02-13
Strange one this, hopefully some one may know to cure it.

When I use to turn this computer on, when the thing went "bleep" the dual boot screen appeared and I selected which OS to boot to, Ubuntu or win (sic) "needed"

But last Saturday I had to back up files from a busted blown "Ubuntu ver 9" computer, to do this I disconnected my IDE drive, "not boot drive its a sata type"  made the other drive slave plugged it into / onto my IDE bus and downloaded all photos etc from said drive.

After doing that I turned off computer removed other drive from my system and re-plugged in MY IDE drive.
I may have moved the sata cable from sata 1 to sata zero, which is where I think it was at, where it should have been plugged in.

Apart from that! nothing else has been moved.

Now when I get the "bleep" to dual boot screen it takes 12 seconds

Any body may know what is slowing down this boot up :confused:

Thanks

Dave

---

### Post by drs305 on 2012-02-13
Don't know what is going on but it might help to run the following commands to make sure Grub is looking in the right places for it's files. The commands assume your bootloader is on the drive designated as 'sda':

```
sudo grub-install /dev/sda  # Rewrites the MBR to point to the Grub 2 files.
sudo update-grub # Recreates the Grub menu, updating UUIDs, devices, etc
```

---

### Post by DaveMcC on 2012-02-13
> **drs305 said:**
> Don't know what is going on but it might help to run the following commands to make sure Grub is looking in the right places for it's files. The commands assume your bootloader is on the drive designated as 'sda':

```
sudo grub-install /dev/sda  # Rewrites the MBR to point to the Grub 2 files.
sudo update-grub # Recreates the Grub menu, updating UUIDs, devices, etc
```


Before I do the above, ? is there any way I can look at grub, and do I do the above via terminal?

Dave

---

### Post by Markg55 on 2012-02-13
Have you checked to see if your BIOS recognized the hard drive?

---

### Post by drs305 on 2012-02-13
> **DaveMcC said:**
> Before I do the above, ? is there any way I can look at grub, and do I do the above via terminal?

Dave

Yes, those two commands are run in a terminal.

You can run the Boot Info script (see the link in my signature line). This script creates a RESULTS.txt which will provide you with lots of information on boot files and partitions. It may be hard for you to understand but there is a "BIS" link in my signature line if you want to run it.

---

### Post by DaveMcC on 2012-02-13
> **drs305 said:**
> Yes, those two commands are run in a terminal.

You can run the Boot Info script (see the link in my signature line). This script creates a RESULTS.txt which will provide you with lots of information on boot files and partitions. It may be hard for you to understand but there is a "BIS" link in my signature line if you want to run it.

Thanks for the info, but I just do not know enough about Ubuntu to do this, I have looked at your links, they just go over my head

Once again thanks for your help but I think I will just leave it.............

I did run this 
sudo grub-install /dev/sda And got no errors reported

And yes Markg55, the bios does see the drives

Dave

---

### Post by drs305 on 2012-02-13
> **DaveMcC said:**
> Thanks for the info, but I just do not know enough about Ubuntu to do this, I have looked at your links, they just go over my head

Once again thanks for your help but I think I will just leave it.............

I did run this 
sudo grub-install /dev/sda And got no errors reported


I understand that some of this stuff can seem overwhelming. If you have specific questions you'd like answered I'd be happy to try. This is a support forum - we wouldn't be here if we didn't want to help.

However, leaving it is fine as well if that is what you are comfortable. 

The second command rebuilds the Grub menu. It's possible there is something that has changed since the menu was first built, and updating it may correct some discrepancy that is forcing Grub to look around for a file rather go directly to it. If you don't want to run it, it will eventually be run by the system when a new kernel is introduced or a Grub script is replaced by a newer one. So there really is no rush - if it's something in the Grub menu that is slowing things down it will be fixed eventually by the system.

Happy Ubuntu-ing.

---

