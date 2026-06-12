---
title: "salvaging ext HD from lightning storm"
date: 2012-07-02
forum: New to Ubuntu
---

### Post by swatPellegrino on 2012-07-02
my Mac mini crashed after a lightning storm and no longer boots up. luckily everything was backed up on an external drive. unfortunately the drive was set up as a time machine backup.

long story short I wish to still use the drive without formatting it but cannot figure out how to get write access. my unix is very rusty but I can get into the /media directory in terminal but can't get to the drive it's self to view files or change permissions. I can read the contents of the drive just fine.

please help!!

---

### Post by swatPellegrino on 2012-07-02
do I need to post more info so people can help? is my question too vague?

---

### Post by swatPellegrino on 2012-07-02
I got it to work by forcing the HD to disable journaling using the diskutil command on a friends MBP in the terminal. then I installed hfsplus and hfsprogs back in ubuntu and was then able to access the HD using terminal where as before I couldn't. I also renamed the volume to not have spaces in the name; not sure if that had anything to do with the fix. anyways, in terminal I did a chmod to the whole volume and was then able to copy files over.

I hope the above non-sense can help someone else.

EDIT:  links included
[http://castyour.net/disable-hfs-journaling-leopard-use-disks-readwrite-linux](http://castyour.net/disable-hfs-journaling-leopard-use-disks-readwrite-linux)

---

### Post by swatPellegrino on 2012-07-03
Ok I still need help. After restarting the problem came back and now I am now not able to copy files from my HD to the external HD.

I feel like the solution is simple and I'm just overwhelmed thinking of what the answer could be.

please help!

---

