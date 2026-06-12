---
title: "Question about installing without a CD or USB stick"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by suniljdsouza1974 on 2011-10-20
Hi,

I was looking to install Ubuntu on this barebones PC I was thinking about purchasing a Zotac PC and going with a 250 GB harddrive:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16856173012&nm_mc=OTC-Froogle&cm_mmc=OTC-Froogle-_-Barebone+Systems+-+Mini+/+Booksize-_-ZOTAC-_-56173012](http://www.newegg.com/Product/Product.aspx?Item=N82E16856173012&nm_mc=OTC-Froogle&cm_mmc=OTC-Froogle-_-Barebone+Systems+-+Mini+/+Booksize-_-ZOTAC-_-56173012)

I don't have a USB stick or an external CD/DVD ROM.  However, I do have 2.5" Sata HDD to USB 2.0 connection.  Would I be able to download Ubuntu onto the hard drive via this connection and then connect the hard drive to the Zotac box and do the install?

Any help would be appreciated.

---

### Post by oldfred on 2011-10-20
If you install grub2 (not even of full install of Ubuntu to the external drive) you can use it to directly loopmount the ISO file and install from that. I do that now from sdb to sdc or my new sdd drives. I have full install of Ubuntu on sdb but add the ISO boot entry to 40_custom.

Hard drive:
Direct boot on hard drive:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

I have installed grub2 to FAT32, NTFS & EXT4 partitions on flash drives and loopmounted ISO from all of them. You do have to manually create grub.cfg, but just need to copy a boot stanza into it.

Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")

These are my entries, but note I use gpt on sdb so I include that where you may need msdos. I also directly boot sdb, so it is hd0, boot drive is always hd0 and other drives follow in motherboard port order with my SATA system.

```
menuentry "Uubuntu 11.10 Oneiric ISO 64bit" {

    set isofile="/iso/oneiric-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd0,4)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

menuentry "Uubuntu 11.04 Natty ISO 64bit" {

    set isofile="/iso/ubuntu-11.04-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd0,4)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}



```

---

### Post by suniljdsouza1974 on 2011-10-21
Hi,

thank you for your reply.  Based on the Zotac PC, I have listed.  Would you recommend going with a 64 Bit install if I get more than 2 gigs of RAM?  Would there be any drawbacks to a 64 Bit install?

Thank you,

Sunil DSouza

---

### Post by oldfred on 2011-10-21
Do not know specs of your computer. But I have run 64bit on my desktop and installed the 64bit on my 5 year old laptop with only 1.5GB of RAM. No real issues with either computer.

Most say you should have at least 2GB of RAM to use the 64bit as the wider footprint uses a bit more RAM that is  a trade off with better 64 bit processing.

---

