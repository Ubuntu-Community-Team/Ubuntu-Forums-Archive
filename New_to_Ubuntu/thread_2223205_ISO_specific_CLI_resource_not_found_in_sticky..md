---
title: "ISO specific CLI resource not found in sticky."
date: 2014-05-09
forum: New to Ubuntu
---

### Post by Kurt_Alan on 2014-05-09
**[SIZE=5][COLOR="#000000"][/COLOR][/SIZE]**

I recently needed to input this from the terminal in recovery mode: ```
 mount -o rw,remount / 
```

I understood the purpose: to mount the file system as read AND WRITE so that I could change ownership of .Xauthority in order to log-in to my session.

But I copied/pasted the code from someone who was most helpful.  How am I going to learn CLI by copying-pasting?  I want to learn the syntax myself but I don't know what the parts mean.

For example, in the above I have no idea what "-o" references.  

A few weeks ago I found out about a website where one can put in code and it will output an explanation of each part of the code and what it stands for.  It is interactive.  But I lost the URL and I cannot find it in the sticky or by Google.

Does anyone know this site?

---

### Post by deadflowr on 2014-05-09
This
[http://explainshell.com/](http://explainshell.com/)

---

### Post by Kurt_Alan on 2014-05-09
**[COLOR="#000000"][/COLOR]**

That's it exactly! Thank you!

---

### Post by sotiris2 on 2014-05-10
Also a way to learn what a command does is to do
```
man command
```

---

