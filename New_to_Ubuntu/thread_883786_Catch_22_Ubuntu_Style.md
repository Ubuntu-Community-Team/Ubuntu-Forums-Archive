---
title: "Catch 22 Ubuntu Style"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by rstritmatter on 2008-08-08
Trying to open synaptic package manager produces this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When I try to run this, I get another error message:

dpkg: requested operation requires superuser privilege

I am not prompted for a password, and when I try to run su or sudo,
my password (which seems to work just fine anywhere but in the console), returns a third error message:

su: Authentication failure


As much as I am frustrated with windows, this is pretty depressing. WTF is going on?

Thanks in advance for your help!

---

### Post by dje on 2008-08-08
what happens when you run:
```
sudo dpkg --configure -a
```

dje

---

### Post by rstritmatter on 2008-08-08
well, it is solved:

sudo dpkg --configure -a

with password works. I don't know why the password does not seem to work without the rest of the command, or why I don't get prompted for a password without sudo (as I seem to recall being the norm in previous installations), but at any rate there's not need to reply.

:guitar:

---

### Post by dje on 2008-08-08
> **rstritmatter said:**
> well, it is solved:

sudo dpkg --configure -a

with password works. I don't know why the password does not seem to work without the rest of the command, or why I don't get prompted for a password without sudo (as I seem to recall being the norm in previous installations), but at any rate there's not need to reply.

:guitar:

su needs the root account to be enabled which is **not** recommended
sudo must be used before a command, not on its own
sudo -i will do much the same as su (take you to a root shell) but without a root account

dje

---

