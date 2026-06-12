---
title: "Copy files and keep GTK updated?"
date: 2009-06-11
forum: Programming Talk
---

### Post by Commander_Bob on 2009-06-11
I am writing a program in python that copies files to my mp3 player. I need a way for it to keep the GUI updated while it copies the song. The solution I came up with was to use threads and use a while loop to wait for the thread to finish. This seems like a terrible way to do it as it polls to see if the thread is done, wasting CPU time.

Is there a better way to do this?

My code is attached. This is my first program with GTK/python so if any thing else is poorly coded please tell me.

Thanks,
Justin Rajewski

---

### Post by froggyswamp on 2009-06-11
> 
use a while loop to wait for the thread to finish
(In Java) all the code that must be run in another thread is put into a separate method and at the end of that method (just before exiting) you can call a notification method that tells your program that the thread is done executing.

---

### Post by Commander_Bob on 2009-06-11
Could you give me a simple example on how to do that? What do you mean by notification method?

Thanks,
Justin

---

