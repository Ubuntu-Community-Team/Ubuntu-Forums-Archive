---
title: "How to Delete Home Directory (Out Of Disk Space)"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by brutus83 on 2008-05-04
I tried to upgrade my 7.04 into 8.04 using Jigdo.
I make new directory named 'dvd-repo' on my Home Directory.
Then, because my disk didn't enough, the process STOPPED.
Then, I was log-out.

When I wanna log-in, there's message :
" GDM could not write to your authorization file. This could mean you are out of disk space on that your home directory could not be opened for writing. In any case, it is not possible to log in. Please contact your system administrator "

My Question :
1. How could I delete the 'dvd-repo', so i could log-in into the system again ?
2. How could I free some disk-space again ?

Thx.
-brutus-

---

### Post by haiji on 2008-05-04
Try to boot with the liveCD and remove the files. 

You can also log-in into system using root account. Just push ctrl+alt+F1 in GDM, use the root user/pass and you will be able to remove files using command line.

---

### Post by BennBuntu on 2008-05-04
I don't fully understand how you got there, but if you wanna remove that directory, long as you can log into command line, (try ctrl+alt+F2).

```
sudo rm -r /home/dvd-repo 
```

the -r means recursive. You'll need root password.

good luck

---

