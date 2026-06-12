---
title: "I can't install bison and flex"
date: 2011-10-12
forum: New to Ubuntu
---

### Post by shashalow on 2011-10-12
Hello,

I install Ubuntu 11.04 on Hp Compaq Intel core duo 32-bit, along side windows 7 through Wubi. but the problem is I can't install bison and flex on Ubuntu. Every time I tried, it kept saying the bison and flex files are missing.
Pls, help I am completely new to Ubuntu.:(

---

### Post by oldos2er on 2011-10-12
Have you updated your sources.list? ```
sudo apt-get update
```

---

### Post by shashalow on 2011-10-14
[IMG]http://home/compac/Desktop/Screenshot-compac@ubuntu:%20%7E.png[/IMG]
Thank you for the suggestion. Although after the UPDATE I still see this message. 

E: Encountered a section with no package:  header
E: problem with MergeList /Var?lib/apt/lists/us.archive.ubuntu.com_dists_natty_main_binary-amd64_packages

Any hope for me?

---

### Post by Rubi1200 on 2011-10-16
> **shashalow said:**
> [IMG]http://home/compac/Desktop/Screenshot-compac@ubuntu:%20%7E.png[/IMG]
Thank you for the suggestion. Although after the UPDATE I still see this message. 

E: Encountered a section with no package:  header
E: problem with MergeList /Var?lib/apt/lists/us.archive.ubuntu.com_dists_natty_main_binary-amd64_packages

Any hope for me?
Try these commands in the terminal (copy/paste for best results):
```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```
The first command removes corrupted package lists, the second refreshes them.

If this works, then try installing those packages again.

---

