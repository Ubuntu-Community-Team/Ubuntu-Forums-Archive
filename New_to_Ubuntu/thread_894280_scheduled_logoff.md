---
title: "scheduled logoff"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by susiriss on 2008-08-19
Hi all,
            I want to log-off my Gnome session automatically at a specific time. So I used the "crontab -e" and typed the following.

```
25 * * * * gnome-session-save --kill --silent
```

in the crontab file, but nothing happened at the specified time. How can I achieve this task? What is wrong with this approach?

Thanks!

-susiriss

---

### Post by fahadsadah on 2008-08-19
Are you sure your time section is correct?
25 * * * * means 25 past every hour

---

### Post by susiriss on 2008-08-19
Time section is not that meaningful. But I put that just for testing.

---

### Post by JillSwift on 2008-08-19
Cron jobs start in their own session, so the command isn't being applied to your login.

There is probably a way to go about what you want to do, sadly I don't know enough to help with that.

---

### Post by Loaded.len on 2008-08-19
pam_time?

something like 

login ; * ; !root ; A10800-2000

That way you would only be allowed to login between 8am and 8pm unless you were root.

---

### Post by fahadsadah on 2008-08-19
Thank you JillSwift, I did not know that.

An alternative cron job, to log out all users:
25 * * * * /etc/init.d/gdm stop

Put this in roots crontab - ```
sudo crontab -e
```

---

### Post by susiriss on 2008-08-19
I want to do this without root privilege.

Thanks !

---

### Post by susiriss on 2008-08-19
I cannot edit the /etc/security/time.conf without root access. Aren't there any other ways ??

Thanks

---

