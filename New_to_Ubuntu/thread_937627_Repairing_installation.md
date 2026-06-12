---
title: "Repairing installation"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by Konstabel on 2008-10-04
I think I might have deleted some packages by mistake that is essential to the working of Ubuntu. Is there a way that I can repair the installation (in console mode)?

---

### Post by Lord DarkPat on 2008-10-04
I suggest that you back up and reinstall. It usually avoids many troubles. I use a separate /home partition, which doesn't get affected when I reinstall ;)

---

### Post by iponeverything on 2008-10-04
> **Konstabel said:**
> I think I might have deleted some packages by mistake that is essential to the working of Ubuntu. Is there a way that I can repair the installation (in console mode)?

What is the problem you having now? Is X not starting? what happens
when you type:

startx

---

### Post by Konstabel on 2008-10-04
When I run startx I get:
[I]
Fatal server error
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

Invalid MIT-MAGIC-COOKIE-1 keygiving up.
xinit: Interrupted system call (errno 4): unable to connect to X server
xinit: No such process (errno 3): Server error.[/I]

The problem I am having is, that I cannot get a ftp or vnc server running at all.

---

### Post by iponeverything on 2008-10-04
The problem I am having is, that I cannot get a ftp or vnc server running at all.

---------

apt-get install vnc4server Pure-FTPd

neither of these are "essential" BTW

---

