---
title: "i want to login to my computer via ssh on my iphone"
date: 2012-01-06
forum: New to Ubuntu
---

### Post by ilikelinuxitisthebest on 2012-01-06
i tryed ssh ipaaddresshere and it just ask me for a password. i enter in my computer password but it says that its wrong. any ideas?


P.S. im using mobile terminal on my jailbroken iphone. I have openSSH installed on my iphone. but it keeps asking for a password i dont know.

---

### Post by Chronon on 2012-01-06
Specify the username or it will default to the current username on the iPhone (which is probably not the right username).

---

### Post by 2F4U on 2012-01-06
You should use

ssh username@computer_ip

with username being the username of the computer. When it asks for a password provide the password for the user on the computer.

---

### Post by ilikelinuxitisthebest on 2012-01-06
can i log in from somewhere else. i.e. when im not connected to the same network as my computer

---

### Post by carranty on 2012-01-06
> **ilikelinuxitisthebest said:**
> can i log in from somewhere else. i.e. when im not connected to the same network as my computer

Assuming your computer is behind a router, then yes but you'll need to configure your computer to have a static IP and enable port forwarding to this IP on your router.

---

