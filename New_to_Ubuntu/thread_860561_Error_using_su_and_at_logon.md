---
title: "Error using su and at logon"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by skirby on 2008-07-15
Hello, 
  Ubuntu 8.04 Server, I am getting this error when I use su:

user@amusgvlx04:~$ su
Password: 
Error
root@amusgvlx04:/home/user# 

I also get an error message box that says ÉRROR when I log in. Anyone have any clues or which .conf files I should start looking in?

Thanks,
  Steven

---

### Post by benfindlay on 2008-07-15
On ubuntu the root account is disabled by default. You use your normal user account and type sudo before any command that needs escalation of user rights to admin privilidges.

You can enable the root account if you want, but by default it's off for security reasons.

Hope this helps!

---

### Post by annda on 2008-07-15
more info:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

you can do
```
sudo su
```
and your user password if you need a root session, for subsequent commands without the need to enter the ubuntu-specific 'sudo' for each of them.

---

### Post by skirby on 2008-07-15
Thank you for your quick reply!  I looked in the auth.log and saw:

Jul 15 21:58:45 amusgvlx04 su[6307]: pam_lwidentity(su:account): cannot contact daemon
Jul 15 21:58:45 amusgvlx04 su[6307]: pam_lwidentity(su:account): PAM config: global:krb5_ccache_type 'FILE'
Jul 15 21:58:45 amusgvlx04 su[6307]: pam_lwidentity(su:account): cannot contact daemon
Jul 15 21:58:45 amusgvlx04 su[6307]: Successful su for root by user
Jul 15 21:58:45 amusgvlx04 su[6307]: + pts/0 user:root
Jul 15 21:58:45 amusgvlx04 su[6307]: pam_lwidentity(su:setcred): PAM config: global:krb5_ccache_type 'FILE'
Jul 15 21:58:45 amusgvlx04 su[6307]: pam_lwidentity(su:session): PAM config: global:krb5_ccache_type 'FILE'
Jul 15 21:58:45 amusgvlx04 su[6307]: pam_lwidentity(su:session): could not create home directory

I pretty new at this so I trying to find the daemon referenced.  I have recently installed Webmin so I suspect this.

---

### Post by skirby on 2008-07-17
FYI.... for those who may have the same issue.  The problem turned out to be the fact that the likewise-open daemon was not starting at system start up.  Modified the rc.d file to include the daemon.  :)

---

