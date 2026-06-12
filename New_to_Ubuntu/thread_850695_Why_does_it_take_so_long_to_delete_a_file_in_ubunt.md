---
title: "Why does it take so long to delete a file in ubuntu?"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by combonautjim1966 on 2008-07-05
I Noticed that it takes literally minutes to delete small files.
Is this normal, a memory or processor speed issue or is it fixable? Thanks!

---

### Post by wolfen69 on 2008-07-05
no, this is not normal. huge files only take a second or two for me. sounds like a borked install.

---

### Post by sharks on 2008-07-05
it takes me 2 or 3 sec to delete 500 mb file

---

### Post by sokam on 2009-10-27
I have similar problem on xubuntu.  Take hours(!) to delete a few gb of files!  Anyone can tell me if there is something I need to look at?

Also, how to delete files without moving them to the trash first?  I think that might help speed things up if instead of moving to trash, I can just delete them immediately.

---

### Post by SuperSonic4 on 2009-10-27
> **sokam said:**
> I have similar problem on xubuntu.  Take hours(!) to delete a few gb of files!  Anyone can tell me if there is something I need to look at?

Also, how to delete files without moving them to the trash first?  I think that might help speed things up if instead of moving to trash, I can just delete them immediately.

0. Necromancy is bad. Create a new topic in future

1. Could be because it has to assess the size of the trash and then allocate it there

2. Use the **rm** command from a terminal (but be careful) or press **Shift** before hitting the **Delete** key

---

### Post by LunaticHiatus on 2009-10-27
what are your specs?
Also, there are different file systems which can optimize your performance. (just an idea) Not that windows has a good one. NTFS hasn't been updated in over what, eight years now?

in linux though, EXT3 is currently dominant, the latest ubuntu (karmic) will be EXT4. there is JFS is good for older computers since its light on the cpu. Reiser which is faster with lots of small files. XFS which is fast and good for big files but notoriously bad recovery. ZFS is being ported, which is slow but incredibly stable. etc. etc.

---

### Post by Penguin Guy on 2009-10-27
No, it's not normal. It might depend a bit on exactly what you're doing: If you're moving them to the trash then it should be done pretty much instantly, if you're properly deleting them then it may take a bit longer. It defiantly shouldn't be taking a few minutes though.

---

### Post by LunaticHiatus on 2009-10-27
I just noticed your using kubuntu. You realize thats the fattest distro possibly ever? might be your computer specs vs. trying to run compiz fusion, widgets, etc. etc. etc.

---

### Post by sokam on 2009-10-27
> **SuperSonic4 said:**
> 0. Necromancy is bad. Create a new topic in future

1. Could be because it has to assess the size of the trash and then allocate it there

2. Use the **rm** command from a terminal (but be careful) or press **Shift** before hitting the **Delete** key


Ah... the "Shift+Delete" is working in a normal speed for me!  Thanks.

I will try to create a new topic next time.  Usually I can find all of my answer if I search in here or google but I just couldn't find the answer.

---

### Post by nerdopolis on 2009-10-27
I read somewhere once that there was a bug in KDE with trash, that when you delete a file (to trash) in a secondary partition, it moves it to the /home folder, which may be in another partition. 

There also is another bug in trash
[https://bugs.kde.org/show_bug.cgi?id=179348](https://bugs.kde.org/show_bug.cgi?id=179348)

They are working on a fix

---

