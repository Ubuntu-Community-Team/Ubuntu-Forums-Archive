---
title: "Questions on Geany."
date: 2007-10-25
forum: Programming Talk
---

### Post by eXeCuTeR+ on 2007-10-25
I downloaded Geany and I found 3-4 bugs:
1. When I press Compile, it writes:
```

gcc -Wall -c "untitled.c" (in directory: /home/lsr/Desktop)
untitled.c:5: warning: return type of ‘main’ is not ‘int’
Compilation finished successfully.

```
There isn't an error in my code, I just typed void main() - it's not an error.
And don't tell me to use int main() 'cause I prefer void main()
It writes this error every time for any code I type.
BTW, Why doesn't it open the DOS window when I compile/execute it?

2. When I press Execute, it writes down:
```

22:47:07: Failed to execute /home/lsr/Desktop/untitled (make sure it is already built)

```
What the...? Why does it write it?
It always shows the same error for any code.

3. Why doesn't the conio.h library work?
I wanted to use getch();
There's probably another library and a function that does the trick, if there's please tell me the name of the library and function.
if there isn't, why does it give me an error?

The conio.h and getch error if you compile it:
```

gcc -Wall -c "untitled.c" (in directory: /home/lsr/Desktop)
untitled.c:3:19: error: conio.h: No such file or directory
untitled.c:6: warning: return type of ‘main’ is not ‘int’
untitled.c: In function ‘main’:
untitled.c:16: warning: implicit declaration of function ‘getch’
Compilation failed.

```
4. It's not a bug but still...
How do I make my program execute/compile - I mean to see the DOS window and see the results of my code.

Please help ASAP.
Thanks.

---

### Post by eXeCuTeR+ on 2007-10-25
Please help me guys. :'(

---

