---
title: "Formatted hard drive and lost space!Help! From 45GB to 3GB!!"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by Felliph3 on 2008-05-16
I am trying to run linux on my second hard drive and it has 45GB. I had to format it to install linux. However i did it and after the install failed for another reason when i got back on windows it had 3GB capacity on that hard drive! It had a 45gb capacity. What happened!!!?

---

### Post by mrpena on 2008-05-16
windows and linux do not have the same type of file system structure.  If you formatted it for linux, windows is unable to write to it.  you'll have to format it in windows if you want to use it in windows.

---

### Post by Felliph3 on 2008-05-16
hmm interesting. Well, i formated IN windows and im using WINDOWS because LINUX failed. I will try again in a little bit. But youre saying I have that space on linux then?

---

### Post by bouta on 2008-05-16
go into windows .and get a program called acronis disk director or paragon disk suite .. and it will detect any hard disk u could partition them and resize or merge them into ur primary hard disk.

---

### Post by Mud.Knee.Havoc on 2008-05-16
> **mrpena said:**
> windows and linux do not have the same type of file system structure.  If you formatted it for linux, windows is unable to write to it.  you'll have to format it in windows if you want to use it in windows.

This is not true.  You can format it in linux for use in linux or windows.

---

### Post by Mud.Knee.Havoc on 2008-05-16
> **bouta said:**
> go into windows .and get a program called acronis disk director or paragon disk suite .. and it will detect any hard disk u could partition them and resize or merge them into ur primary hard disk.

There's no need to spend $50 for a Windows program just to resize or repartition a hard drive. 

Try [http://partedmagic.com](http://partedmagic.com)
EDIT: or install gparted in Applications->Add/Remove (not sure if that one needs any particular repositories enabled or not)

---

### Post by Felliph3 on 2008-05-17
I managed to install and apparently that I can only use 3GB in windows and the rest of it can be used in Linux. Thanks for the help, i guess its solved/.

---

