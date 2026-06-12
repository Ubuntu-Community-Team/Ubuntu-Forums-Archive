---
title: "after xp install, ubuntu gone"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by Padrhino on 2008-10-08
I was using xp first. But for a project i need linux environment and i installed ubuntu 8.04. After that my xp is gone. It was saying 'hal.dll missing' and xp wasn't started. So i formatted my pc and re-installed xp. After that ubuntu is gone now. I don't see it os selection or anywhere.
Do i need to install ubuntu again? If so, how can i prevent getting hal.dll error on xp? Is there a good solution for this?

---

### Post by billgoldberg on 2008-10-08
> **Padrhino said:**
> I was using xp first. But for a project i need linux environment and i installed ubuntu 8.04. After that my xp is gone. It was saying 'hal.dll missing' and xp wasn't started. So i formatted my pc and re-installed xp. After that ubuntu is gone now. I don't see it os selection or anywhere.
Do i need to install ubuntu again? If so, how can i prevent getting hal.dll error on xp? Is there a good solution for this?

No.

XP just overwrote the grub and replaced it with it's mbr.

You can reinstall the grub using the "[super grub disk]("http://www.supergrubdisk.org/")" live cd.

After installing it you will have the option to boot ubuntu or windows at boot up.

---

### Post by handydan918 on 2008-10-08
> **Padrhino said:**
> I was using xp first. But for a project i need linux environment and i installed ubuntu 8.04. After that my xp is gone. It was saying 'hal.dll missing' and xp wasn't started.Well, if xp was gone, you wouldn't be getting an error message that mentioned a .dll file. >  So i formatted my pc and re-installed xp. After that ubuntu is gone now. I don't see it os selection or anywhere.
Do i need to install ubuntu again?Yes. Just make sure you read one of the how-to's in regard to setting up a dual-boot system BEFORE you start.>  If so, how can i prevent getting hal.dll error on xp? Is there a good solution for this?I am unaware of this error being caused by installing Ubu, or any other Linux variant, so can't comment on how to avoid it, other than to not use Windows.:)

---

### Post by Padrhino on 2008-10-09
I use xp, i love xp in fact :) but i need ubuntu sometimes because of some restrictions. I see on the internet some people experienced same problem after ubuntu installation. the hal.dll missing problem. May be because i'm not an experienced user, so i get that error. Thanks for replies, i solved the problem.

---

### Post by handydan918 on 2008-10-09
> **Padrhino said:**
> I use xp, i love xp in fact :) but i need ubuntu sometimes because of some restrictions. I see on the internet some people experienced same problem after ubuntu installation. the hal.dll missing problem. May be because i'm not an experienced user, so i get that error. Thanks for replies, i solved the problem.

Great! Perhaps you could share your solution so that others who follow this thread don't mutter about you....

---

### Post by Padrhino on 2008-10-10
> **handydan918 said:**
> Great! Perhaps you could share your solution so that others who follow this thread don't mutter about you....

yea you are right. i solved the problem using "super grub disk". It worked for me.

---

