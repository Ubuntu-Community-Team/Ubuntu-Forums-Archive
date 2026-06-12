---
title: "gcc can't find file"
date: 2011-12-22
forum: Programming Talk
---

### Post by DanWebb314 on 2011-12-22
[SIZE=2]I am new to Ubuntu Linux gcc.  I have writen c++ programs for windows.  I can't get off the ground with gcc.  If I use gedit, do I store the hello.c in document?  If so, why does:  [/SIZE]
[SIZE=2] [/SIZE][SIZE=2]gcc first.c -o first  [/SIZE]
[SIZE=2] [/SIZE][SIZE=2]not work.  It can't find the file.  [/SIZE]

---

### Post by ubix on 2011-12-22
[LIST=1]
[*] Is it C++ or C file; for C files you use **_gcc_** command, for C++ **_g++_**
[*] Please post exactly the command you are using
[*] Show us the output of **_ls -la_** in the directory where you are compiling; hopefully it is not too crowded.
[*] Also tell us what is the error message
[/LIST]

---

### Post by Petrolea on 2011-12-22
> **DanWebb314 said:**
> [SIZE=2]I am new to Ubuntu Linux gcc.  I have writen c++ programs for windows.  I can't get off the ground with gcc.  If I use gedit, do I store the hello.c in document?  If so, why does:  [/SIZE]
[SIZE=2] [/SIZE][SIZE=2]gcc first.c -o first  [/SIZE]
[SIZE=2] [/SIZE][SIZE=2]not work.  It can't find the file.  [/SIZE]

You must run the command when you're in the same directory as the file. You probably used some IDE on Windows that took care of that.

---

### Post by lisati on 2011-12-22
*Thread moved to **Programming Talk**.*

Suppose you have the following c program saved in file hello.c: 
```

#include <stdio.h>
int main(void)
     {
     printf("Hello world!\n");
     return 0;
     }

```

Assuming you've just saved the file, you would use something like this to compile it:
```

gcc hello.c -o hello

```
Assuming it compiles correctly, you'd then need to run it with something like this:
```

./hello

```

EDIT/Disclaimer: the code shown is not intended as an example of good programming technique; it is included for illustrative purposes only.

---

### Post by |{urse on 2011-12-22
you need to issue the command from the directory in which you saved your source file. Or specify the absolute path to the source.


Edit: D'oh, someone covered that above

---

### Post by ubix on 2011-12-22
Enter the following in terminal:

```
mkdir my-c-test
cd my-c-test
echo "int main(void){}" > test1.c
gcc test1.c -o test1
ls -l
```


You should now see something like:

```

-rwxr-xr-x 1 you you 8335 2011-12-22 20:10 test1
-rw-r--r-- 1 you you   17 2011-12-22 20:10 test1.c

```

---

### Post by trent.josephsen on 2011-12-22
> **lisati said:**
> EDIT/Disclaimer: the code shown is not intended as an example of good programming technique; it is included for illustrative purposes only.

That's for sure -- you used Whitesmiths! ;)

---

### Post by DanWebb314 on 2011-12-24
Thank you!
cd Documents
makes a difference. Now I have compiled several 'hello world' programs.

This question is just about solved.

Should this question start a new thread?

if i change "hello world" to "hello world\n",  It does not like the escape sequence?

---

### Post by Petrolea on 2011-12-24
> **DanWebb314 said:**
> Thank you!
cd Documents
makes a difference. Now I have compiled several 'hello world' programs.

This question is just about solved.

Should this question start a new thread?

if i change "hello world" to "hello world\n",  It does not like the escape sequence?

That would mean newline. If you want to actually write \n, you'll have to write \\n.

---

### Post by DanWebb314 on 2011-12-24
> **Petrolea said:**
> That would mean newline. If you want to actually write \n, you'll have to write \\n.
Yes I want new line.  Why does the escape sequence '\n' not work?

---

### Post by DanWebb314 on 2011-12-24
What is the difference between
 #include <iostream>
and
 #include <stdio.h>

g++ and gcc have a preference. ?

---

### Post by trent.josephsen on 2011-12-24
<iostream> can only be used in C++.

<stdio.h> should only be used in C.

(If you would find it convenient to use a <stdio.h> function in C++, you should #include <cstdio> instead, which doesn't pollute the primary namespace.)

Edit:  wait, am I misremembering the namespace thing?  Somebody please correct me if I'm mistaken

---

### Post by Arndt on 2011-12-24
> **DanWebb314 said:**
> Yes I want new line.  Why does the escape sequence '\n' not work?

In what way does it not work? What happens instead?

---

### Post by DanWebb314 on 2011-12-25
[SIZE=2]when I compile I get this error

htest.c:5:10: warning: unknown escape sequence" '\h' [enabled by default][/SIZE] [SIZE=2]

when I execute, the h gets printed and does not cause a return.[/SIZE]

---

### Post by fdrake on 2011-12-25
> **DanWebb314 said:**
> [SIZE=2]when I compile I get this error

htest.c:5:10: warning: unknown escape sequence" '\h' [enabled by default][/SIZE] [SIZE=2]

when I execute, the h gets printed and does not cause a return.[/SIZE]

you mean "\n" for a new line?
can you post here the line of code containing the "\h"

---

### Post by trent.josephsen on 2011-12-25
For the love of all that is holy, **POST CODE**.  When all you give us is error messages and contextless questions, the best we can do is guess.

---

### Post by DanWebb314 on 2011-12-25
> **fdrake said:**
> you mean "\n" for a new line?
can you post here the line of code containing the "\h"

OMG  yes!  Change \h to \n and it works!  I can't believe I didn't see my mistake.

---

### Post by DanWebb314 on 2011-12-25
> **trent.josephsen said:**
> For the love of all that is holy, **POST CODE**.  When all you give us is error messages and contextless questions, the best we can do is guess.
If you could tell me how to POST CODE, I will.  Where does it tell you how to post code and similar info?  I have looked and can't find it.  After your reply, I will no doubt mark this thread solved!

---

### Post by fdrake on 2011-12-25
> **DanWebb314 said:**
> If you could tell me how to POST CODE, I will.  Where does it tell you how to post code and similar info?  I have looked and can't find it.  After your reply, I will no doubt mark this thread solved!

link [http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

on the text field you see "#" simbol . Select your cod and click on it and you will see the [code] tags around it. or you can just type them by hand at the beginning and at the end.

---

### Post by DanWebb314 on 2011-12-25
Thank you!  I doubt I could have found that on my own.  Here is a little program I wrote.  I will post it just so I can use my new knowledge.
```

/*prime.c  --  prime number generator.*/ 
#include <stdio.h> 
#define L 3600 
int main() 
{ 
 
 int a[L], i, q, r, n=3, c=1, l; 
 a[1]=3; 
 printf("  Input limit: "); 
 scanf("%d",&l); 
 while (++c<l) 
 { 
   rz: n+=2; 
   if (n<0) return 0; 
       i=0; 
   do { q=n/a[++i]; 
    r=n%a[i]; 
      if (r==0) goto rz; 
      } 
   while (q>a[i]); 
 
      a[c]=n; 
      printf(" %d  %d\n",c+1,n); 
 } 
 return 0; 
}


```Yes, it has a poor use of a goto.

This puppy is going to be set to SLOVED!

---

