---
title: "[SOLVED] Firestarter Firewall"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by Jakey_TheSnake on 2008-10-18
Hi All, 

I am using Firestarter and it appears the only way to have it running is to have it open as a program. 

If I close it, it completely disappears from the systray. Does this mean it is not running? 

If so, how can I keep it running but without a window up. 

Thanks, 

Jake

---

### Post by Vishal Agarwal on 2008-10-18
in the terminal issue this command :
> ps -ef | grep firestarter 

it will show you the status for fire starter. Also search the forum, there is plenty of posts regarding fire starter. You will learn many things regarding Firestarter thru those posts.

---

### Post by owenll on 2008-10-18
It says this on their website: [http://www.fs-security.com/docs/tutorial.php](http://www.fs-security.com/docs/tutorial.php)

> A frequently asked is question is, what happens when you quit the program. The answer is that the firewall will keep functioning. If you are running Firestarter as a system service, which is automatically set up for you when installing Firestarter from a binary package, the firewall is in many cases even running before you start the program. 

---

### Post by Jakey_TheSnake on 2008-10-18
Never mind, just found the answer myself. 

> When you install Firestarter from a package the program is automatically registered to run as a system service. This means the firewall is also running even if the graphical program is not. 

Please lock topic, thanks.


edit: thank you anyway owenll, found out just before you posted :P

edit2: 

```
jake      7838  7818  0 12:15 pts/0    00:00:00 grep firestarter
```

Is the output of your command.

---

### Post by owenll on 2008-10-18
> **Jakey_TheSnake said:**
> Never mind, just found the answer myself. 

Please lock topic, thanks.

edit: thank you anyway owenll, found out just before you posted :P

On a side note, how do I mark a topic as solved?


[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Jakey_TheSnake - one small comment: it does not help others, and can be confusing if you edit the post to remove the question after finding the answer.

---

### Post by gn2 on 2008-10-18
Firestarter isn't the firewall, it is simply a GUI tool for adjusting the firewall settings.

It has been argued that having Firestarter running is actually a security vulnerability.

[**This post**]("http://ubuntuforums.org/showthread.php?t=510812") is worth reading for more information on security in Ubuntu.

---

