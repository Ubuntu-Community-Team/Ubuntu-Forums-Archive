---
title: "C++ help"
date: 2012-09-27
forum: Packaging and Compiling Programs
---

### Post by Abimael09 on 2012-09-27
So I ran g++ and then ran ./a.out, but somethings not right, Im learning C++, but this is my first time using Linux while programming


I prefer using Text Editor over IDE's

Any help?

---

### Post by spjackson on 2012-09-27
What do you mean by "somethings not right"?

It looks right to me. The program has compiled successfully, it has run correctly and done what you told it to. You might want a newline after your second line of output, in which case you need to add that to your program.

---

### Post by Abimael09 on 2012-09-27
> **spjackson said:**
> What do you mean by "somethings not right"?

It looks right to me. The program has compiled successfully, it has run correctly and done what you told it to. You might want a newline after your second line of output, in which case you need to add that to your program.


Nvm, i See it, simple noob mistake

---

### Post by Niemand000 on 2012-09-28
I'm trying to learn C++ too, but am having trouble trying to find a g++ compiler?  Probably the dumbest question you've all heard so far.  I thought Ubuntu 12.04 came with one already?  And how are you saving those files as .cpp.  When I "touch 1program"  it creates a file that has no ending?  Simply ~/Document/"C++ Programs"/1program

---

### Post by MG&amp;TL on 2012-09-28
> I'm trying to learn C++ too

Yay!

> but am having trouble trying to find a g++ compiler?

You need to install the *build-essential* and *g++* packages.

  > Probably the dumbest question you've all heard so far.

Believe me, I've heard worse. ;)

> I thought Ubuntu 12.04 came with one already?

Nope, Ubuntu is aimed at laypeople, and most laypeople don't program.

> And how are you saving those files as .cpp.

You're either misunderstanding Linux filenames, or misunderstanding how to use *touch*. Linux (and most programs within it) doesn't really care what file extensions you use. That said, it's a good idea to name things appropiately, if only to distinguish between them. 

> When I "touch 1program"  it creates a file that has no ending?

That's what you told it to do. What else did you expect?

```
touch 1program.cpp
```

would add a ".cpp" file extension.

---

### Post by Niemand000 on 2012-09-29
> **MG&TL said:**
> Yay!



You need to install the *build-essential* and *g++* packages.

  

Believe me, I've heard worse. ;)



Nope, Ubuntu is aimed at laypeople, and most laypeople don't program.



You're either misunderstanding Linux filenames, or misunderstanding how to use *touch*. Linux (and most programs within it) doesn't really care what file extensions you use. That said, it's a good idea to name things appropiately, if only to distinguish between them. 



That's what you told it to do. What else did you expect?

```
touch 1program.cpp
```would add a ".cpp" file extension.

Thanks! That worked! : )

---

### Post by Niemand000 on 2012-10-01
While going through this ([http://www.cprogramming.com/tutorial/lesson2.html](http://www.cprogramming.com/tutorial/lesson2.html)) tutorial, I ran across Boolean operators and was totally lost.  A little help?

---

### Post by MG&amp;TL on 2012-10-02
> **Niemand000 said:**
> While going through this ([http://www.cprogramming.com/tutorial/lesson2.html](http://www.cprogramming.com/tutorial/lesson2.html)) tutorial, I ran across Boolean operators and was totally lost.  A little help?

You really should start a new thread, but I'll let it slide as I already answered your previous one. ;)

I'll need more specifics to go into more detail about a particular area, but basically you can get your program to decide things for itself. 

However, computers don't have 'grey areas' or 'fuzzy bits'. They can only decide if a condition is one thing or the other. In computer language, TRUE or FALSE.

**Operators** determine whether the **operands** they are given match the conditions for the operator, then evaluate to TRUE if they do, or FALSE if they don't.

Examples:

1 < 2: TRUE
1 > 2: FALSE
2 == 2: TRUE
2 < 2: FALSE
2 <= 2: TRUE

Read up on operators if you wish to know more about a particular one, or about others.

Once you've decided if a condition is TRUE or FALSE, the computer can then do something with it. An example is a 'if' statement, which only executes the code in the block if the condition evaluates to true:

Example:

```

<snip syntax stuff>

if(6 < 8) {
    std::cout << "Yay, maths works!" << std::endl;
}

```



I'll need more details if you want more information. :)

---

