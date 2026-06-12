---
title: "polling a directory on a windows computer"
date: 2014-02-07
forum: New to Ubuntu
---

### Post by tomvo on 2014-02-07
I wan't to do polling on a directory on a PC running windows,

i used cifs for the mounting and this works, I'm seeing all the files, directory's.....

then I"m using the "inotifywait -e modify,create,move /home/tom/pas" in a .sh file to do the polling.

this only works if I add, change... on my linux system, if I add or create a file on the PC nothing happens 

but the "ls-command" shows the new files.....

help would be greatly appreciated.

Tnx

---

