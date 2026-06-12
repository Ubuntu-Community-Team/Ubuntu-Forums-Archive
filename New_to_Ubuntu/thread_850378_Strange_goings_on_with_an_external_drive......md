---
title: "Strange goings on with an external drive....."
date: 2008-07-05
forum: New to Ubuntu
---

### Post by Tubbytee on 2008-07-05
Hi guys,

I've just bough a FreeAgent external usb drive and when I first plugged it in (with my system running) it automounted nicely and worked great. However, I wanted to make an ext3 partition on it, which I did, but then when I plugged it into my system, it wouldn't automount! I could mount it fine with pmount though.

However, when I reboot, it mounts it fine, it just doesn't automount when I 'hot plug' it!

Any ideas? 

Also, all of a sudden, my Linux laptop is able to write to an NTFS drive with no problems (that's the reason I made the ext3 partition, the drive is meant for transfering files from my laptop to my desktop which has XP on it!), I'm glad of this, just be nice to know why it works all of a sudden!

Thanks in advance for any help!


Pierce

---

### Post by neurostu on 2008-07-05
well did you install any programs recently?  Anything like fuse?  It could be that the NTFS drivers got installed when you installed something else... (I think they might be ubuntu-restricted-extras, not sure though)...

If you want to automount the drive you need to add the drive to your fstab file.

---

### Post by Tubbytee on 2008-07-07
Ok, I can do that, but that doesn't explain why it automounts when I reboot! (At least it doesn't to a newbie like me!)

Also, as mentioned originally, when I first plugged it in, it automounted fine, then when I added and ext3 partition, all of a sudden it stopped working!

Thanks for your help so far, I know (just!) how to make it work, I'd just like to really understand what's going on.

---

### Post by Tubbytee on 2008-07-07
Ok, I tried editing my fstab file, added an entry for the external drive, and......

It still didn't work!

It's being listed in the devices as /dev/sdb1/ does that have any relevance? I mean, that's how linux lists normal drives right?

As I mentioned, it mounts fine on it's own at reboot and pmount works fine, so I can use it easily enough but I'd like to be able to just plug it in and have it automount (I'm lazy like that!)

Thanks again for the help so far.

---

