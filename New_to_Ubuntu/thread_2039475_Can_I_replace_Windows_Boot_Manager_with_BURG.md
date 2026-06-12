---
title: "Can I replace Windows Boot Manager with BURG?"
date: 2012-08-08
forum: New to Ubuntu
---

### Post by queerkhajiit on 2012-08-08
EDIT: Got help in the IRC chatroom and figured things out!

---

### Post by cariboo on 2012-08-10
Can you share the solution with the rest of us?

---

### Post by queerkhajiit on 2012-08-10
> **cariboo907 said:**
> Can you share the solution with the rest of us?

I should note that my laptop has two hard drives; I'm using one for Windows and one for Ubuntu, so my solution might not apply to your set-up. 

It turns out that I installed Ubuntu using Wubi/the Windows Installer, so I had to [migrate Wubi]("https://help.ubuntu.com/community/MigrateWubi") to a partition I created with GParted. After verifying that the migration was successful, I deleted the partition that the Wubi Ubuntu install was on. Then (on a LiveCD) I ran GParted and resized the partition to fill all the free space on the hard drive (including the space that the Wubi Ubuntu install occupied). Doing this caused failure to boot (caused I think by moving the partition to the beginning of the drive), so I ran Boot-Repair on a LiveCD and ran the recommended repair. Automagically, and by luck, it replaced the Windows Boot Loader with Grub.

Now it's just a matter of replacing Grub with BURG, which I haven't done yet! But hopefully it should just be the standard process which is well-documented online.

---

