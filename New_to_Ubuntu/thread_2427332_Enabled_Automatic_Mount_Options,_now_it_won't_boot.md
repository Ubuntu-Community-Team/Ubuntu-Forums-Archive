---
title: "Enabled Automatic Mount Options, now it won't boot"
date: 2019-09-20
forum: New to Ubuntu
---

### Post by zarniwoopvannharl on 2019-09-20
I was trying to mount an external drive that it wasn't recognising for some reason. I then went into disk utility, found a drive I thought was that one, went into the mount options for that drive and changed the option for it to use the automatic mount options. This was not the main drive my OS is on, but probably a remnant of the previous one I had or the home directory. I am currently in safe mode trying to revert that setting using the root command prompt.

Using the latest Ubuntu version.

I changed the first option in the Disk Utility menu, under mount options, in what I thought was the ext drive. 

So basically what I need is a command to switch off automatic mount options.

Ran:
    /# cat /etc/fstab

(...) 

    /boot was on /dev/sda1 during installation UUID=9762da9f-b9f0-4a9f-9796-ab14d69b3f5f /boot ext4 defaults 0 2 

    /dev/mapper/ubuntu--vg-swap_1 none swap sw 0 0

And yes, I'm aware this was silly of me. Note to self, never change settings when tired.

---

### Post by TheFu on 2019-09-20
I've never used any GUI to setup mounts.
Please post the full contents of the fstab file using *code tags*.

---

### Post by zarniwoopvannharl on 2019-09-20
> **TheFu said:**
> I've never used any GUI to setup mounts.
Please post the full contents of the fstab file using *code tags*.
How do I do that using the root command prompt in safe mode?

---

### Post by TheFu on 2019-09-20
Google "ubuntu fstab" for a general how-to guide.

---

### Post by zarniwoopvannharl on 2019-09-21
> **TheFu said:**
> Google "ubuntu fstab" for a general how-to guide.

```
  /# cat /etc/fstab
/etc/fstab: static file system information. 

Use 'blkid' to print the universally unique identifier for a
device; this may be used with UUID= as a more robust way to name devices
that works even if disks are added or removed. See fstab(5).

<file system> <mount point> <type> <options> <dump> <pass>

/boot was on /dev/sda1 during installation UUID=9762da9f-b9f0-4a9f-9796-ab14d69b3f5f /boot ext4 defaults 0 2

/dev/mapper/ubuntu--vg-swap_1 none swap sw 0 0   
```

---

### Post by TheFu on 2019-09-21
> **zarniwoopvannharl said:**
> ```
  /# cat /etc/fstab
/etc/fstab: static file system information. 

Use 'blkid' to print the universally unique identifier for a
device; this may be used with UUID= as a more robust way to name devices
that works even if disks are added or removed. See fstab(5).

<file system> <mount point> <type> <options> <dump> <pass>

/boot was on /dev/sda1 during installation UUID=9762da9f-b9f0-4a9f-9796-ab14d69b3f5f /boot ext4 defaults 0 2

/dev/mapper/ubuntu--vg-swap_1 none swap sw 0 0   
```

Thanks for using *code tags*. It helps.

If that is really the fstab, then it is broken. Comments characters have been removed for some reason and a newline is missing.  In files like this details cannot be almost correct.  Newlines and lines that should be ignored are absolutely critical.
Also, I don't see the root partition/LV which must be mounted.  Whatever happened, it is bad.  It appears that LVM is being used on this system.  I use LVM myself.

Please post the output from these commands, including the exact command:
```
ls -l /dev/ubuntu*-vg/
blkid
lsblk
sudo parted -lm
```

Looks like we need to recreate the fstab from scratch, manually.  Be extremely careful if you ever edit the file again. It is clear that someone edited it and removed at least a few lines.  That often happens when someone uses a root shell or some GUI program as a filemanager/editor.   A common thing that people do is to make a copy of the file BEFORE they attempt to edit it.
For example:
```
sudo cp fstab fstab-bak
```

---

### Post by zarniwoopvannharl on 2019-09-21
> **TheFu said:**
>  snip 

Thanks ever so much for replying. 

Here we go. 

```
 ls -l /dev/ubuntu*-vg/
total 0
lrwxrwxrwx 1 root root 7 Sep 21 20:05 root - > ../dm-1
lrwxrwxrwx 1 root root 7 Sep 21 20:05 swap_1 - > ../dm-2
```

