---
title: "sudoers entry for Admin"
date: 2021-12-01
forum: New to Ubuntu
---

### Post by rich332 on 2021-12-01
Hi folks.

I have entered the following into /etc/sudoers, but it's still asking for myuser's password when **sudo** is used.  Any idea why?

```
[COLOR=#232629][FONT=-apple-system]    myuser            ALL=(ALL) NOPASSWD: ALL[/FONT][/COLOR]
```[COLOR=#232629][FONT=-apple-system]

Any insight appreciated.  Cheers[/FONT][/COLOR]

---

### Post by ActionParsnip on 2021-12-01
If you copy the root line in the file but use your username instead of root. Obviously retain the root line but make a copy.

I suggest you make a root prompt in a second terminal so that you can get yourself unstuck if you barf the file.

---

### Post by rich332 on 2021-12-01
So it's the following instead:

myuser                 ALL=(ALL:ALL) ALL

---

### Post by ActionParsnip on 2021-12-02
> **rich332 said:**
> So it's the following instead:

myuser                 ALL=(ALL:ALL) ALL

If that is what the root user has then yes. Again, before you mess with sudoers, run
```

sudo su -

```
So that you have a root prompt and can wind back the file if you break it.

---

