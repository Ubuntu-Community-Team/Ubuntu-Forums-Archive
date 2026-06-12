---
title: "I suddenly can't commit my project with SVN!"
date: 2008-09-12
forum: Programming Talk
---

### Post by irrdev on 2008-09-12
I have been using RapidSVN for several months now, no problems. However, in the past few days, I have found that the client has become completely unusable. RapidSVN simply crashes with no warning whenever I try to Commit, Add/Remove files or otherwise make changes to the working copy of my project. I installed SVN WorkBench and the exact same problem persists, making me believe that this is an SVN problem, and not a client problem. 

I tried reinstalling libsvn1, but to no avail. I have also tried using a new working copies and other unused working copies with both RapidSVN and SVN WorkBench. Both client promptly crash whenever I add/remove files, or try to commit my project. Highly unusual, but extremely annoying. The log files reveal nothing. I am extremely desperate to get back to work, but I have no idea how to fix this. Can anybody help me out?

---

### Post by mssever on 2008-09-12
> **irrdev said:**
> Can anybody help me out?
What happens when you use the CLI svn client? ```
svn rm somefile
svn add someotherfile
```

---

### Post by irrdev on 2008-09-12
> **mssever said:**
> What happens when you use the CLI svn client? ```
svn rm somefile
svn add someotherfile
```
That's what I am currently using. The CLI svn client works fine, even with the projects that I was trying to use with RapidSVN and SVN WorkBench. Usually I would assume that the GUI client is the problem, but it seems odd that the exact same problem would exist with two entirely different clients. As I already mentioned, I thought the libsvn1 library might be the problem and completely reinstalled it, but this didn't fix anything either.

---

### Post by mssever on 2008-09-12
> **irrdev said:**
> That's what I am currently using. The CLI svn client works fine, even with the projects that I was trying to use with RapidSVN and SVN WorkBench. Usually I would assume that the GUI client is the problem, but it seems odd that the exact same problem would exist with two entirely different clients. As I already mentioned, I thought the libsvn1 library might be the problem and completely reinstalled it, but this didn't fix anything either.
Hmm... I tried RapidSVN once and found it intolerably slow (it doesn't play nice with my high-latency satellite internet connection). I just use the cli version and it's fine. The only feature that I miss is a graphical diff. Aside from that, it isn't possible to make a GUI that's easier to use than the CLI version.

So, since I don't use RapidSVN, I don't know what to tell you.

---

### Post by rnodal on 2008-09-12
I would recommend kdesvn. I have been using it for a long time without problems. Also, have you tried running the application from the command line? Sometimes when you start a GUI application from the terminal they *normally* report problems. Have you tried debugging the application with gdb? That sometimes also helps to figure out what the problem is. 

-r

---

### Post by Zugzwang on 2008-09-12
> **irrdev said:**
> That's what I am currently using. The CLI svn client works fine, even with the projects that I was trying to use with RapidSVN and SVN WorkBench. 

Ok, then try starting those programs from the command line in order to get error message eventually put out to the console.

---

### Post by Amon_Re on 2008-09-12
> **irrdev said:**
> I have been using RapidSVN for several months now, no problems. However, in the past few days, I have found that the client has become completely unusable. RapidSVN simply crashes with no warning whenever I try to Commit, Add/Remove files or otherwise make changes to the working copy of my project. I installed SVN WorkBench and the exact same problem persists, making me believe that this is an SVN problem, and not a client problem. 

I tried reinstalling libsvn1, but to no avail. I have also tried using a new working copies and other unused working copies with both RapidSVN and SVN WorkBench. Both client promptly crash whenever I add/remove files, or try to commit my project. Highly unusual, but extremely annoying. The log files reveal nothing. I am extremely desperate to get back to work, but I have no idea how to fix this. Can anybody help me out?

Hey, both clients also bombed out on me in combination with my SVN server, i access the SVN using the dav_svn Apache module on an https link.

Using the console & the nautilus scripts however work, not a solution but maybe the issue's are related.

---

### Post by rnodal on 2008-09-12
> **Amon_Re said:**
> Hey, both clients also bombed out on me in combination with my SVN server
Your svn server also crashed?

-r

---

### Post by Amon_Re on 2008-09-12
> **rnodal said:**
> Your svn server also crashed?

-r

Err, no :) The clients bombed out when *accessing* my svn server, as in, the combination of my svn server and the clients cause the clients to crash.

I'd be worried if an svn client manages to crash my Apache :lolflag:

---

### Post by rnodal on 2008-09-12
> **Amon_Re said:**
> Err, no :) The clients bombed out when *accessing* my svn server, as in, the combination of my svn server and the clients cause the clients to crash.

I'd be worried if an svn client manages to crash my Apache :lolflag:

:lolflag:
-r

---

### Post by Jiddo on 2008-11-07
Hello!

I have the exact same problem on both my computers (both my laptop and my desktop PC). Sorry to bump this old thread, but I really need some solution for this. Anyone got any ideas?

Yours, Jiddo.

---

