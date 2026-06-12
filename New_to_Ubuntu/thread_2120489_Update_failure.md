---
title: "Update failure"
date: 2013-02-26
forum: New to Ubuntu
---

### Post by ex-wirecutter on 2013-02-26
After a recent kernel update which seemed to work , I decided to delete the old one . Big mistake . Now when I try to boot I get an error signal saying no kernel installed . It seems my laptop is looking for the earlier one and can't find it so it thinks no system is installed . Is this a grub problem?
if so how do I edit it to look for the later kernel ?

---

### Post by Bashing-om on 2013-02-26
ex-wirecutter;

See if this works to get you back up.

Boot ubuntu; but, soon as the bios screen clears - depress and hold the shift key -> grub menu. I expect a number of older kernels to exist (perhaps in sub menus - depending on the version installed). Choose any -> can you boot to the desk top ?

If so, What results from terminal code:
```
sudo apt-get update
sudo apt-get upgrade
```Hopefully the latest kernel will again be pulled in.
[INDENT][INDENT]just try'n to help 

[/INDENT][/INDENT]

---

### Post by ex-wirecutter on 2013-02-27
Thanks for the reply , but perhaps I did not explain myself . By the way I'm
trying to boot Lubuntu if it makes any difference , but I don't even get as far as the desktop , just an error message saying it can't find any working Kernel. I can't understand it , when I first rebooted after the upgrade it 
worked O.K. now I just get the error message . Wish I had'nt deleted the old linux images .

---

### Post by Bashing-om on 2013-02-27
ex-wirecutter;

Did you delete ALL your kernels ??? Such that none remain ? If that is the case then the fix is beyond my experience -????

Else if there remains a kernel in lubuntu's grub menu ..see if you can boot from one of them.


[INDENT][INDENT]try'n to help

[/INDENT][/INDENT]

---

