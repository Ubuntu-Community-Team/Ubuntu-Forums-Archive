---
title: "lost bootloader - help"
date: 2011-09-19
forum: New to Ubuntu
---

### Post by risoundz on 2011-09-19
Hello.

I installed Ubuntu with wubi and after the update I couldn't boot anymore.
I have 3 windows XP and ubuntu

I followed the instructions on Wubi megatread running windows recovery CD, did FIXBOOT but when I do FIXMBR it says I will lose my partitions.

can someone help with an idea to fix my multibootloader.

1- ubuntu was installed on the 2nd XP 
2- should I try to fix it from ubuntu liveCD?

partition configuration:

1-windows xp - Audio workstation
2-       "   - Internet, office apps
3-      "    - software tests 
4- GENERAL   - separate partition for doc,files,music,video.

I don't mind to lose 2nd,3rd XP but I really need MY audio DAW and MY General partition.


I hope someone can help

Thanks

Ricardo

---

### Post by Draggem on 2011-09-19
Are ye using grub-boot-loader?

If so try doing this with your ubuntu LiveCd:

I) Let’s find where Ubuntu is installed on your hard disk:

sudo fdisk -l

Device Boot Start End Blocks Id System
/dev/sda1 * 1 2611 20972826 83 Linux
/dev/sda2 2612 60279 463218210 83 Linux
/dev/sda3 60280 60801 4192965 82 Linux swap / Solaris

My ubuntu partition is /dev/sda1 (it has the asterisk under Boot).

II) Armed with this information, mount the Ubuntu partition:

sudo mount /dev/sda1 /mnt

III) Install the GRUB2 boot loader:

sudo grub-install --root-directory=/mnt /dev/sda

That’s /dev/sda — the hard disk itself, not the ubuntu partition – /dev/sda1.

IV) Unmount the Ubuntu partition and restart the computer like so:

sudo umount /dev/sda1 ; sudo reboot

V) If you have more than one OS installed, re-detect OSes like so:

sudo update-grub

That’s it.

---

### Post by varunendra on 2011-09-19
By default, a wubi installation uses a "root.disk" file as installation partition, not a physical partition. So the above grub restore method will not work.

@risoundz,
If the message says something like *"This computer appears to have a non standard partition table.... (blah-blah) .... fixmbr **MAY** damage .... "*, then it is normal. It doesn't necessarily mean you will lose partitions. Although, there is a potential risk if the partition table is really messed up, but by your description, I don't see a possibility of anything wrong with the partitions.

Most probably, it is just a matter of entering 'y' at fixmbr's prompt (ignoring the warning), and you will be able to boot XP again. But if you are really worried about those partitions, then get an external drive, backup necessary data, and go ahead with fixmbr. If for some reason, that is not possible, you may install lilo in the mbr (using live environment of ubuntu) which will boot your xp without problems. Please post back if you wish to go that way (although I really don't see much risk in trying fixmbr).

---

