---
title: "Partition Mounting"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by SamerBerjawi on 2008-05-15
Why do I have to open the partition that hardy is not installed on everytime i boot, so that I can access it later on.

---

### Post by Tatty on 2008-05-15
What do you mean by 'open the partition'?

---

### Post by SamerBerjawi on 2008-05-15
My Harddisk is divided into three partitions, the one where Hardy is Installed, a swap partition, and 75GB Part.
In Hardy, I used to have an icon of the 75GB part on desktop when I boot, but with gutsy this doesn't appear until I go to Places > 75GB Media

---

### Post by UnWarierMage224 on 2008-05-15
You might want to edit your /etc/fstab file to have that partition mounted for you at boot. I do not know the code off the top of my head, so I will leave that to someone more experienced to give you, but that's something you might want to consider.

EDIT: Actually, I will give you the code I'm using, or at least what I did....

In my media folder I created a folder for the partition (/wherever/somefoldername)
then in the etc/fstab file I added the following line:

```

/dev/sda5     /wherever/somefoldername     /ntfs    /defaults    0    0

```

The first bit corresponds to the actual... portion of the filesystem. That information can be retrieved with some command (which I do not know) 
The second bit corresponds to what folder you want that drive to be mounted to. 
Third bit is what kind of filesytem (vfat, ntfs, ext3, etc) it is 
Fourth bit is boot options.. I think its safest to leave it at defaults. 
the last two bits, I'm not sure about. Hopefully someone wiser will be more clear in explanations. 

Hope this helps, 

EDIT - A warning: fstab is not something to be trifled with (mess with it incorrectly, you could hose the whole system), so I would recommend checking with someone wiser than me before you attempt to do anything to it.

-'Mage

---

