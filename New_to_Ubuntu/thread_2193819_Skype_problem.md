---
title: "Skype problem"
date: 2013-12-14
forum: New to Ubuntu
---

### Post by a_nero on 2013-12-14
I installed the skype finaly after some hour trying, and now i locked the launcher to the side bar, but if I open it, he'll be blue and nothing happens, why is that ? ._. I have Ubuntu 12.04 64bit

---

### Post by oldrocker99 on 2013-12-14
Skype is owned by Microsoft; I quit using it and do all my videochatting with Google Hangouts. It requires a plugin, but the sound and video, I think, beat Skype, and I have no worries about being "scroogled." (Yet another tone-deaf ad campaign from the originators of closed-source)

---

### Post by claracc on 2013-12-15
What way have you installed skype?.

As this link points, [http://askubuntu.com/questions/284725/install-skype-on-ubuntu-12-04-lts-64-bit](http://askubuntu.com/questions/284725/install-skype-on-ubuntu-12-04-lts-64-bit) it seems there is problems with 64 bits installation. From this same link, there are various possible fixes, see the "answers" part of the link, specially answer 5 seems to work

---

### Post by asus-user on 2013-12-15
> **oldrocker99 said:**
> Skype is owned by Microsoft; I quit using it and do all my videochatting with Google Hangouts. It requires a plugin, but the sound and video, I think, beat Skype, and I have no worries about being "scroogled." (Yet another tone-deaf ad campaign from the originators of closed-source)

I suggest you re-install it again like this:
1- In Terminal:
```
sudo gedit /etc/apt/sources.list
```
and here uncomment (if commented) the lines that add software from *Canonical Partners *(two lines).

2- In Terminal:
```
sudo apt-get update
sudo apt-get install skype

```

If this didn't work, report any error messages you get here.

---

