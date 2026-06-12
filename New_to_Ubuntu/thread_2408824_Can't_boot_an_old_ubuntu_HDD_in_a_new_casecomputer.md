---
title: "Can't boot an old ubuntu HDD in a new case/computer"
date: 2018-12-23
forum: New to Ubuntu
---

### Post by camelface on 2018-12-23
I ran an ubuntu computer for 5+ years with a 600gig harddrive until about 3-4 years ago when the computer's power supply failed. Since then, the hard drive was extracted from the old case, and we (father and I) were able to boot from this hard-drive in his Vista computer case (with the vista harddrive disconnected and using my ubuntu harddrive as the main and only one). This allowed me to copy my files from the ubuntu drive to an external hard drive and I was good to go. 

Unfortunately, that external hard drive was a piece of crap and I have to copy my files from my old ubuntu HDD again. For some reason, when we plug this hard drive as the main one in my father's new computer and case (made for a windows 10 build), we can't get past the bios. Are there bios settings that I should be clicking off that will allow me to proceed into the ubuntu that's loaded into the drive? The frustrating thing is that the HDD is recognized in the Bios, but like I said, it won't go further. 

We tried with plugging both my ubuntu HDD and my father's windows 10 HD, and it goes into windows 10. No matter how much we fiddle with the "disk management" tool, we can't get the drive to show up in My PC to access the videos and picture files of my ubuntu drive. 

Thanks for all your help, happy holidays.

---

### Post by Impavidus on 2018-12-23
Chances are that the old Ubuntu system was installed in bios mode, but your Windows 10 computer is booting in UEFI mode. Set it to legacy mode and it may work.

You could also connect the old hard drive to a Linux computer (internally or using an enclosure via usb) and access the hard drive without booting it. That should work, provided the hard drive is still OK. The rather old Ubuntu system on the hard drive may have difficulty booting on more recent hardware.

---

### Post by camelface on 2018-12-23
After changing it to Legacy mode, it did proceed to Ubuntu's (or xubuntu or lubuntu, I forget which one I had put in last) desktop wallpaper, but there are no icons or taskbars loaded. The only thing I can do is: 1) move mouse pointer around; 2) press f12 to load a gray/black window with no ability to type in it; or 3) control alt delete which brings up the usual window asking to restart, shutdown or cancel. 

The next step I was thinking of doing is making a boot disk or install disk with one of the newer versions of xubuntu or ubuntu (without formatting the HDD) and seeing if that will lead me to access an OS and the files. Any other thoughts?

---

### Post by CatKiller on 2018-12-23
If your objective is simply to get the files off it, you don't need to boot it. Just boot off a live USB and copy the files wherever you want to copy them to.

---

### Post by camelface on 2018-12-24
Thanks for your responses. My Lubuntu bootable USB didn't work right (bugged at a self-test) screen, so I will try the latest ubuntu download.

---

### Post by camelface on 2018-12-24
I was able to boot from the ubuntu live CD. Now it's telling me my files on the HDD have some kind of protection. Any way to unlock permissions?

---

### Post by Autodave on 2018-12-24
Sounds like the drive may have encrypted?

---

### Post by camelface on 2018-12-25
I am not able to change the permissions using the ubuntu liveCD. So I would like to install the OS, but for some reason, it does not allow the same function I used to use, which was basically to update the OS while keeping the files. Now, for some reason, the installer tells me this option will erase my old files. Could it be because I have xubuntu or another ubuntu offshoot and that it is not compatible with an update of OS?

edit: 

Looking at the files and folders, it seems like the ones that are protected are protected randomly (some folders in my picture files but not others, same in the music category). When I go in permissions, the user has full access but "group" and "other" has none. Because I'm not the user in this liveCD, there's no way for me to change it prima facie.

edit2: 

But I was indeed able to copy over most of the files (95%), so I am quite grateful to you for helping.

---

### Post by oldfred on 2018-12-25
If new system is UEFI and you boot installer in UEFI boot mode, it may want to convert drive to gpt which would erase MBR partitions.

Can you manually mount read only? Change example sdb# with your partition.
       Read only mount  may work 
sudo mkdir /mnt/temp
sudo mount -o ro /dev/sdb# /mnt/temp
sudo -H nautilus /mnt/temp

---

### Post by camelface on 2018-12-25
To be honest, your explanation is a bit too complex for me. 

The other thing to complicate things is that the intaller offers to install on the external hard drive and not on the HDD I have plugged in the motherboard.

Things used to be simpler in the old days...

---

### Post by oldfred on 2018-12-25
Post this:
sudo parted -l

---

### Post by CatKiller on 2018-12-25
> **camelface said:**
> for some reason, it does not allow the same function I used to use, which was basically to update the OS while keeping the files. Now, for some reason, the installer tells me this option will erase my old files. 

Before you were booting off the hard drive and using the cd as a bunch of files. Now you're booting off the cd and using the hard drive as a bunch of files. 

> Looking at the files and folders, it seems like the ones that are protected are protected randomly (some folders in my picture files but not others, same in the music category). When I go in permissions, the user has full access but "group" and "other" has none. Because I'm not the user in this liveCD, there's no way for me to change it prima facie.
You can become root when running the live cd exactly as you could when running it normally.

---

### Post by camelface on 2018-12-25
> **CatKiller said:**
> Before you were booting off the hard drive and using the cd as a bunch of files. Now you're booting off the cd and using the hard drive as a bunch of files. 


**You can become root when running the live cd exactly as you could when running it normally.**

Can you tell me how to do this with the new OS version? That would simplify things greatly.

---

### Post by CatKiller on 2018-12-25
> **camelface said:**
> Can you tell me how to do this with the new OS version? That would simplify things greatly.

```
sudo -H *thing you want to run*
```

So to run the file manager as root, you'd use
```
sudo -H nautilus
```

---

