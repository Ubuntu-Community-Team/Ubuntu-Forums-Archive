---
title: "ufw script asking for confirmation"
date: 2013-02-20
forum: New to Ubuntu
---

### Post by bigmonmulgrew on 2013-02-20
Hi guys
I've written a script to apply some common settings on a fresh install of ubuntu server.

It includes the line 
sudo ufw enable

At this point execution pauses and askes for confirmation warning that it may disrupt ssh session.

Is there a way to force it to continue without asking so it does not require user input

---

### Post by rburkartjo on 2013-02-21
bit try this script

where xxx is your password

#!/bin/bash
echo xxx | sudo -S ufw status verbose
sleep 15

will just open in the terminal and you dont have to imput your password

---

### Post by bigmonmulgrew on 2013-02-22
Hi
Its not the password that is stopping it.

Its complaining that activating the firewall might disconnect any open ssh sessions (see attached).

---

