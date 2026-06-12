---
title: "change user to auto log in"
date: 2014-01-29
forum: New to Ubuntu
---

### Post by squakie on 2014-01-29
Just put xubuntu on my sister's old laptop (had Windows XP and had some sort of viri or rootkit - ran VERY poorly).  When I went through the setup I let it default to making the account require a password at login instead of auto login.  Didn't realize I had done that.  So, went to users/groups to the specific user and changed password to not prompt for password at login.  Unfortunately that must not be what I needed to do, as it still asks for the password.  I see nothing in the users/groups menus for auto-login toggle.

Help?  Thanks

---

### Post by Lars Noodén on 2014-01-29
I have the following in /etc/lightdm/lightdm.conf

```

[SeatDefaults]
autologin-guest=false
autologin-user=lars
autologin-user-timeout=0
autologin-session=lightdm-autologin

```

---

### Post by squakie on 2014-01-29
Thanks Lars - worked like a champ!

---

