---
title: "distros"
date: 2012-01-20
forum: New to Ubuntu
---

### Post by Karlof on 2012-01-20
Hi Forum 

I have two distros on my computer and I want to erase one 

and install ubuntu

Help please I know nothing about partition work

Cheers

---

### Post by cortman on 2012-01-20
In the distro you want to remove/overwrite, run

```
sudo fdisk -l
```

in a terminal to see which partition it is on. Then when you go to install Ubuntu, select "something else" and select to format and install on that partition. If you already have a swap partition you shouldn't need to worry about creating one of them.

---

### Post by Karlof on 2012-01-20
Thankyou

Karlof

---

### Post by cortman on 2012-01-20
Re-evaluating, I would rather recommend you download and run [boot info script]("http://sourceforge.net/projects/bootinfoscript/"), which is very verbose and will give you all the info you need. Instructions can be found [here]("http://bootinfoscript.sourceforge.net/").

---

