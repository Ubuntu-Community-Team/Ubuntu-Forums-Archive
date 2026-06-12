---
title: "C ide"
date: 2012-09-16
forum: Programming Talk
---

### Post by manudo on 2012-09-16
I have Ubuntu 12.04, I'm new using it so please be patient to explain.

I've installed Ajunta, Eclipse, Code:Blocks, KDevelop, Geany and I run a "Hello World" program and no one work like Windows IDE's.

I run "Hello world!" program in Geany it runs well, but if I run a larger code program it has this error. Note that when I compile, Geany doesn't show me errors.

Here's the code if needed, it's a multiplicator.

```
#include <stdio.h> 
 
int main() 
{ 
      int st, nd, result; 
       
      printf("Enter the first number "); 
      scanf("%d", &st); 
      printf("Enter the second number "); 
      scanf("%d", &nd); 
      result = st * nd; 
      printf("The result of your multiplication is %d", result); 
      getchar(); 
      getchar(); 
}
```Error in Geany is attached.

Feel free if you want to share a better IDE for C or C++.

Thank you! ;)

---

### Post by MG&amp;TL on 2012-09-16
> I've installed Ajunta, Eclipse, Code:Blocks, KDevelop, Geany and I run a "Hello World" program and no one work like Windows IDE's.
Are you expecting them to be? Visual Studio is good, but a complete nightmare if you don't follow its use-case.

> I run "Hello world!" program in Geany it runs well, but if I run a larger code program it has this error. Note that when I compile, Geany doesn't show me errors.You're trying to execute the wrong file. Go to the Build->Set build commands and that should help. Although if I recall, both Anjuta and Code::Blocks do this fine. Geany doesn't really seem to be intended as an IDE, more as a text editor with some handy development features, which it does very well.

> Feel free if you want to share a better IDE for C or C++.
The ones you've tried are what we have. You probably just need to spend a little time figuring them out, as you no doubt did for the MS IDEs.

---

### Post by safarin on 2012-09-16
> **manudo said:**
> 

```
#include <stdio.h> 
 
int main() 
{ 
      int st, nd, result; 
       
      printf("Enter the first number "); 
      scanf("%d", &st); 
      printf("Enter the second number "); 
      scanf("%d", &nd); 
      result = st * nd; 
      printf("The result of your multiplication is %d", result); 
      getchar(); 
      getchar(); 
}
```Error in Geany is attached.


The screenshot show you compile using g++ not gcc..
This code is for C or C++ programming??

I compile using geany with no problem.. just got warning because you dont put return 0...

---

### Post by tienlbhoc on 2012-09-16
You can try netbean with c++, but I think you need reinstall compile packages first

---

### Post by manudo on 2012-09-16
> **MG&TL said:**
> 
You're trying to execute the wrong file. Go to the Build->Set build commands and that should help.

Yeah, but. What I have to do in the Set Build Commands box, I mean, what I have to do right there?

By the way, I'm trying Anjuta.

> **safarin said:**
> The screenshot show you compile using g++ not gcc..
This code is for C or C++ programming??

I compile using geany with no problem.. just got warning because you dont put return 0...

Yeah, I don't see a big difference between C and C++, and even if I put return 0; Geany returns that error.

---

### Post by MG&amp;TL on 2012-09-16
> **manudo said:**
> Yeah, but. What I have to do in the Set Build Commands box, I mean, what I have to do right there?

By the way, I'm trying Anjuta.

Erm...the command to execute your binary. I don't really know what you're asking, sorry. If you don't know how to build and run executables in Linux, you're probably barking up the wrong tree with an IDE, at least IMO. Learn to manually compile things, then you can use an IDE if you wish.

Anjuta is probably more up your street. It has a more Visual Studio feel, with Projects and whatnot.

> Yeah, I don't see a big difference between C and C++, and even if I put return 0; Geany returns that error.

EDIT: Uh-oh. Refer my earlier comment about IDEs- they just complicate things for new developers. My advice is not to use one, and just to use a simple text editor until you get the hang of stuff.

---

### Post by manudo on 2012-09-16
> **MG&TL said:**
> Erm...the command to execute your binary. I don't really know what you're asking, sorry.

Doesn't matter, I've tried Anjuta and finally I understand it. I use terminal to check the executables, but If I double-click it in the explorer it doesn't show me nothing, what's happening?

> **MG&TL said:**
> EDIT: Uh-oh. Refer my earlier comment about  IDEs- they just complicate things for new developers. My advice is not  to use one, and just to use a simple text editor until you get the hang  of stuff.

Yeah, sometimes I use gedit and compile with gcc, but I use IDE's because there are some errors in terminal that I can't understand.

---

### Post by MG&amp;TL on 2012-09-16
> **manudo said:**
> Doesn't matter, I've tried Anjuta and finally I understand it. I use terminal to check the executables, but If I double-click it in the explorer it doesn't show me nothing, what's happening?



Yeah, sometimes I use gedit and compile with gcc, but I use IDE's because there are some errors in terminal that I can't understand.

Okay, whatever works for you. :)

For  some reason unknown to me, nautilus ("explorer") won't run executables, even if they're graphical. So yeah, it's a terminal job.

My apologies, I kind of assumed you were having basic problems, not IDE problems. :) 


Problem with that is that you'll get the exact same errors in an IDE. So I'm not sure what you mean by that.

---

### Post by manudo on 2012-09-16
IDE's tells you where is the expected part, or simply where is the error. It's easier to me.

Thank you by the way! :D

---

### Post by MG&amp;TL on 2012-09-16
> **manudo said:**
> IDE's tells you where is the expected part, or simply where is the error. It's easier to me.

Thank you by the way! :D

So does *gcc*. :P

Not a problem.

---

### Post by manudo on 2012-09-16
It just that I'm used to program with software.

---

