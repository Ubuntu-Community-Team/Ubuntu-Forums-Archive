---
title: "Rapid GUI Builder in C"
date: 2007-03-12
forum: Programming Talk
---

### Post by lucks on 2007-03-12
hi!:) 

am working on something called ARtoolkit (in C) and i have to create an interface ( in C) for it...

is there any rapid GUI builder in C which is easy and rapid to build the interface? well someone told me GUI builder such as javaSwing,netbeans..etc

but am using Gtk+ according to some recommendations..now am stuck in my project because i am havong problem to integrate it with ARtoolkit:( 

since i have little time and have to submit my project in 3 days, i am looking for something very easy,simple and which can be rapidly developed (such as drag and drop..etc) but in C..

i would be much grateful if someone can suggest me some Rapid GUI builders as well as their link from where i can download them and try... 

Again someone told me there is VB also..well its a rapid GUI builder but very difficult to integrate with ARtoolkit which is in C..however he also says that it is possible unless we do binding:confused: 

well its the first time am hearing about binding..can someone send me info about that and how is it done? please help:( 


thanks

---

### Post by encompass on 2007-03-12
Try glade.  I use it with python... but it is really built for C and C++.  I think it should work just fine for what you need.  Plenty of documentation.

---

### Post by lucks on 2007-03-12
thanks encompass..

i was trying with gtk but am having problem with some code..i have try to integrate it with ARtoolkit but i got 1 error which is PACKAGE-undeclared identifier....i dont know what it is since its glade which generate the code...

i dont know how to solve it...any idea about that?:(

---

### Post by lnostdal on 2007-03-12
```

lars@ibmr52:~/mounts/lars@nostdal.org/programming/c$ cat undeclared.c

#include <stdio.h>

int some_variable;

int main()
{
  printf("some_variable: %d\n", sxxm_variable);
  return 0;
}


lars@ibmr52:~/mounts/lars@nostdal.org/programming/c$ gcc -g -Wall undeclared.c -o undeclared
undeclared.c: In function &#8216;main&#8217;:
undeclared.c:7: error: &#8216;sxxm_variable&#8217; undeclared (first use in this function)
undeclared.c:7: error: (Each undeclared identifier is reported only once
undeclared.c:7: error: for each function it appears in.)

```

---

### Post by edyson on 2007-03-12
There is no such thing as rapid GUI building with C... only long and painful. Take it from someone who's written 30000+ lines of GTK+ code in C: build the GUI in a language like python/ruby/tcl (with wxWindows/Fox/tk respectively) and learn to make C extensions.

---

