---
title: "Server Desktop GUI questions"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by Dthorton15 on 2008-11-29
my ?'s are in bold because i just type whats on my mind and confuse people some times.

Hello,
I want to transfer some files from my My Book 500 GB external. And yeah, I can put up with terminal only but for this it will go by much faster.

Basically I was wondering if there was a command to get the bear bones ubuntu desktop gui on my server w.o the open office and all(**and what is it if it exists**). Then if I could just take it off like 5 hours later because my server is sooo slowww after I do waht I want to do(**and what is it if its possible**).

I messed my server up big time. So I need to format, but I want to keep the directory that I have on all my windows PC's as my G: Drive. So I figured I would TAR it then put it on my my book, then reformat and fresh install ubuntu server. Then put the tar back on and untar it using the desktop gui to make it ezier

**if there is an easier way to do it plz feel free to tell me.**


**also what would be the command to transfer the tar to my external? thanks**

---

### Post by a0u on 2008-11-29
If it's just TARing and moving a file, everything can be done with the terminal.
> 
```
tar -cvvf foo.tar foo/
```tar contents of folder foo in foo.tar
To move a file:
```
mv <path_to_file> <path_to_destination>
```

For a GUI:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
Near the end of the webpage, there are steps to install a minimal GUI.  It won't be GNOME, however.

---

