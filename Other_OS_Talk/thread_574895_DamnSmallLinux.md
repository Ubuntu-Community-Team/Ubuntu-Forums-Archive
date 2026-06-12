---
title: "DamnSmallLinux"
date: 2007-10-13
forum: Other OS Talk
---

### Post by Ricky2005 on 2007-10-13
I have been using DSL for a couple of months now; All of a sudden I had this urge to install talk and talkd, which I did. The daemon is still refusing the connection which is a huge problem and I wondered if anyone on here could help me please?

I also have a little other problem too; Upon boot I get this message "EXT2-fs warning: maximal mount count reached, running e2fsck is recommended." - Could someone possibly tell me this problem in simpler terms? Note: I can still start DSL, it's just an message which comes up. :lolflag: 


Thank you VERY much! =]

---

### Post by Ricky2005 on 2007-10-13
I thought this deserved another post from me.. Just to explain; if someone could tell me  how  to remove talk and talkd that'll be appericated; I used apt-get install talk and apt-get install talkd to install it.

Thanks in advance guys.

---

### Post by Ricky2005 on 2007-10-14
I've solved this problem; for the reference I used the badblocks command for example; badblocks /dev/hda2 ... badblocks /dev/hda3 .. badblocks /dev/hda1 .. That solved the 2fsck popping up (Sorry to repost just thought if people was having the same problem...) Thanks.=]

---

### Post by tgalati4 on 2007-10-14
What is the output of:

>sudo apt-get remove talkd talk

---

### Post by Ricky2005 on 2007-10-14
> **tgalati4 said:**
> What is the output of:

>sudo apt-get remove talkd talk

The following packages will be REMOVED:
  talk talkd
0 upgraded, 0 newly installed, 2 to remove and 128 not upgraded.
Need to get 0B of archives.
After unpacking 172kB disk space will be freed.
Do you want to continue? [Y/n]

---

