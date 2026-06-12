---
title: "[SOLVED] &amp;quot;python hello.py&amp;quot; does not run."
date: 2009-01-08
forum: Programming Talk
---

### Post by kapok on 2009-01-08
I have been running my computer on Ubuntu for about a month now. I must say, I am quite impressed with how well everything works. Most obstacles I have encountered could be conquered by simply copying and pasting command lines i found here. It has worked so well that I am inspired to contribute to the community myself, and because of that I have decided to take up programming. My question is:


when i type "python" into the command prompt, python comes up.
when i type "print("Hello World")", it shows "Hello World"
but when i save that command to a text file (named hello.py) and type "python hello.py", I receive the error: python: "can't open file 'hello.py': [Errno 2] No such file or directory"

All guides I can find on the Internet say this should simply work. What am I doing wrong?

---

### Post by aszxcv on 2009-01-08
type python and a space

then drag and drop your script in the terminal

---

### Post by Exershio on 2009-01-08
open up terminal, change to the directory with the **hello.py**, and execute this command:
> chmod +x hello.py
That will make hello.py an executable script, which allows you to "run it", in which you then just type the following into terminal whenever you want to run it:
> ./hello.py


edit: I forgot to add, you need to add this line to the beginning of your script in order for it to be able to execute, as far as I remember:

> #!/usr/bin/python

Sorry if that was a bit confusing, that's the way I normally do it :P

---

### Post by kapok on 2009-01-09
Thank you guys.
It works now that it's executable, but it still doesn't run when i just click it. Is there any way to run Python without the Terminal? Is there any way to make the file run in Python(in the Terminal) when i double click it?

I have tried adding "Python" to the top line of my program. It works, I think, but it just flashes up for a second. Is there a way to get it to stay up afterwards?

---

### Post by kapok on 2009-01-09
Also, I don't understand how programming in Linux works. If i write something in C++, can i compile it into an actual "executable" file? How? Are the languages native to Linux the only ones available to us?

---

### Post by tom66 on 2009-01-09
If you write a program in C(++) you can compile it. Use 'gcc -o *outfile* *cfile*' for C, and 'g++ -o *outfile* *cppfile*' for C++. Then, type './*outfile*' to run your program. Of course, replace *outfile*, *cfile* and *cppfile* with the respective files. You can call outfile anything, it needs no extension.

---

### Post by kapok on 2009-01-09
Thanks.
I'm excited about starting with C.

---

### Post by Reiger on 2009-01-09
> **Exershio said:**
> > #!/usr/bin/python

I'd like to suggest replacing that line with:
```

#!/usr/bin/env python

```

Not every distribution may have the python interpreter at /usr/bin/python (Ubuntu does) but the env utility is nearly always located at /usr/bin/env. (Or so some kind soul once told me before.)

Anyway the point is that this way the shell/environment will find out which 'python' to run. Works also for other interpreters:
```

#!/usr/bin/env perl

```

@OP: you can only obtain executables "in the C/C++ sense" from  a source which is compiled to machine-lanaguage. However even after 'simply compiling' you will still make it executable just as if it were a python script. Read/Write only files will only ever be read/written as long as your file system is healthy.

---

