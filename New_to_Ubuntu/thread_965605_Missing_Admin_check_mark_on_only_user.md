---
title: "Missing Admin check mark on only user"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by jrlorang on 2008-10-31
I am unable to download and install updates.
The administrator check box is not checked on my profile.
Is the any way to fix this?
No other admin's on this pc. :(

---

### Post by SunnyRabbiera on 2008-10-31
Did you install Ubuntu yourself or was it pre installed?
Also did you disable your administrative access by mistake?

---

### Post by drs305 on 2008-10-31
If you run "id" in terminal, you should see a listing for "admin". If you don't, you aren't listed in the 'admin' group.  If you are no longer listed in the admin group (can't use sudo, for instance) you will have to exit ubuntu to add yourself to the admin group.  

You can boot from the recovery cd, select the option for the root prompt, and run the following:
```
adduser *yourusername* admin
```
Example: adduser joe admin

or:

```
usermod -a -G admin *yourusername*
```
Example: usermod -a -G admin joe

---

### Post by jrlorang on 2008-11-04
Since my ubunto was very basic I reloaded from scratch.
I added an extra user with admin priv.
My account had Admin.
Later in the day I went back and look an my account the admin check mark was missing.. 
I used the extra account and reset my account back to admin.
I had not done any other thing that would change my account.
So far so good.

---

### Post by jrlorang on 2009-01-30
This missing admin check mark hapend twice now on a new load of 8.10.
Did install and checked the user section. Made sure admin was checked.
Added a Admin Id with all item checked. 
Rebooted machine and Admin check marks missing on both IDs.

Any Idea why this happens?

---

