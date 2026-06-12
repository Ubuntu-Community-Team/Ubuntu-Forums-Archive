---
title: "Can you put a variable into a for loop as one of the conditions?"
date: 2011-10-12
forum: Programming Talk
---

### Post by ClientAlive on 2011-10-12
I have a challenge I've been struggling with a bit lately. I need to figure out how to take two user input entries (numbers) and multiply them - but - also using a for loop that starts at zero, increments by one, and stops at whatever number the user entered for one of their entries. The problem is that the end/ stopping point for the for loop is defined by one of the user input entries (or, I think, needs to be). I tried experimenting around a little by putting a variable into one of the conditions for the for loop but got errors from the compiler. I'm stumped.

Anyone have an idea the might help?

---

### Post by cgroza on 2011-10-12
It would be very helpful if you specify the language and show us your existing code.

---

### Post by lisati on 2011-10-12
> **cgroza said:**
> It would be very helpful if you specify the language and show us your existing code.

I agree that knowing which language you are using might be helpful.

As a side note, the languages I've used generally allow for variables as part of the conditions of loops.

---

### Post by Bachstelze on 2011-10-12
I shall add that the condition of a for loop *must* be a variable (i.e. something that can vary) because otherwise either it is always false and the loop is never entered, or it is always true and you get an infinite loop (and if you want an infinite loop, why put a condition at all?).

---

### Post by Arndt on 2011-10-13
> **Bachstelze said:**
> I shall add that the condition of a for loop *must* be a variable (i.e. something that can vary) because otherwise either it is always false and the loop is never entered, or it is always true and you get an infinite loop (and if you want an infinite loop, why put a condition at all?).

Using for ( ; ; ) and then breaking out from the middle of the loop is quite common, if the language allows it.

If the original poster shows some code written in that way which does exactly what he wants, we can perhaps rewrite it into a nicer for loop.

---

### Post by Bachstelze on 2011-10-13
> **Arndt said:**
> Using for ( ; ; ) and then breaking out from the middle of the loop is quite common, if the language allows it.


Such a loop has no condition, hence

> (and if you want an infinite loop, why put a condition at all?)

---

### Post by Arndt on 2011-10-13
> **Bachstelze said:**
> Such a loop has no condition, hence

It's late here, so maybe I'm a bit daft, but I don't understand. Do you call all for ( ; ; ) loops infinite loops?

(Sorry for not including the material that you quote - the forum ought to do it.)

---

### Post by Bachstelze on 2011-10-13
Well, for (;;) *is* an infinite loop. ;) So if you want to have an infinite loop, you just don't put a condition at all, so it is irrelevant to the issue of whether or not you put vairalbes in conditions.

---

### Post by nvteighen on 2011-10-13
I think what the OP is referring to is whether it is allowed to modify per user input a variable that is used as a condition of a for-loop.

AFAIK, it is allowed, but it may drive your code into wreckage, as you'll have to design code that doesn't interfere with the "step" statement of the loop. I highly recommend you to use a while-loop for such a case.

---

### Post by jwbrase on 2011-10-14
> **Bachstelze said:**
> Well, for ( ; ; ) *is* an infinite loop.

Not really:

```
i=0;
for (;;)
{
    if (!(i<10))
        break;
    doStuff();
    i++;
}
```

Is equivalent to:

```
for (i=0; i < 10; i++)
{
    doStuff();
}
```

Which is manifestly not an infinite loop.

Now, if you were to write a for ( ; ; ) loop without any break statement in it, that would be an infinite loop. Now, I don't see why one would want to put ones terminating condition in an if -> break inside the loop rather than as "for (;;condition)", but the two structures do the same thing.

---

### Post by jwbrase on 2011-10-14
> **ClientAlive said:**
> The problem is that the end/ stopping point for the for loop is defined by one of the user input entries (or, I think, needs to be). I tried experimenting around a little by putting a variable into one of the conditions for the for loop but got errors from the compiler. I'm stumped.

You mean like this?:

```
int i;
j=getUserInput();
for(i = 0; i < j; i++)
{
    doStuff();
}
```

---

### Post by lisati on 2011-10-14
> **jwbrase said:**
> Not really:

```
i=0;
for (;;)
{
    if (!(i<10))
        break;
    doStuff();
    i++;
}
```

Is equivalent to:

```
for (i=0; i < 10; i++)
{
    doStuff();
}
```

Which is manifestly not an infinite loop.

Now, if you were to write a for ( ; ; ) loop without any break statement in it, that would be an infinite loop. Now, I don't see why one would want to put ones terminating condition in an if -> break inside the loop rather than as "for (;;condition)", but the two structures do the same thing.
Agreed: I find that your second example is "nicer", because the "for" statement tells me something about what kind of behaviour to expect from the loop, where as the first example doesn't.

It probably doesn't matter so much with smaller projects, but with larger projects, having a clear idea of what the code does becomes more important.

---

### Post by Bachstelze on 2011-10-14
> **jwbrase said:**
> Not really:

```
i=0;
for (;;)
{
    if (!(i<10))
        break;
    doStuff();
    i++;
}
```

Is equivalent to:

```
for (i=0; i < 10; i++)
{
    doStuff();
}
```

Which is manifestly not an infinite loop.

Now, if you were to write a for ( ; ; ) loop without any break statement in it, that would be an infinite loop. Now, I don't see why one would want to put ones terminating condition in an if -> break inside the loop rather than as "for (;;condition)", but the two structures do the same thing.

Not sure if trolling or totally missed the point...

*EDIT:* But rest assured I know about break, thank you very much.

---

### Post by ClientAlive on 2011-11-09
Oh my goodness guys. I'm sorry I went mia like that. I've been sooo busy with school and everything else and I lost track that I had posted this thread until just now. That was a while back and I did learn how to do that since then. If I can recall from memory an example would be something like

```

int UserInuput, i;

printf("Please enter your input: \n");
scanf("%i", &UserInput);

for(i=0; i<=UserInput; i++)
   {
      code you want to execute
   }

```

Thanks for all your input and examples. Again, I appologize for losing track like that.

Jake
----------------

Edit:

Oh, and its C language that we're learning.  :)
----------------

Edit 2:

That was a while back now. I remember working on that for at least two full days before even reaching out for help. It was something for a class project. I had struggled and sturggled with the concept of using the user's input for the middle condition of the for loop, the stopping point. I don't recall now if I even got that assignment in. I've gotten into the habit of continuing to work on these projects until I get them right though, even if I don't make the deadline. I'll look for the file; and, if I can find it, I'll come attach it here so you guys can see what it was all about. If I can't find it, well, in a nutshell I needed to make a program that calulated the distance a vehicle traveled based on the user input of mile per hour and lenght of time traveled. It was to print out a list with data for each hour along the way and the distance at that time. It meant that I would have to control the program execution with the user input and it just about killed me to figure that out. I'll look for the file and attach it if I can find it.
-----------------

Edit 3:

I found it. It looks like I never did get that done. Base on the kind of stuff we're doing now though I confident I could knock something like that out pretty easy. I think its one of the those one's I need to revisit and make sure I do the job propper. I'll never get credit for it since I missed getting it in, but I can give myself credit for leaning how to do it I guess. Anyhoo, I've attached the file as I last left it.

---