```
blkid
/dev/mapper/sda5_crypt: UUID="ef1FDJ-DPTB-CS9Q-w3Cy-RlgN-POUp-hjsNHV" TYPE="LVM2_member"
/dev/mapper/ubuntu--vg-root: UUID="05c5339c-3f8d-4af5-875c-ccb5a0c87a01" TYPE="ext4"
/dev/sda1: UUID="9762da9f-b9f0-4a9f-9796-ab14d69b3f5f" TYPE="ext4" PARTUUID="108dd22e-01"
/dev/sda5: UUID="ae7181cc-e6af-46d5-98ff-6217cdcda0cf" TYPE="crypto_LUKS" PARTUUID="108dd22e-05"
/dev/mapper/ubuntu--vg-swap_1: UUID="d6858d6f-cc4a-404a-ba05-4b3437519c05" TYPE="swap"

```


[IMG]https://imgur.com/9yq3KSx.png[/IMG]

```

sudo parted -lm
BYT;
/dev/sda:250GB:scsi:512:512:msdos:ATA Samsung SSD 860:;
1:1049kB:768MB:767MB:ext::boot;
2:769MB:250GB:249GB:::;
5:769MB:250GB:249GB:::;

BYT;
/dev/mapper/ubuntu--vg-root:248GB:dm:512:512:loop:Linux device-mapper (linear):;
1:0.00B:1028MB:1028MB:linux-swap(v1)::;

BYT;
/dev/mapper/ubuntu--vg-root:248GB:dm:512:512:loop:Linux device-mapper (linear):;
1:0.00B:248GB:248GB:ext4::;

Error: /dev/mapper/sda5_crypt: unrecognised disk label
BYT;
/dev/mapper/sda5_crypt:249GB:dm:512:512:unknown:Linux device-mapper (crypt):;


```

Hope these help.

---

### Post by TheFu on 2019-09-21
Posting images make copy/paste impossible. Thanks for making it harder for me to help. ;(
Also, encryption makes this much harder. Would have helped if that was mentioned previously.  If you touched the crypttab, I think reinstalling will be easier. I have no answer.

I don't see any EFI storage.  This is a legacy boot system?

If you didn't, then make this your /etc/fstab file:
```

# <file system>                  <mount point> <type> <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root               /     ext4 noatime,errors=remount-ro 0 1
UUID=9762da9f-b9f0-4a9f-9796-ab14d69b3f5f /boot ext4 defaults,noatime  0  2
/dev/mapper/ubuntu--vg-swap_1             none  swap    sw  0 0
```

Reboot. Good luck.

---

### Post by zarniwoopvannharl on 2019-09-21
> **TheFu said:**
> Posting images make copy/paste impossible. Thanks for making it harder for me to help. ;(
Also, encryption makes this much harder. Would have helped if that was mentioned previously.  If you touched the crypttab, I think reinstalling will be easier. I have no answer.

I don't see any EFI storage.  This is a legacy boot system?

If you didn't, then make this your /etc/fstab file:
```

# <file system>                  <mount point> <type> <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root               /     ext4 noatime,errors=remount-ro 0 1
UUID=9762da9f-b9f0-4a9f-9796-ab14d69b3f5f /boot ext4 defaults,noatime  0  2
/dev/mapper/ubuntu--vg-swap_1             none  swap    sw  0 0
```

Reboot. Good luck.

 Thanks. I do have full access to the encrypted partition via the root command prompt in recovery mode. Sorry for the screenshot, the post mucked up the table otherwise. I didn't touch the crypttab by the way. Not sure what you mean by legacy boot system. It's Ubuntu 18.04 or whatever the supported version is. 

I'll try what you mention though and let you know if it works.

---

### Post by TheFu on 2019-09-21
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) is 1 method. UEFI is how all Windows 8 and later systems boot, usually.  All ChromeOS systems boot using UEFI and Apple started it long, long, ago with EFI booting.  There are good things about UEFI booting. Pretty much every normal PC/Laptop made in the last 9 yrs supports UEFI booting.

Legacy boot is another.  Legacy is the way systems booted using BIOS since around 1980. Often, newer machines can also be setup to use "Legacy boot", but this is at the cost of some new security features.

---

### Post by zarniwoopvannharl on 2019-09-22
> **TheFu said:**
> 
```

# <file system>                  <mount point> <type> <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root               /     ext4 noatime,errors=remount-ro 0 1
UUID=9762da9f-b9f0-4a9f-9796-ab14d69b3f5f /boot ext4 defaults,noatime  0  2
/dev/mapper/ubuntu--vg-swap_1             none  swap    sw  0 0
```


This worked like a charm. You're my hero! Thanks ever so much.

---

