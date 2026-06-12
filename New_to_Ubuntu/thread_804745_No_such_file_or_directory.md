---
title: "No such file or directory"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by Jimmy9pints on 2008-05-23
I always have this problem when I am trying to manually install something. If I place a file on the desktop, cd ~/Desktop, make it executable and then type a command to run the file (in this case ./installsongbird.sh). I get the response "No such file or directory". 

I have seen other people complain of this in the past so it must be a common newbie problem. Does anyone know why?

---

### Post by bwhite82 on 2008-05-23
You are either not in the correct directory, perhaps the file is in a folder on the desktop? Or another newbie mistake is that the command line is case sensitive, so make sure the file isn't something like: InstallSongBird.sh instead. Your best bet is to simply type the first few letters (being mindful of case) then simply hit the TAB key which will auto-complete the rest of the name.

---

### Post by Maestro23 on 2008-05-23
Just downloaded the songbird tarball from their site for a quick test.

Copied to my home directory and did the following:

> tar -xvf  Songbird_0.5_linux-x86_64.tar.gz

cd Songbird

./songbird

License Agreement window popped up.

---

