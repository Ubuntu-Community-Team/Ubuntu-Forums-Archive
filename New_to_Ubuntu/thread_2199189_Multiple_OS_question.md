---
title: "Multiple OS question"
date: 2014-01-12
forum: New to Ubuntu
---

### Post by h_piper on 2014-01-12
I was wondering if anyone has tried this. I currently have a dual boot Ubuntu and Win7. Could I also install Ubuntu Wubi in windows for a quick way to jump into Linux quickly and back out again, or would that mess up the permanent install of Ubuntu on my other partition, or just confuse the heck out of my computer in general?

---

### Post by Frogs Hair on 2014-01-12
Hello and Welcome

You would still have to reboot , so there is no advantage in installing with Wubi . I can't tell you if installing with Wubi would even work with a dual-boot because it uses the Windows boot loader.

---

### Post by Impavidus on 2014-01-12
Quickly jumping into Linux and back out again is possible if you install Linux in a virtual machine under Windows. That's a whole different kind of thing but certainly possible, if your hardware is up to it.

---

### Post by tgalati4 on 2014-01-12
Of course it will mess with your mind.  You will see the green pastures of the Windows desktop and wonder if the grass is greener on the other partition.

[WUBI]("https://help.ubuntu.com/community/Wubi") keeps the installation on your Windows drive or a drive that you select.  So you could create 3 partitions, one with Windows, one with your WUBI install and one with a normal Ubuntu installation.  Over time you might get confused as to how you have customized each one, since any changes in one environment will only affect that environment.

I do not know how WUBI reacts if you choose a drive/partition that already has Ubuntu installed to it.  Let us know how it works.

A better plan is to partition your machine correctly, use WUBI until you get bored or lose your mind, then [migrate]("https://help.ubuntu.com/community/MigrateWubi") your WUBI install to a normal Ubuntu installation and regain your sanity.

---

