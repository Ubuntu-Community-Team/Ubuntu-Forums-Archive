---
title: "Very slowboot (8 mins!!) 12.04"
date: 2012-10-01
forum: New to Ubuntu
---

### Post by Doobs too on 2012-10-01
Evening all,

I'm having real trouble fixing my very slow boot problem. I originally thought it was my ethernet adapter as the line before the big pause in dmesg said :-

[ 3.750961] sd 6:0:0:0: [sdb] Attached SCSI removable disk [ 364.079424] ADDRCONF(NETDEV_UP): eth0: link is not ready

I created .conf file to disable the ethernet (using [this]("http://askubuntu.com/questions/149514/disable-ethernet-permanently-to-speed-up-boot-time") link) but now it still takes ages to boot with two pauses, lines either side of the pause are pasted below. If anyone can help....oh it's a Toshiba NB200 Netbook running 12.04 alongside Vista....I'd be extreemly grateful.

[    2.881199] EXT3-fs (loop0): write access will be enabled during recovery
[  152.999583] kjournald starting.  Commit interval 5 seconds

[  165.000740] EXT3-fs (loop0): mounted filesystem with ordered data mode
[  472.475814] udevd[370]: starting version 175


Thank, Al

---

### Post by oldfred on 2012-10-02
Welcome to the forums.

Because it says loop, is this a wubi install?

Normally I would suggest fsck, but it is different commands for wubi version.

Standard install fsck:
#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

IF wubi see this:
How-to: Recover files from Wubi install with LiveCD
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)
[Script] Mount Wubi Disk from Linux mount old wubi in new install
mount ntfs partition first:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)
mkdir /mnt/windows
mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/ubuntu

Wubi install fsck:
sudo mkdir /media/win
sudo mount /dev/sda1 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk
Then check if you can mount it & read it:
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt

---

### Post by Avery Bolles on 2012-10-03
I'm not sure where you are getting stuck exactly.. If I were you I would just backup and reinstall, thats the really simple way. If there is still a problem that lets us know it's hardware configuration, not an error.

---

### Post by jlamorie on 2012-10-15
Gidday there,

I had very slow bootup problems with my NB200 with Meego. I had to  add "pci=nomsi" to the kernel boot parameters, so it might work for you (although this Meego installation is, I assume, an older kernel than that on Ubuntu 12.04).

I've seen other reports (in the Arch Linux forums) about changing the SATA controller from AHCI to Compatibility mode in the bios.  I don't know what that would do for dual boot between windows and linux.

There's quite a bit of advice available if you simply google "toshiba nb200 linux slow boot".

Hope that helps.

Joshua

---

### Post by Ermie on 2012-10-16
It is very timely. I experience the same. Thanks for this thread. i will start trouble shooting.

---

### Post by bcbc on 2012-10-17
I had the same issue on a Toshiba NB205 netbook - it took many minutes to boot up. To fix it I used the kernel boot option: nohz=off 

Not sure if it's still required as I don't run Ubuntu on it anymore (or applies to the NB200), but I'd try this and see if it fixes it.

---

