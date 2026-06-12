---
title: "Strange User Account Error"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by Landara on 2008-10-09
When I relog, after I enter my password, I get this error popping up which I have to click ok on in order to continue into the GUI.

> Users $HOME/.dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions. Users $HOME directory must be owned by user and not writable by others.

I don't understand this, I had it working fine, and was attempting to set up Samba by following this guide step by step.

> [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

This not only didn't make my Vista PC and Linux PC able to see one another, it apparently fubared something.  And before you guys ask, yes, I am certain I did everything this guy said, with no typos(I copy/pasted).

---

### Post by cmnorton on 2008-10-09
You must have changed protections on your directory. I get that for any graphical logins whose home directories need to be set to group w.

Edit:
-------
Why this error occurs is another matter. 

Here is one possible workaround:

[http://ubuntuforums.org/showthread.php?t=371052](http://ubuntuforums.org/showthread.php?t=371052)

---

### Post by Landara on 2008-10-09
Thanks got it! :)

---

### Post by directcharitycontribution on 2008-10-14
> **Landara said:**
> When I relog, after I enter my password, I get this error popping up which I have to click ok on in order to continue into the GUI.


I don't understand this, I had it working fine, and was attempting to set up Samba by following this guide step by step.



This not only didn't make my Vista PC and Linux PC able to see one another, it apparently fubared something.  And before you guys ask, yes, I am certain I did everything this guy said, with no typos(I copy/pasted).

[http://ubuntuforums.org/search.php?searchid=49602307](http://ubuntuforums.org/search.php?searchid=49602307)

---

