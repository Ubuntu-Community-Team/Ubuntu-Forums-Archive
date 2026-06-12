---
title: "Remove Ubuntu on 2nd HDD....?"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by lambogalardo on 2008-06-26
[FONT="Arial"]Hello, 
I am wanting to remove my Ubuntu off a 2nd HDD. I want to be able to remove the drive to later use it as external storage (its original job till i installed linux). I'm not sure of exactly what to do. I have found a site that is really helpful if you only have one HD, that both XP and Linux are on, but 2nd HDD stuff is harder to find. I'll check up often, so i should reply to questions within a few hours. Thanks in advance,
Jay[/FONT]

---

### Post by kansasnoob on 2008-06-26
It depends a lot on what your other Operating System is, but this may help:

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by lambogalardo on 2008-06-26
lol... i just was reading that site, but it caters more towards single HDD. My 2nd OS is XP. thx

---

### Post by kansasnoob on 2008-06-26
Well, since you're going to end up with XP only the fact that Ubuntu is on a second hard drive really doesn't matter.

Most importantly after removing Ubuntu you'll no longer have GRUB so you'll need to restore XP's mbr:

[http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console](http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console)

You can delete Ubuntu and format the other drive however you like with Gparted.

---

### Post by lambogalardo on 2008-06-27
that's what i have been looking at doing, but when i purchased this computer dell was a bunch of cheap asses and didn't include a restore/install disk. we do however have another one at home, but its XP SP1, does that matter, or will they both work? Thanks.

---

### Post by kansasnoob on 2008-06-27
No problem anewguy wrote a tutorial for just such a circumstance:

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

using:

[http://www.download.com/MbrFix/3000-2094_4-10485990.html?tag=lst-0-1&cdlPid=10485991](http://www.download.com/MbrFix/3000-2094_4-10485990.html?tag=lst-0-1&cdlPid=10485991)

I've used it and it works.

---

