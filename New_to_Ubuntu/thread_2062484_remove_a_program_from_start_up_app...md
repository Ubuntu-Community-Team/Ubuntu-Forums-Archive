---
title: "remove a program from start up app.."
date: 2012-09-25
forum: New to Ubuntu
---

### Post by jcka005 on 2012-09-25
**help! i added a program on the start up applications few hours ago and it didn't work well..**

now i want to remove it from the list..after i restart it from showing the lockpix, i tried to remove it but it freezes showing the lockpix again..
so i have to restart it again and remove it from the list as fast as i could..

**can i remove it from the list using the other user account? **

anybody there who understands what i'm saying?** kindly help me please.**thankyou.

---

### Post by stinkeye on 2012-09-25
What program did you add and was it to startup applications?
Don't understand what the lockpix is?
Is the program not allowing you to reach the desktop?

---

### Post by jcka005 on 2012-09-27
i added "mkahawa" to start up applications..it is a tool for cyber cafe management..

lockpix is the image that blocks the person from opening the pc (which is the client pc)

the lockpix starts to run after 10 seconds of showing the desktop..

i have tried once, as fast as i could, i went to system settings and have reached the start up applications and about to remove mkahawa from the list..unfortunately, 10 seconds is not enough for me..i was about to click the remove button but the lockpix suddenly appear..

that is why i am asking if i can remove it from the start up applications using the other user account..
thankyou..

---

### Post by critin on 2012-09-27
It's odd that you can't change it as administrator or root.   There are no edit options anywhere?
Wow...

If the 'other user acct' is allowed to remove it, it wouldn't be secure would it?  You could always try, and I would.


I found this forum where you might find help.  It appears to be the dev or someone closely related to "mkahawa" posting there.  The last posts are from this year.

[http://ubuntuforums.org/showthread.php?t=1295156](http://ubuntuforums.org/showthread.php?t=1295156)

---

### Post by akoskm on 2012-09-27
I'm curious what happens if you boot in rescue mode (where you have no gui at all).
If you are able to do that just log in with your user through the terminal and remove the application.
```

sudo apt-get remove *<appname>*

```
Then boot in normal mode, read the documentation and finally install the application again.

---

