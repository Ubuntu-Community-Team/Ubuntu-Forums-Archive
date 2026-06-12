---
title: "Messed up"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by dinotaz on 2008-08-07
Hi (Ubuntu hardy 8.04)

New user and i have messed up my usere`s and groups, i cannot change the settings, if i press unlock it gives me this error

**[B]Could not authenticate**[/B]

and when i try updates it gives me this error


[B]Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '56623107' '--update-at-startup' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.
[/B]

Please help

---

### Post by tamoneya on 2008-08-07
most likely you are not in the sudoers file:[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by dinotaz on 2008-08-07
luis is not in the sudoers file.  This incident will be reported.

This is the error i get when i try the link you sent me.

Thanks

---

### Post by ibuclaw on 2008-08-07
You'll have to drop down to runlevel 1 to get back sudo permissions.

Reboot your PC into Recovery Mode (option two in the GRUB menu) and select the "root shell" option.

then type in (get a pen and paper, and this is CASE sensitive):
```
usermod -a -G admin **yourname**
```
replace "yourname" with your username.
then:
```
exit
```
and select the "resume normal boot" option and you'll have sudo permissions back.

Regards
Iain

---

### Post by dinotaz on 2008-08-07
Hi

Thank you very much. All is back to normal.

Luis

---

