---
title: "Ctrl+[Key] stopped working in Terminal"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by jasonkostempski on 2008-06-04
If, for example, I use ctrl+p to access my history I get ^P. I found 1 suggestion to delete my user account but that's a lame answer. I know there must be a correct way to fix it but I can't seem to find it. I'm an absolute beginner on Linux, the best idea I could come up with is to edit ~/.bashrc but I didn't know where to go from there.

---

### Post by tamoneya on 2008-06-04
i believe it should be ctrl-shift-p.  That is how it is for most shortcuts in terminal.

---

### Post by jasonkostempski on 2008-06-04
I had tried that, I get the same thing when I do that, '^P'. I confirmed that if I create a new user it supports ctrl+p, tab, up arrow, etc and it has color coding when, for example, ls is run. My user does not. I'm sure recreating my account will fix the issue but I'd rather learn the real cause of the problem. I also noticed I don't have the user@hostname before $.

---

### Post by tamoneya on 2008-06-04
right click in terminal and check input methods.  Mine is set to System.  Check to see if yours is as well.  When did this start happening?  what did you do around that time that may have caused this?

---

### Post by jasonkostempski on 2008-06-04
It is set to system. It's hard to say what I did, it's a new install and I've been doing a lot to get it set up and most of the time I've been blindly pasting commands into the terminal. I found the post that mentioned deletion [http://ubuntuforums.org/showthread.php?t=623725]("http://ubuntuforums.org/showthread.php?t=623725"), but again I was hoping to figure out the root of the problem.

---

### Post by jasonkostempski on 2008-06-05
Well, I was about to give in and delete my account. While I was setting up the temp account to transfer my data to, I notice a setting that was different. Under System->Administration->Users and Groups->Advanced my 'Shell' path was set to /bin/sh. On the temp account it was set to /bin/bash so I switched mine back to /bin/bash and logged out, when I logged back in everything worked fine. I have no clue how that got switched or if it ever was correct.

---

