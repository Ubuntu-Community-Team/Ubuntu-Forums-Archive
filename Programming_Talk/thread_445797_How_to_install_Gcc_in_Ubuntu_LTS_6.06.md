---
title: "How to install Gcc in Ubuntu LTS 6.06"
date: 2007-05-16
forum: Programming Talk
---

### Post by Gefox4 on 2007-05-16
I'm using Ubuntu LTS 6.06. Now, I installed Kdevelop package, but I can't compiler any program by C language. When I type:
```
gcc -o name name
```
It say: 
```
bash: gcc command not found
```
And when I type:
```
man gcc
```
it say like that, too.
So how can I do with this, please show me the way to exit this mistake soon because I very need that for my study.

---

### Post by kaamos on 2007-05-16
Install the package "build-essential"

---

### Post by taurus on 2007-05-16
```
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

