---
title: "lightdm.log.1"
date: 2014-08-18
forum: New to Ubuntu
---

### Post by premier.renz on 2014-08-18
is it safe to delete this file? because it eats a lot of space (194Gb) on my hdd. thanks in advance

---

### Post by Elfy on 2014-08-18
good lord - you might want to check what's going on there, because if you've got recurring issues it's possible it'll just fill up again

But to answer the question -  yes it's safe to delete, it's a backup of lightdm.log, you'll need to do so with sudo or a root permed file manager

---

### Post by premier.renz on 2014-08-18
> **Elfy said:**
> good lord - you might want to check what's going on there, because if you've got recurring issues it's possible it'll just fill up again

But to answer the question -  yes it's safe to delete, it's a backup of lightdm.log, you'll need to do so with sudo or a root permed file manager


thanks for the reply Elfy. im new to ubuntu. and im having problems regarding our server. i cant log in, and the hdd is 100% used. now im planning to delete the lightdm.log.1 file so i can free up some space. 

how do i check whats going on the lightdm?

---

### Post by Elfy on 2014-08-18
>  how do i check whats going on the lightdm? read it ... probably got the same type of thing going on - check in lightdm.log to see if the same thing is still happening

Edit - I don't mean read all of it - it's likely to be reaaaaaaally long - but if you've got a recurring issue it should be easy to spot ;)

```
sudo cat /var/log/lightdm/lightdm.log | more
```

Ctrl+c to stop reading it

---

