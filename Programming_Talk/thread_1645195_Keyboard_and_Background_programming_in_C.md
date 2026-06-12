---
title: "Keyboard and Background programming in C"
date: 2010-12-14
forum: Programming Talk
---

### Post by c2tarun on 2010-12-14
hi friends
I want to create an application that can
1. run in background
2. monitor all the keyboard activities.

and these two requirements are the two difficulties as well. I don't know how to run a program continuously in background, and how to monitor keyboard activities without hindering other processes. Can anyone guide me to some concepts that can help me.

---

### Post by dwhitney67 on 2010-12-14
Would it not have been easier to state that you want to develop a **key-logger** application so that you can snoop on other user's as they type at the keyboard?

---

### Post by c2tarun on 2010-12-14
> **dwhitney67 said:**
> Would it not have been easier to state that you want to develop a **key-logger** application so that you can snoop on other user's as they type at the keyboard?


I was actually trying to build that only, but not to snoop on other users, but to use it on my system only. Is there anything wrong?

---

### Post by PaulM1985 on 2010-12-14
> **c2tarun said:**
> I was actually trying to build that only, but not to snoop on other users, but to use it on my system only. Is there anything wrong?

Are you not sure what keys you are pressing?

---

### Post by dwhitney67 on 2010-12-14
> **c2tarun said:**
> I was actually trying to build that only, but not to snoop on other users, but to use it on my system only. Is there anything wrong?

Providing assistance to someone to develop a key-logger is a sensitive subject.  You might get some help if you Google for a sample application.

As for running an application in the background, Google for how to develop a daemon process.  Keyboard inputs surely are available via the character device driver that is loaded by the kernel.

---

### Post by c2tarun on 2010-12-14
guys if you are thinking that I am going to misuse this application then i can assure u I have no such intentions, knowing how to break a lock doesn't makes us a burglar.
I used one application of this type long time back when i was using windows. Since I m using ubuntu I looked into many things in C programming. I just wanted to make this application as a good exercise. If anyone can, then please help me. 
You guys are pretty experienced user of ubuntu and I really respect you, if I am violating any policies of this forum by asking this question then i m extremely sorry, tell me once and I'll remove this thread.
Thank you

---

### Post by worksofcraft on 2010-12-14
[xnee]("http://en.wikipedia.org/wiki/Xnee") is a Linux macro recorder that not only logs keys but also mouse activity.
It contains modules that you can include in your applications and I suspect these would provide all the functionality that you want. It is open source so if you study how it works then you will learn how it is done too :)

---

### Post by c2tarun on 2010-12-14
> **worksofcraft said:**
> [xnee]("http://en.wikipedia.org/wiki/Xnee") is a Linux macro recorder that not only logs keys but also mouse activity.
It contains modules that you can include in your applications and I suspect these would provide all the functionality that you want. It is open source so if you study how it works then you will learn how it is done too :)

Thanks, at least you trusted me :)

---

### Post by _joachim_ on 2010-12-14
The "hi friends" bit put me right off..

---

### Post by kwyto on 2010-12-15
You should use assembly, it actually quite fun and easy. "for this application at least". And you can integrate it to C.  _asm{ //assembly code }

---

