---
title: "Urgent - Badly uninstalled, problems booting"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by Gonz_91 on 2008-09-06
Hi

I decided I wanted to reinstall ubuntu, in order to start over.

I'm a linux n00b, as you might see in my other posts.
And, as a n00b, I uninstalled ubuntu just the way I souldn't: formatted its partitions. And of course, GRUB tells me to go for a walk every time I try to boot Vista.

Can anyone help? I have some important stuff in there, nothing too important, but I *really* want to avoid reinstalling Vista.


Help plz :(:(

---

### Post by Gonz_91 on 2008-09-06
Oh, and when I try to reinstall it, using the live cd, the partitioner won't start. Why? Beats me




Help plz!

---

### Post by Gonz_91 on 2008-09-06
I did this:
[http://www.winvistatips.com/fix-mbr-a116.php]("http://www.winvistatips.com/fix-mbr-a116.php")

I couldn't run /fixboot, it gives back an error.

Now it says BOOTMGR is missing.

Help please

---

### Post by Tatty on 2008-09-06
EDIT : I just realised what i wrote is rubbish, so im re-writing this post

You are going down the right lines on this one, as your grub information is stored by default in your ubuntu partition, when you removed the partition you removed all of grubs info.  So you need to re-install your windows MBR.

I have never had to reintall a Vista MBR before im afraid so i cant really help too much, are you certain you are typing the command correctly?

```
Bootrec.exe /fixMBR
Bootrec.exe /fixBoot
```

---

