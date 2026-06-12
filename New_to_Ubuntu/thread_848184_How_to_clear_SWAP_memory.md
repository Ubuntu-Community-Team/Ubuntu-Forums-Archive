---
title: "How to clear SWAP memory"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by wariskampar on 2008-07-03
Before I fire up VirtualBox (to use XP), my SWAP partition was empty. During XP session, it was 300-400Mb while RAM was around 900Mb (out of 1GB). This is understandable since VirtualBox requires a lot of memory and I also set XP virtual memory to 512 Mb. However, after closing XP and VirtualBox subsequently, there is still some 'residue' memory in SWAP (about 200 Mb). I have to log out to clear this memory but there is still about 52 Mb in it. How do I clear SWAP after using VirtualBox without log out or restart system?

---

### Post by 4-Ever-Euphemistic on 2008-07-03
Im afraid i cant be of help to you.

But can you possibly outline how you set your windows virtual
memory to 512MB?

Thanks!

---

### Post by Elfy on 2008-07-03
Why are you trying to clear your swap? It's not necessary - it will clear itself as required.

Is it causing you a problem.

---

### Post by Elfy on 2008-07-03
> **4-Ever-Euphemistic said:**
> Im afraid i cant be of help to you.

But can you possibly outline how you set your windows virtual
memory to 512MB?

Thanks!

If you must put questions regarding window sin here do so in athread of your won in the windows forum. As it is right click your my computer - use advanced and performance tab I think and set it there.

---

### Post by chrisccoulson on 2008-07-03
If you want everything that has been swapped out to be placedback in to physical RAM, then the quickest way is to do:
```
sudo swapoff -a
sudo swapon -a
```
Turning the swap off will automatically move all swapped pages back in to physical RAM (if you've got enough of it)

---

### Post by 4-Ever-Euphemistic on 2008-07-03
> **forestpixie said:**
> If you must put questions regarding window sin here do so in athread of your won in the windows forum. As it is right click your my computer - use advanced and performance tab I think and set it there.

Fair enough.I thought it would be handy to quickly ask
rather create a whole new thread.

But point noted!

---

### Post by harirarn on 2011-06-22
I have a similar problem and don't have the root access as well.
So I guess I can't use the suggested method.
I do some memory taking simulations which fill the memory. Later the memory becomes free and still a lot of swap stays filled. When I need to analyse the simulations, I have to logout-login oterwise the system slows down.
So is there some other method to clear the swap?

---

### Post by r-senior on 2011-06-22
When you have an extremely memory hungry program it bumps everything else into swap. When the memory hungry program stops, things you want to use have to come back out of swap and into memory. So you experience some initial slowdown. It shouldn't last.

The swapoff/swapon method just forces everything back into memory in one go. It's not an instant thing. There will be lots of disk churning and a delay while things are recovered from swap.

---

### Post by ElijahLynn on 2012-03-06
> **chrisccoulson said:**
> If you want everything that has been swapped out to be placedback in to physical RAM, then the quickest way is to do:
```
sudo swapoff -a
sudo swapon -a
```
Turning the swap off will automatically move all swapped pages back in to physical RAM (if you've got enough of it)

This is Gold!

---

### Post by Elfy on 2012-03-06
Old thread closed.

---

