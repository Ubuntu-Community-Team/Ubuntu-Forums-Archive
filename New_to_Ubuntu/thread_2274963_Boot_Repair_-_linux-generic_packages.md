---
title: "Boot Repair - linux-generic packages"
date: 2015-04-23
forum: New to Ubuntu
---

### Post by Ruehle_EDV on 2015-04-23
Hello,
im about to give up.

# cloned source harddrive with ubuntu 12.04 to a bigger harddrive with clonezilla
# get [COLOR=#ff0000]error when booting[/COLOR] from cloned harddrive 
```
[COLOR=#ff0000]error: file not found.[/COLOR]
grub rescue> ls
(hd0) (hd0,msdos1)
grub rescue> ls (hd0)
[COLOR=#ff0000]error: unknown filesystem.[/COLOR]
grub rescue> ls (hd0,msdos1)
[COLOR=#ff0000]error: bad filename.[/COLOR]
```
# tried to fix the grub error with boot repair ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair))
 Boot Repair runs into an [COLOR=#ff0000]error[/COLOR]: 
```
Please enable a repository containing the [linux-generic] packages in the software sources of Debian GNU/Linux (sda1). Then try again.
```
# tried to reinstall grub ([http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)) but got stuck when i try 
```
chroot /mnt
```
```
[COLOR=#ff0000]chroot: failed to run command ´/bin/bash': Accessing a corrupted shared libary[/COLOR]
```
# I tried all of this with ubuntu 12.04 64bit and 14.04 64bit, with linux mint cinnamon and finally with the boot-repair-disk (live lubuntu with boot-repair)

# I also tried to backup the mbr and grub with dd from the original harddrive:
```
sudo dd if=/dev/sda of=mbr+grub_bup bs=512 count=63
```
And restored it on the cloned hdd:
```
sudo dd if=mbr+grub_bup of=/dev/sdb bs=512 skip=1 seek=1 count=62 
```
but i still cannot boot...

If this helps, here you can find the boot-info:
[http://paste.ubuntu.com/10871419/](http://paste.ubuntu.com/10871419/)

I read much blogs, posts, forums without success or maybe im just blind.

I would really appreaciate if u can help me to fix the cloned drive.

---

### Post by oldfred on 2015-04-23
It does not look like it is finding /boot and then /boot/grub. So you do not have a grub menu nor kernels found by Boot-Repair.
Then it also cannot find repository to use to do updates when chrooted.

This is why I prefer just to do a full new install. If you just copy /home over then you have most of your system. And if you installed lots of apps you can export that as a list and easily reinstall. Only if you also manually edited system config files like grub, network or other might you also want /etc or some settings from /etc if not same version.

Is this perhaps an older BIOS? There is an old issue with very old BIOS that must boot from the first 137GB of a drive. So those installing to a new much larger drive need to have a separte / (root) fully within the first 137GB and use rest as /home or use a /boot at beginning of drive that is fully inside 137 limit.

My backup procedure is to have what I need to fully restore system when I do a new install or upgrade. Still what oldfred does, but added some of the updates from other links.
       Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
      
 Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)
[http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997)

---

### Post by Ruehle_EDV on 2015-04-24
Hello oldfred,

thank you for your answer but a fresh install is exactly what i wanted to avoid.
I know, i can backup and restore but i also know that it will take ages to get all of it to work again.
Thats why i tried to clone the hard drive.

The Machine and the BIOS are like 3 or 4 years old. 
The source HDD has 250 GB, so i think the 137 GB bug can be excluded, cant?
> It does not look like it is finding /boot and then /boot/grub.
I think there is a /boot and /boot/grub on sda. 
Further iam able to ls those locations.
Look at the first lines of the boot info script:
```
Grub2 [COLOR=#666666]([/COLOR]v1.99[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sda and looks at sector 1 of 
the same hard drive [COLOR=#AA22FF]**for **[/COLOR]core.img. core.img is at this location and looks 
[COLOR=#AA22FF]**for**[/COLOR] [COLOR=#666666]([/COLOR],msdos1[COLOR=#666666])[/COLOR]/boot/grub on this drive.
```
Any other suggestions?

---

### Post by oldfred on 2015-04-24
BIOS should not be issue if only 3 or 4 years old.

But script did not show /boot and its contents. Can you browse from live installer and see if yo uhave a /boot folder with kernels & grub.cfg in /boot/grub?

What version of Ubuntu?
Was your old install up to date and using a working mirror for its updates?

---

