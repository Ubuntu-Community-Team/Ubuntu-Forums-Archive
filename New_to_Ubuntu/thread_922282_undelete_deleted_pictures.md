---
title: "undelete deleted pictures"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by CarvalhoPepe on 2008-09-17
How to undelete accidentally deleted pictures on a memory card?

---

### Post by t0p on 2008-09-17
Is the memory card still in your computer, or have you removed it?  If it's still mounted, the files could still be in the .trash folder.  If the card's been unmounted/removed... I don't know.

---

### Post by jemate18 on 2008-09-17
> **CarvalhoPepe said:**
> How to undelete accidentally deleted pictures on a memory card?

1. mount the memory card
2. open the memory card using nautilus
3. click view
4. click show hidden files

If you see .trash click on it and select the pictures you have undeleted and then restore them..

If there is no .trash, sorry, I dont know of a way of retrieving it.

---

### Post by MegaJim on 2008-09-17
I think trash is automatically emptied when a volume is unmounted

---

### Post by lukjad on 2008-09-17
Not in my experience. The above posters are correct. Most of the times it is as simple as showing the hidden files and dragging it out of the .trash folder.

---

### Post by billgoldberg on 2008-09-17
> **MegaJim said:**
> I think trash is automatically emptied when a volume is unmounted

That's not the case.

Sometimes you get a prompt asking you to do it, but it doesn't happen automatically.

--

If the trash is emptied, I have no idea how to do it.

You might try some software for it, depending on the filesystem. 

Google "FS data recovery". Most likely it will be fat32, so use "Fat32 data recovery".

---

### Post by CarvalhoPepe on 2008-09-18
> **jemate18 said:**
> 1. mount the memory card
2. open the memory card using nautilus
3. click view
4. click show hidden files

If you see .trash click on it and select the pictures you have undeleted and then restore them..

If there is no .trash, sorry, I dont know of a way of retrieving it.

Thanks, Jemate 18,
but what is nautilus? Should I have it? Where can I get it?

---

### Post by SuperSonic4 on 2008-09-18
Nautilus is your file browser and you should have it if you're running GNOME which you should be looking at the ubuntu tag. You can press alt + f2 and type in /media which takes you to your /media folder

---

### Post by hellion0 on 2008-09-18
As long as you haven't overwritten the pictures with other data, it can be recovered. Assuming it's been "permanently" deleted (not present in .trash/), go with billgoldberg's suggestion of looking for data recovery software for that USB drive's filesystem, and DON'T add new files to the drive!

---

### Post by bumanie on 2008-09-18
Photorec from [here]("http://www.cgsecurity.org/wiki/PhotoRec")

---

