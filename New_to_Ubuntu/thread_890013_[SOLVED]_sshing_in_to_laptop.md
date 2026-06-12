---
title: "[SOLVED] sshing in to laptop"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by moose4204l on 2008-08-14
I can ssh into my server laptop from inside my network, how do I ssh in from outside the network?

---

### Post by cgkades on 2008-08-14
you'll have to set up your home router to use port forwarding (or virtual server, depending on what your router calls it), or (very dangerous) you can put your laptop in the DMZ (also setup from the router)

if you need help with your router setup let me know, i can walk you through it. also you may want to look into dynamic dns so you dont have to remember your outside IP address.

---

### Post by moose4204l on 2008-08-18
what kind of port forwarding do i do?

edit:

i want to ssh into my server box. i already have a port open for http which allows traffic to my apache server sites. i want to be able to ssh in and control it from outside my lan

---

### Post by billgoldberg on 2008-08-18
> **moose4204l said:**
> what kind of port forwarding do i do?

edit:

i want to ssh into my server box. i already have a port open for http which allows traffic to my apache server sites. i want to be able to ssh in and control it from outside my lan

Opening up port 22 on the router I guess.

---

