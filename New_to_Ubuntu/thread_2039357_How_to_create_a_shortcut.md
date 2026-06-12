---
title: "How to create a shortcut ?"
date: 2012-08-08
forum: New to Ubuntu
---

### Post by paichkash on 2012-08-08
hi
i have a 2 harddisks... both ide.. 
one has ubunut.. other has windows and 3 partitions.. my third partition has some data i want to create a shortcut to that folder on my desktop.. 
when i right click on that folder the  make link is greyed out..

the folder to which i want to create a shortcut is located at

```
/media/WIN_/torrents/my data/ 
```

i want a short cut on desktop that when double clicked opens my data folder..

i tried the ln command like 

```
ln -s /media/WIN_/torrents/my\ data/  ~/Desktop
```

and the shortcut is placed on desktop but when i click it i get.
The Link "vtc redhat" is Broken. Move it to Trash?

---

### Post by papibe on 2012-08-08
Hi paichkash.

My guess is that your data directory is in a disk that hasn't been mounted. I would recommend either using autofs to mount it at request, or mount it permanently on fstab.

I hope that helps. Tell us if you need more help with that.
Regards.

---

### Post by paichkash on 2012-08-08
i am new to ubuntu and learning it... 

it is mounted i can see the icon for that partition on my desktop and navigate to that folder using the explorer (?) and  also open the files there by double clicking it..

thanks for such an incredibly quick reply.

---

### Post by drmrgd on 2012-08-08
I might be off here, but I think the target syntax isn't quite correct.  To me what you ran looks like the target name is 'Desktop', and not 'my data' like I think you intended.  Try this (assuming you want to call the link 'my data'):

```
ln -s /media/WIN_/torrents/my\ data/ ~/Desktop/my\ data
```

---

### Post by paichkash on 2012-08-08
> **drmrgd said:**
> I might be off here, but I think the target syntax isn't quite correct.  To me what you ran looks like the target name is 'Desktop', and not 'my data' like I think you intended.  Try this (assuming you want to call the link 'my data'):

```
ln -s /media/WIN_/torrents/my\ data/ ~/Desktop/my\ data
```

thanks that did the job as i wanted.:guitar:

---

