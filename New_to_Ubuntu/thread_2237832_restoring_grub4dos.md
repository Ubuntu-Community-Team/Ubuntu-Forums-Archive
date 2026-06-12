---
title: "restoring grub4dos"
date: 2014-08-04
forum: New to Ubuntu
---

### Post by wimpy2 on 2014-08-04
I used to use grub4dos, but after reading some information about grub2, I installed grub2. I found the information to be inaccurate, and I would now like to restore my old position. The system can also boot various distros of puppy linux (from which the original grub4dos came). I would like to just boot into one of the puppies and run grub4dos config. The menu.lst on the first partition should not need altering. Once having booted lubuntu, I would like to uninstall grub2. I'm hoping this will be possible, without doing any damage to the lubuntu setup. When I installed lubuntu, it insisted on a grub boot loader location, so I gave it the USB stick (which I later re-formatted) and used grub4dos..
Any help or suggestions would be appreciated.

---

### Post by yancek on 2014-08-04
Are you able to boot the computer?  To what, one of the Puppy installs?  What bootloader are you using to boot, if you can boot?  Where did you install Lubuntu, one of the internal hard drives?  a usb drive?  You can boot Lubuntu from a system with Grub Legacy such as Puppy if you know which partition the Lubuntu boot files are on, which we don't know.

What is the specific problem with Lubuntu?  Not able to boot?  If you put its boot files on a partition which you later formatted that would happen.  I'm not really clear on what the problem is.

---

### Post by oldfred on 2014-08-04
This is now old, but I installed puppy and booted it with grub2 on my hard drive.

 I did have to move lupu-511.sfs to the top level of the partition ( same as /boot not inside /boot) and created /boot/lupu511 with all the other files including vmlinux & initrd.gz.

menuentry "Puppy 511" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos12)'
        linux /boot/lupu511/vmlinuz root=/dev/ram0 pmedia=atahd loglevel=7 pkeys=us 
        initrd /boot/lupu511/initrd.gz
}

---

### Post by wimpy2 on 2014-08-04
Thank you both for the replies.
@yancek None of your questions address the question I asked. Grub2  and grub4dos both work. I just prefer grub4dos to grub2 - it's a lot quicker and easier to understand. I wanted to know whether removing grub2 would damage my installation of lubuntu.
@oldfred As I said, I can boot all my puppy distros  with grub2. It's just that I don't like it much. The reasons I installed grub2 were based on erroneous expectations. At the time I installed grub2, it warned me that because of the distance lubuntu's boot files lay from the start of the disk, it may take longer to boot or might even fail. It hasn't failed yet, but it certainly takes longer.

---

### Post by oldfred on 2014-08-04
I do not know if grub4dos will directly boot Lubuntu.
The only other case of grub4dos we see is those with EasyBCD for Windows Vista or later. And that uses grub4dos menu entry to chain to grub2 installed into the partition boot sector (PBR).
Installing grub2 into PBR is not recommended as it converts to blocklists or hard coded addresses. If you have a major update to grub or fsck that moves files address is wrong and you have to reinstall grub to PBR.

Ubuntu does have grub legacy in repository but not grub4dos.

---

### Post by wimpy2 on 2014-08-04
I can assure you that grub4dos will boot lubuntu 14.04  and Mint Mate 14.04. The PC I'm on now is an all-linux version, which I converted from grub4dos to grub2. I also have a multi-booting PC which uses grub4dos to boot Lubuntu, Puppy or Windows XP Pro. I think I'll take a chance and just do the conversion. At  the worst I can just reformat the Lubuntu partition and install another linux distro or even re-install Lubuntu.
UPDATE I booted a puppy linux through grub2 and ran grub4dos config. There doesn't seem to be any damage to Lubuntu. I haven't tried to uninstall grub2. I'm just letting it sit in Lubuntu, though it won't be called upon to do anything - I think. Now back to normal. I'll mark this as "Solved"

---

