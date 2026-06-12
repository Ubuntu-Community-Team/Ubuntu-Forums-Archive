---
title: "Permissions"
date: 2014-01-06
forum: New to Ubuntu
---

### Post by janderstonblog on 2014-01-06
I was reading some security articles and in my misguided attempt to secure my system, I've created a big problem.

I used the chmd 700 $home command but now I can't even load up my home folder or any application like Firefox. How to remedy this? Thanks
Bash is showing permission denied for terminal

When I click on home, t says could not display /home/Jaymes. This location is not a folder

---

### Post by devine.steve on 2014-01-06
sudo chmod -R 755 /home/Jaymes should fix this.

---

### Post by deadflowr on 2014-01-07
Hopefully post #2 can help.
But in retrospect, what was the full command that you tried?

---

