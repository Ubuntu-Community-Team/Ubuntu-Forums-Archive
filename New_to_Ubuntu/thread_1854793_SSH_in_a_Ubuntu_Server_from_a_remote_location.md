---
title: "SSH in a Ubuntu Server from a remote location"
date: 2011-10-05
forum: New to Ubuntu
---

### Post by hawkins524 on 2011-10-05
hey all

ive been playing with linux for a year or so now, mainly Fedora though.

i have recently installed a SSH web server using Ubuntu Server 10.4LTS to use it as a web server. everything is working perfectly while im on my home network, however i cannot figure out how to set it up so that i can SSH into the server, either with Putty or WinSPC, from a remote location.

any help would rock thanks

hawkins

---

### Post by 4llf0rn0t on 2011-10-05
Have you enabled port forwarding in your router?

---

### Post by y2pk001 on 2011-10-05
Port forward port 22 on your router to you SSH server

---

### Post by hawkins524 on 2011-10-05
how would i do this ?

---

### Post by lisati on 2011-10-05
> **hawkins524 said:**
> how would i do this ?

It depends on your router, many have a browser-based control panel.

---

### Post by hawkins524 on 2011-10-05
i have been looking through the browser-based control panel and there is no mention of port forwarding or mapping. i have a vodafone home gateway router

---

### Post by 4llf0rn0t on 2011-10-05
Does it have Advanced or NAT Setting? or Virtual Server?

---

### Post by lisati on 2011-10-05
> **hawkins524 said:**
> i have been looking through the browser-based control panel and there is no mention of port forwarding or mapping. i have a vodafone home gateway router

On my router (a "freebie" from another provider) it's called "Game and application sharing"

---

### Post by hawkins524 on 2011-10-05
> **4llf0rn0t said:**
> Does it have Advanced or NAT Setting? or Virtual Server?

i just found the NAT settings

---

