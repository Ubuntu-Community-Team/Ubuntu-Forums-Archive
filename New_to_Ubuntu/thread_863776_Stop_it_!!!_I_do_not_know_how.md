---
title: "Stop it !!! I do not know how??"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by just_linux on 2008-07-18
OK
I needed to downland many file from a website {Some pdf file }:popcorn:
But it done not stop it keeps downaloding every sing file there and I can not stop it
I used 
wget w 2 -r -A pdf [www.sam.com](www.sam.com)
and it keeps creatting forlders and so on. 
So I wonder it I run the code how shoul;d I cancle it?
I closed the treminal already????

Please help:guitar:

---

### Post by R3linquish3r on 2008-07-18
"sudo killall wget" should do it

---

### Post by t0p on 2008-07-18
You need to be careful with wget! If you run it with the -r option, it will work recursively, which means it will follow every relative link in the site and, basically, download the entire site to your computer.

Before you run wget again, it'd be an idea to check out the manpage for it, ie run
```
man wget
```

---

### Post by drubin on 2008-07-18
Most important param of wget that i can think of is l (that is a lower case L) that tells wget how many levels down it needs to carry on getting all the files.

Unless the commands are sent to the background. via the "&" operator. these should stop the "process" or any for that matter.

ctrl+c should do it.
Closing the terminal
killall wget   -> This one should be used sparingly as it could stop processes you never knew were running (If they were run by the same command)


A nice command for viewing all running proccessing.
```
ps -ef
```

I always include the -ef it tells it to show all running process as well as the commnand that started them.

```
kill PID
```
where PID is the PID from the command 'ps'

Hope this gets you started.

---

