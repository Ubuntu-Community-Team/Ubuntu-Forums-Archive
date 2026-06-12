---
title: "gparted/ SD card help"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by rye_ on 2008-04-27
hi,

I had bought an asus eee a while back and had intended to mount /home to an sd card on boot up, not realising that the gutsy kernel was incapable of doing this.

now when I insert the SD card my other desktop or laptop, the card is not visible  in nautilus.  I had a look with gparted and I'm told that the filesystem is kaput, and I'm unable to format it, being told the card is mounted read only. (screenshots attatched)





I'd really appreciate it if someone please advise me on this, to get a fully working sd card.

Thanks 

Ryan

---

### Post by southernman on 2008-04-27
The card may very well be shot, but riddle me this:

Look in Places > Computer and see if it shows up there as being mounted?

If it's mounted, from within ubuntu, I don't think gparted can change it. Unmount it and try again.

If it isn't mounted, chances are it's toast.

edited_ Perhaps doing:
```
sudo gparted
```
will help... dunno

---

### Post by Joshua Netterfield on 2008-04-27
On SD Cards there is a read-only switch on the side of it. Try switching it... just a guess...

---

### Post by rye_ on 2008-04-27
thanks very much
fairly embarrassing,

Ryan

---

### Post by southernman on 2008-04-27
> **rye_ said:**
> thanks very much
fairly embarrassing,

Ryan
Tell me about it. guess who's not using SD cards! :p

---

