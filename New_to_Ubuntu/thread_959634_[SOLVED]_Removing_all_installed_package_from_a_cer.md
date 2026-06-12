---
title: "[SOLVED] Removing all installed package from a certain repository"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by billgoldberg on 2008-10-26
I just realised I used the Ubuntu 8.04 medibuntu repo instead of the 8.10 repo.

I could just remove all the packages I installed, but I was wondering if you can remove all apps from a certain repo without hunting down the separate packages.

I prefer a cli way, but it doesn't have to be one.

*If anyone is wondering, I haven't had any problems with the packages.*

---

### Post by markharding557 on 2008-10-26
won't they be updated when you change to the 8.10 repo?

---

### Post by sancho panza on 2008-10-26
How about opening Synaptic and clicking the 'Origin' option in the bottom-left to sort by repository and then choosing the repo of interest in the list on the left column?

---

### Post by Paqman on 2008-10-26
I wouldn't sweat it too much. If there's any real difference between the two then (surely) it's that the 8.10 repo contains some updated packages. Just switch to the 8.10 repo, run the update manager and it should update you into line with that. You shouldn't need to remove anything.

---

### Post by Xiong Chiamiov on 2008-10-26
> **markharding557 said:**
> won't they be updated when you change to the 8.10 repo?
Yes, it will.  I'd recommend doing this, as otherwise you could get into some fun [dependency hell]("http://en.wikipedia.org/wiki/Dependency_hell").

---

### Post by billgoldberg on 2008-10-27
Ok.

I wasn't 100% sure it would be updated when I added the other repo.

Thanks for the tips.

---

