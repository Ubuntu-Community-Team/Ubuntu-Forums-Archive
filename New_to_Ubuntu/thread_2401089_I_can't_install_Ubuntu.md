---
title: "I can't install Ubuntu"
date: 2018-09-13
forum: New to Ubuntu
---

### Post by astralmagickian on 2018-09-13
I'm trying to install either 16.04.3 x64 or 17.04 on my 17-x115dx hp and when i try to install 17.04 it never boots up,  it shows an error saying "pci bus error severity=corrected,  type=physical layer,  id=00e5 (receiver Id) device [8086:9d15] error status/mask=00000001/00002000 [ 0] receiver error.            (First) 

When I try to install 16.04.3 i can get to the desktop, i can install it only it freezes at disc partitioning after I've made my selection,  and gives me the very same error.

How can I install Ubuntu on my laptop?

Also,  in the installation menu, i get the error "The attempt to mount a file system with type vfat in SCSI1 (0,0,0,), partition #1 (sda) at / boot/ efi failed. 

You may resume partitioning from the partition menu"

---

### Post by Autodave on 2018-09-13
First of all, don't even try 17.04 since it is no longer supported. Major releases come out every 2 years and are supported for 5 years. In the iterim, every 6 months a release is issued, but that release is only supported until the next release.  16.04 (20*16 *April *04*) was a long term release (LTS) and now 18.04 is available which is also an LTS.

Did/does this computer have Windows installed?  Are you trying to dual boot Win & Linux?  Have you disabled *fast boot *in the BIOS?  Even if you are replacing Win with Linux, you will still need to disable fast boot and then shut down Windows before trying to boot to your Linux install medium.

Some info on your PC would probably make it easier for people here to help you.

---

### Post by astralmagickian on 2018-09-13
It was running Windows but it got corrupted i can't reboot into it. I only have internet on my phone so i can't download and install a new version. I can get internet once it's installed however. I put the model number in my original post

---

### Post by Autodave on 2018-09-13
OK....do the 16.04.  Do you know how to get into the BIOS and disable fast boot?  On an HP, you will probably get into the BIOS by hitting F10.  Turn the computer on and instantly start pressing the F10 key quickly and repeatedly.  Once that key press is recognized you will either be in the BIOS or given the option to go into it.  At that point you will only have your arrow keys to use for navigation.  You will have to look through the screens to find it (fast boot) and disable it. Then, you need to save and exit.  Allow Windows to try and boot even if it won't.  Force a shutdown if you have to.  Now, boot from your install medium.

---

### Post by astralmagickian on 2018-09-13
I can't find fast boot...I found secure boot.

---

### Post by Autodave on 2018-09-13
You didn't say what version of Win you were running and I (stupidly) didn't ask. If if it was early Win7 or before, then you won't find fastboot. You will need to turn off secure boot, however.  Sorry for the confusion.  Let me know what happens.

---

### Post by astralmagickian on 2018-09-13
Tried it.  Now I get an error after i tell it to erase the disk and install Ubuntu,  "the attempt to mount a file system with type vfat in scsi1 (0,0,0), partition #1 (sda) at /boot/efi failed.  You may resume partitioning from the partitioning menu"

---

### Post by astralmagickian on 2018-09-13
And it was windows 10

---

### Post by Autodave on 2018-09-13
There has to be an option for fast boot in there somewhere: keep digging.  Sorry, but I just cannot give you an exact location.

I wouldn't even mess with manually partitioning the drive (if that is what you are doing): just select erase entire disc and install Ubuntu.

---

### Post by astralmagickian on 2018-09-13
There is no fast boot option and i am erasing everything.  Install still stops at that same place. With that same error

---

### Post by Autodave on 2018-09-13
That sounds like exactly what you get when the fast boot is not shut off.  This is difficult without having your PC in front of me.

You may have to disable UEFI boot and enable Legacy boot: that my give you the option to turn off fast boot.

Another thing you can try is to reset the BIOS to factory settingd (you should find that option on the main screen).  After that, the fast boot option should be visible.

---

