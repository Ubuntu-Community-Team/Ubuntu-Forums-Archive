---
title: "= does not work in boot menu"
date: 2014-07-28
forum: New to Ubuntu
---

### Post by abberik on 2014-07-28
So i somehow accidentally changed my password, and found a couple of tutorials online how to reset passwprd. I followed a tutorial ([http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/](http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/)) and i did not see any  "recovery mode" option so i  pressed "e" to put in the line as the tutorial said, i started to edit, but realised that i cannot type in  "=". Is there any way to "copy paste" in the bootmenu?

And if its relevant i use swedish keyboard layout

---

### Post by coldcritter64 on 2014-07-28
What version of Ubuntu are you using ? That tutorial you are following is way out of date. Note the OS version in the grub list shows 8.04 (Hardy Heron from April 2008). Newer versions of Ubuntu run grub-2, that tutorial is showing grub-legacy ("Grub stage 1.5" no longer exists in newer versions, for instance).

You will need to find a more up to date tutorial to follow. Let us know what version you are running and someone here should be able to provide you a link and / or more appropriate information to help you. Techniques required can change over such a long period (6 years in this case).

Edit: here is a newer link (dated about 2012) [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
 The link info is similar but this one notes newer versions may need to have the root drive remounted read/write to make any changes. That old link would not have accounted for such a situation.

---

### Post by abberik on 2014-07-28
Thank you, i am currently using 1.4.04 LTS. Also the reason why i didnt use that tutorial is becouse of that when i came to the bootmenu there was no alternative to recoveryboot. therefore i tried the other older version. after 45 minutes of guessing the password i have now solved the problem anyways. :P Thx bro

---

### Post by coldcritter64 on 2014-07-28
> ...is becouse of that when i came to the bootmenu there was no alternative to recoveryboot...

If you are ever missing the recovery options you actually can use a normal boot option, press "e" to edit the entry (like you tried in your 1st post originally), remove the "quiet" and "splash" from the boot line and replace those with the word "single". That is the only difference between a normal boot and a recovery boot.

You were asking about using the "=" sign in the boot menu only from what is in the contents of that out of date tutorial it appears now. Good to hear you managed to get it working :)

Please mark your thread as "Solved" if all is OK. There is a guide on how to do so linked in my signature line if needed. Cheers.

---

### Post by grahammechanical on 2014-07-28
There is a recovery mode with Ubuntu 14.04. We find it by opening the Advanced Options For Ubuntu sub-menu at the Grub menu. One of the big improvements of Grub 2.0 over the previous version is the use of sub-menus to make a neater menu.

Regards

---

### Post by coldcritter64 on 2014-07-28
> **grahammechanical said:**
> There is a recovery mode with Ubuntu 14.04. We find it by opening the Advanced Options For Ubuntu sub-menu at the Grub menu. One of the big improvements of Grub 2.0 over the previous version is the use of sub-menus to make a neater menu.

Regards

Thanks grahammechanical, I wasn't actually aware of a sub menu with 14.04, my last Ubuntu install 12.04 still included the recovery in the main menu. Only sub menu I was aware of is the "older versions" one in 12.04. This sounds a much neater idea for the menus, will have to do an install soon to see it ;).

@ OP, this info will save you editing the boot entry altogether.

---

