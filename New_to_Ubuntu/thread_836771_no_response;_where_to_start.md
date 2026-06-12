---
title: "no response; where to start?"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by lnebrown on 2008-06-21
i have a pretty fresh install of 8.04.  When i try to "Add/Remove..."-->(pick apps)-->"apply changes", the window goes grey and nothing happens.  also, the terminal command "gksudo nautilus" doesn't do anything either.  is there a method of getting more feedback of what is happening?

---

### Post by drs305 on 2008-06-21
Some are having problems with corrupted hosts files. I believe it effects both sudo and updates. What is the output of:
```
cat /etc/hosts
```

There should be no .additionalinfo after 127.0.1.1 yourcomputername

---

### Post by lnebrown on 2008-06-22
127.0.0.1 localhost
127.0.1.1 curtis-desktop.Tux-Net

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by AndThenWhat on 2008-06-22
> **lnebrown said:**
> i have a pretty fresh install of 8.04.  When i try to "Add/Remove..."-->(pick apps)-->"apply changes", the window goes grey and nothing happens.  also, the terminal command "gksudo nautilus" doesn't do anything either.  is there a method of getting more feedback of what is happening?

yes, the way to get more feedback would be:

```
gksudo -d nautilus
```

---

### Post by cariboo on 2008-06-22
Edit your /etc/hosts file to look like this:

```
127.0.0.1 localhost
127.0.1.1 curtis-desktop
```

That should clear up your problems. To open up /etc/hosts in an editor. press Alt-F2 and enter the following:

```
gksu gedit /etc/hosts
```

Jim

---

