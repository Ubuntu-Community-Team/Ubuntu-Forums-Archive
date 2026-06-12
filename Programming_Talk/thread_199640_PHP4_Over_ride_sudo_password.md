---
title: "PHP4: Over ride sudo password"
date: 2006-06-19
forum: Programming Talk
---

### Post by fopetesl on 2006-06-19
I have this script:
```

<?php
`sudo halt`;
?>
```
It fails when I test it from browser and I note that apache2 error log has the line:
[COLOR="Red"]Password:[/COLOR]
in it.
I have edited /etc/sudoers to read:```
root ALL=(ALL) ALL
user_me ALL=(ALL) NOPASSWD:ALL
apache ALL=(ALL) NOPASSWD:ALL
php4 ALL=(ALL) NOPASSWD:ALL
%www-data ALL=(ALL) NOPASSWD:ALL
%admin ALL=(ALL) NOPASSWD:ALL
```Whatever, I still get password request. 

How do I bypass the password prompt from a php script?

---

### Post by fopetesl on 2006-06-19
It seems that the order in which sudo authentications are placed into the sudoers file is significant.
Note my first attempt failed but this one succeeds:
```
# User privilege specification
root ALL=(ALL) ALL
user_me ALL=(ALL) NOPASSWD:ALL
apache2 ALL=(ALL) NOPASSWD:ALL # seems not to be significant?
php4 ALL=(ALL) NOPASSWD:ALL # -------- " --------------- 

# Members of the admin group may gain root privileges
%admin ALL=(ALL) NOPASSWD:ALL
%www-data ALL=(ALL) NOPASSWD:ALL # [COLOR="Red"]IS[/COLOR] significant
```

which is not particularly secure so I need to tidy that up.

---

### Post by SMFS_Usagi on 2010-03-02
I did this and finally got sudo to work on my system.  However I am concerned about the security issue.

Could someone please address the "clean-up" and security problem mentioned in this post.

Thanks

---

### Post by Barrucadu on 2010-03-02
`sudo` allows pretty fine-grained control (down to exact arguments you can use with a command), so on my server I have several rules for the http user allowing specific commands to be used without a password.

---

### Post by lavinog on 2010-03-03
You could create a command file with write permissions for the webserver.
and use a daemon running with admin privleges to check that file for specific commands.

The daemon could have a list of approved commands, and custom responses. (You can add extra logging prior to actually halting.)

---

