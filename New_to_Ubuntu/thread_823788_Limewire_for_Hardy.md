---
title: "Limewire for Hardy"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by garytaylor on 2008-06-09
Newbie is lost. I tried to install Limewire with the Synaptic Package Manager, I get the following: E: dpkg was interrupted, you must manually run
'dpkg--configure-a' to correct the problem. Haven't a clue.

---

### Post by Het Irv on 2008-06-09
open a terminal and type
```
sudo dpkg --configure -a
```

It will ask for your password, just type it in and press enter.  Don't worry if it doesn't look like you are typing, the characters won't show up.  After that finishes try to install it again.

The terminal is under Applications -> Accessories -> Terminal

---

### Post by stchman on 2008-06-09
> **garytaylor said:**
> Newbie is lost. I tried to install Limewire with the Synaptic Package Manager, I get the following: E: dpkg was interrupted, you must manually run
'dpkg--configure-a' to correct the problem. Haven't a clue.

Limewire is not in the repos.  You have to download a foreign package.

---

### Post by Hobo Joe on 2008-06-09
Use Frostwire. It's the Linux equivelant of Limewire.

---

