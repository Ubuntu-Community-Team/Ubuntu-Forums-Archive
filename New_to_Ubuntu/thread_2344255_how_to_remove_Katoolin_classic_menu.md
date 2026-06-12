---
title: "how to remove Katoolin classic menu"
date: 2016-11-23
forum: New to Ubuntu
---

### Post by hasan5599 on 2016-11-23
hi guys ..............

I installed katooling in my ubuntu 16.04 but now I want to remove kali classic menu  but not other package...............I tried and my terminal replys ........

```
hasan@Anaymous-Pc:~$ sudo su -
[sudo] password for hasan: 
root@Anaymous-Pc:~# apt-get remove classicmenu 
E: Invalid operation get
root@Anaymous-Pc:~# apt remove classicmenu 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package classicmenu
root@Anaymous-Pc:~# sudo apt-get --purge remove classicmenu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package classicmenu
root@Anaymous-Pc:~# sudo apt-get --purge remove classic menu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package classic
root@Anaymous-Pc:~# sudo apt-get remove classicmenu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package classicmenu
root@Anaymous-Pc:~#
```


How to remove CLASSIC MENU ?? THANKS

---

### Post by DuckHook on 2016-11-24
&#65279;Based on the hints and other info in your post, I am concluding:

[LIST=1]
[*]You have activated the superuser account. For security reasons, this is not recommended and is unnecessary in Ubuntu, which uses *sudo*,
[*]In any case, in choosing to install the Kali suite, you are opening yourself up to further security concerns anyway,
[*]Which also skirts with offending the provisions in the forum CoC prohibiting discussion of penetration tools that can be misused by the unscrupulous.
[*]
[/LIST]
Nonetheless, here are a few general rules when using apt:

[LIST=1]
[*]You can only use apt to uninstall a package if that was also the way you installed it. In other words, if you installed katoolin directly from a compiled source file or in any way other than apt (or its equivalents, like synaptic), then you cannot uninstall it with apt.
[*]Even if installed with *apt*, you can only uninstall a package by citing its exact and proper package name. If the package is not named "classicmenu", then you can't remove it using this name no matter how many times you try.
[*]Do not assume that any given feature is neatly encapsulated in its own package. Katoolin's "classic menu" may be part of a larger package of goodies called something else entirely. It may also use its own menuing system (having nothing to do with apt) to add/remove features.
[*]
[/LIST]
I (and most members of this forum) do not use Kali, nor Katoolin, so do not know the answers to the above. You must do your own research to answer these questions.

---

