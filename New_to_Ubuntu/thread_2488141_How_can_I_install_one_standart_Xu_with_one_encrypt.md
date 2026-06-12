---
title: "How can I install one standart Xu with one encrypted LVM XU ?"
date: 2023-06-24
forum: New to Ubuntu
---

### Post by yanech on 2023-06-24
Hi.
I Need 2 versions of Xubuntu on my workstation (MSI Cubi N JSL with N6000 proc, if that matters).
One everyday installation for everyone in the familly, and one encrypted for sensitive work.
Installing one of both is easy, but i don't know how to install the other to be able to choose the one I want when booting.
How should I organize my partitions ?
Thanks.

---

### Post by Bashing-om on 2023-06-24
Hello yanech - Welcome to the Forums.

From Gparted - set up partitions manually - and label these partitions - later you will appreciate that labeling :D
for your consideration - a set up on one of my disks:
> 
sudo fdisk -lu >>
Disk /dev/sda: 111.79 GiB, 120034123776 bytes, 234441648 sectors
<snip>
/dev/sda1  *         2048  16386047  16384000  7.8G 83 Linux
/dev/sda2        16386048  36866047  20480000  9.8G 83 Linux
/dev/sda3        36866048  49154047  12288000  5.9G 83 Linux
/dev/sda4        49154048 172034047 122880000 58.6G  5 Extended
/dev/sda5        49156096 110596095  61440000 29.3G 83 Linux
/dev/sda6       110598144 131078143  20480000  9.8G 83 Linux
/dev/sda7       131080192 151560191  20480000  9.8G 83 Linux
/dev/sda8       151562240 160163839   8601600  4.1G 82 Linux swap /
//

<snip>

sudo blkid >>
/dev/sda1: LABEL="x2204root" UUID="1460de17-30e4-4566-b181-18c17b62887a" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="c6c4079f-01"
/dev/sda2: LABEL="x2204home" UUID="5cd50446-1330-4130-a521-1ea936c9fc2a" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="c6c4079f-02"
/dev/sda3: LABEL="x2204var" UUID="69b1f02a-5e00-415e-ab75-78fdd63f72a3" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="c6c4079f-03"
/dev/sda5: LABEL="u2210" UUID="0b89d785-9ba8-4bd5-a41a-43462459c230" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="c6c4079f-05"
/dev/sda6: LABEL="bups" UUID="a0c6dc1f-51d3-4824-b770-ce42d777277a" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="c6c4079f-06"
/dev/sda7: LABEL="data" UUID="fe9cee2e-6812-46e1-b0a0-b03d5094763a" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="c6c4079f-07"
/dev/sda8: UUID="5e1c0b41-6fda-4231-877c-1e0601a626b5" TYPE="swap" PARTUUID="c6c4079f-08"
<snip>


Now be aware my 22.04 install is a "testing bed" - the partitioning is verry small ! For a daily driver I would suggest at least 3 times as large - depending on use cases - might want /home much larger :D And rather than a swap partition I would allow the installer to make a swap file.

For booting (I currently do have 4 'buntu's installed on this system) I do recommend that the boot menu be maintained from the primary (admin's) installation. in your alternate (secondary) install disable os_prober.
Boot your secondary and run terminal command:
```

sudo chmod -x /etc/grub.d/30_os-prober
sudo update-grub #to promulgate the change#

```
Reboot into the primary and here run only:
```

sudo update grub

```
such that grub picks up the secondary install and from the primary you are able to boot either install - this prevents a possible recursion of entries in grub's config files.

[INDENT]just the way I do it - YMMV
[/INDENT]

---

### Post by yanech on 2023-07-10
Hi, 
Thank you for your help, I have read your reply several times after reading other threads.

If I'm correct, you are only using unencrypted partitions.
I have tried and been successful in installing several distros on the same drive.

Things start to go wrong when I had an encrypted partition.
If I'm correct, I need a GPT partition table.
then, on my disk, I need an EFI system partition, a small /boot unencryped partition, and an encrypted partition for my first OS.

I have then tried to add an encrypted or unencrypted partition for a second OS, but then the first one is unavailable.
(EFI system partition, /boot for OS1, encrypted partition with OS1, /boot for OS2, encrypted partition with OS2 for instance,
or EFI system partition, / for OS1, /boot for OS2, encrypted partition with OS2, and other unlikely setups)

I've read articles about a bootloader partition, but nothing worked for me.

If you can point me to some solutions, that would really be helpful.

Yanech.

---

