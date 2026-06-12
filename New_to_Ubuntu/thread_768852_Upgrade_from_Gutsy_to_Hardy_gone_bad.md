---
title: "Upgrade from Gutsy to Hardy gone bad"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Jefbuntu on 2008-04-26
I realized after doing the upgrade by internet that hardy didn't recognize my disk partitions. It created a folder called new that has bin, etc, sbin and stuff like that in it. It didn't upgrade grub because it only shows gutsy on it but seems to boot into hardy. During boot process it fails at:

setting kernel variables
error    vm.mmap_min_addr is an unknown key

everything else gets an OK.  it starts up but there's no mouse or keyboard control and it doesn't connect to the internet.

Right now I'm booting off a rescue cd  using /dev/sda4 as my root drive and everything seems to be working fine. How do I fix it so I can boot normally?

Do I need to somehow upgrade grub in MBR then copy/move the folders/files from the "new" folder to the proper partition?

Thanks for any help you can give.

---

### Post by Jefbuntu on 2008-05-28
I finally backed everything up and did a clean install from CD. Everything works fine now.

---

### Post by ZabiGG on 2008-05-28
Great ;) Happy you found your solution.

Would you mind marking your post solved so we can concentrate on helping others?

Click on the SOLVED link in my signature to learn how.

Thanks in advance,

Z.

---

