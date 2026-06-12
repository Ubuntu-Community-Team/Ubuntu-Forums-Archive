---
title: "[SOLVED] dual boot, fresh install, which drive to set grub install?"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by snuffy on 2008-11-29
I have a just done a fresh dual boot install of windows xp, followed by intrepid. The problem is that i have no grub menu on startup.  I let the grub menu install itself in the default location (hd0) i think it is.

I installed with the following partitions:

/dev/sda
   sda1    /
   sda2    swap
   sda3    /home

/dev/sdb
   sdb1    file storage

/dev/sdc
   sdc1   windows
   sdc5   file storage


i think the problem is that i have to set the grub menu to install on a specific partition in step 7 of the gui install screens. i don't know which partition to set it to. should it be sdc1? 

thanks for any help.
tim.

---

### Post by Olivier2371 on 2008-11-29
You could try the following,

Boot from the cd/dvd, then select try ubuntu.

Then Click on Application->Accessories->Terminal.
(this will open the Terminal window)

Type the following command in sequence:
What is in between parentheses is for information only. 
sudo grub
root (hd0,1)
setup (hd0)
quit

Restart the computer,(make sure you remove the disk)
Now you should be able to see grub menu.

Hope this Helps.

---

### Post by MasterSander on 2008-11-29
yeah you could do that. if you should reinstall you should install the grub to the MBR on /dev/sdc since that's your boot partition (because of windows), you can change it though.

---

### Post by snuffy on 2008-11-29
I installed grub to dev/sdc.

now all i get on bootup is a whole page of:

GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB 


????

should i have installed to dev/sdc1?   or sdc0 or something?

---

### Post by Olivier2371 on 2008-11-29
Personally I would have install windows first on sda, then Ubuntu on sdb,

and leave the third hard drive for sharing files between both system.

Which of your drives is set as master, and as slave?

You can recover the boot to windows by inserting the windows disk, then go on recovery mode.

From the windows disc in recovery mode, you could go to dos prompt, then type "fixmbr, then fixboot".

Should you require more info just ask.

---

### Post by caljohnsmith on 2008-11-29
When you say you have no Grub on start up, what happens on start up? Do you boot directly into Windows? If so, how about changing the boot order in your BIOS so that the Ubuntu drive boots first, and then install Grub to the MBR (Master Boot Record) of the Ubuntu drive by specifying /dev/sda as the location of Grub during installation (don't install Grub to the partition boot sector by choosing a partition). Or since you all ready have Ubuntu installed, simply do the following in a terminal (Applications > Accessories > Terminal):
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
And that will install Grub to the MBR of the sda Ubuntu drive. How about giving that a shot and letting me know how it goes.

---

### Post by snuffy on 2008-11-29
I've never had this problem before when installing on the same system.

sdc is the master. sdb and sdc are slaves as i recall.

I'll try a few things, but might need your help again! :-)

cheers.





> **Olivier2371 said:**
> Personally I would have install windows first on sda, then Ubuntu on sdb,

and leave the third hard drive for sharing files between both system.

Which of your drives is set as master, and as slave?

You can recover the boot to windows by inserting the windows disk, then go on recovery mode.

From the windows disc in recovery mode, you could go to dos prompt, then type "fixmbr, then fixboot".

Should you require more info just ask.

---

### Post by snuffy on 2008-11-29
booted into the live CD and did the following in a terminal:

```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```

but i still get the same page full of GRUB GRUB GRUB.... when i reboot.

---

### Post by caljohnsmith on 2008-11-29
Are you sure you are booting the sda drive on start up? If so, getting that kind of Grub error often means that your HDD isn't configured quite right in BIOS. How about going into your BIOS and change the settings for the sda drive one-by-one to see if it makes a difference? Look for settings like "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, ACPI, DMA, etc. Let me know how that goes.

---

### Post by snuffy on 2008-11-30
After messing around with nothing working i decided to throw the whole thing in the trash and go back to windows! .....


Only kidding! ....

I did get annoyed though, so repartitioned everything...

I now have following partitions:

/dev/sda
sda1    /Home ext3 (200GB)

/dev/sdb
sdb1     Backup ext3 (200GB)

/dev/sdc
sdc1    Windows NTFS  (20GB)
sdc2    Ubuntu / ext3  (20GB)
Linux-swap  (2gb)
sdc3    Downloads  ext3  (40GB)

I haven't installed anything yet.

It doesn't seem logical that my partitions for operating systems are on sdc. Should they be on sda?  will this cause more trouble when installing grub?  how can i swap my sdc partition naming for the sda one?

---

### Post by snuffy on 2008-11-30
Hmm, turns out ubuntu didn't like my partitions. after install it simply booted straight into windows. 

i unplugged my other hard drives, and tried again, this time it worked. i then plugged my hard drives back in.

seems ok now. thanks all.

will have to work out how to set one of my other drives to /home now.

cheers.

---

