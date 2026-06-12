---
title: "Problem with disks"
date: 2018-01-02
forum: New to Ubuntu
---

### Post by krychul on 2018-01-02
Hello.
First I need to say that I'm newbie in Ubuntu so I dont understand a lot of thinks in it.
My PC: Win 10 64x home. Disks: SSD samsung evo 350 250gb and HDD Seagate 1tb

Yesterday my PC worked great until today morning when I tried to start it and error 0xc0000e9 happened. I tried to fix it with Win 10 bootable usb but its not working. Then I used live ver of Ubuntu 16.04.3 LTS and checked that my system disk (SSD) and crap disk (HDD) cannot be opened. This is what it says:

**SSD error**:
```
 "Error mounting /dev/sdb2 at /media/ubuntu/Dysk SSD: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999" "/dev/sdb2" "/media/ubuntu/Dysk SSD"' exited with non-zero exit status 13: ntfs_mst_post_read_fixup_warn: magic: 0x10263e57  size: 1024   usa_ofs: 27348  usa_count: 50790: Invalid argument
Record 6 has no FILE magic (0x10263e57)
Failed to open inode FILE_Bitmap: Input/output error
Failed to mount '/dev/sdb2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details."

```
[B]HDD error: 
[/B]```
"Error mounting /dev/sda1 at /media/ubuntu/Seagate 1TB: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999" "/dev/sda1" "/media/ubuntu/Seagate 1TB"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option."

```
After this I tried to check SSD with 
[B]testdisk:
[/B]```
Disk /dev/sdb - 250 GB / 232 GiB - CHS 30401 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0  32 33    63 221 30    1024000
 2 P HPFS - NTFS             63 221 31 30341 204 32  486415001
 3 P Windows RE(store)    30341 226 30 30401  10  9     950272

```
[B] Deeper search:
[/B]```
Disk /dev/sdb - 250 GB / 232 GiB - CHS 30401 255 63
The harddisk (250 GB / 232 GiB) seems too small! (< 1840 GB / 1714 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...
The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
>  Linux                23617 150 22 31776 113 17  131072000
   FAT16 <32M           39008 153 25 223806  36 39 2968772514
   FAT16 <32M           117673 222 54 119238 130  1   25135877

```
and in advenced settings boot sector and backup boot sector have OK status. I didnt do anything more in testdisk because I dont know what im doing and I dont want to mess up it even more.

And last thing I tried was **Boot-Repair** and it didnt worked. This is my report: [https://paste.ubuntu.com/26306970/](https://paste.ubuntu.com/26306970/)

Now I gave up.
Help me Obi-Wan Kenobi. You are my only hope.

---

### Post by Impavidus on 2018-01-02
The problem with your HDD is entirely expected. I don't think anything is wrong with that one. Windows 10 doesn't really shut down, but uses some kind of hibernation, which makes it harder for Ubuntu to access the Windows file system. It's a feature you have to disable if you want to install Ubuntu, but for now you can try and mount the HDD read-only to read the files on the hard drive and make backups on an external drive, if you need.```
sudo mount -t ntfs -o ro /dev/sda1 /mnt
```If it asks for a password, just hit enter. Then use the file manager and navigate in your file system to /mnt and you should find the contents of your 1TB drive.

You may also be able to take the HDD out of the computer and plug it into a different Windows computer and that should be able to access the files.

Your SSD is in a worse state. I don't think Ubuntu can fix it for you (Ubuntu isn't very good at fixing Windows problems) and it might actually be broken

---

