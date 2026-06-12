---
title: "Python/PHP/Apache Problem"
date: 2008-10-06
forum: Programming Talk
---

### Post by gmoeck on 2008-10-06
I'm guessing that the following is a configuration issue, but I've been playing with it all morning, and haven't gotten just about anywhere. 

I have a python script that I want to run from a php based website, so what I was planning on doing was running exec, or a system, passing in something akin to "python script.py". However, when doing this, I don't seem to have access to python at all. I can use exec or system to do other commands (ls, grep, etc.), but not python.

The part that has me really stumped is that I can access php, and ruby, but not python. Both "php --version", and "ruby --version", return values to the webpage, but "python -V" gives me nothing. 

Any ideas?

---

### Post by mssever on 2008-10-06
Have you tried executing the script directly, without prefixing python (./script.py)? It may be that your $PATH is messed up.

---

### Post by gmoeck on 2008-10-06
Yea, I've tried that, as well as giving full path names to the system. It's weird, because with the full path names, it works with php and ruby, but not python although they're in the same file location (/usr/bin). I can't even pull the python version number out of the system. But I can no problem sshd in.

---

### Post by drubin on 2008-10-06
post the output of 
```
which python
```

---

### Post by gmoeck on 2008-10-07
Both the console and the php page give "/usr/local/bin/python"

---

### Post by drubin on 2008-10-07
> **gmoeck said:**
> Yea, I've tried that, as well as giving full path names to the system. It's weird, because with the full path names, it works with php and ruby, but not python although they're in the same file location **(/usr/bin)**. I can't even pull the python version number out of the system. But I can no problem sshd in.

> **gmoeck said:**
> Both the console and the php page give "**/usr/local/bin/pytho**n"


So maybe put the full path as (/usr/local/bin/python).  This might solve the issue I have had pathing issues with this before. 

Here is  java related post it might be relvent.. 
[http://ubuntuforums.org/showpost.php?p=5831549&postcount=24](http://ubuntuforums.org/showpost.php?p=5831549&postcount=24)
Then take a look at the thread
[http://ubuntuforums.org/showthread.php?t=922399](http://ubuntuforums.org/showthread.php?t=922399)

---

### Post by y@w on 2008-10-07
Make sure you're doing all these tests as the user the website will be running as. For Ubuntu it's www-data by default.

---

### Post by drubin on 2008-10-07
> **y@w said:**
> Make sure you're doing all these tests as the user the website will be running as. For Ubuntu it's www-data by default.

ye hehe see my post above above ^^

---

### Post by gmoeck on 2008-10-07
Still get nothing on system("/usr/local/bin/python -V"). 

I've come up with another way around having to integrate it into php though, so I worked around the problem.

---

