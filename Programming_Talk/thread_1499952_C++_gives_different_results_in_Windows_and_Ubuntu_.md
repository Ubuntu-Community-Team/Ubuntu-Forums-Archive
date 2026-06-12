---
title: "C++ gives different results in Windows and Ubuntu 10.04 with g++"
date: 2010-06-02
forum: Programming Talk
---

### Post by powerchess on 2010-06-02
I have compiled the same program and I get different results when the program is run in windows and in ubuntu, in windows I run it with Dev C++. 

I was wondering if someone could provide insight on this. My expected result is the one that Windows gives. However, I would really like to work in Ubuntu. 

Thanks 

Note: this is a copy of [http://ubuntuforums.org/showthread.php?p=9400362#post9400362]("http://ubuntuforums.org/showthread.php?p=9400362#post9400362")

---

### Post by MadCow108 on 2010-06-02
it is for sure no bug in gcc
You either have a bug in your code which shows differently on a different compiler/architecture
or your code does not conform with C++ standard, making it non-portable between platforms.

Either way, without a code sample we cannot help.

---

### Post by Simian Man on 2010-06-02
It's not a bug in g++, it's a bug in your program.  C++ has a lot of undefined behavior in it.  That means your program can do a lot of things where there is no one outcome you can be sure of.  Hence it can be handled differently by different compilers and they can both be correct according to the standard.

What is the actual problem you have with g++?  Because you will have to fix it.

---

### Post by powerchess on 2010-06-02
I managed to isolate the problem. I now believe it is with my code. 

```

                else if(a[i]==0)
		{
			if(i!=0)		{temp[i]=0;}
			else 			{if(ran()<prob){temp[0]=-1;}}
		}
```

Somehow temp[0] is being set to 1. 

(I am looping through the indices of the array a) 
and am storing temporary values in temp. I need a mechanism to clear temp. (I tried both delete temp and delete[] temp and they dont seem to work)

if I do  
```

                else if(a[i]==0)
		{
			if(i!=0)		{temp[i]=0;}
			else 			{if(ran()<prob){temp[0]=-1;}else{temp[0]=0;}}
		}
```

The program works fine

---

### Post by trent.josephsen on 2010-06-02
Ugh.  Indent your code properly.

```
else if (a[i] == 0) {
    if (i != 0) {
        temp[i] = 0;
    } else {
        if (ran() < prob) {
            temp[0] = -1;
        }
    }
}
```

or more typical

```
else if (a[i] == 0) {
    if (i) {
        temp[i] = 0;
    } else if (ran() < prob) {
        temp[0] = -1;
    }
}
```

Incidentally, when I ran your code through indent -kr, it noted that you didn't have a space between the = and the -, which might do what you want but might also be interpreted as the old form of the -= decrement operator.  Probably not your problem, but without more context we can't say.  Please post a compilable program that exhibits your problem, not tiny fragments.

---

### Post by Simian Man on 2010-06-02
In addition to what Trent said, you should also have better variable names than "a" and "temp".  You should also have comments, if not for your own sake then at least when you post your code onto a forum.

As it is, nobody will be able to help you because you have given us no clue as to what this code is even vaguely supposed to be doing.

---

### Post by Dougie187 on 2010-06-02
> **trent.josephsen said:**
> Ugh.  Indent your code properly.

```
else if (a[i] == 0) {
    if (i != 0) {
        temp[i] = 0;
    } else {
        if (ran() < prob) {
            temp[0] = -1;
        }
    }
}
```

or more typical

```
else if (a[i] == 0) {
    if (i) {
        temp[i] = 0;
    } else if (ran() < prob) {
        temp[0] = -1;
    }
}
```

Incidentally, when I ran your code through indent -kr, it noted that you didn't have a space between the = and the -, which might do what you want but might also be interpreted as the old form of the -= decrement operator.  Probably not your problem, but without more context we can't say.  Please post a compilable program that exhibits your problem, not tiny fragments.

+1. Looks like your problem is lack of white space.

---

### Post by powerchess on 2010-06-02
Im sorry, I have a lot of clauses, that is why I chose to indent it the way I did. It makes for easier reading. Rather than easier debugging. 

The large number of clauses is also the reason I am not posting the entire code. Most of the code is irrelevant. 

Anyway, when I initialized temp to be all 0's, The issue was fixed.. I wonder why initializing is causing the problem.

---

### Post by MadCow108 on 2010-06-02
> **powerchess said:**
> Im sorry, I have a lot of clauses, that is why I chose to indent it the way I did. It makes for easier reading. Rather than easier debugging. 

The large number of clauses is also the reason I am not posting the entire code. Most of the code is irrelevant. 

Anyway, when I initialized temp to be all 0's, The issue was fixed.. I wonder why initializing is causing the problem.

the value of uninitialized data is undefined. It can be anything.
On windows you probably where just lucky that it was zero.

These kind of errors can easily be found with the tool valgrind.
You should check it out. It's very easy to use and extremely helpful.

---

### Post by powerchess on 2010-06-02
Thanks for your help.
I am fine with it being undefined, my issue arose since somehow it was being set to 1. 

i.e. in a previous iteration of the loop if it had been set to 1, and I had done
delete [] temp
then when I had re-declared the variable temp, it was using the previous values.

---

### Post by Simian Man on 2010-06-02
> **powerchess said:**
> Thanks for your help.
I am fine with it being undefined, my issue arose since somehow it was being set to 1. 

i.e. in a previous iteration of the loop if it had been set to 1, and I had done
delete [] temp
then when I had re-declared the variable temp, it was using the previous values.

You should never use delete or delete [] on variables that have not been created with new and new [] respectively.  Variables that you just declare should not ever be deleted.

---

### Post by MadCow108 on 2010-06-02
this is uninitialized data -> undefined behavior.

You cannot count on the fact that the next allocation will reuse the memory from the last loop (although it is likely), so it can also be something else than 1.

---

### Post by powerchess on 2010-06-02
Ahh, I think I may know what is causing this.. 
Does g++ keep track of where temp is pointing even after I delete temp? 
i.e.
Do I need to perform 
```

delete [] temp;
temp = NULL;

```

---

### Post by powerchess on 2010-06-02
> **Simian Man said:**
> You should never use delete or delete [] on variables that have not been created with new and new [] respectively.  Variables that you just declare should not ever be deleted.

It was created with new. rather new []

---

### Post by MadCow108 on 2010-06-02
> **powerchess said:**
> Ahh, I think I may know what is causing this.. 
Does g++ keep track of where temp is pointing even after I delete temp? 
i.e.
Do I need to perform 
```

delete [] temp;
temp = NULL;

```

please provide some context on what you want to do.
Memory allocation can be pretty complex. You should not make any assumptions on it which are not explicitly documented in the C++ language standard.
E.g. standard glibc implementation does not really free the memory immediately but instead puts it in a free-list for latter use.
You cannot predict when it will really be given back to the system.

At the question:
Generally no. The compiler/runtime library doesn't care if you set the pointer to NULL.
But sometimes you want to do that to indicate that the memory has been free'd and cannot be reused.
If you want this depends on program context. In C++ this is only rarely needed as the language has it has better means of memory management (STL containers, RAII, smart pointers etc.) but in C code you often see this.

---

### Post by trent.josephsen on 2010-06-02
> **powerchess said:**
> Thanks for your help.
I am fine with it being undefined, my issue arose since somehow it was being set to 1.
It was not "being set to" anything.  You used an undefined value.  Uninitialized variables can have absolutely any value, including values that when loaded into memory could cause your computer to crash, [or cause demons to fly out of your nose](http://www.catb.org/~esr/jargon/html/N/nasal-demons.html).  You were lucky that it exhibited itself as a simple bug, rather than appearing to work (as it did on Windows) or doing something more damaging (as it might somewhere else).

> i.e. in a previous iteration of the loop if it had been set to 1, and I had done
delete [] temp
then when I had re-declared the variable temp, it was using the previous values.

Stop.  This kind of analysis is meaningless.  You invoked undefined behavior.  That means that nothing you write, from this point forward, is ever obliged to do anything sensible or be related in any way to the rest of your code.  In this case, it does indeed appear that you are re-using the same memory for temp, and the memory still holds the same values as the previous iteration.  However, because the behavior is undefined, running it again isn't necessarily going to result in the same output.  Undefined programs aren't required to be deterministic, don't have to adhere to any standards, and aren't likely to obey any logical rules whatsoever (especially at high optimization levels).  Trying to ascertain what the implementation is "really" doing can only end in grief.

---

