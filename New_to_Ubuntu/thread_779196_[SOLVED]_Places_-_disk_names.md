---
title: "[SOLVED] Places - disk names"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by ubername on 2008-05-02
Hi

I hope I am not posting this twice, I thought I had posted it an hour ago or so, but I don't see it.

In my 'Places' menu I have a couple of disks named e.g. '70.3 GB Media', '100.2 GB Media'

I would like to rename them to something more meaningful, but wherever I try (right-clicking, selecting properties from Nautilus etc.) I get nowhere. Any help?

TIA

---

### Post by y-aji on 2008-05-02
Being a newbie as well, I would guess this is a dangerous idea.  You could definately rename the shortcuts on your desktop, just right click and hit rename.. But, i have a feeling those in the actual folder should stay the same, but i could definately be wrong..

---

### Post by ubername on 2008-05-02
> **ubername said:**
> Hi

I hope I am not posting this twice, I thought I had posted it an hour ago or so, but I don't see it.

In my 'Places' menu I have a couple of disks named e.g. '70.3 GB Media', '100.2 GB Media'

I would like to rename them to something more meaningful, but wherever I try (right-clicking, selecting properties from Nautilus etc.) I get nowhere. Any help?

TIA

Ok I found my previous post. Odd. It didn't show up under the 'search all your threads' option.

---

### Post by ubername on 2008-05-02
> **y-aji said:**
> Being a newbie as well, I would guess this is a dangerous idea.  You could definately rename the shortcuts on your desktop, just right click and hit rename.. But, i have a feeling those in the actual folder should stay the same, but i could definately be wrong..

Thanks Y-Aji

I don't have the icons on my desktop anymore, (I used ubuntu-tweaks to get rid of them) but when I did, right clicking didn't give a rename option. But thankyou for reading and offering advice, that is what the forums are for.

---

### Post by PeterJS on 2008-05-02
The way Ubuntu labels removable drives is based on the partition label. If a partition is not labeled Ubuntu will use a generic XX GB volume label. How you go about labeling partitions depends what file system is on the partition.

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by ubername on 2008-05-02
> **PeterJS said:**
> The way Ubuntu labels removable drives is based on the partition label. If a partition is not labeled Ubuntu will use a generic XX GB volume label. How you go about labeling partitions depends what file system is on the partition.

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

Thanks for that, funnily enough I had tried the 

sudo e2label /dev/sda1 newlabel

command before, but it seemed to make no difference, and when I looked at the output from 'mount' I could see no difference. For what it's worth, one of the drives is internal and the other is a USB drive. I hate to admit this, but I have formatted half the USB drive as NTFS using Vista, and got the option to give it a name there (I called it 'USB Windows'). This shows up just fine in ubuntu! It is a bit frustrating that the partition that I configured under Windows is easier to make recognisable (by name)  than those under Ubuntu.

---

### Post by ubername on 2008-05-03
> **PeterJS said:**
> The way Ubuntu labels removable drives is based on the partition label. If a partition is not labeled Ubuntu will use a generic XX GB volume label. How you go about labeling partitions depends what file system is on the partition.

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

Thanks for this. All my disks are nicely named now. I needed to mess about a bit with unmounting and rebooting, but all done. I would mark this thread closed if I could.

Mods: Can you mark this as closed?

---

