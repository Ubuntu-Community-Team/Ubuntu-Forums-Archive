---
title: "Proper syntax for path to an external hard drive?"
date: 2021-01-29
forum: New to Ubuntu
---

### Post by euanpreston on 2021-01-29
Hi all,

Hopefully someone can help me solve what is no doubt a very straightforward issue. I'm attempting to recover data from a corrupt EXT4 drive that is encrypted with LUKS. I'm following the solution set out here: [https://askubuntu.com/questions/875361/cannot-mount-ext4-luks-anymore](https://askubuntu.com/questions/875361/cannot-mount-ext4-luks-anymore)

The solution appears to work, however the path given for the drive.img has fsck create it in my home folder. Unfortunately, the USB drive that I'm trying to save is much larger than my internal disk has capacity for. I therefore need to create the image on another USB disk.

The command the solution provides is this:

```
sudo dd if=/dev/dm-1 of=~/drive.img 
```

What I tried was this:

```
sudo dd if=/dev/sdb1 of=/dev/sda1/drive.img
```

...but that yields the error "dd: failed to open /dev/sda1/drive.img' : Not a directory

Can anyone help, please? Is there something obvious I'm doing wrong?

---

### Post by ActionParsnip on 2021-01-29
you don't access drives using /dev to write to them. You need to mount the /dev/sda1 to a folder, then use the mount point as the output of dd

Why do you not have backups of the data? Surely this would be far easier and more likely to succeed......?

---

### Post by euanpreston on 2021-01-29
> **ActionParsnip said:**
> you don't access drives using /dev to write to them. You need to mount the /dev/sda1 to a folder, then use the mount point as the output of dd

Why do you not have backups of the data? Surely this would be far easier and more likely to succeed......?

Hah! I knew that was coming! And you're very right - I do have backups, but unfortunately not for the most very recent files. I was in fact mounting in order to back up the latest data when the fault occurred.

Thanks for the knowledge. Really grateful.

---

### Post by euanpreston on 2021-01-29
Problem solved. ActionParsnip, I owe you a coffee. Thanks again.

---

### Post by ActionParsnip on 2021-01-29
Time to review backups :)

---

