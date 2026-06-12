---
title: "Wine"
date: 2012-04-22
forum: New to Ubuntu
---

### Post by Anurg72 on 2012-04-22
I have Dual boot Ubuntu and Win7(Primary) . How to access .exe programs installed by wine in Drives other than C  like in E or F drive?

---

### Post by Paqman on 2012-04-22
If I understand you correctly you're trying to use Wine to run applications that you have installed through Windows? That's not really how Wine works. In general you'll have to install the program again in Ubuntu. Wine has a fake C: drive in your home folder, applications will be installed into that and can be run from there.

You may want to install one of the front ends for Wine, such as PlayOnLinux. It's excellent, and makes Wine work much better.

---

### Post by forrestcupp on 2012-04-22
Paqman is right. But if you happen to be talking about doing things the other way, Windows can't run software that was installed with Wine in Linux, either. You have to have everything installed twice, once in Linux with Wine, and also once in Windows.

Also, keep in mind that Wine isn't 100% compatible, so it won't run every Windows program you throw at it.

---

### Post by TheGuyWithTheFace on 2012-04-22
If you're dual booting, why not just run your windows programs in windows?

---

### Post by tmaranets on 2012-04-22
Paqman and forrestcupp are right. You will have to install the programs you have on Windows again to run them on Wine. Or since you are dualbooting, run your Windows programs on Windows and Ubuntu programs on Ubuntu.

---

### Post by forrestcupp on 2012-04-23
> **TheGuyWithTheFace said:**
> If you're dual booting, why not just run your windows programs in windows?

> **tmaranets said:**
> Or since you are dualbooting, run your Windows programs on Windows and Ubuntu programs on Ubuntu.

I can see why he would want to do it. There are lots of times when a person might need to run a program and not want to reboot his computer to do it.

---

### Post by Mark Phelps on 2012-04-23
You also need to be aware that anything you "RE"-install to use in Wine is likely to also require reactivation -- and with some products, this will "break" activation.

Also, as mentioned, you need to check the WineHQ website BEFORE you try to install anything to use with Wine. That site has compatibility ratings of different versions of Windows apps and games.  Anything not listed is liable NOT to work.  Anything rated less than Gold is going to be a waste of time to install because some features simply won't work.

You have to weight the difficulties of reinstalling to use Wine, and the loss of some functionality, against the incovenience of rebooting.

---

