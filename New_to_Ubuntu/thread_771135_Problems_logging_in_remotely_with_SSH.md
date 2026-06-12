---
title: "Problems logging in remotely with SSH"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by echomikeromeo on 2008-04-27
I installed OpenSSH on my Ubuntu machine and am now trying to login on my Mac. When I type "ssh username@computername" (replacing my actual username and computer name), I get this error message:

```
ssh: Error resolving hostname computername: No address associated with nodename
```

What am I doing wrong?

---

### Post by kai60 on 2008-04-27
Hi mate,

I presume that you are trying to log into your Ubuntu box from your Mac, however, this should work either way, replace computername with the IP address of the box that you are trying to connect to.

Let me know how you go.

---

### Post by echomikeromeo on 2008-04-27
How do I find out the IP address of my Ubuntu machine?

---

### Post by kai60 on 2008-04-27
Open up a shell and type ifconfig, that will give you the IP address on your ethernet interface.

---

### Post by echomikeromeo on 2008-04-27
Thanks! It's working now. :)

---

### Post by hyper_ch on 2008-04-27
if you're going to do this on a regular base, assign your ubuntu computer a static IP in your lan.

---

### Post by echomikeromeo on 2008-04-27
How do I do that?

---

### Post by hyper_ch on 2008-04-28
by changing from DHCP to static... enter IP, network mask, gateway...

---

### Post by jw5801 on 2008-04-28
> **hyper_ch said:**
> by changing from DHCP to static... enter IP, network mask, gateway...

Some routers also have an option to reserve an IP for a specific MAC address, which makes it a little easier if you want a static IP at home but also travel around and use networks elsewhere.

---

