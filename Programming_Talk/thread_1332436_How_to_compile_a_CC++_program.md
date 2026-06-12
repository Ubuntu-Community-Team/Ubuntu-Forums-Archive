---
title: "How to compile a C/C++ program"
date: 2009-11-20
forum: Programming Talk
---

### Post by Dark Sorrow on 2009-11-20
I have written a simple C Hello World program using a Code::Block 8.2 IDE which i have downloaded. When ever I build my file i get **Nothing to Build** message in my Build Log Tab.
When i run then i get the following error message.
> sh: /home/ishaankarnik/HelloWorld: Permission denied

Press Enter to continue.

---

### Post by Arndt on 2009-11-20
> **Dark Sorrow said:**
> I have written a simple C Hello World program using a Code::Block 8.2 IDE which i have downloaded. When ever I build my file i get **Nothing to Build** message in my Build Log Tab.
When i run then i get the following error message.

I don't know how your IDE works, but it seems there is a program HelloWorld which isn't executable. That may be because there were errors during an earlier compilation/linking and the resulting file wasn't removed.

Use a shell to see if this is the case. If so, remove the file and try again.

---

### Post by Dark Sorrow on 2009-11-20
I have downloaded and installed several C/C++ IDE like Code::Block, Anjuta IDE and KDevelop from Add/Remove program.
I have written a simple hello world program but i am unable to compile it.
In Code::Block IDE the problem i face after i build or run is explained in the following thread.
[http://ubuntuforums.org/showthread.php?p=8352802#post8352802](http://ubuntuforums.org/showthread.php?p=8352802#post8352802).
In Anjuta IDE their is no effect after i execute program.
I even tried to compile using the terminal by giving the complier name gc/gc++ and then the absolute path of my file.
The files i created using IDE are C source code(text/x-csrc).

---

### Post by Slimbo on 2009-11-20
Is [COLOR=DarkGreen]build-essential[/COLOR] installed ?

---

### Post by Can+~ on 2009-11-20
> I even tried to compile using the terminal by giving the complier name gc/gc++ and then the absolute path of my file.

What was the output of this one?

---

### Post by cariboo on 2009-11-20
Please don't double post on the same subject, I have merged your two threads.

---

### Post by Dark Sorrow on 2009-11-20
> **Can+~ said:**
> What was the output of this one?

(1)For the files i created using IDE i get the following error>  
[b]File Format not recognized
collect2: ld returned 1 exit status[/b]. However the file type shown in property window is **C source code (text/x-csrc)**.
(2)For the files i created using gEdit i get the following error
> [b]/tmp/ccKgLpYn.o:(.en_frame+0x11): undefined reference to '__gxx_personality_v0
collect2: ld returned 1 exit status[/b].
Here the file type is **C++ source code(text/x-c++src)**.

---

### Post by Dark Sorrow on 2009-11-20
> **Slimbo said:**
> Is [COLOR=DarkGreen]build-essential[/COLOR] installed ?

How do i find if build-essential is installed? If not installed then how should i install.

---

### Post by dwhitney67 on 2009-11-20
> 
/tmp/ccKgLpYn.o.en_frame+0x11): undefined reference to '__gxx_personality_v0
collect2: ld returned 1 exit status.
Here the file type is C++ source code(text/x-c++src).

I bet you are using 'gcc' to compile a C++ source module.  Use 'g++' instead, or alternatively link with the stdc++ library.

Option 1:
```

g++ module.cpp

```

Option 2 (which is not often used):
```

gcc module.cpp -lstdc++

```

P.S.  To install build-essential:
```

sudo apt-get install build-essential

```
This instruction is CLEARLY indicated in the stickies.

---

### Post by Dark Sorrow on 2009-11-20
> **dwhitney67 said:**
> I bet you are using 'gcc' to compile a C++ source module.  Use 'g++' instead, or alternatively link with the stdc++ library.

Option 1:
```

g++ module.cpp

```

Option 2 (which is not often used):
```

gcc module.cpp -lstdc++

```

P.S.  To install build-essential:
```

sudo apt-get install build-essential

```
This instruction is CLEARLY indicated in the stickies.

But what about the first case where the file is of type Csource code (text/x-csrc). It should atleast work with **gcc** normally.

---

### Post by dwhitney67 on 2009-11-21
> **Dark Sorrow said:**
> But what about the first case where the file is of type Csource code (text/x-csrc). It should atleast work with **gcc** normally.
Yes, and it also works with 'g++'.  The convention, however, is to use 'gcc' with C code, 'g++' with C++.

---

