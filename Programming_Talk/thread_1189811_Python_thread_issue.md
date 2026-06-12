---
title: "Python thread issue"
date: 2009-06-17
forum: Programming Talk
---

### Post by lexe-cc on 2009-06-17
Hi,

i'm trying to write a small testing program since im quite new to python.

The program:
I connect a bluetooth device to my program using sockets. When connecting im opening 2 sockets (send & receive). 
The receive socket is used to receive data from the bluetooth device. This is done in a while clause so the function is constantly checking for new available data from the device. This function is started in a child thread so the main thread wont get blocked. (using the start_new_thread method) The function prints out any incoming data from the device in the terminal.

I can only see the output from the child thread while the main thread is put to sleep for a while. Is there any possible way to see the print output from the child thread without having to pause the main thread?

Thanks in advance!

---

### Post by lexe-cc on 2009-06-18
bump ..

---

### Post by smartbei on 2009-06-18
This sounds like a case where using select would be useful. Check out the python module select.

Using select.select, you should be able to make your program single threaded, thus solving the problem.

Another option you might want to try is to flush the stdout buffer:
```

import sys
sys.stdout.flush()

```
Do that after you print the data out. Not sure if that will work, but it's worth a try.

---

### Post by lexe-cc on 2009-06-19
Thx for your reply! ill try this when i get home :)

---

