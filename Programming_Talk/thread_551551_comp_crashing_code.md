---
title: "comp crashing code"
date: 2007-09-15
forum: Programming Talk
---

### Post by tennvolsmb on 2007-09-15
ok i just made this code to see if it would work but now im stuck..... can anyone tell me what i need to do because whenever i try to run this on windows it brings up the command prompt and does not seem to do its job right...... i do not wish to reproduce this code in any way it is just to see if i could.... can anyone tell me what i am doing wrong?

```
#include <iostream>
#include <cstdlib>

using namespace std;

int main() 
{

    while (1) 
    {

    int * memleak = new int;
    *memleak = 10;
    }
    
    return 0;
    
}
```

---

### Post by gnusci on 2007-09-15
Your program never finish, you have an infinite loop

[PHP]
#include <iostream> //<----- not used
#include <cstdlib>  //<----- not used

using namespace std;

int main() 
{
    while (1) //<----- do forever
    {
          int * memleak = new int;
          *memleak = 10;
    }
    return 0;
}
[/PHP]

so you never rich the end, thats why look like a command line prompt. What do you want to do?

---

### Post by aks44 on 2007-09-15
> **tennvolsmb said:**
> what i am doing wrong?

- **while (1)** is an infinite loop, without any **break** statement you can't get out of it.
- you allocate memory without releasing it (each and every **new** must be matched by exactly one corresponding **delete**).

Those two points mean that the program will eat up your CPU and your memory until the OS can't allocate more memory, which will trigger a std::bad_alloc exception and make your program crash.


That's what you did wrong.

---

### Post by tennvolsmb on 2007-09-15
well actually the idea is to eat up the cpu speed and make the ram overload causing a crash.... but it seems like it does not happen ever... i was just trying it out on my test computer (computer i never use anymore) so how do i speed up the process?

---

### Post by tennvolsmb on 2007-09-15
also everytime i run the program i get this message saying

```
H:\COMPCR~1.EXE
The NTVDM CPU has encountered an illegal instruction.
CS:0de2 IP:0103 OP:63 6c 75 64 65 Choose 'Close' to terminate the application
```

it then give the option of close or ignore

then it give another message saying

```
H:\COMPCR~1.EXE
The NTVDM CPU has encountered an illegal instruction.
CS:0de2 IP:0119 OP:63 6c 75 64 65 Choose 'Close' to terminate the application
```

and the same options again


now a crash program should not give the option saying its illegal.... how can i get rid of this?

---

### Post by tennvolsmb on 2007-09-15
come on guys please this was a basic crash program that i wrote and would really like understand what i did wrong so i dont make an error ona program i am currently working on

---

### Post by aks44 on 2007-09-15
> **tennvolsmb said:**
> how can i get rid of this?

Come on, our job as programmers is to create stable and well behaved programs, and *get rid* of bugs.

Do you really think you'll find any sane programmer willing to help you to achieve the exact contrary? If you want to experiment and make your computer crash, you're all by yourself.

As far as I'm concerned I won't take the responsability to give you such a knowledge which could easily be misused. I thought you would have been able to read between the lines of my first post (I perfectly understood your goal at first glance, mind you) but it seems not.

---

### Post by gnusci on 2007-09-15
> **aks44 said:**
> Come on, our job as programmers is to create stable and well behaved programs, and *get rid* of bugs.

Do you really think you'll find any sane programmer willing to help you to achieve the exact contrary? If you want to experiment and make your computer crash, you're all by yourself.

As far as I'm concerned I won't take the responsability to give you such a knowledge which could easily be misused. I thought you would have been able to read between the lines of my first post (I perfectly understood your goal at first glance, mind you) but it seems not.

The same, I have not find myself thinking about how to make a voluntary crash of my system, that is your own business.

---

### Post by tennvolsmb on 2007-09-15
you really dont understand.... the concept of this program was to see if i could make it possible... i am more of a creator not so much a destroyer im not looking for an insane person i am looking for a person who knows about program that will tell me how to fix this. I already know the program works.. but there are other ways that a program like this that is meant to help not destroy.... so please understand that and do not post if you are going to be negative about a simple programming question in the programming forums. thanks and have a SUPER day

---

