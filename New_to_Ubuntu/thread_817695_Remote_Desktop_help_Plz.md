---
title: "Remote Desktop help Plz"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by Foxfire on 2008-06-03
I put this code in the terminal

 x11vnc -forever -usepw -httpdir /usr/share/vnc-java/ -httpport 5800  

I cant connect from my lap top to my desktop  has long as I dont close out the terminal but when I close it i cant connect again.

Does anyone know how to fix this?

---

### Post by tamoneya on 2008-06-03
what happens if you hit alt-F2 and run that command there.

---

### Post by Foxfire on 2008-06-03
so far so good  but Cant connected from desktop to laptop

---

### Post by krunge on 2008-06-04
> **Foxfire said:**
> I put this code in the terminal

 x11vnc -forever -usepw -httpdir /usr/share/vnc-java/ -httpport 5800  

I cant connect from my lap top to my desktop  has long as I dont close out the terminal but when I close it i cant connect again.


Use the "-bg" x11vnc option to have it go into the background.

You may want to add "-o ~/.x11vnc.log" to have its messages go to that file (this helps in debugging connection problems).

Or put it into the background using the standard shell '&' method:

```
x11vnc -forever ...  &
```

include "-o ~/.x11vnc.log" here too.  Any command can be put into the background using '&'.

---

