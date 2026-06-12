---
title: "How does autoremove work"
date: 2013-03-16
forum: New to Ubuntu
---

### Post by ViliX64 on 2013-03-16
Hi, I just wanted to ask, how does autoremove command work? When I type:
```
sudo apt-get autoremove wine
```
Will it search all packages containing name "wine" and uninstall them?

---

### Post by sudodus on 2013-03-16
> **ViliX64 said:**
> Hi, I just wanted to ask, how does autoremove command work? When I type:
```
sudo apt-get autoremove wine
```
Will it search all packages containing name "wine" and uninstall them?
See ```
man apt-get
``` to learn about how to perform different actions with apt-get.

```
sudo apt-get remove wine
``` will remove the program package wine. If you want to remove also configuration files, you can run
```
sudo apt-get purge wine
``` There will still remain personal files (belonging to wine or windows programs), that you have created yourself.

---

### Post by ViliX64 on 2013-03-17
I did "sudo apt-get autoremove wine" but it menu list, it still persist..
Please help me here: [http://ubuntuforums.org/showthread.php?t=2126309](http://ubuntuforums.org/showthread.php?t=2126309)

---

### Post by ibjsb4 on 2013-03-17
Number 3 & 4

[https://help.ubuntu.com/community/AptGet/Howto#Removal_commands](https://help.ubuntu.com/community/AptGet/Howto#Removal_commands)

---

