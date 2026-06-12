---
title: "keyboard keys not working not mapping?"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by Im Sofa King on 2008-08-25
I have searched for a similar issue but don't seem to find one.  I put ubuntu on an old HP Pavilion and it has worked fine, until about a week ago when a couple of the keys just quit working the "T" and "Y".  I have seen multiple posts about a num lock issue but it is not that also doesn't to my knowledge seem to be a different keyboard mapping issue, but I am not completely sure about that.

Another problem is that I can't log into my account since my password has a "t" in it.  I am unsure how to proceed.  Any help would be greatly appreciated.

Thanks

Sofa

---

### Post by Im Sofa King on 2008-08-27
bump

---

### Post by prshah on 2008-08-27
> **Im Sofa King said:**
>  I put ubuntu on an old HP Pavilion and it has worked fine, until about a week ago when a couple of the keys just quit working the "T" and "Y".  

When booting up, press ESC to load the GRUB menu. When the menu shows up, press "c" for a command line. Check if "T" and "Y" are working here. 

I suspect they won't which means that it is a hardware issue (broken keyboard). The GRUB bootloader is the very first thing, and does not use Ubuntu's keyboard mapping settings.

If it works in the GRUB command line, then your suspicion about it being a keyboard-mapping related issue may be right; post back in that case.

---

