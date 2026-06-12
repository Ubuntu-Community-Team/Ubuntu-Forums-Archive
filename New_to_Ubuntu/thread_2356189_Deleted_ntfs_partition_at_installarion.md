---
title: "Deleted ntfs partition at installarion"
date: 2017-03-20
forum: New to Ubuntu
---

### Post by dokika2 on 2017-03-20
Hi
I had two ntfs partition. On the first I wanted install Ubuntu.
Now I can boot the computer from an external HD and what I see 
is a "New Volume". 
Please let me know how to recover the ntfs partition?
Thanks a lot,
doki_2

---

### Post by yancek on 2017-03-20
> I had two ntfs partition. On the first I wanted install Ubuntu.

Installing any Linux on an ntfs filesystem won't work.  You need to format with a Linux filesystem.
Diid you have a working installation of some windows on the computer?  If so, which windows version?
Is if using UEFI/GPT or is it using the older MBR?
When you boot from the external drive, what are you selecting to boot?  Ubuntu? Windows? 
The information you posted is too limited for anyone to do any more than guess so I would suggest you boot the Ubuntu DVD or flash drive and go to the site below and download and run the boot repair as explained at the site.  Select the option to Create BootInfo Summary rather than trying to make repairs.  That will provide helpful details about your problem.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Bucky Ball on 2017-03-21
Welcome. To recover the NTFS partition you could try using Testdisk, but as above, from the information you've given, not much to go on for us to help. You would need to be a bit more specific. You mention installing, then external drives. We have no idea what you're doing, what you've done or what you're installing where. :)

But your main question here is how to retrieve that partition as sounds like you don't want to lose what was on it. You are positive you have wiped the partition during install and that is on the external drive? Anyhow, more detail, please.

---

