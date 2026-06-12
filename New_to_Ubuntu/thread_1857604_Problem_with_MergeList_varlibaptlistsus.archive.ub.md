---
title: "Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid_un"
date: 2011-10-10
forum: New to Ubuntu
---

### Post by dntwrryboutit on 2011-10-10
Error occurred while processing libsdl-sound1.2 (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid_universe_binary-i386_Packages

Can someone help me figure out what this means and how to fix it? I am running 10.04.3 and kernel 2.6.32-34. Well thanks in advance anyway.

---

### Post by wildmanne39 on 2011-10-10
Hi, welcome to the forum! This should fix the problem. Please open a terminal by hitting ctrl+alt+t then copy and paste these commands into the terminal one at a time.
```
sudo rm /var/lib/apt/lists/* -vf
```
The first command will remove the damaged list and when you run the second command it will replace it with a new list.
```
sudo apt-get update
```
Thank you

---

