---
title: "Very Simple Python Script problem"
date: 2006-07-16
forum: Programming Talk
---

### Post by Skia_42 on 2006-07-16
Okay, I have a very simple python script and I do not know how to run it in the terminal.
The script (x.py) is this:
> 
def printParity(x):
  if x%2 == 0:
    print x, "is even"
  else:
    print x, "is odd"
  
  if x > 0:
    print x, "is positive"
  else:
    print x, "is negative"
Since printParity(x) is a function, I should be able to replace x with a value and get a response. But I don't know how to "load" the core file.
I tried:
> 
skye@ubuntu:~/Desktop$ python x.py
skye@ubuntu:~/Desktop$ python
Python 2.4.3 (#2, Apr 27 2006, 14:44:20)
[GCC 4.0.3 (Ubuntu 4.0.3-1ubuntu5)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> printParity(20)
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
NameError: name 'printParity' is not defined


---

### Post by jordilin on 2006-07-16
First of all, execution permission:
```
chmod +x nameofprogram.py
```
Secondly, you have to put the line #!/usr/bin/python at the top of your source file.
Thirdly just run the program by:
```
./nameoftheprogram.py
```

---

### Post by Skia_42 on 2006-07-16
> **jordilin said:**
> First of all, execution permission:
```
chmod +x nameofprogram.py
```
Secondly, you have to put the line #!/usr/bin/python at the top of your source file.
Thirdly just run the program by:
```
./nameoftheprogram.py
```

The permission modification makes sense.

The Line "#!/usr/bin/python" is a comment correct? If so then it is not needed but it's considered god form.

I tryed to run the script but it simply did this:
> 
skye@ubuntu:~/Desktop$ ./x.py
skye@ubuntu:~/Desktop$


---

### Post by ifokkema on 2006-07-16
Might just be me, but your script seems nothing more than a function declaration. There's no call to the function in the sample code you sent, so there's no output. If you've provided the entire script to us, maybe you should add
```
printParity(5)
```
to the end or so.

---

### Post by Ragazzo on 2006-07-16
> **Skia_42 said:**
> The permission modification makes sense.

The Line "#!/usr/bin/python" is a comment correct? If so then it is not needed but it's considered god form.

I tryed to run the script but it simply did this:

The line #!/usr/bin/python is called a shebang. It tells which program to run the script with.

---

### Post by Skia_42 on 2006-07-16
Yes that works, thank you. I was trying to make it do something that It wasn't made to do. Thank you for your help.

---

### Post by Skia_42 on 2006-07-16
> **Ragazzo said:**
> The line #!/usr/bin/python is called a shebang. It tells which program to run the script with.
Okay, but how does it do that when the entire line is a comment and ignored during interpretation?

---

### Post by Ragazzo on 2006-07-16
> **Skia_42 said:**
> Okay, but how does it do that when the entire line is a comment and ignored during interpretation?

It is ignored by the Python interpreter. It's the shell that reads it.

---

### Post by ifokkema on 2006-07-16
> **Skia_42 said:**
> Okay, but how does it do that when the entire line is a comment and ignored during interpretation?
It may be a comment to your scripting language, but when executing the file, bash reads out the shebang line to tell which interpreter to use.
[EDIT]Just got beaten to it. Can't get your answers faster than this :)[/EDIT]

---

### Post by Skia_42 on 2006-07-16
> **Ragazzo said:**
> It is ignored by the Python interpreter. It's the shell that reads it.
Okay, thanks. I just wanted to make sure I understood comments. So the exclamation point tells the shell to read it?

---

### Post by ifokkema on 2006-07-16
> **Skia_42 said:**
> Okay, thanks. I just wanted to make sure I understood comments. So the exclamation point tells the shell to read it?
It's specifically the #!<path_to_interpreter> that does the trick. If you write a PHP executable, you still use #!, while comments in PHP are usually done by using //.

---

### Post by Ragazzo on 2006-07-16
never mind...

---

### Post by digimars on 2006-07-16
I've been taught to use 

```

#! /usr/bin/env python

```
instead.  Supposedly it offers better portability.

---

### Post by Skia_42 on 2006-07-16
Thank you both for your help. I love the ubuntu forum community, you don't get flamed.

---

### Post by christhemonkey on 2006-07-16
I also have learnt to use 
```
#! /usr/bin/env python
```

Though normally i dont bother, i just type into a terminal:
```
python mypythonscript.py 
```

---

### Post by ifokkema on 2006-07-16
> **Skia_42 said:**
> Thank you both for your help. I love the ubuntu forum community, you don't get flamed.
Ur welcome 8)

---

