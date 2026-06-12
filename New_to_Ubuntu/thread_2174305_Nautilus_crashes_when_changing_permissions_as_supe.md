---
title: "Nautilus crashes when changing permissions as super-user"
date: 2013-09-13
forum: New to Ubuntu
---

### Post by Jonathan Precise on 2013-09-13
Hello all!

When I try to change permissions of a folder, there is a message saying:

> Error changing permissions
Sorry, could not change permissions, as _*my-real-user*_ is not a valid user. (See attachment)

Nautilus then crashes.

Note: this only happens when I run nautilus as root:

```
gksu nautilus
```

Note 2: this did not happen with the gnome 3 PPA installed. However, this PPA breaks some other programs I have.

Is there a way to work this around?

[HR][/HR]I'm using ubuntu 13.04. This did not happen with 12.04 LTS.

---

### Post by vanadium on 2013-09-14
I cannot reproduce the issue. Does it work for you with the command line? My Ubuntu version is 13.04.

---

### Post by Jonathan Precise on 2013-09-14
> **vanadium said:**
> I cannot reproduce the issue. Does it work for you with the command line? My Ubuntu version is 13.04.

It does not work, neither command-line or through the launcher:(.
Update: Installed 13.04 on another PC and same issue!

---

### Post by Jonathan Precise on 2013-09-17
Update: I actually have a bug-report on this. [LP#1225563]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1225563")

---

### Post by newb85 on 2013-09-17
Actually, if you're launching Nautilus using gksu, then for that Nautilus session, you're logged in as root.

That said, I can confirm that this happens to me as well.  I'll mark the bug as affecting me.

---