### Post by aks44 on 2007-09-15
> **tennvolsmb said:**
> but there are other ways that a program like this that is meant to help not destroy....

I'd be curious to hear how a program which goal is to bring a machine down could "help" anyone?... :roll:

---

### Post by tennvolsmb on 2007-09-15
that is not what i meant.... i meant more in a general form.... all i am saying is that i created a program that destroys, but this same type of program can also be used for good it would just need a little program change... i did not mean to say that a program to destroy can be used for good....... listen all i am saying is that i am trying to learn programming, not for bad but for good.... so what if i create a bad program every now and then, i do not ever plan on launching a virus/worm/trojan etc.... its just one of those "see if you can" type of things..... please understand this... now if you want to give me a similar program that would do something completely different yet written almost the same feel free to.... sorry for the misunderstanding there.

---

### Post by tennvolsmb on 2007-09-15
and besides the whole idea of this was to learn how to speed up such a process

---

### Post by gnusci on 2007-09-15
fix it with:

[PHP]
#include <iostream> //<----- not used
#include <cstdlib>  //<----- not used

using namespace std;

int main() 
{
    while (1) //<----- do forever
    {
          int * memleak = new int;
          *memleak = 10;
          delete memleak; // <---- fix it!
    }
    return 0;
}  
[/PHP]

---

### Post by tennvolsmb on 2007-09-15
well thanks for you respond but now when i test it, it just gives me a lot of messages saying that it has encounterd an illegal operation and gives me the option to close ignore but if i ignore more just pop up

---

### Post by tennvolsmb on 2007-09-15
any clue about that problem?

---

### Post by Lux Perpetua on 2007-09-15
Apparently people in this forum are rather quick to judge. 

tennvolsmb - I still don't understand what you're saying is wrong with the program, but perhaps the "problem" is that the OS is too smart for your shenanigans. 

However, if all you want to do is increase the rate at which your program consumes memory, then you can try **new int[1000]** instead of **new int**, i. e., consume 4 kilobytes at a time rather than 4 bytes.

---

### Post by tennvolsmb on 2007-09-15
well thank you for understanding i will try that out and see what happens but thanks again

---

### Post by tennvolsmb on 2007-09-15
and also could you tell me if that consumes like just the cpu speed and the ram memory or does it also consume actual hd space?  sorry for this simple question but i am very new to program and i am trying to get the full experience which is the reason i made this

---

### Post by aks44 on 2007-09-15
> **tennvolsmb said:**
> ```
H:\COMPCR~1.EXE
The NTVDM CPU has encountered an illegal instruction.
CS:0de2 IP:0103 OP:63 6c 75 64 65 Choose 'Close' to terminate the application
```

This error is typical of a 16-bit program running on Windows XP. Since 16-bit technology has been dead for about 10 years now, people may have hard time helping you with such an error which is very compiler and platform specific.

May I suggest that you get a decent, up to date compiler? On Windows, [mingw]("http://www.mingw.org/") is quite correct. If you need an IDE, [Code::Blocks]("http://www.codeblocks.org/") is fine.


> **Lux Perpetua said:**
> Apparently people in this forum are rather quick to judge.

That was not a judgment, only a constatation. The OP is trying to make his computer crash, which is the opposite of good programming practices.


> **tennvolsmb said:**
> could you tell me if that consumes like just the cpu speed and the ram memory or does it also consume actual hd space?

When physical memory is exhausted, the OS will start swapping out. As most Windows setups still have the default "dynamic swap", swap (thus memory) space is only limited by the hard drive free space. Although your program doesn't write to the disk, it somewhat consumes disk space because of this mechanism.

---

### Post by gnusci on 2007-09-15
You should read few things about memory allocation....

[http://en.wikipedia.org/wiki/Malloc](http://en.wikipedia.org/wiki/Malloc)
[http://www.linuxjournal.com/article/6390](http://www.linuxjournal.com/article/6390)
[http://www.eskimo.com/~scs/cclass/notes/sx11a.html](http://www.eskimo.com/~scs/cclass/notes/sx11a.html)

---

### Post by CptPicard on 2007-09-15
And when you get that working, you can continue your education as the programming equivalent of a terrorist by learning about the [fork bomb]("http://en.wikipedia.org/wiki/Fork_bomb")... :-\"

---

