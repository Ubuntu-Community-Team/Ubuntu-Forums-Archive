---
title: "Ubuntu 18.04 Stopped Asking for Login Password"
date: 2019-11-27
forum: New to Ubuntu
---

### Post by michael-bielesky on 2019-11-27
Hi,

I had always the lock screen on, but now no password is needed to enter my computer when freshly started. It will lock the screen if unattended or when coming back from hibernation. However, I can just hit the power button, reboot the computer and I will not be asked for the password. Any thoughts on what's going on?

Mike

---

### Post by uRock on 2019-11-27
When you search **"Users"** then open the app, is **Automatic Login** enabled? I know this won't answer "why" it was changed.

---

### Post by michael-bielesky on 2019-11-28
> **uRock said:**
> When you search **"Users"** then open the app, is **Automatic Login** enabled? I know this won't answer "why" it was changed.

Yes, the **Automatic Login **was indeed enabled. The thing is that I don't recall changing it. The change requires my password so there is no way I did it by accident. Should I be concern about this? Have others reported something similar in the past?

Mike

---

### Post by uRock on 2019-11-28
Hi Mike,

I just made that change to one of my users and it is listed in auth.log which can be found in /var/log/. It looks like this;
```
Nov 28 08:05:28 OxfordComma polkitd(authority=local): Operator of unix-session:c2 successfully authenticated as unix-user:urock to gain TEMPORARY authorization for action org.freedesktop.systemtoolsbackends.set for system-bus-name::1.128 [users-admin] (owned by unix-user:urock)
Nov 28 08:05:36 OxfordComma chpasswd[5391]: pam_unix(chpasswd:chauthtok): new password not acceptable
Nov 28 08:05:36 OxfordComma gpasswd[5393]: user urock2 added by root to group nopasswdlogin
```

I am looking to see if any other logs give more information. This shows which user was authenticated to make the change.

---

### Post by michael-bielesky on 2019-12-02
Thanks uRock, but unfortunately the log history seems to be only limited to 4 days which after the change happened.

Mike

---

