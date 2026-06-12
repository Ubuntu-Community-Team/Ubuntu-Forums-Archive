---
title: "Is there any way to save the current session whenever we want?"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by legolas_w on 2008-08-16
Hi
Thank you for reading my post
Is there any way to save the current session whenever we want and load it when we need?

for example to save all running applications and also their states now and recover the session an hour later?

Thanks

---

### Post by dje on 2008-08-16
System >> Preferences >> Sessions and on the "session options" tab ;)

dje

---

### Post by legolas_w on 2008-08-16
That will save and reload the session when we log out and when we log in, I want to do it on-deamnd. 

save a session now, recover it the next day or any time that i need that specific session.

Thanks

---

### Post by Dougie187 on 2008-08-16
You could look into using the command line programs
```
gnome-session-save
```
and
```
gnome-session-remove
```

You can use gnome-session-save to save the current session (on demand) and then when you are logging in, under sessions, select the run * script option, i forget the exact name of it, but its like the second one down. and that will restore the session you saved.

You could even go about assigning ```
gnome-session-save
``` to a key and then just hit that key whenever you want to save the current session. I would guess that doing it more then once would just save the last one. So I would say only one is saved at any given moment.

---

