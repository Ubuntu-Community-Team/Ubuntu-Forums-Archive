---
title: "[SOLVED] Windows and Ubuntu on same partition"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by junglebear on 2008-10-24
Hi all :)

Ok I have a problem, I installed Ubuntu last night and I've got Microsoft Office running on it, which was my last requirement ticked off so now I want to uninstall windows.

However, I've gone into GParted and there are 2 partitions, one which is my backup files etc. and the main one, which I have managed to install both XP and Ubuntu onto!

So I'm wondering if there is any way I can uninstall windows from the partition or will I have to format and start all over again?
I hope not!

Any help, info or directions would be much appreciated.

Cheers

---

### Post by Crandom on 2008-10-24
Did you install using WUBI or by putting in a disk and restarting your computer? If you installed by using WUBI, then I doubt your chances.

---

### Post by eragon100 on 2008-10-24
> **junglebear said:**
> Hi all :)

Ok I have a problem, I installed Ubuntu last night and I've got Microsoft Office running on it, which was my last requirement ticked off so now I want to uninstall windows.

However, I've gone into GParted and there are 2 partitions, one which is my backup files etc. and the main one, which I have managed to install both XP and Ubuntu onto!

So I'm wondering if there is any way I can uninstall windows from the partition or will I have to format and start all over again?
I hope not!

Any help, info or directions would be much appreciated.

Cheers

I am afraid you'll have to reinstall, but I am not 100% sure :(

If you wait one week hoewever, you can do a clean install with the next version of ubuntu, 8.10 intrepid ibex, which is due out on 30 october. 
Ubuntu releases two versions per year, so the next one will be in april 2009.

Also, how on earth did you manage to install both windows and ubuntu to the same partition?

---

### Post by junglebear on 2008-10-24
> **eragon100 said:**
> 
Also, how on earth did you manage to install both windows and ubuntu to the same partition?

To be honest, I have no idea. I installed using unetbootin and wasn't entirely sure what I was doing. It didn't give me the option to repartition, it did it all automatically, and I ended up with Ubuntu installed on the same partition as windows.

I thought re-install would probably be the case :(

Thanks for the help anyway guys :)

---

### Post by OldGrey on 2008-10-24
If you go for a complete reinstall do Windows first, otherwise you will have problems with Grub. Secondly, I do not know what unebootin is, but I suggest that you use the install option on a standard live CD

Sorry, not reading your original post properly, just use a live CD and during install go for the complete disc.

---

### Post by Duck2006 on 2008-10-24
> If you go for a complete reinstall do Windows first, otherwise you will have problems with Grub.

Not true, all you have to do is reinstall grub and it all up and running again.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by junglebear on 2008-10-25
Well I formatted the partition and re-installed ubuntu, now with 2 partitions and it's running a whole lot smoother. Job done. :)

---

### Post by Paqman on 2008-10-25
You don't need to reinstall.

You can use [LVPM](http://lubi.sourceforge.net/lvpm.html) to transfer Ubuntu to it's own partition. Then you can do what you like with the old Windows NTFS partition.

---

