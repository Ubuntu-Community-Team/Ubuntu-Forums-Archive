---
title: "hardware question for new Ubuntu machine"
date: 2013-02-09
forum: New to Ubuntu
---

### Post by Old Jimma on 2013-02-09
Hi Community:

I'm building a new Ubuntu machine and only want to use an SDD... no HD.

All of the files I want are on an old Ubuntu machine.

Can't I simply create a mount point on the SSD and mount the directories I want that reside on the old Ubuntu machine?

What is the best way to do this? samba? what?

Thanks,
Old Jimma, yippie aiee kay-oh!

:)

---

### Post by arpanaut on 2013-02-09
Use of fstab would probably be the easiest if the drive will be installed on the new rig.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Paqman on 2013-02-10
If you're talking about a lot of data probably the easiest thing to do is unplug the hard drive from the old machine and plug it into the new one temporarily. It will show up as an icon in the dash and you can click on it to mount it, copy your data across to the SSD and you're good to go.

---

### Post by Old Jimma on 2013-02-10
Hi:

I am talking about alot of data!

The new computer will be a MythTV frontend... and grab large HD TV files from the old computer, stream them across my home network, and play them on my new computer, a MythTV frontend.

Is there any problem with that?

Old Jimma

---

### Post by Paqman on 2013-02-10
Ah, right I understand you now. You want to stream video stored on your old machine to your new one?

That's no problem. As you say, you can simply mount the shares from the old machine to a mount point in the new one's filesystem. I would use NFS since they're both Linux machines. NFS is fast and pretty easy to set up, and since you're streaming across your network security isn't a big deal.

[https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto)

---

### Post by Old Jimma on 2013-02-10
Yo Paqman and Arpanaut:

thanks for your replies and your guidance!

Oldest of the Old Jimmas

---

