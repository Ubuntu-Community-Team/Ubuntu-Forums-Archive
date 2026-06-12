---
title: "[SOLVED] Black Highlights in Terminal"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by boof1988 on 2008-11-05
Have been trying to learn about mounting devices and such.  I installed Ubuntu using a flash-drive.  This seems to cause two extra lines to be added to /etc/fstab that prevent mounting of USB flash drives.  {Note: see [this thread](http://ubuntuforums.org/showthread.php?t=574988)}.

Here are the last two lines of /etc/fstab (I have commented them out already):
```
#/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

```

Now... there were two folders (labeled: cdrom0 & cdrom1) in /media and an additional third folder (labeled: cdrom).  This third folder is a link to cdrom0.  This leads to my question...

Since folder 'cdrom' is a link to folder 'cdrom0' I guess the black highlighting means it's a broken link?  See screen-shot below.

Can I remove the folder 'cdrom' from /media without causing problems (which I obviously don't know about yet)?

A little more information... I put a data DVD in the drive and it auto mounts.  But since I'm a noob, I don't know if there are any other hidden problems due to what I have done here.

---

### Post by talsemgeest on 2008-11-05
There should be no problems. Even if something goes wrong you should be able to make the directory again.

I say go for it! Hope this helps :)

---

### Post by boof1988 on 2008-11-06
> **talsemgeest said:**
> There should be no problems. Even if something goes wrong you should be able to make the directory again.

I say go for it! Hope this helps :)

Will give it a shot.  Thanks for the reply.

Guess I have another question now... Where do I look (what file) to find the "rules" or "settings" (where I can change them) that make the folder 'cdrom' a link to another folder.  Would like to know this since I'm trying to understand better how the system works.  Use 'chown' or chmod' maybe?  But I'd really like to know where the information is kept rather than just changing it without knowing.

So I guess I'll wait to remove the directory until I know how to change the "*link*" status.

Thanks

---

### Post by talsemgeest on 2008-11-06
Well if the link is there on startup, it will be in your /etc/fstab .

---

### Post by boof1988 on 2008-11-06
I went ahead and removed /media/cdrom.  Believe it was created when I installed using USB but I'm not sure.  I guess the black-highlighting is because the file was a broken link.

---

### Post by talsemgeest on 2008-11-06
Ok, I hope it works for you. Tell me if you have any more problems.

---

