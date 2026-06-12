---
title: "What's the difference between gksu and sudo?"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by tactx on 2008-05-30
What's the difference between gksu and sudo?

---

### Post by kpkeerthi on 2008-05-30
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Joeb454 on 2008-05-30
That link offers a very good explanation :)

Basically (and this is a very basic explanation) - gksu(do) is for graphical applications, lets say gedit, for editing your menu.lst ```
gksudo gedit /boot/grub/menu.lst
```
And sudo is for non graphical terminal stuff, say apt-get ```
sudo apt-get install amarok
```

---

