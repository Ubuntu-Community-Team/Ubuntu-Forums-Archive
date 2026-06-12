---
title: "[SOLVED] How do I upgrade to 8.10 without burning a CD?"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by simontaylor on 2008-11-03
Dear Ub-users,

Since I installed 8.04 I've been unable to burn CDs or DVDs. I've been waiting for the 8.10 upgrade hoping that this will fix the bug I've lived with for ... a long time. 

I see from the links on the forum that 8.10 has been released. I wish to upgrade without burning a CD. I had no problem so doing with Hardy Heron --- except that to which I've already referred: no CD burns!

& +, I'm right in thinking I will not lose any of my files when I upgrade? That the settings/preferences/permissions/passwords will be carried over from 8.04 to 8.10? ?

Thanks,

Simon

---

### Post by taurus on 2008-11-03
Maybe this is what you want.

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by Sorivenul on 2008-11-03
You could:
```
gksudo update-manager
```
There should be a notification of the new 8.10 release and a question of if you wish to upgrade.  

OR

You could replace each instance of "hardy" in your /etc/apt/sources.list with "intrepid".  Then:
```
sudo apt-get update
```
```
sudo apt-get dist-upgrade
```
If you choose this route, make sure to back up your sources.list first.

---

### Post by simontaylor on 2008-11-03
Thank you. Don't know why I didn't see that before. Not enough coffee.

s.:guitar:

---

