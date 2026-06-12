---
title: "Boot Error"
date: 2015-03-31
forum: New to Ubuntu
---

### Post by gdsuta on 2015-03-31
Hi guys. I'm really a new Ubuntu user. I use Ubuntu 14.10 on my Dell-Inspiron 4050. Yesterday I just updated my Ubuntu base. Now I couldn't start the booting. I ran into the following error:
'grub rescue, attempt to read or write outside of disk 'hd0'. I had tried Boot Repair application and got this link: [http://paste.ubuntu.com/10710839](http://paste.ubuntu.com/10710839)
Please help what should I do. I have some important files in my documents foldere. Thank you.

---

### Post by bardo2 on 2015-03-31
Hi,

after reading through most of your info (which was excellent, btw), i would say: your system looks _almost_ fine. You should be able to boot an older kernel from the grub boot menu (advanced  options -> select firrst entry (kernel 34).

I see a missing boot entry for the newest kernel. several things might have caused it, you will have to investigate...
assuming, you fixed the offending problem situation, you will have to run
```
sudo update-grub
```
but check, if the new kernel & initrd had been built successfully first!
gl

edit: a quick note, 14.10 is going to go end-of-life pretty soon, i guess

---

### Post by Impavidus on 2015-03-31
I see a long list of input/output errors on /dev/sda, which *might*  indicate a hardware problem. In any case, use the live disk to access  your file system and create backups of your important files on an  external drive. Just to be sure.> **bardo2 said:**
> edit: a quick note, 14.10 is going to go end-of-life pretty soon, i guess
14.10 has had 5 months of its total of 9 months of support. Its successor hasn't been released yet, so continue using it for a few months more.

---

### Post by bardo2 on 2015-03-31
i totally agree to the above. I hadnt seen the errors, because my reading was slower (and incomplete).

---

