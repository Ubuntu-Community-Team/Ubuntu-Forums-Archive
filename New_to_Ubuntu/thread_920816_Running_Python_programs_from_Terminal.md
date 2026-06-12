---
title: "Running Python programs from Terminal"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by GeoffreyBernardo on 2008-09-15
If the program file (e.g. hello.py) is saved in the default folder (e.g. /home/user), then the program can be run in the Terminal by simply typing **python hello.py**.

But, if the program file is stored in some other folder, the program does not run when you type in the above.

What is the solution?

I will appreciate any help. Thank you.

---

### Post by anotherdisciple on 2008-09-15
You need to make it 
```
/path/to/file/hello.py
```

---

### Post by Mornedhel on 2008-09-15
This is because you are in your home folder by default when you start a terminal. Either type the entire path :

python /path/to/your/file.py

or go to the relevant folder :

cd /path/to/your
python file.py

You should probably check out some shell tutorials.

---

### Post by anotherdisciple on 2008-09-15
My signature has a "Terminal For Beginners" link... it will explain all of this in a simple way. Give it a try.

---

### Post by GeoffreyBernardo on 2008-09-15
Thanks Guys! I got it right!

---

### Post by anotherdisciple on 2008-09-24
Good! Can you mark this thread as solved please?

---

### Post by billgoldberg on 2008-09-24
> **anotherdisciple said:**
> Good! Can you mark this thread as solved please?

It's not good to ask this for old threads.

I just wasted 1 minute reading this thread because of that.

---

### Post by anotherdisciple on 2008-09-24
> **billgoldberg said:**
> It's not good to ask this for old threads.

I just wasted 1 minute reading this thread because of that.

Whoops... didn't realize it was an old thread... I was just going through my posts to see if anyone replied.

I'm trying to get as many people as I can in the habit of doing this so that people don't waste minutes reading solved threads. Sorry though.

---

