---
title: "[SOLVED] DPKG help?"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by KatanaMonk on 2008-09-24
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

I get this when I try to add programs.  Is there anything that I can do?  It happened after I upgraded to Hardy heron.

---

### Post by Qrikko on 2008-09-24
I think you just need to do what it say, namely run:
```
dpkg --configure -a
```
as root. 

if I don't remember wrong :)

---

### Post by KatanaMonk on 2008-09-24
Nevermind, I added "sudo" to the front of it and it worked.

---

### Post by Sef on 2008-09-24
> I think you just need to do what it say, namely run:
     Code:
     dpkg --configure -a 
as root. 

if I don't remember wrong :smile:Not quite correct. It's ```
sudo dpkg --configure -a
```

---

### Post by Joeb454 on 2008-09-24
> **Qrikko said:**
> I think you just need to do what it say, namely run:
```
dpkg --configure -a
```
as root. 

if I don't remember wrong :)

Correct. Though with Ubuntu it's basically ```
sudo dpkg --configure -a
``` From a terminal :)

---

### Post by jemate18 on 2008-09-24
In case you didn't know how to execute the above post as root....

1. Applications -> Accessories -> Terminal
2. ```
sudo dpkg --configure -a
``` 
3. Type your password and hit ENTER key

---

### Post by jemate18 on 2008-09-24
please mark this thread as solved.....

---

### Post by Qrikko on 2008-09-25
> **Sef said:**
> Not quite correct. It's ```
sudo dpkg --configure -a
```

Ah I thought it was kind of covered with "as root" :) 

since you could do it any way you like (su, root-terminal and so on) as long as you have super-user privileges :)

---

