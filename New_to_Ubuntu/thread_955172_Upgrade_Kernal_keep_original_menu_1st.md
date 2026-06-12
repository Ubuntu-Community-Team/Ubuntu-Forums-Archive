---
title: "Upgrade Kernal keep original menu 1st"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by wapfu on 2008-10-21
Hi,

Given that I have updated to a new kernal 2.6.24-21 and when it asked to keep the original menu 1st - I said yes. One of the other options is to add developers list - something like that, check difference etc.
My list shows 2.6.24-19 as current.

I have the downloaded GUI for Boot Menu settings and set it to boot to windows etc.
Preceeding kernal upgrades, I have acepted the developers list and ended up with duplicates etc and the new list appended to the old and had to delete entries etc to get back something that could be used at boot.

How can i update the menu list to show the new kernal now?

Thanks and Regards
Bill

---

### Post by chuckyp on 2008-10-21
Edit the /boot/grub/menu.1st file. You can make any changes you would like in there.

---

### Post by evilkastel on 2008-10-21
Well, I'm not sure what you want, but seems like your GRUB is not showing the updated kernel, if i'm not wrong. So, here is the way I solved it. Get startup-manager from Synaptic (if that is the GUI you got, better yet) in the advanced options you set the GRUB to limit kernels to 1, and restart. it should now show the latest kernel only. If it does'n work youu might check in the main options that in the "main OS" options, your updated kernel is shown. If it isn't, well, you'll need support for a more experienced user than me, because you might aswell need to edit the grub list manually (gedit way).

---

### Post by wapfu on 2008-10-23
Cheers to all.
Thanks
Regards
Bill

---

