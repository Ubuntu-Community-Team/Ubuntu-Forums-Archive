---
title: "[SOLVED] access Wubi install of Kubuntu in Windows?"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by meindian523 on 2008-05-31
Not exactly a newbie,but I'm a newbie to the concept of Wubi installation.I installed Kubuntu 8.04(64 bit) under Windows XP Professional(32 bit)(is that the problem?:confused: )There's a Ubuntu folder under C:\ but there's no item in the start menu and no mention of it in the Program files.How do I get Kubuntu to boot up within Windows?

---

### Post by GOROSSI on 2008-05-31
Yes the 64 under 32 might be an issue just uninstall and reinstall the 32 or x86 version

---

### Post by shifty_powers on 2008-05-31
you don't. reboot and you should be given the option of going inot either winodws or kubuntu ;)

---

### Post by shifty_powers on 2008-05-31
> **GOROSSI said:**
> Yes the 64 under 32 might be an issue just uninstall and reinstall the 32 or x86 version

has nothing to do with it ;)

---

### Post by GOROSSI on 2008-05-31
Also When you install under Wubi it doesn't run under windows It create a virtual disk image which the grub boot loader can use on boot see [http://en.wikipedia.org/wiki/Wubi_%28Ubuntu%29](http://en.wikipedia.org/wiki/Wubi_%28Ubuntu%29)

---

### Post by meindian523 on 2008-05-31
I will try that and be back.

---

### Post by GOROSSI on 2008-05-31
> **shifty_powers said:**
> has nothing to do with it ;)

Yes it could if the Grub boot loader installed by wubi is compiled in x86

---

### Post by meindian523 on 2008-05-31
I also have a Ubuntu 7.04 installation,on a real partition,now that I read the Wikipedia entry,I think I need to look in the Windows boot menu since the Ubuntu 7.04 grub doesn't have an entry for Kubuntu.Thanks GOROSSI.

---

### Post by GOROSSI on 2008-05-31
Cool I thought that would solve it as when I had a look a wubi it set's up GRUB on what arcitecture your host is using i.e 32bit xp system. 
Mine would be fine had I did what you did as my Vista install is X64 so I could do Both it's just that a 32bit bootloader can't excute a x64 install

---

### Post by meindian523 on 2008-05-31
Ok,it works,but it takes a real long time to boot.Also,restart doesn't actually restart,it just shuts down and sits there.Doesn't respond to either Reset button or the CPU power button.I had to shut off the power and turn it back on to get it booting.Any ideas why this is?

---

### Post by meindian523 on 2008-05-31
Is "Restart not working" a bug or a feature?

---

### Post by meindian523 on 2008-06-02
Restart works.

---

