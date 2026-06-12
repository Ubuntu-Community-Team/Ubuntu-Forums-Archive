---
title: "Problems in add/remove , synaptic GUI updates and more..."
date: 2008-06-08
forum: New to Ubuntu
---

### Post by MaximB on 2008-06-08
For a few weeks now I'm having major problems in most of the GUI aspects of Ubuntu.
First I thought it might be a kernel problem but I've updated to the latest and the problem remains.

I cannot update via GUI (update notifier) not install programs in GUI mode.
It just opens (in the best cease) doesn't asks for password and doesn't reacts.
I suspect that the problem *could* be in "gksu" package but removing it also removes vital program that without them I can risk not to be able to connect to the Internet again.

I also had before the kernel update a problem that sometimes no graphical program will open if I click on it, I suspect that it could be connected somehow.

I am using Ubuntu Heron - the most unstable distro for me so far.

---

### Post by MaximB on 2008-06-09
Help still needed.

---

### Post by cdtech on 2008-06-09
Did you try the command line:
```
gksu "update-manager -c"
```

---

### Post by cariboo on 2008-06-09
Check your /etc/hosts file and make sure it looks something like this:

```
127.0.0.1	localhost 
127.0.0.1	intrepid
```

where your hostname should be in place of intrepid. To find your hostname if you don't know it:

```
hostname
```

I had the same problem. Some how the host name got added behind localhost.

Jim

---

### Post by MaximB on 2008-06-10
Thanks a LOT.
I do remember that I've changed my hostname about a week ago.
But I never suspected that it might be a problem.

---

