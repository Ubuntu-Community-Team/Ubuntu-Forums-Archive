---
title: "How to make C program in ubuntu?"
date: 2016-12-03
forum: Programming Talk
---

### Post by 1ritesh on 2016-12-03
Hello,
How to make C program in ubuntu?

---

### Post by howefield on 2016-12-03
Thread moved to the "*Programming Talk*" forum.

---

### Post by 1ritesh on 2016-12-03
ok, where  to write c programe?

---

### Post by kpatz on 2016-12-03
Here's a tutorial: [http://www.improgrammer.net/how-to-write-c-program-in-ubuntu/](http://www.improgrammer.net/how-to-write-c-program-in-ubuntu/)

But in a nutshell, you'll need build-essential, which will give you the C compilers and libraries:

```
sudo apt-get install build-essential
```

Then you'll use an editor to create your code, such as gedit, or in the terminal, vi or nano.

```
gedit myprog.c &

...or...

nano myprog.c

...or...

vi myprog.c
```

Save your code as a .c file (for our example let's call it myprog.c), and to compile it, in a terminal:

```
gcc -o myprog myprog.c
```

If it compiles without errors, run it in the terminal with:

```
./myprog
```

You can also create a program in C++ by giving the file a .cpp suffix instead of .c, and compiling it using g++ instead of gcc.

---

### Post by 1ritesh on 2016-12-05
what to do next for compiling and output?[ATTACH=CONFIG]272551[/ATTACH]

---

### Post by mörgæs on 2016-12-05
From the post above:

> **kpatz said:**
> ...to compile it, in a terminal:

```
gcc -o myprog myprog.c
```


---

### Post by 1ritesh on 2016-12-05
not working...

---

### Post by lisati on 2016-12-05
> **1ritesh said:**
> not working...

From the display in the screenshot in your previous post, exit the editor with Ctrl+X, then use the gcc command.

---

### Post by 1ritesh on 2016-12-08
hello what to do after saving it is not compiling And running?
gcc -o myprog myprog.c

what does pid mean here??

please tell steps

---

### Post by karl96 on 2016-12-08
pid means process id.

By the looks of it you've got it the wrong way?

```
 gcc myprog.c -o myprog 
```

---

### Post by spjackson on 2016-12-08
There is no functional difference between these two
```

gcc -o myprog myprog.c
gcc myprog.c -o myprog

```
The message in your 3rd screenshot is because you are opening the source file with nano when you already have it open in nano. This has got nothing to do with C or programming; if you edit the same file twice at the same time you may get a warning from your editor.

---

### Post by karl96 on 2016-12-08
Agreed, didn't notice that first time looking.

GCC should still find the source file though shouldn't it? As long as it is saved.

---

### Post by 1ritesh on 2016-12-08
nothing happen

---

### Post by kpatz on 2016-12-08
When you run **gcc -o myprog myprog.c** it just compiles and links the program to create a binary called myprog.

To run it, enter this in the terminal:
```
./myprog
```

---

### Post by 1ritesh on 2016-12-09
hello,
the last code was working by run command
how to write addition program and save it?

---

### Post by karl96 on 2016-12-09
Do exactly the same thing, by the looks of it the issue is you haven't actually told your program to print the results to the screen. I would tell you how but i'll leave that to you as a learning exercise :)

---

### Post by 1ritesh on 2016-12-17
hello,
this is my new addition program how to run it and compile?[ATTACH=CONFIG]272740[/ATTACH]

---

### Post by lisati on 2016-12-17
> **1ritesh said:**
> hello,
this is my new addition program how to run it and compile?
The same way as described in post 4 of this thread.

---

### Post by 1ritesh on 2016-12-20
Hello when i write code for two sum of number it show error here it is[ATTACH=CONFIG]272775[/ATTACH]

---

### Post by lisati on 2016-12-20
You need to use the name of the saved file in place of "myprog.c" in the gcc command, and adapt the name of the output file accordingly.

---

### Post by 1ritesh on 2016-12-20
i have done not working showing error

---

### Post by kpatz on 2016-12-20
You named it myprog1.c, not myprog.c.  So to compile it use the command:```
gcc -o myprog1 myprog1.c
```
and to run it, use```
./myprog1
```

---

