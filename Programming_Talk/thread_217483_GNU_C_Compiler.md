---
title: "GNU C Compiler"
date: 2006-07-17
forum: Programming Talk
---

### Post by ThaDoctor99 on 2006-07-17
Hi, The GNU C Compiler is working like the other GNU compilers with 

path/to/file.something -o file.out
and then 
path/to/file/out.something ?
Right ?
I cant do those fancy code blocks... :-(

Greetings Tobias

---

### Post by thumper on 2006-07-17
Is there a question here?

If just typeing stuff in quickly use (code)stuff(/code) but use square brackets.

---

### Post by Note360 on 2006-07-17
Pretty much.

---

### Post by ThaDoctor99 on 2006-07-17
Okey let me clear the question.
How do the GNU C Compiler work ?

Greetings.

---

### Post by tzulberti on 2006-07-17
g++ file.cpp -o file
./file

---

### Post by ThaDoctor99 on 2006-07-19
What about if it is not a C++ program ?

---

### Post by mvaniersel on 2006-07-19
> What about if it is not a C++ program ?

```

gcc file.c -o file
./file

```

---

### Post by HolyJoe on 2006-07-19
I cannot get ur means...

If u want to compile a C program, the following is "hello world" program in C:

/*file: main.c*/
#include <stdio.h>
int main(int argc, char *argv[]) {
    printf("hello world\n");
};

then call gcc to complie ur program:
$gcc -Wall -o main main.c

---

### Post by ThaDoctor99 on 2007-03-17
What about recommending the -ansi also ? I use this all the time while  compiling know, even though I am more liking lisp :-) one of those insane language where you do something a lot different from what almost every other language as doing, but I am better at perl, just need to know some of the more advanced thing...
:-)

besides c++ is way cooler, there are some things in c++ that is pretty neat, but C isn't to terrible.

---

