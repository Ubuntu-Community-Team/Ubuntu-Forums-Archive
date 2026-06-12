---
title: "How to enable repositories in Ubuntu server?"
date: 2015-08-15
forum: New to Ubuntu
---

### Post by remmas-sido on 2015-08-15
Hello guys 
I'm running Ubuntu 12.04 Server in a virtual box and I am not able to install any software and I'm getting a lot of dependency issues, so I guess that the repositories are not enable by default so what's the command line way to enable all of them, and also when I update the system using sudo apt-get update I'm getting the error failed to fetch due to hash sum mismatch maybe that's why I can't install any software? 
Thank you

---

### Post by mikewhatever on 2015-08-15
Repositories are in a text file /etc/apt/sources.list, you may want to copy/paste it here for review.

---

### Post by TheFu on 2015-08-15
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)  and [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine) should help.

---

### Post by remmas-sido on 2015-08-15
> **mikewhatever said:**
> Repositories are in a text file /etc/apt/sources.list, you may want to copy/paste it here for review.
Do you know how to copy/paste from virtual environment to a physical one?

---

### Post by TheFu on 2015-08-15
> **remmas-sido said:**
> Do you know how to copy/paste from virtual environment to a physical one?

Don't treat it like it is a VM. Treat it like it is any other server anywhere in the world. Do NOT use the console - i.e. don't open the window by double-clicking on the VM inside virtualbox.

Use ssh and a terminal, then use standard X/Windows select/paste. 

If you are stuck on Windows still, use putty to ssh in and the mouse works a little differently for select/paste, but it isn't bad.

If you get ssh setup correctly, this server is available to you from ****anywhere** in the world** that you have internet connectivity and these methods for select/paste work exactly the same - from cross the room or around the globe.

---

