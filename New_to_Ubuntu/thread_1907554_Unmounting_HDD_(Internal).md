---
title: "Unmounting HDD (Internal)"
date: 2012-01-11
forum: New to Ubuntu
---

### Post by Lukeyslife on 2012-01-11
Right so i have my partition and i wanted to format it so that i can reinstall my windows vista i try to use GPARTED to unnmount it but it says could not unmount partition /dev/sda1
because of mount points / (root), next step i researched how to manually unmount and found by using terminal commands such as sudo umount /dev/sda1 it requires password i enter that in and it says umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
any help will be appreciated

---

### Post by sandyd on 2012-01-11
> **Lukeyslife said:**
> Right so i have my partition and i wanted to format it so that i can reinstall my windows vista i try to use GPARTED to unnmount it but it says could not unmount partition /dev/sda1
because of mount points / (root), next step i researched how to manually unmount and found by using terminal commands such as sudo umount /dev/sda1 it requires password i enter that in and it says umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
any help will be appreciated
Just install windows vista over it. Boot up from Vista OEM, and delete the partitions.
Install.

---

### Post by Lukeyslife on 2012-01-11
> **sandyd said:**
> Just install windows vista over it. Boot up from Vista OEM, and delete the partitions.
Install.


i forgot to mention i tried this but on the installation it said my partition was full even though i have 65gb spare

and also on installation it said about formatting or removing the partition but that didnt work either had an error code
also i think its because i need it to be a NTFS format but i forgot how to change that

---

### Post by Double.J on 2012-01-11
> **Lukeyslife said:**
> i forgot to mention i tried this but on the installation it said my partition was full even though i have 65gb spare

and also on installation it said about formatting or removing the partition but that didnt work either had an error code
also i think its because i need it to be a NTFS format but i forgot how to change that

Are you trying to edit yor primary drive from inside an ubuntu booted off that device? This isn't advisable for the reason that you can't unmount the drive completely. Try running from the Live CD

I wouldn't advise setting up ntfs with gparted for use with the windows installer - this sometimes goes wrong, better to use free space or fat32.

You are trying to install Windows before Ubuntu aren't you? Windows MUST go before Ubuntu (far left) on the disk - this may be why you were unable to create the partition.. either that or you are already using too many primary partitions?

---

### Post by Double.J on 2012-01-11
> **Lukeyslife said:**
> i forgot to mention i tried this but on the installation it said my partition was full even though i have 65gb spare

When you say your *_partition_* has 65GB free space, do you mean your linux (EXT formatted) partition has space free in it? Windows can't read anything but NTFS and FAT file systems - it definitely can't shrink a Linux partition - you'd have to do this from a live CD

---

### Post by Lukeyslife on 2012-01-11
> **gnu/mirow said:**
> Are you trying to edit yor primary drive from inside an ubuntu booted off that device? This isn't advisable for the reason that you can't unmount the drive completely. Try running from the Live CD

I wouldn't advise setting up ntfs with gparted for use with the windows installer - this sometimes goes wrong, better to use free space or fat32.

You are trying to install Windows before Ubuntu aren't you? Windows MUST go before Ubuntu (far left) on the disk - this may be why you were unable to create the partition.. either that or you are already using too many primary partitions?

i have 2 partitions one which is 1003mb recovery partition i believe
one that has ubuntu on it it says 0.0mb free space on that one because its not a NTFS which is the primary drive, i used to have vista installed then it froze on re installation couldnt recover it so used linux instead now i have both discs for vista and ubuntu and wanting to have just vista not a dual boot of both

---

### Post by Double.J on 2012-01-11
> **Lukeyslife said:**
> i have 2 partitions one which is 1003mb recovery partition i believe
one that has ubuntu on it it says 0.0mb free space on that one because its not a NTFS which is the primary drive, i used to have vista installed then it froze on re installation couldnt recover it so used linux instead now i have both discs for vista and ubuntu and wanting to have just vista not a dual boot of both

If you're looking to get rid of ubuntu and go back to vista, first make sure that you have a copy of all of your data - and check that copy, then use the Ubuntu live cd. in gparted delete the ubuntu partition then run the Windows vista installer- shouldn't have any problems with it now :)

On behalf of the community Sorry you're leaving!

---

### Post by Lukeyslife on 2012-01-11
> **gnu/mirow said:**
> If you're looking to get rid of ubuntu and go back to vista, first make sure that you have a copy of all of your data - and check that copy, then use the Ubuntu live cd. in gparted delete the ubuntu partition then run the Windows vista installer- shouldn't have any problems with it now :)

On behalf of the community Sorry you're leaving!


thanks im only leaving because i need some programs that arent compatible with linux but otherwise ubuntu is i believe an absolutely amazing OS :) soon ill have really good pc and have dual boot with ubuntu on it

---

### Post by Lukeyslife on 2012-01-12
so when i run the cd what do i press Ubuntu with generic linux 3.0.0 and run gparted?

---

### Post by mikechant on 2012-01-12
There's usually a CD boot option called something like 'try ubuntu without changing your hard drive', select that and then use gparted, as you said. The Live CD will usually mount the swap partition if it exists, you can just right click it and select swapoff if I remember correctly, then you can delete the swap partition, the main Ubuntu partition and any other Ubuntu related partitions.

---

### Post by Lukeyslife on 2012-01-12
> **mikechant said:**
> There's usually a CD boot option called something like 'try ubuntu without changing your hard drive', select that and then use gparted, as you said. The Live CD will usually mount the swap partition if it exists, you can just right click it and select swapoff if I remember correctly, then you can delete the swap partition, the main Ubuntu partition and any other Ubuntu related partitions.

right thanks ive deleted the swap off now do i remove the other partition aswell

---

### Post by CharlesA on 2012-01-12
> **Lukeyslife said:**
> right thanks ive deleted the swap off now do i remove the other partition aswell
Yeah, then install Vista.

---

