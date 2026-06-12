---
title: "Terminal and superuser"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by djlobina on 2008-05-10
Hello everyone,

I am an absolute beginner at using Ubuntu, but after installing it on my machine, I'm willing to learn as much as I can.
I do, however, have a problem. I was running my first update when my internet connection crashed and the installation process didn't complete. Since then, I get an error message every time I try to run the Package Manager which says:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I don't know how to do either, but I assumed that the first problem should be resolved via the Terminal. I accessed it and typed in 'dpkg --configure -a' but it said I needed 'superuser' privilege to do that. Unfortunately, I have not v been able to work around that problem, even after reading the Help Manual.

Any help will be much appreciated. I hate the fact I've run into such problems right after installing Ubuntu!

Many thanks.

---

### Post by mkoehler on 2008-05-10
Hey,

   To gain superuser privileges, precede the command with "sudo".  In your case, the command you would want to run is ```
sudo dpkg --configure -a
```

---

### Post by Austin_KW on 2008-05-10
You need to run the command with sudo
sudo dpkg --configure -a

and enter your password when prompted

---

