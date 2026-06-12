---
title: "How to learn c."
date: 2014-12-18
forum: Programming Talk
---

### Post by Mojume_Azuka_Emman on 2014-12-18
Hi everyone,i just installed ubuntu 14.04 os. I'm new to ubuntu and i want to learn how to code in the c language. How do i go about i? I used bloodshed dev c++ with a software wine but it doesn't work properly. I can't find a c compiler. Help please!!!!!!!

---

### Post by Elfy on 2014-12-18
*Thread moved to **Programming Talk**.*

Have a look at [http://ubuntuforums.org/showthread.php?t=1766253](http://ubuntuforums.org/showthread.php?t=1766253)

---

### Post by flaymond on 2014-12-19
I believe every Ubuntu and Linux distros come with gcc compiler. If it's not available to you, use this command to install it


```
sudo apt-get install gcc
```


You can try using only text editor and a compiler (gcc) to make and run your program.

Try this to  if you want use text editor -

1. Open text editor 
2. Type this : 

```
 #include <stdio.h>

main()

{
  printf("Hello, world!\n");

}


```

3. Save it in your home directory as hello.c
4. Open Terminal, and type cd (This will make you go to home directory)
5. Type gcc <yourfilename> (in this case hello.c)
6. The gcc <yourfilename> command will compile the code in the hello.c and make it as executable. (It will create the compiled code as a.out executable file)
7. Type ./a.out
8. It will print Hello World and that mean your compiling is done and run without errors.


or if you want use an IDE that make your life easy to compile -



If me, I would not prefer using BloodShed Dev IDE because it's already ***outdated and discontinued.***

 I prefer you to try Code::Blocks IDE (you can use both C and C++ programming on it) because it user friendly and easy to set up. You also should learn some basics using Bash Shell (Terminal). I learning Python 2 and found it easy....(still stuck at OOP)...if you new to programming...try something 'easy' first. C/C++ is far more hard because those are 'engine-and-metal' programming language...but..a lot of people today can make C/C++ as their first language because a lot of learning sources out there. :KS

I prefer Code::Blocks to use for your IDE (it's light)
Eclipse for Java and C/C++(You can do much more in this, but it's very heavy)
or Geany for simple IDE.

You can download 3 of these IDE using Ubuntu Software Center and view the description to make you choosing more easy.

---

### Post by Darth Riker on 2014-12-19
> **InterProg said:**
> I believe every Ubuntu and Linux distros come with gcc compiler. If it's not available to you, use this command to install it


```
sudo apt-get install gcc
```





Hmm. Wouldn't it be better to just do:

```

sudo apt-get install build-essential

```

Anyway - this is just repeating information that can be found from the link Elfy posted - [http://ubuntuforums.org/showthread.php?t=1766253](http://ubuntuforums.org/showthread.php?t=1766253) . Make sure to click on all the links in the post and have a read.

---

### Post by flaymond on 2014-12-19
Thanks for your act to improve my comment :KS. I'm new to Ubuntu, I don't know much yet, but hope will be more than that..someday ;).

---

### Post by David_Camp on 2014-12-22
There are a lot of C tutorial you can find on Google.com. Easy to find.

---

### Post by Gustaf_Alhll on 2014-12-27
Start off like me, buy a book.
The only difference between us is that I started off with Java while you want to start of with C. Both works fine, but if you aren't familliar with any sort of programming language, you should try Python first.
Then again, as David Camp said:
> There are a lot of C tutorial you can find on Google.com.
But remember, internet is a dangerous place. So be sceptic.

---

### Post by ofnuts on 2014-12-27
> **Gustaf_Alhll said:**
> Start off like me, buy a book.

+1

To the OP, there is programming and there are programming languages. Only programming counts. Languages are just tools. You'll learn plenty of languages in your programming career (one every two to three years....).

Of course you cannot learn programming without learning at least one language, but some languages are easier to learn and are better at covering technicalities that get in the way when you are a beginner (memory management, in particular). AS said by many here, Python is pretty good for this.

---

