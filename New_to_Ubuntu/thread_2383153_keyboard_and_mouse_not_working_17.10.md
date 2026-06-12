---
title: "keyboard and mouse not working 17.10"
date: 2018-01-21
forum: New to Ubuntu
---

### Post by wyledog3 on 2018-01-21
upgraded from 16.04 to 1710 now have no keyboard or mouse within ubuntu. the only place the keyboard will work is when i go into the grub on boot up. My question is can i resolve this issue using grub commands.

---

### Post by DuckHook on 2018-01-21
> **wyledog3 said:**
> upgraded from 16.04 to 1710 now have no keyboard or mouse within ubuntu…can i resolve this issue using grub commands.
Welcome to the forums, wyledog3.

Short answer: no you cannot. GRUB is very primitive. It's designed with just enough horsepower to bootstrap your real OS. Anything more would be pointless and inefficient.

You will have better luck booting into a LiveUSB then chrooting into the upgrade. The general procedure for chrooting into an install is here: [https://help.ubuntu.com/community/LiveCdRecovery#Update_Failure](https://help.ubuntu.com/community/LiveCdRecovery#Update_Failure)
Be sure to read through the whole process first. Don't just blindly implement those steps without understanding where you may have to make changes, especially which partition is actually the one used by your install.

It will still be problematic to chase such an issue down because there are so many different reasons for things going wrong. It may save you time to simply reinstall. Hope that you are backed up. If not, then now is the time to do so. Reinstall is a minor inconvenience. Loss of data can be catastrophic.

---

### Post by wyledog3 on 2018-01-21
Really appreciate the quick response very helpful info. Fortunately for me i backed up my files in 16.04 before the upgrade.I will take your advice and go the easy way and re install. :D

---

### Post by DuckHook on 2018-01-21
I don't usually like to advise reinstall. It almost seems like the problem has won. But if you can't even use your keyboard, then how can you fix anything? In circumstances like yours, reinstall is the best.

Good Luck and Happy Ubuntu-ing!

---

