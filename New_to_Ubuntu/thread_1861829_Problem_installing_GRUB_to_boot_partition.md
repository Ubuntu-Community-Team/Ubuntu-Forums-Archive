---
title: "Problem installing GRUB to boot partition"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by els01x on 2011-10-16
My HDD has 4 partitions

/dev/sda1 - W7 encrypted with Truecrypt
/dev/sda2 - ext2, boot partition
/dev/sda3 - encrypted LVM, where I install Ubuntu
----/root, ext4
----/home, ext4
----/swap
/dev/sda4 - NTFS, just for regular storage

So I go through the installation with the alternate iso (11.10), manually format both the boot and encrypted LVM, just like always. Everything is normal until the GRUB installation. I set /dev/sda2 as the target for the Grub installation but I encounter this error:

```
"WARNING!! Install the GRUB boot loader on a hard disk

Unable to install GRUB in /dev/sda2
Executing 'grub-install /dev/sda2' failed.

This is a fatal error."
```
 
So I continue the installation without the boot loader and finish it.

I boot with a live CD and issue the following command:

```
sudo grub-install /dev/sda2
```

And I get the error:

```
"grub-probe: error: cannot find a device for /boot (is /dev mounted?).
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
```

Any ideas?

I got this problem in my netbook too. Had to decrypt the windows partition to install grub on the MBR, which is troublesome to say the least.

Thank you in advance.

---

### Post by Perfect Storm on 2011-10-16
Try set it to sda instead of sda2

---

### Post by els01x on 2011-10-16
> **Artificial Intelligence said:**
> Try set it to sda instead of sda2

Yeah, that's the problem. Setting it to sda would intall it to the MBR, killing the truecrypt boot loader, locking me out of the Windows partition. Hence why I have a separate boot partition for GRUB.

What I don't understand is why it refuses to install there :/

---

### Post by sadaruwan12 on 2011-10-16
You're better of installing it on to your MBR rather than to partition and you're trying to install it to the /boot partition where all boot related files are so might that be the case and why do you say that'll lock you out of your windows I don't think that'll happen 'cos I've triple booted a system without any issue so why are you so afraid of installing it on to your MBR.

---

### Post by Perfect Storm on 2011-10-16
Is /boot set as Primary?

---

### Post by drs305 on 2011-10-16
I don't know anything about encrypted LVM partitioning, but from the LiveCD, if you can, mount your Ubuntu partition *and* your /boot partition before trying to install Grub. That could be the problem.

Mount Ubuntu (/mnt), then the /boot partition (/mnt/boot), then run the command. With it mounted in this manner I don't think you would have to use the "--force" option to get it to write to your sda2 partition.

---

### Post by els01x on 2011-10-16
> **sadaruwan12 said:**
> You're better of installing it on to your MBR rather than to partition and you're trying to install it to the /boot partition where all boot related files are so might that be the case and why do you say that'll lock you out of your windows I don't think that'll happen 'cos I've triple booted a system without any issue so why are you so afraid of installing it on to your MBR.

The problem with installing to the MBR in this case is that Truecrypt installs its own bootloader on the MBR, so if install GRUB to the MBR (which AFAIK, doesn't recognize truecrypt system partitions), then I'll be locked out of the W7 partition.  > **Artificial Intelligence said:**
> Is /boot set as Primary?

Yes, /dev/sda2 is a primary partition.

> **drs305 said:**
> I don't know anything about encrypted LVM  partitioning, but from the LiveCD, if you can, mount your Ubuntu  partition *and* your /boot partition before trying to install Grub. That could be the problem.

Mount Ubuntu (/mnt), then the /boot partition (/mnt/boot), then run the  command. With it mounted in this manner I don't think you would have to  use the "--force" option to get it to write to your sda2  partition.

OK, I tried this from the Live CD:

```
#sudo apt-get install -y lvm2 (so the system can read the LVM)
#vgchange -a y (to activate the volumes within the LVM)
#sudo su
#cd /
#mount /dev/UBUNTUSTUDIO/root /mnt
#mount /dev/sda2 /mnt/boot
```This is the part I'm not sure of

```
#grub-install /dev/sda2
```I get this error:

```
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?),
```I then tried these other commands:

```
#grub-install /mnt/boot
#grub-install /mnt
```But I get the same error as above with both :sad:

---

### Post by drs305 on 2011-10-16
I don't know if I understand how your system is set up, since I find your /root designation a bit confusing (but it's probably just me). It could be related to LVM and how the partitions are designated therein.

When you mount '/root' to /mnt, is the entire OS mounted or is it just the 'root' folder; i.e. does "ls /mnt/root" return all the Ubuntu system folders such as "etc", "home", "boot" or does it only show the normal /root folders such as ".cache", ".config" and "Desktop".

I think it will be best if I just step aside and let LVM-experienced users figure this one out.

---

### Post by els01x on 2011-10-16
> **drs305 said:**
> I don't know if I understand how your system is set up, since I find your /root designation a bit confusing (but it's probably just me). It could be related to LVM and how the partitions are designated therein.

When you mount '/root' to /mnt, is the entire OS mounted or is it just the 'root' folder; i.e. does "ls /mnt/root" return all the Ubuntu system folders such as "etc", "home", "boot" or does it only show the normal /root folders such as ".cache", ".config" and "Desktop".

I think it will be best if I just step aside and let LVM-experienced users figure this one out.
It shows all the system files, except home of course, since that's in another partition within the LVM (there's root, home and swap).

The problem is particularly weird because I've done this type of installations before, it's the first time GRUB goes crazy on me :/

---

### Post by drs305 on 2011-10-16
Partly, at least, I missed the forest for the trees since you are running from the LiveCD.

If you are booting from the LiveCD, you also should specify the / or boot directory. After mounting the root partition (your /root) and /boot, and since you are using Grub 1.99, let's identify the 'boot' folder:

```
sudo grub-install --boot-directory=/mnt/boot --force /dev/sda2
```

I haven't tried using the 'force' option with combination of commands, but at worst it just won't run and give you an error.

---

