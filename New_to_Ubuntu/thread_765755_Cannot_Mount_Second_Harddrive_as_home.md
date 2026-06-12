---
title: "Cannot Mount Second Harddrive as /home/"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by Literati on 2008-04-24
I'm trying to do exactly what I did on 7.10 to mount /home/:

root@matt:/home/matt# sudo cp -rp /home/* /media/testmount/
cp: cannot stat `/home/matt/.gvfs': Permission denied

And that's what I get. 
Does anyone have any idea why I'm getting this error. Obviously (as I've tried root), nothing is working.

---

### Post by logos34 on 2008-04-24
> **Literati said:**
> 
root@matt:/home/**matt**[COLOR="Red"]#[/COLOR] **sudo **cp -rp /home/* /media/testmount/
cp: cannot stat `/home/matt/.gvfs': Permission denied

You're using sudo when you're already root user (#).  And maybe you need to change to root dir before copying home:

# logout
$ cd /
$ sudo cp -a /home/* /media/testmount/

EDIT: just tried it and sudo doesn't seem to affect matters, so maybe you just need to run it from / directory

---

### Post by bodhi.zazen on 2008-04-24
Best follow a guide when moving home :

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by stevek123 on 2008-04-24
> **bodhi.zazen said:**
> Best follow a guide when moving home :

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

bodhi - this is a really nice guide. I'd found it and linked to it when I first installed but messed up the moving of my /home - and lost personal settings and bookmarks (including this link). I sure wish I'd had this last night before I screwed up my hald/usb configs!!! Thanks for keeping the link fresh - I believe it used to be on the beginner how-to page but I lost it during their latest forum upgrade....

---

