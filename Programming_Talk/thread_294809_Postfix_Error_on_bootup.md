---
title: "Postfix Error on bootup"
date: 2006-11-07
forum: Programming Talk
---

### Post by indytim on 2006-11-07
I'm in the process of rebuilding my Dapper Gnome installation (a really long story).  In the LAMP installation (php4, mysql5, apache2), while installing mysql I (mistakenly) specified the Internet option for mail.  My environment will be a localhost not open to the outside.  Need to run smtp for normal mail.

I'm encountering a boot error on postfix and cannot send outgoing mail.

Attached snippet from the /etc/postfix/main.cf :


```
mydestination = ubuntu-pc@smtp-server.<my smtp address here>, ubuntu-pc, localhost.localdomain, localhost
```

I believe that I need to specify localhost for the mail environment when installing mysql?? 

Would appreciate feedback on resolving the postfix problem and regaining my outgoing mail smtp.  I have stopped Apache2 and uninstalled MySQL (for the moment).

Thanks,

IndyTim

---

### Post by mitch.c on 2006-11-07
> **indytim said:**
> I'm encountering a boot error on postfix and cannot send outgoing mail.

Attached snippet from the /etc/postfix/main.cf :


```
mydestination = ubuntu-pc@smtp-server.<my smtp address here>, ubuntu-pc, localhost.localdomain, localhost
```

I believe that I need to specify localhost for the mail environment when installing mysql?? 

Would appreciate feedback on resolving the postfix problem and regaining my outgoing mail smtp.

Knowing the error you receive at boot might be helpful, as would some output from /var/log/mail.* logs...

mydestination tells what mail should be handled locally, so in most cases, the default if fine:
```
mydestination = $myhostname, localhost.$mydomain, localhost
```
Post some of the details mentioned above, and let's see if we can figure this out.

---

