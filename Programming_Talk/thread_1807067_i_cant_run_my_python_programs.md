---
title: "i cant run my python programs"
date: 2011-07-18
forum: Programming Talk
---

### Post by falcon12 on 2011-07-18
hey everyone im having trouble running my simple program in python im new to all of this so im sorry if this is a newbi*e *question but like i write a simple program like so:
print ("hello")
and i save it as a .py file and when i try to run it in terminal nothing happens but when i try to run it in my IDLE python shell it works just fine. also if i try to manualy locate it in terminal and tell python to run it it also works fine. so basically im asking how i can simply double click on the file and it will run with no problems?:confused:
thanks help is appreciated :)

---

### Post by TwoEars on 2011-07-18
How are you running it?

```
python script.py
``` 
should work fine.

If you want to run it through ./script.py -

```
#!/usr/bin/env python
print "hi"

```
Will work, provided you chmod +x script.py first. 
I see you're including brackets - you don't need to (nor should you) if you're using Python 2.x

---

### Post by Snowboi on 2011-07-18
Open up a terminal

cd into the directory with the .py file
Eg if its in Downloads do

```
cd /home/*username*/Downloads
```
- NOTE : CASE SENSITIVE.

then you choose to run your file with python by doing

```
python *filename*.py
```

- Replace *username* with the name of the directory.
- Replace *filename* with the name of the file.

> so basically im asking how i can simply double click on the file and it will run with no problems
You mean open it in the terminal when you double click? By default it should open it up in G-edit.

---

### Post by falcon12 on 2011-07-19
well basically im asking is there a way to double click it and the program will run automatically without going through command line just like an application like g-edit will open automatically?

---

### Post by Hairy_Palms on 2011-07-19
as TwoEars said
> #!/usr/bin/env python
print 'something'

---

### Post by TwoEars on 2011-07-19
> **Hairy_Palms said:**
> as TwoEars said

With chmod +x, of course. :)

---

### Post by Hairy_Palms on 2011-07-19
yea and that :)

---

### Post by Zugzwang on 2011-07-20
> **falcon12 said:**
> well basically im asking is there a way to double click it and the program will run automatically without going through command line just like an application like g-edit will open automatically?

One thing about the solution that Hairy_Palms and TwoEars offered: This will work, but for console I/O in your application, no window will pop up to show you the results. Thus, if your application contains a "print" command, for example, you won't see the output. Thus, you need to run your script from a terminal yourself.

If at some point, you perform GUI (graphical user interface) programming, the problem will vanish, as then you will be presenting your data in a window, which *will* be visible.

---