### Post by eXeCuTeR+ on 2007-10-25
Help Please =[

---

### Post by eXeCuTeR+ on 2007-10-25
Omg Please Help Me!!!

---

### Post by eXeCuTeR+ on 2007-10-25
Please guys im crying :'(

---

### Post by hikaricore on 2007-10-25
Calm yourself, if no one has answered your post, it means that no one who has seen it so far knows what Geany is.

Perhaps you should post some info and links about this program so people don't need to go out of their way searching for it.  ^_^

---

### Post by eXeCuTeR+ on 2007-10-25
How do I do it with KDevelop then?

---

### Post by hikaricore on 2007-10-25
I think this thread might be better recieved in the Programming Talk forum: [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

So I'm moving it over.  Best of luck.  ^_^

---

### Post by LaRoza on 2007-10-25
1. It is a warning, use "int main(void)" or "int main(int argc,char ** argv)". Don't be sloppy. Also, there is no DOS window in Linux.

2.getch() is not standard. Write your own, or find an alternative in the standard library.

3. It doesn't run because it isn't linked.

The rest will be answered once you fix your code.

You bumped your post many times in four hours. That is not a good way to get an answer. How are people supposed to know the post in unanswered if it has not 0 replies? Then Unanswered Posts Team, of which I am a member, uses the forums unanswered posts query to help people. Excessive and premature bumping makes our job hard.

Don't assume bugs. Your information gave error messages from gcc, and worked perfectly. Several bugs did exist, but that was in your code, not Geany or gcc's.

---

### Post by LaRoza on 2007-10-25
Do this:

Create a new file, named hw.c, and enter this text:

[php]
#include <stdio.h>

int main(int argc,char ** argv)
{
    puts("Hello world");
    return 0;
}
[/php]

Open a terminal in the same directory, type:

```

gcc hw.c -o hw

```

It should be compiled.

To run:

```

./hw

```

I am not familar with Geany, although I just downloaded the Windows version to try out, because I happened to be using Windows at the time.

Usually, IDE's have a "compile" and "build" command. I imagine Geany does too.

---

### Post by LaRoza on 2007-10-25
> **eXeCuTeR+ said:**
> 
And don't tell me to use int main() 'cause I prefer void main()

BTW, Why doesn't it open the DOS window when I compile/execute it?

When I press Execute, it writes down:
```

22:47:07: Failed to execute /home/lsr/Desktop/untitled (make sure it is already built)

```



Your post was long, and had much to address, so here I am again.

0. If your prefer to violate rules of the language, don't complain.

1. Because you didn't link it, and your are not using DOS.

2. It is not built. I imagine a file with a .o extension was created, link it "gcc fileName.o".

---

### Post by eXeCuTeR+ on 2007-10-25
I have to type gcc name.c -o name all the time?
Geany has a compile and execute options, but the execute option seems to be not working.
It gives this:
04:08:13: Failed to execute /home/niv/Desktop/untitled (make sure it is already built)
How do I link it?


Sorry for the spam posts, that was my brother, we are sharing this account.


BTW,
Do you guys know a built IDE?

BTW 2 (lol),
My brother wasn't actually crying :O

---

### Post by LaRoza on 2007-10-25
> **eXeCuTeR+ said:**
> I have to type gcc name.c -o name all the time?
Geany has a compile and execute options, but the execute option seems to be not working.
It gives this:
04:08:13: Failed to execute /home/niv/Desktop/untitled (make sure it is already built)
How do I link it?


Sorry for the spam posts, that was my brother, we are sharing this account.


No, just use the arrow keys.

I already said how to link.

gcc <file> -o <name>    == <file> will be compiled and named <name>

gcc -Wall ....                   == strict warnings
 
gcc -c <file>                   == <file> will be compiled, but not linked (Geany did this), file named <file>.o will be the result.

gcc <file>                       == <file> will be compiled, linked.

---

### Post by LaRoza on 2007-10-25
> **eXeCuTeR+ said:**
> 
BTW,
Do you guys know a built IDE?

BTW 2 (lol),
My brother wasn't actually crying :O

A built IDE? Geany is built, unless you have the source and haven't compiled it.

Get yourself your own account, and then work on this. I'll assume any further posts are your brothers'.

---

### Post by eXeCuTeR+ on 2007-10-25
> **LaRoza said:**
> No, just use the arrow keys.

I already said how to link.

gcc <file> -o <name>    == <file> will be compiled and named <name>

gcc -Wall ....                   == strict warnings
 
gcc -c <file>                   == <file> will be compiled, but not linked (Geany did this), file named <file>.o will be the result.

gcc <file>                       == <file> will be compiled, linked.
All right.
I understand how to link it,
but I'm still looking for a built IDE so I could just press Execute and it'll execute it, with no "terminal-typing".
Is there a kind of this IDE?

---

### Post by LaRoza on 2007-10-25
> **eXeCuTeR+ said:**
> 
but I'm still looking for a built IDE so I could just press Execute and it'll execute it, with no "terminal-typing".
Is there a kind of this IDE?

Yes, Geany and all IDE's. I am not familiar with Geany's interface, so I did what Geany does for you. Look at your errors, they give the command that was issued. 

If you want to learn how to use Geany, do it. I don't use it. I work through the command line.

---

### Post by eXeCuTeR+ on 2007-10-25
Whoops! Fixed it!
Works perfectly!

Thank you all.

---

### Post by LaRoza on 2007-10-25
> **eXeCuTeR+ said:**
> 

Simple code, wonder why it doesn't work.

BTW,
How can I fix this 'Execute' thing? Would you please help me with that?

The code is not good, don't assume the size of a char. (You sovled it, your forgot to return.)

I don't know Geany, use the documentation. [http://geany.uvena.de/files/geany-0.11.pdf](http://geany.uvena.de/files/geany-0.11.pdf) The manual is also installed with Geany.

---

### Post by LaRoza on 2007-10-25
> **eXeCuTeR+ said:**
> 
Thank you all.

Unlike you, I am a single person :-)

No problem.

---

### Post by eXeCuTeR+ on 2007-10-25
> **LaRoza said:**
> Unlike you, I am a single person :-)

No problem.

Sorry mate ;)
1 Last thing,
from now on, my brother isn't gonna use my account, lol :P

P.S
Are you a C programmer?

---

### Post by LaRoza on 2007-10-26
> **eXeCuTeR+ said:**
> 
P.S
Are you a C programmer?

I am not limited to one language, but yes, I do use C.

---

### Post by TekNullOG on 2008-05-15
> **LaRoza said:**
> Do this:

Create a new file, named hw.c, and enter this text:

[php]
#include <stdio.h>

int main(int argc,char ** argv)
{
    puts("Hello world");
    return 0;
}
[/php]

Open a terminal in the same directory, type:

```

gcc hw.c -o hw

```

It should be compiled.

To run:

```

./hw

```

I am not familar with Geany, although I just downloaded the Windows version to try out, because I happened to be using Windows at the time.

Usually, IDE's have a "compile" and "build" command. I imagine Geany does too.

I had a similar problem with Geany so I tried to run it from a terminal as you mention here.

Compiling it with gcc seems to work great but when I try to run it, i get a permission error.

> sudo: unable to execute ./exemple: Permission denied


I double checked and I have execute permission with the file and folder.

What might be the cause?

Thanks

---

### Post by TekNullOG on 2008-05-15
I got it to work. I moved it to another folder and I have no permission errors now.

This is just really weird.

---

