---
title: "[SOLVED] HDD has disappeared"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by oldtom on 2008-05-28
Hi All,
I installed Ubuntu 8.04 from within XP using Wubi and it is operating ok. Have a choice of booting into windows or ubuntu and all seems well.

But my D: drive name has been changed to DVD-Ram drive according to windows explorer and is empty. It is recognised as a 40Gig drive in all the utilities but if I copy files to it they are seen as "files waiting to be copied to the CD". I don't know how this happened. I've done something dumb. How can I get back this drive so it is seen as a normal hard drive. There does not appear to be a format option available for it so where to from here. :confused:

Any help would be welcome.
Thanks

---

### Post by sayakb on 2008-05-28
From the device manager in XP, disable your CD/DVD drive.
Now, download Partition Magic Pro, install it and run it.
There, change the Drive label for the Hard-drive as D: and apply the changes.
Then from device manager, re-enable the CD/DVD drive.

---

### Post by oldtom on 2008-05-29
Thanks for that.
Just to be clear. Is the Partition Magic Pro software you mention the Norton product for windows and is it important to DL a particular version. Is it ok to just install any demo version to perform this job then uninstall it. Norton products have given me grief in the past. Is there a way to do this in Linux say using GParted or something similar. Do know why this would have happened in the first place. I've not encountered this before.

And thanks again for your very concise instructions. :)
Cheers!


> **LinuxIsInnovation said:**
> From the device manager in XP, disable your CD/DVD drive.
Now, download Partition Magic Pro, install it and run it.
There, change the Drive label for the Hard-drive as D: and apply the changes.
Then from device manager, re-enable the CD/DVD drive.

---

### Post by oldtom on 2008-05-29
Worked a treat. Thankyou. :):):)

---

