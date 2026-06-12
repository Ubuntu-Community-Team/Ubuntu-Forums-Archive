---
title: "cant open ubuntu"
date: 2013-12-04
forum: New to Ubuntu
---

### Post by tomblackok1234 on 2013-12-04
hi 
i had ubuntu load in windows
which worked very well

then i did an update

now it will not load up

what i get now
is just 
words no icons etc

i login in like
this

and all i have now
is 



welcome to ubuntu 12.10 https//help.ubuntu.com/
blake@blake-thinkcentre-m57e:$




can you help
its the files that are most inportant i love to load them on to a hard drive

if ubuntu cant be saved



thank you

---

### Post by Bucky Ball on 2013-12-04
Try typing:

```
start lightdm
```

You are using Wubi, Ubuntu installed inside Windows? It has been dumped and is no longer available on newer versions. Which release are you using? I presume 13.04?

Wubi was for trying Ubuntu before doing a regular hard drive install. Not a permanent solution. Not many people use it around here so no Wubi gurus and not easy to get help with. 

Try that command I gave and see what happens. Good luck.

---

### Post by tomblackok1234 on 2013-12-04
im useing 12.10

---

### Post by Bucky Ball on 2013-12-04
That's why there was a Wubi option. I would advise a dual-boot instead, or try that command I gave you in my last post.

---

### Post by tomblackok1234 on 2013-12-04
so have i lost all the files on there then??

i dont uderstand your last message

---

### Post by tomblackok1234 on 2013-12-04
i thought it was s dual boot

---

### Post by tomblackok1234 on 2013-12-04
oh sorry im think it is a dual boot 

how can we test to see which it is????

---

### Post by tomblackok1234 on 2013-12-04
i did try that and sadly 

it did nothing help ful

but came out with what looks like nonsence

---

### Post by tomblackok1234 on 2013-12-04
thank you

---

### Post by Bucky Ball on 2013-12-05
You said you installed Ubuntu inside Windows, like a Win application, not on its own partition. That is a Wubi install. ;)

What nonsense did it come out with when you issued 'start lightdm'? Try 'start unity'.

My other message was regarding the fact that I think 12.10 had the Wubi option on it. The more recent versions don't.

---

### Post by Impavidus on 2013-12-05
Run **blkid**. It will show you the partitions present on your hard drive. If it lists ext3 or ext4 partitions and ntfs partitions, you have a regular dual boot. If there are just ntfs partitions, it's wubi.

By the way, if the last post on the thread is yours you're free to edit it instead of making a new post. It saves us some scrolling and with less posts on a thread it's more likely people will read it.

---

### Post by tomblackok1234 on 2013-12-06
Ok right it is a dual boot and not wusi

is there any thing I can do thank you

---

