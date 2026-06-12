---
title: "Ubuntu 18 - VNC two sessions not allow with the same user"
date: 2021-10-03
forum: New to Ubuntu
---

### Post by yshaer12324 on 2021-10-03
Hi All

I tried to open 2 VNC sessions on fresh Ubuntu 18 but once I success to open one session the second session with the same user is disconnect .
any body know if it's new Ubuntu security?
or maybe there is workaround?

Thanks.
Yossi.

---

### Post by ActionParsnip on 2021-10-03
What are you doing on the remote system once you get connected using VNC? There may be a sleeker solution to what you want to do.

---

### Post by bijayalaxmi1808 on 2021-10-04
VNC can be configured to run on different display ports and each can be configured to allow different users.
But logging in the same user multiple times on a single VNC session, seems to be never heard of (at least for me).

Let's say you are already logged in.
Now, if someone else want to login to the VNC session, then he/she must have a different username right?
Why do you want to share your credentials to other to login?

I am just curious what could be the use case?
Anyway, found [this article]("https://www.cpqlinux.com/how-to-configure-vncserver-to-remote-access-in-fedora-linux/") which explains how to configure VNC for Fedora but still the configurations can be used on any distro and hence Ubuntu as well.
I hope that would be helpful for you what you search!

---

### Post by yshaer12324 on 2021-10-04
Hi

Thanks for the replay!
the VNC configured with 3 session under /etc/xinted
our developer like to work with 2 session and more but once they open one session with port 5901 and need to open another session with port 5902 with the same user the second session disconnected.
if I open 3 sessions with different users is working fine.
the OS is Ubuntu 18, with Ubuntu 16 no issue at all.

Thanks.

---

