---
title: "Unable to boot"
date: 2023-07-10
forum: New to Ubuntu
---

### Post by suziesue on 2023-07-10
I am new to ubuntu and totally clueless. Since this morning my system wont boot gets stuck on grub menu. I have followed advice from multiple articles on this forum with no success. It seems my grub files has become so messed up overnight (without me changing anything or plugging any devices in) that I now have to format and reinstall. All the articles I can find on how to do this requires me to be able to access applications which I can not as I cannot get past the grub screen. Any advice will be greatly appreciated? I think at this point my questions is how/can I create an Ubuntu bootable USB if I am not able to access my applications nor terminal...ie I can't get past Grub terminal?

---

### Post by Impavidus on 2023-07-10
Do you still have the live disk you used to install Ubuntu? That's the one you need.

---

### Post by yancek on 2023-07-11
What do you see on screen when you try to boot?  Is it a blinking cursor, the word grub>, something else?

>  I have followed advice from multiple articles on this forum 

Not a good idea which probably made the problem worse.  If you are unfamiliar with a problem but aware of this or another forum, best to post the question first.  If you have the Ubuntu usb, try to boot that.  The system doesn't make changes to itself unless you are doing an update which may have happened overnight if you have auto-update enabled.  

If you have the Ubuntu usb and can't fix this problem you might try running boot repair with the "Create Boot Info Summary" option and do not try to make any repairs.  Site at the link below.  Use the 2nd option explained at the site

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by MAFoElffen on 2023-07-14
> **suziesue said:**
> ...which I can not as I cannot get past the grub screen. 

...ie I can't get past Grub terminal?
Which would beg the question: Are you stuck at the Grub Menu? Or at the "command prompt" of Grub?

---

