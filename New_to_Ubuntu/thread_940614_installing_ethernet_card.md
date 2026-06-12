---
title: "installing ethernet card"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by ikarthik on 2008-10-07
hi guys i am using UBUNTU 8.04LTS.i have intex silan sc92031 pci fast ethernet card in my computer.I am not able to configure this ethernet card in ubuntu 8.04lts edition.i have tried a lot but ended in vein .i am not able to access internet to upgrade my linux .

         HELP ME GUYS ! HOW TO CONFIGURE IT!

---

### Post by BugBuster on 2009-12-15
Pretty old thread I know..
However I too have the same ethernet card and was looking for a solution to it. I knew that Ubuntu Hardy had a module sc92031 for this card, but still the card would not work.

But I have managed to solve this issue by running the following command in ubuntu hardy;

$sudo update-pciids

and then reboot the computer.

So now I figure out that the module was already there in ubuntu hardy but the chipset was not recognised.

By now many people may not have this issue as the later versions of ubuntu detect the card OTB.

However for people still on Hardy might find this useful.

Thanks!!

---

