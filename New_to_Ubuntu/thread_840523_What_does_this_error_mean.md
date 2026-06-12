---
title: "What does this error mean?"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by melrokz on 2008-06-25
Hi! I'm Melvin form Kerala, India. I've got a Rconnect usb modem zte mg880 and have been able 2 connect successfully ! Thanks 2 a quick search in google, and some tweaking on my own. Now, I get an error message like this:

WvDial<Err>: Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
WvDial<Err>: --> PAP (Password Authentication Protocol) may be flaky.
WvDial<Err>: Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
WvDial<Err>: --> CHAP (Challenge Handshake) may be flaky.
WvDial<Notice>: Pid of pppd: 6209

what could this possibly be?

---

### Post by Het Irv on 2008-06-25
Permission Denied usually means that something needs to be run as root for it to work.  Those error messages look like something (you?) is trying to change the password files.

Please don't quote me on this, I have no experience with this kind of thing.

---

### Post by WRDN on 2008-06-25
The message appears because, you need root privileges to edit the file.
When typing the command, type 

```
sudo [command]
```

You will then be prompted for the root password.

You could also use the "su" command, and again, you will be prompted for the password.

You could also use the "gksudo" command to allow you to have root privileges when navigating in Nautilus.

---

### Post by RequinB4 on 2008-06-25
What they said :)

See my signature for an explination of sudo and root

---

