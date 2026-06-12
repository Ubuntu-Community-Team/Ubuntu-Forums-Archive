---
title: "[SOLVED] Firefox Addon Issue"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by Bonzzai on 2008-06-16
I opened up Firefox right after I installed a new add-on.. (Chatzilla). The problem is, I can no longer click the menu bar at top or right click my toolbar... I wanted to delete Chatzilla from wherever it's installed, but I don't know where that is...

Could anyone help me out with this? D:
Thanks bunches...

---

### Post by kpkeerthi on 2008-06-16
Look in **.mozilla** in your Home directory.

---

### Post by alienexplorers on 2008-06-16
go to ~/.mozilla/firefox/*.default  look for the extensions folder.  You might have to open them to find out which one to delete since some are loaded without names only numbers.

---

### Post by Bonzzai on 2008-06-16
Oh, I really should have mentioned before, sorry.
I did look as much as I could in the .mozilla directory, couldn't find anything that had anything similar to 'chatzilla' in its name.

I did a file search on it, and I did find a desktop configuration file (?) in /usr/share/app-install/desktop. Also an image file.

---

### Post by Bubba64 on 2008-06-16
If it is a add on it should be in tools-add ons click on it then click on remove.

---

### Post by Bonzzai on 2008-06-16
> **Bubba64 said:**
> If it is a add on it should be in tools-add ons click on it then click on remove.

Well that was one of the problems, I couldn't click on the 'Tools' button on the menu bar :P


Also, I found a file with a chatzilla file inside and deleted the foler. I restarted the computer, also, and now Firefox is working like before.

Thanks, and sorry for the waste of forum space n//n

---

### Post by alienexplorers on 2008-06-16
No question is a waste of space.  You always learn something new.

---

