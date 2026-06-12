---
title: "grup boot loader missing after shut down, boot-repair failed, please help!"
date: 2017-12-27
forum: New to Ubuntu
---

### Post by itsjoeyzeng on 2017-12-27
I have dual-boot (Ubuntu 16.04 & win10) on surface4. This morning  I had my Ubuntu froze so I had to shut down by pressing the power  button. 
  Somehow that messed up the grup boot-loader. First I could load into  win10 but after trying boot-repair in a USB Ubuntu, either system won't  boot. Here is the boot report, please help...
  [https://paste.ubuntu.com/26265560/](https://paste.ubuntu.com/26265560/)

---

### Post by oldfred on 2017-12-27
Probably not grub that is messed up, but your partition.
Forcing shutdown often corrupts system, so then you have to resolve that first then resolve whatever issue you really have. But sometimes system is just doing something in background and needs time to respond.

       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is, and S can be before E, but others should be in order
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)
[URL="https://askubuntu.com/questions/926461/whats-the-difference-between-the-magic-reisub-reset-and-holding-down-the-power"]https://askubuntu.com/questions/926461/whats-the-difference-between-the-magic-reisub-reset-and-holding-down-the-power

      [/URL]
 To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors, best to run anyway: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

In your case with NVMe drive, command would be more like this for your device.
sudo e2fsck -C0 -p -f -v /dev/nmve0n1p6
 

    [URL="https://askubuntu.com/questions/926461/whats-the-difference-between-the-magic-reisub-reset-and-holding-down-the-power"]
[/URL]

---

### Post by itsjoeyzeng on 2017-12-27
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/nvme0n1p6
                                                                               
      616173 inodes used (29.27%, out of 2105344)
         976 non-contiguous files (0.2%)
         599 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 554233/147
     3789304 blocks used (45.07%, out of 8407552)
           0 bad blocks
           1 large file

      439600 regular files
       97158 directories
         111 character device files
          50 block device files
           1 fifo
          37 links
       79207 symbolic links (61586 fast symbolic links)
          37 sockets
------------
      616201 files
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/nvme0n1p6
e2fsck 1.42.13 (17-May-2015)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

      616173 inodes used (29.27%, out of 2105344)
         976 non-contiguous files (0.2%)
         599 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 554233/147
     3789304 blocks used (45.07%, out of 8407552)
           0 bad blocks
           1 large file

      439600 regular files
       97158 directories
         111 character device files
          50 block device files
           1 fifo
          37 links
       79207 symbolic links (61586 fast symbolic links)
          37 sockets
------------
      616201 files


These indicate the partition is fine? Now I really want to do is just reinstall grup, but system won't let me.

After boot-repair, I have following message when boots:

Failed to open \EFI\BOOT\grubx64.efi  - NOT FOUND
Failed to load image \EFI\BOOT\grubx64.efi: NOT FOUND
Start_image() returned NOT FOUND

---

### Post by oldfred on 2017-12-27
I have seen others with that error but do not know where it is coming from.
Ubuntu boots from /EFI/ubuntu/grubx64.efi or /EFI/ubuntu/shimx64.efi.

And UEFI boots from /EFI/Boot/bootx64.efi as a hard drive entry or fallback entry.

But there should not be /EFI/Boot/grubx64.efi as a choice to boot.
If you have grubx64.efi in /EFI/Boot change it to bootx64.efi. Normally Boot-Repair does that by copying shimx64.efi and renaming it.

Post this:
sudo efibootmgr -v

And in Boot-Repair's advanced mode, do the full reinstall of grub. Be sure to boot Ubuntu live installer in UEFI boot mode, then add ppa for Boot-Repair.
       [https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

