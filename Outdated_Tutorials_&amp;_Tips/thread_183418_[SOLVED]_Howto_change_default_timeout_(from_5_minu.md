---
title: "[SOLVED] Howto: change default timeout (from 5 minutes) in sudo"
date: 2006-05-28
forum: Outdated Tutorials &amp; Tips
---

### Post by arnieboy on 2006-05-28
Some of you might not like the default timeout of 5 minutes after which sudo asks for your password again in a session. To change that do the following:
```
sudo visudo
```
scroll down and add the following line at the end:
> Defaults:user_name  timestamp_timeout=10
1) Change **user_name** to your actual user name. 
2) Change **10** (in minutes) to anything you wish. A value of **-1** will make it infinite (for a single session).
3) Hit Ctrl-X and then hit Y.
You are all set!

---

### Post by frodon on 2006-05-31
Nice guide arnie ;)

Does it work for dapper too ?

---

### Post by arnieboy on 2006-05-31
[QUOTE=frodon]Nice guide arnie ;)

Does it work for dapper too ?[/QUOTE]
works for all ubuntu releases frodon.

---

### Post by Sammi on 2006-05-31
So if I set it to infinite(-1), is there a manual way to turn superuser off after I use a sudo command?

---

### Post by arnieboy on 2006-05-31
[QUOTE=Sammi]So if I set it to infinite(-1), is there a manual way to turn superuser off after I use a sudo command?[/QUOTE]
superuser is not "ON" when u use sudo. u merely let your user account gain super user permissions. 
if u set it to -1, the sudo password will not timeout till u log out of your account.

---

### Post by Sammi on 2006-05-31
I understand that much. Just wasn't clear enough in my previous post. The thing I was wondering is if there is another way of taking superuser priveledges away from the user account, after a sudo command with an infinite timer has been issued, other that logging off ofcourse?

If not then that option is kind of useless I think. Could just as well just make a root account if I wanted to stay in superuse mode all the time.

---

### Post by BobSongs on 2006-05-31
[QUOTE=Sammi]So if I set it to infinite(-1), is there a manual way to turn superuser off after I use a sudo command?[/QUOTE]
If you set **sudo**'s time to infinite (-1) you can kill it at any time with the following```
sudo -K
```This works regardless how long you set **sudo** to last. :)

---

### Post by Sammi on 2006-06-01
There we go. Thx! :D

---

### Post by karthick87 on 2010-12-24
Short and useful how to :)

---

