---
title: "Unmovable files"
date: 2011-09-28
forum: New to Ubuntu
---

### Post by Acquisitio on 2011-09-28
I have just Ubuntu installed and have noticed that there are much more unmovable files on my C disk after the installation of Ubuntu than it was before- while I was using Windows.  When the defragmentation of the disk is finished there are much more green space,i.e. unmovable files. I would say more than ten times more. While I was using Windows, there was not too much unmovable files. Can anyone tell me what this means and what could be done with them.
Thank you.

---

### Post by androssofer on 2011-09-28
> **Acquisitio said:**
> I have just Ubuntu installed and have noticed that there are much more unmovable files on my C disk after the installation of Ubuntu than it was before- while I was using Windows.  When the defragmentation of the disk is finished there are much more green space,i.e. unmovable files. I would say more than ten times more. While I was using Windows, there was not too much unmovable files. Can anyone tell me what this means and what could be done with them.
Thank you.

Did u install ubuntu via wubi (within windows) or did u dual boot it(seperate partition)?

---

### Post by Acquisitio on 2011-09-28
> **androssofer said:**
> Did u install ubuntu via wubi (within windows) or did u dual boot it(seperate partition)?

Well, when I said that I have Ubuntu installed I actually wanted to say that someone did it for me. I have Ubuntu and Windows both on my computer now and when I turn on or restart my computer I am asked to chose the system. I want Linux but I suppose I will need the time to learn about it so I will use Windows little more time.
As for your question, I saw the wubi in my computer and I was told to use it if there would be  need for re-installation of the system. So I have wubi in my computer and suppose that is the answer...

---

### Post by bcbc on 2011-09-28
The virtual disk wubi uses is large and windows tends to avoid defragmenting it. You could move it to an external drive, defrag, and then move it back. But depending on how big it is and how much space you have remaining it could still end up non-contiguous.

Wubi is designed to try out Ubuntu. If you move to a real dual boot you won't have this issue, plus it's better long term.

---

