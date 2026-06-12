---
title: "Bored at work..."
date: 2007-06-28
forum: Programming Talk
---

### Post by g3k0 on 2007-06-28
In an attempt to find the G stands for in GNU and to achieve world domination,  I have put my computer to the task of finding the end of the recursion.

```
//In an attempt to find the G stands for in GNU and to achieve world domination,
//I have put my computer to the task of finding the end of the recursion.

#include <iostream>

void GNU(){
  std::cout << GNU() << "is not unix\n";
}

int main(){
  std::cout<< "GNU Stands For: " << GNU();

  return 0;
}


```

---

### Post by skeeterbug on 2007-06-28
Did it ever find the end? Or are you letting it run? :)

---

### Post by davmaz on 2007-06-28
I don't know if this ran for you (I doubt it).  You need to put the line:
using namespace std; 
below the includes...

You could also be more verbose (not using the using namespace keyword) and do this:
std::cout << "bla bla" << std::endl;

---

### Post by Jessehk on 2007-06-28
> **skeeterbug said:**
> Did it ever find the end? Or are you letting it run? :)

Well, eventually he'll get a stack overflow (I think).

---

### Post by rjack on 2007-06-28
The HURD version!

```
#include <stdio.h>

void hurd (void);

void
hird (void) {
        hurd ();
        printf ("of Interfaces Representing Depth\n");
}

void
hurd (void) {
        hird ();
        printf ("of Unix-Replacing Daemons\n");
}

int
main (int argc, char **argv) {
        printf ("HURD stands for :");
        hurd ();
        return 0;
}
```

---

### Post by g3k0 on 2007-06-29
> **skeeterbug said:**
> Did it ever find the end? Or are you letting it run? :)

You will know when I reach the end.. I will have achieved world domination!

> **davmaz]I don't know if this ran for you (I doubt it). You need to put the line:
using namespace std said:**
> 

How dare you question my coding abilities!  My programs always compile the first time!  Besides, I did put std:: before the couts.. see no edits....

[QUOTE=Jessehk]Well, eventually he'll get a stack overflow (I think).

Nonsense! My stack is run by magical gnomes who have stack extending abilities.  Not only that.. its a physical stack!

[QUOTE=rjack]The HURD version![/QUOTE]
Hah! you will be foiled by the doubly recursion and lack of magical gnomes with stack extending abilities.  The world is MINE!

---

### Post by MiCovran on 2007-06-29
> **g3k0 said:**
> I have put my computer to the task of finding the end of the recursion.

You will know when I reach the end.. I will have achieved world domination!

My stack is run by magical gnomes who have stack extending abilities.  Not only that.. its a physical stack!

Hah! you will be foiled by the doubly recursion and lack of magical gnomes with stack extending abilities.  The world is MINE!


LOL You need help, I think.

> **g3k0 said:**
> How dare you question my coding abilities!  My programs always compile the first time!  Besides, I did put std:: before the couts.. see no edits....
BTW, it does NOT compile, void() in cout :D

---

### Post by ankursethi on 2007-06-30
```
while 1 :
    print "WTF, mate?"
```

---

