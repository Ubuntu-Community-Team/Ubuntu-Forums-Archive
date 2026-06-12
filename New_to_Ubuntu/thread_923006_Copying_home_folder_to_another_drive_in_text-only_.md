---
title: "Copying home folder to another drive in text-only login (need the code)"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by alwiap on 2008-09-17
I was about to reformat my hard drive (I dual boot Windows XP and Linux Mint) and I changed my xorg.conf file.

It doesn't boot up correctly, after re-doing the xorg.conf file when I booted it in safe mode or whatever it's called, don't remember, and I still can't get the X server to work.

My question is:  I just want to back up my home folder, and don't care about recovering the system, what should I type into a text-login bootup which I can get into so I can recover my home folder and copy its contents to an external hard drive?

I already know how to access a text-only mode in the OS selector screen, and that works, so I just want to copy my home folder to an external hard drive (I also don't remember what hard drive is which, I guess 'sudo fdisk -l' will tell me that?)

Thanks so much and I am actually away from that specific computer with this problem but will get back to it tommorow.

---

### Post by iaculallad on 2008-09-17
On your terminal:

```
cp -R /home/your_username /destination
```

---

### Post by alwiap on 2008-09-17
> **iaculallad said:**
> On your terminal:

```
cp -R /home/your_username /destination
```

thank you I will try this when I can access the computer!  Will there be any notification that it worked correctly (I don't want to accidently not copy my files, they are important)

Thanks again!

---

### Post by hellion0 on 2008-09-17
If the prompt comes back and there were no errors beforehand, it worked fine.

---

### Post by Tatty on 2008-09-17
Try running ```
sudo xfix
``` to repair your xorg.  failing that try ```
sudo dpkg-reconfigure xserver-xorg
```

Although if you are in recovery mode you probably wont need to type sudo.

To mount an external hard-drive you first need to find out the name of the device - and you are correct this can be found with sudo fdisk -l.

Lets assume that the drive is /dev/sdaX.

You would first make a directory to mount the drive to:
```
sudo mkdir /mnt/externaldrive
```

Then you would mount the drive:
```
sudo mount /dev/sdaX /mnt/externaldrive
```

Your drive is now available at /mnt/externaldrive/.  For the sake of order, lets create a directory on your drive to backup your home folder to:
```
sudo mkdir /mnt/externaldrive/homebackup
```

Then finally you need to copy your files with:
```
sudo cp -R /home /mnt/externaldrive/homebackup
```

Bear in mind that this will probably mess up the permissions on all your files.  Which is not a problem if you are simply trying to back up your personal data, but this is not a method to be used if you intend on simply copying all your settings to a new install.

---

### Post by iaculallad on 2008-09-17
> **alwiap said:**
> thank you I will try this when I can access the computer!  Will there be any notification that it worked correctly (I don't want to accidently not copy my files, they are important)

Thanks again!

On a successful CP operation, it will just bring you back in the terminal prompt without displaying any message/error message. But when error occurs, operation will break and prompts you with an error.

---

### Post by Locutus_of_Borg on 2008-09-17
cd to the location of the folder you wish copied

input this:
find . -depth -print0 | cpio --null --sparse -pvd /new/

change /new/ to the location of where you want the new /home

this is better than using cp -R

---

### Post by alwiap on 2008-09-17
> **Tatty said:**
> Try running ```
sudo xfix
``` to repair your xorg.  failing that try ```
sudo dpkg-reconfigure xserver-xorg
```

Although if you are in recovery mode you probably wont need to type sudo.

To mount an external hard-drive you first need to find out the name of the device - and you are correct this can be found with sudo fdisk -l.

Lets assume that the drive is /dev/sdaX.

You would first make a directory to mount the drive to:
```
sudo mkdir /mnt/externaldrive
```

Then you would mount the drive:
```
sudo mount /dev/sdaX /mnt/externaldrive
```

Your drive is now available at /mnt/externaldrive/.  For the sake of order, lets create a directory on your drive to backup your home folder to:
```
sudo mkdir /mnt/externaldrive/homebackup
```

Then finally you need to copy your files with:
```
sudo cp -R /home /mnt/externaldrive/homebackup
```

Bear in mind that this will probably mess up the permissions on all your files.  Which is not a problem if you are simply trying to back up your personal data, but this is not a method to be used if you intend on simply copying all your settings to a new install.

Thanks for this info, and yes, I only want files like documents and pictures moved, I am changing distros and don't need the personal settings of my desktop.

---

### Post by Ptero-4 on 2008-09-18
you could also use cp -a instead since it copies recursively, without confirmation prompts and preserves permissions all in one single switch.

---

### Post by alwiap on 2008-09-18
I booted in text only mode, and unfortunately it asks for my root password (I entered my user password), and it's invalid.  Any ideas, or is there a default root password?  Thanks.

---

### Post by jvc26 on 2008-09-18
Ubuntu doesn't have a root user password by deafult, as the root account is disabled. Perhaps a blank password? Did you boot into single user mode (i.e. place 'single' on the end of the boot line in GRUB?)

Il

---

### Post by alwiap on 2008-09-18
> **Illuvator said:**
> Ubuntu doesn't have a root user password by deafult, as the root account is disabled. Perhaps a blank password? Did you boot into single user mode (i.e. place 'single' on the end of the boot line in GRUB?)

Il

Sorry, just to clarify I am using Linux Mint.  And yes, I have tried entering a blank password.  As far as booting into single user mode, I will try adding that line to the end and see what happens.  Thanks

---

### Post by alwiap on 2008-09-18
Well, I just booted into the recovery mode again, here is the line of code at the bottom before I start loading it ('single' was already there)

root=/dev/sda2 ro single

---

