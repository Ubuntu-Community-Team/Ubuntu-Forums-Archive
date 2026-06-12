---
title: "annoying webcam issue"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by danmeetswood on 2008-09-30
I can see my webcam using Ekiga, but using any other program, like Cheese, it tells me that /dev/video0 doesn't exist, even though it does... What do I do?

---

### Post by danmeetswood on 2008-09-30
sort of fixed, turns out it only does that when I'm visiting live.yahoo.com, which says it's being used by another program... but works with Cheese and other programs when that website is closed.

---

### Post by danmeetswood on 2008-09-30
Well, can't get it to work with Flash. Probably a common problem. If anyone knows how to do it, I wouldn't mind you telling me.

---

### Post by Crafty Kisses on 2008-09-30
Post the results of > lsusb, and see if it's on the list.

---

### Post by danmeetswood on 2008-09-30
```
dan@dennis:~$ lsusb
Bus 004 Device 002: ID 0c45:62c0 Microdia 
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:00e1 Microsoft Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
```
The webcam works with everything but Flash programs. So it being recognized isn't the problem.

---

### Post by Crafty Kisses on 2008-09-30
Like what kind of flash programs, like Stickam?

---

### Post by danmeetswood on 2008-09-30
Yeah, Stickam, live.yahoo, anything on firefox that runs through flash, you know?

---

### Post by danmeetswood on 2008-09-30
anybody?

---

### Post by ewan86 on 2008-10-04
IM just reading up on webcam issues as I can't get mine to work at all and I noticed yours is a microdia as well. How did you get it to work??

mine is: Bus 001 Device 003: ID 0c45:6130 Microdia

thanks for any help, sorry cannot help with your issue as I am a complete ubuntu virgin!!

---

