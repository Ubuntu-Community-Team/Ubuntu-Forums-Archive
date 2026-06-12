---
title: "Working on C"
date: 2013-12-12
forum: Programming Talk
---

### Post by wingnut2626 on 2013-12-12
Hey guys.  Im working on learning C and I am having some trouble.  I think whats going on is that the Book that I'm using to learn this is severly outdated.  Basically I am trying to create a string, and print from the first place in the string on to the end (like reading a last name).  Here is the code:

```
#include <stdio.h>


char name[20] = "Roy Hibbert";


int position= 0;


void main(){


    while(name[position]!=' '){


        position++;
    
    }


    printf(&name[position]);


}



```


and also there is a way to do it using pointers :

```
#include <stdio.h>


char name[20] = "Derrick Rose";


char *SurnameStart = name;


void main(){
    
    while(*SurnameStart != ' '){
        
        SurnameStart++;
        
    }
    
    SurnameStart++;
    
    printf(SurnameStart);
    
}

```

Here is the warning that is generated when I attempt to compile either of these:

warning: format not a string literal and no format arguments [-Wformat-security]
  printf(SurnameStart);

What am I doing wrong?  And can someone explain to me the importance of pointers anyhow?  Not even sure why these are necessary.  Thanks in advance

---

### Post by steeldriver on 2013-12-12
Oops WRONG! see below...

---

### Post by wingnut2626 on 2013-12-12
Thats crazy because this is how the book has it explicitly laid out....

---

### Post by wingnut2626 on 2013-12-12
Is it possible that this is using a different version of C?

---

### Post by steeldriver on 2013-12-12
Oops sorry I misread your code

It compiles OK in gcc (even with -Wall -ansi -pedantic) even though 'SurnameStart' is not a string literal, I think ('name' is though)

How exactly are you trying to compile it?

---

### Post by trent.josephsen on 2013-12-12
Warnings are normal and expected; they don't necessarily mean you've done something wrong.

In this case the warning means that surnameStart can't be checked by the compiler, and if it contains any % specifiers, printf will try to use them (with possibly disastrous results). The defensive way to program this line is like this:
```
printf("%s", surnameStart);
```
(Also note that you should add "\n" to the end of the format string if you want to see the result.)

If you compile your code with -Wall -Wextra -std=c11 -pedantic, you'll also get an error saying that main() must return int. This is true in any standard version of C. If your book uses "void main()", do yourself a favor and get rid of it. (The book, I mean.)

Aside from that, your code has an awful lot of unnecessary blank lines, most of which I would remove. Readability counts.

---

### Post by wingnut2626 on 2013-12-12
I just added a %s in there.  Makes sense, that would be a formatted string.  Wonder why the book has it like that?  Maybe to make me start flying on my own?

---

### Post by wingnut2626 on 2013-12-12
Yeah when I am finished, i take the blank lines out.  They are in there so that i can print it out and write my own notes in there.  For the future i will eliminate them before posting again.  Thanks!

---

