---
title: "matlab installation problem"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by ipolitis on 2008-07-09
Hi guys,

I am trying to install Matlab r2008a from an .iso image that I have successfully mounted. However, when I try to:
*sudo sh install*
I get a message "Can't open install".
When I try:
*sh install*
then the installation begins but then I cannot write into the /usr/local/bin directory as required by the installation.

Does anyone have an idea on how to tackle this problem?
Thanks

---

### Post by ibuclaw on 2008-07-09
What are the file permission of the install script?
```
ls -l install
```
Also, try switch to root first
```
sudo -s
[INSERT YOUR PASSWORD]
./install
exit

```

Regards
Iain

---

### Post by ipolitis on 2008-07-09
Thanks for the hint.

It turns out that the problem was simpler than i thought.
I had to mound the .iso with AcetonelSO2 as sudo user.

Thanks for the quick response
Ilias

---

