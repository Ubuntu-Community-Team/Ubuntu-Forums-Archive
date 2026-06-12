---
title: "Slow boot Ubuntu 16.04 LTS"
date: 2017-11-25
forum: New to Ubuntu
---

### Post by vistus on 2017-11-25
Hi,

I am experiencing slower boot times than before, and cannot seem to figure out where the problems is.
Any ideas how to speed it up?


Startup finished in 8.351s (kernel) + 17.864s (userspace) = 26.216s

Systemd-analyze blame: 

```
          10.522s dev-sda1.device
          8.886s ufw.service
          7.651s systemd-tmpfiles-setup-dev.service
          4.502s snapd.service
          3.881s NetworkManager.service
          3.370s keyboard-setup.service
          3.217s accounts-daemon.service
          3.144s ModemManager.service
          2.140s systemd-sysctl.service
          2.130s thermald.service
          1.910s iio-sensor-proxy.service
          1.540s apparmor.service
          1.286s lightdm.service
          1.045s systemd-journald.service
          1.035s grub-common.service
           996ms sys-kernel-debug.mount
           971ms irqbalance.service
           958ms systemd-modules-load.service
           914ms console-setup.service
           871ms avahi-daemon.service
           774ms dev-hugepages.mount
           773ms dev-mqueue.mount
           649ms polkitd.service
```
Although the total boot time is not super-high, I think most of these services should not take seconds to load with the set-up I am using. Initially, the boot time was even higher but I already disabled some of the unnecessary services.


Details: 

Mem. 16 GB
Processor Intel® Core™ i7-4810MQ CPU @ 2.80GHz × 8
Graphics GeForce GTX 870M
OS Ubuntu 16.04 LTS 64-bit

All help is much appreciated.

---

### Post by oldfred on 2017-11-25
What kind of drive?
And what is sda1? It may need fsck if ext4 or dosfsck if your UEFI ESP partition.

This is mine from i5-4690K system with Samsung_SSD_840 128GB drive.
```
fred@Asusz97:~$ systemd-analyze blame
          8.128s NetworkManager-wait-online.service
          5.128s udev-configure-printer@-devices-pci0000:00-0000:00:14.0-usb3-3\
          2.452s apt-daily.service
           383ms apt-daily-upgrade.service

```

---

### Post by vistus on 2017-11-26
About the drive, here is lshw -class disc -class storage    *-storage                       description: SATA controller        product: 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode]        vendor: Intel Corporation        physical id: 1f.2        bus info: pci@0000:00:1f.2        version: 05        width: 32 bits        clock: 66MHz        capabilities: storage msi pm ahci_1.0 bus_master cap_list        configuration: driver=ahci latency=0        resources: irq:34 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:f7b1a000-f7b1a7ff   *-scsi:0        physical id: 1        logical name: scsi0        capabilities: emulated      *-disk           description: ATA Disk           product: ST1000LM024 HN-M           vendor: Seagate           physical id: 0.0.0           bus info: scsi@0:0.0.0           logical name: /dev/sda           version: 0001           serial: S2ZWJ9EF204211           size: 931GiB (1TB)           capabilities: partitioned partitioned:dos           configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=1a5f9f3d   *-scsi:1        physical id: 2        logical name: scsi3        capabilities: emulated   .   I'm new to ubuntu so unfortunately I don't know what you mean by "And what is sda1? It may need fsck if ext4 or dosfsck if your UEFI ESP partition". Can you please elaborate on that?

---

### Post by vistus on 2017-11-26
Sorry about the format. I don't know why it came out that way.

---

### Post by oldfred on 2017-11-26
If from terminal output copy & paste directly. Then add code tags. Easy to add code tags using Forum's advanced editor & # icon.

Just wanted to know if SSD or HDD. And if SSD, you may need to update firmware.

Post this, so we can see what sda1 is:
sudo parted -l

---

### Post by vistus on 2017-11-26
Hi yes I copy pasted the previous from terminal but for some reason that was how it appeared after posting.

Here is sudo parted -l

Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  983GB   983GB   primary   ext4            boot
 2      983GB   1000GB  17,1GB  extended
 5      983GB   1000GB  17,1GB  logical   linux-swap(v1)


Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/cryptswap1: 17,1GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0,00B  17,1GB  17,1GB  linux-swap(v1)

---

### Post by oldfred on 2017-11-26
I do not know details on encrypted /home. 
Since you have encrypted swap, I assume you have an encrypted /home?

I still think this works with encrypted /home, but you will have to give password so it is open?
 To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s), run both.
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda1 

I have seen where users recreate swap, does UUID of swap match UUID in fstab?
Or one user just had a DVD in drive and for some odd reason system was trying to run a fsck on it?
Check you do not have UEFI/BIOS adding devices like a floppy that you do not have. System will try to mount a device and have to time out.

---

### Post by vistus on 2017-11-26
Hi yes my /home is encrypted. I ran sudo e2fsck -C0 -p -f -v /dev/sda1 after booting from usb:
                                                                                 
       809128 inodes used (1.35%, out of 60006400)
         9683 non-contiguous files (1.2%)
          908 non-contiguous directories (0.1%)
              # of inodes with ind/dind/tind blocks: 0/0/0
              Extent depth histogram: 756620/241
     40967214 blocks used (17.07%, out of 240017408)
            0 bad blocks
           15 large files
 
 
       677437 regular files
        61768 directories
           55 character device files
           25 block device files
            0 fifos
           36 links
        69830 symbolic links (52175 fast symbolic links)
            4 sockets
 ------------
       809155 files


As for UUID of swap matching the UUID in fstab, I did check this earlier and they do match. Also as far as I can tell, there is nothing out of ordinary in BIOS, like adding non-existent devices.

---

