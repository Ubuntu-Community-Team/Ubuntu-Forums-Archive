---
title: "Applications not installing (user not root?)"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by oboesqueaks on 2008-08-01
Anytime I try to do something regarding adding or removing applications, I get this message:

Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '-o' 'Synaptic::closeZvt=true' '--parent-window-id' '39845891' '--update-at-startup' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

However, I *should* be the administrator as I am the only user.  I got this computer from someone else (traded comps) and I tried to avoid reinstalling the OS since it's an Eee PC and I have yet to buy a flash drive.  My roommate helped me change the root password, so I can login as root and I can login as my user, but neither of us could figure out why I kept getting this error.  I'm entering the right password...

If anyone knows what I should do, or if I just have to reinstall Xubuntu, please please help me.

---

### Post by northern lights on 2008-08-01
This looks like an error output from 'gksudo' rather than synaptic.

Are you in the sudoers file? (/etc/sudoers)

[https://help.ubuntu.com/community/Sudoers]("https://help.ubuntu.com/community/Sudoers")

---

### Post by oldos2er on 2008-08-01
So your friend modified Ubuntu to have a root account, as well as a user account? I'm asking because Ubuntu disables the root account on a standard install. Try entering the other password...? Please post back the result.

---

### Post by oboesqueaks on 2008-08-01
> **oldos2er said:**
> So your friend modified Ubuntu to have a root account, as well as a user account? I'm asking because Ubuntu disables the root account on a standard install. Try entering the other password...? Please post back the result.

I actually made both of them the same (bad for security but good while I'm still figuring this out.  I actually think the guy I traded computers with had modified it to have a root account.  I'm really new to this and learning as I go.

---

### Post by oldos2er on 2008-08-01
Did you check the sudoers file, as northern lights suggested?

---

### Post by unutbu on 2008-08-01
oboesqueaks, perhaps try typing
```

groups
```
It will list all the groups to which your are a member. In particular, to run sudo, you must be a member of the 'admin' group. If you do not see 'admin' in the output of groups, then 

To add yourself to the admin group:
Reboot your computer, press ESC to get to the GRUB menu, select "Recovery Mode". This will drop you to a root shell. Type

```
gpasswd -a USERNAME admin
```

where you should replace USERNAME with your real user name.

---

