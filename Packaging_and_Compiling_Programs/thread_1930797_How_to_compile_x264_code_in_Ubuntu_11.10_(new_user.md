---
title: "How to compile x264 code in Ubuntu 11.10 (new user)"
date: 2012-02-24
forum: Packaging and Compiling Programs
---

### Post by skyjuice88 on 2012-02-24
Dear Ubuntu community,

I have just started using Ubuntu or Linux to be precise since a few days back and I am still learning to get around. So I have this project where I need to get a H.264 source code in C where I would need to "insert" some short video to see its output. 

This is one of the codes that I managed to find 
[http://www.videolan.org/developers/x264.html](http://www.videolan.org/developers/x264.html)
Since I am new to Linux, I have difficulties compiling/running the code. 

I know I have to change the directory using the command 'cd' to the same place where the folder is located and execute it by typing 'gcc -g myprogram.c -o myprogram-' but this doesn't seem to work.

I'm not sure if this link teaches the right way to run it. [http://wiki.videolan.org/UnixCompile](http://wiki.videolan.org/UnixCompile) and it sounds quite complicated to a new user like me.

I'm sorry for asking so many questions but I'd really appreciate if someone could give me some guidance. Thank you very much.

---

### Post by Eiji Takanaka on 2012-02-24
What are you trying to accomplish dude?

Are you trying to get x264 encoded videos running on vlan?

If so you might want to look into the good,bad and ugly plugins(mencoder i think don't hold me to that though) available via the respository.

If you want to do a wee spot of x264 encoding, then the x264 encoder is available via the videolan website. 

As for compiling it have you tried the old faithful

 ./configure, make, sudo make install? 

Just been to that website, did you untar it first?

Then tried the above commands in the x264-snapshot-20120223-2245 folder?

---

