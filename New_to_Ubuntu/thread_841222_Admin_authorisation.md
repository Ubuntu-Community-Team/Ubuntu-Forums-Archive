---
title: "Admin authorisation?"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by Jamface on 2008-06-26
I am the administrator but when I try to create a shared folder on my host to test my 2 machine network I get a message which says I am not authorised to create shares, but the window does not bring up another window which would allow me to put in my administrator password.  How can establish my credentials before I start setting up the share?

---

### Post by pedro_orange on 2008-06-26
Open nautilus as su.

```
sudo nautilus
```

NB: Some ppl have reported problems with this.

---

### Post by chrisccoulson on 2008-06-26
> **pedro_orange said:**
> Open nautilus as su.

```
sudo nautilus
```

NB: Some ppl have reported problems with this.

That should be
```
[Color="Red"]gk[/Color]sudo nautilus
```
You shouldn't run graphical applications with sudo, as you can end up with some important files in your home folder becoming owned by the root user, preventing you from logging in.

---

