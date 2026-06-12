---
title: "Can't find app.."
date: 2008-10-21
forum: New to Ubuntu
---

### Post by Skyker on 2008-10-21
I just installed an application using synaptic, but I can't find it, any suggestions on how to find this file??  It was Mednafen.  And I've tried doing the app finder and it can't find it...  Is there any other way?

---

### Post by Marshal0505 on 2008-10-21
Open up a terminal and type it's name to start it.
I think most if not, all programs end up in /usr/bin/.
So when you type a programs name, the system will try to execute 

```
/usr/bin/*name*
```

---

### Post by Skyker on 2008-10-21
Apparently the file doesn't exist..

---

### Post by Marshal0505 on 2008-10-21
Since i'm not familiar with the program myself, I tried installing it myself.
This is what I did.
added the 'testing' repo in sources 
typed 
```
apt-get install mednafen
```

and finally to start it I typed 'mednafen'
All worked without a hitch, could you possibly repeat your steps to see if all went well.If it's already on your system you will get the message "Mednafen is already the newest version" and no changes will be made.

---

### Post by Marshal0505 on 2008-10-21
As a rule in general to find stuff you can always use 'locate'

first do ```
sudo updatedb
```
followed by the 'locate' command , in this case
```
locate mednafen
```

result:/usr/games/mednafen

This is where mednafen ends up on your system

---

### Post by Skyker on 2008-10-22
thanks i'll try it :)

---

### Post by cardinals_fan on 2008-10-23
*wrong thread*

---

