---
title: "[SOLVED] Do I need avahi-daemon running all the time?"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by lovinglinux on 2008-09-22
The title is self-explanatory. When I run **sudo netstat -plntu** 2 instances of avahi-daemon shows up associated with ports 5353 and another one that varies. Additionally I have dhclient associated with port 68. None of this services are actually listening, as far as I can tell, but since Windows paranoia is still haunting me I would like to know if these services are necessary, if they can cause any security risk and how can I disable them if they are not necessary?

---

### Post by HermanAB on 2008-09-22
Avahi and Resolvconf are some of the first things I stop after a new install.

---

### Post by philinux on 2008-09-22
> **HermanAB said:**
> Avahi and Resolvconf are some of the first things I stop after a new install.

Could you explain why?

---

### Post by lovinglinux on 2008-09-22
> **philinux said:**
> Could you explain why?

...and how? :)

---

### Post by jARLAXL on 2008-09-23
> **lovinglinux said:**
> ...and how? :)

i found these hope they can help you out:
why:
[http://fixunix.com/networking/328831-what-avahi-daemon.html](http://fixunix.com/networking/328831-what-avahi-daemon.html)
how:
[http://www.len.ro/work/tools/ubuntu-feisty-fawn-on-a-dell-latitude-d820/disabling-avahi-daemon](http://www.len.ro/work/tools/ubuntu-feisty-fawn-on-a-dell-latitude-d820/disabling-avahi-daemon)

---

### Post by lovinglinux on 2008-09-23
Thank you. I will try that and see if I don't get any undesirable effects.

---

### Post by lovinglinux on 2008-09-23
Didn't worked. Avahi is still there.

---

### Post by seeker5528 on 2008-09-23
> **HermanAB said:**
> Avahi and Resolvconf are some of the first things I stop after a new install.

I can understand wanting to stop avahi.
Why stop resolvconf?

Later, Seeker

---

### Post by jARLAXL on 2008-09-24
> **lovinglinux said:**
> Didn't worked. Avahi is still there.

think they changed the /etc/default/avahi-daemon file
try services from system and disable avahi from there.

---

### Post by lovinglinux on 2008-09-24
> **jARLAXL said:**
> think they changed the /etc/default/avahi-daemon file
try services from system and disable avahi from there.

I tried that before and didn't worked but now works. Weird.

Thanks.

---

### Post by Todamont on 2011-12-27
ok now the question is: what is resolvconf and do I need it?

---

### Post by CharlesA on 2011-12-27
> **Todamont said:**
> ok now the question is: what is resolvconf and do I need it?
Create a new thread with your question.

This one is over 3 years old.

---

