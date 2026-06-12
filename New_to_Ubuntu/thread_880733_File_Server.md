---
title: "File Server"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by OuT.Law on 2008-08-05
Hello .......

N00b askin for help with ubuntu desktop, how can i make a file server in ubuntu desktop ?
i searched for tutorials and i found one but it was on KDE not Genome and thats a problem for me.
so guys anyone can help me with a step by step tutorial or something like this ? 
BTW im new to linux :lolflag:

Thanx in advance

---

### Post by hyper_ch on 2008-08-05
who shall connect to it? Other linux systems? Windows systems? ....

---

### Post by OuT.Law on 2008-08-05
> **hyper_ch said:**
> who shall connect to it? Other linux systems? Windows systems? ....

Windows Systems ! :)

---

### Post by hyper_ch on 2008-08-05
then use Samba - I'm sure you'll find a howto on that.

---

### Post by jamesrfla on 2008-08-05
All you have to do is make a folder that you are going to share and then right click it and hit sharing options. Make sure it downloads and installs samba then log out and log back in then go back to sharing options and share your folder.

---

### Post by GrnFrag on 2008-08-05
Can you share mount points using that method?   specifically i'm mounting ISO's and want to share them, like the CD's they're supposed to be

---

### Post by y@w on 2008-08-05
Yeah, you can share any directory. The mounted ISO's are just a mountpoint, just like /, /home, etc..

---

### Post by GrnFrag on 2008-08-05
so you mount to whatever directory you want?  i attempted to mount an iso to a directory under my /home that i'd created for the purpose.   However i got a message that it wasn't a valid mount point.   Do you have to mount to a lower level?  Like /home or could i use make something else?  Like /data or /iso

---

### Post by y@w on 2008-08-05
Well.. whatever place you decide to mount has to exist as an empty directory. So, no you can't mount it as /home. It can be /home/user/iso1 as long as that directory exists.

---

### Post by GrnFrag on 2008-08-05
ahha.  that explains it.   must be empty.   Thanks for the advice, i'm trying it now

---

