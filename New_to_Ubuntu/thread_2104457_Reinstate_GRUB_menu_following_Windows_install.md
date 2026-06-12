---
title: "Reinstate GRUB menu following Windows install"
date: 2013-01-13
forum: New to Ubuntu
---

### Post by julinalex07 on 2013-01-13
Hi guys , iam in a bit of trouble with my Ubuntu, windows system..

I installed ubuntu 10.10 on my windows sytem by modifying a partition that was used earlier by ubuntu 11.04(which was not working) , so i formated that partition and installed ubuntu 10.10 , now there is no booting at all , it keeps saying "Verifiying DMI Pool Data 
No such device as '(some number)'
grub rescue>"

I tried booting from windows Xp setup and it is not booting either (the same message appears) , i really need my windows , 
i really hope any one could help me..

---

### Post by cocos1d on 2013-01-13
Burn Ubuntu LiveCD on some other computer, boot from it. At least you will be able to see what's going on with your disks, but do not experiment with boot-repair and testdisk like I did, I just screwed my ubuntu this way.

By the way XP should have a repair option in its setup.

---

### Post by coffeecat on 2013-01-13
@julinalex07, welcome to the forum.

We need to get an overview of your system before anyone can advise you how to repair it. Boot up the live Ubuntu CD on the affected computer, choose 'try Ubuntu' to get to the live desktop, ensure you are connected to the internet, and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script - the instructions are on that page - and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags to preserve formatting and for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

This should give us the information needed.

---

### Post by Pjotr123 on 2013-01-13
Don't install 10.10. It's long dead: no security updates. Using it is very dangerous.

Pick a supported version, for example 12.04 LTS. This may fix your booting problem for Windows, as well.

---

