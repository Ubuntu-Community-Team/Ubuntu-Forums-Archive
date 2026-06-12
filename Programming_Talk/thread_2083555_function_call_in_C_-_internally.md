---
title: "function call in C - internally"
date: 2012-11-12
forum: Programming Talk
---

### Post by IAMTubby on 2012-11-12
Hey,
I would like to know how a function call happens in C internally.

Say  I have a code as follows
```

int main(void)
{
 display();
}  

int display()
{
 printf("\nEntered the function : display");
} 

```What exactly happens when I call ```
display();
```I know that on doing a printf("%p",display);, it gives the addres s of the display function.
So does calling display using the syntax display(); act as a format specifier for accessing maybe (*display)(); ?, the same way we print a string by giving the starting address to the %s format specifier as printf("%s",somelocation);


Thanks.

PS : The original purpose of this post  is to help  me visualize how ```
(*display)();
``` works. I would be more interested in knowing **how the function call happens** rather than what happens upon a function call(like local variables getting pushed into stack etc). Although this would be great to know as well, I wouldn't want to trouble you with an open ended question as that. So maybe you can reply to the original question and give a link on the second.

---

### Post by Bachstelze on 2012-11-13
You cna start here: [http://en.wikipedia.org/wiki/Call_stack](http://en.wikipedia.org/wiki/Call_stack)

And if you want to go further: [http://www.amazon.com/dp/0136108040/](http://www.amazon.com/dp/0136108040/)

---

### Post by Bachstelze on 2012-11-13
Note also that this is architecture-dependent...

---

### Post by IAMTubby on 2012-11-13
> **Bachstelze said:**
> You cna start here: [http://en.wikipedia.org/wiki/Call_stack](http://en.wikipedia.org/wiki/Call_stack)

And if you want to go further: [http://www.amazon.com/dp/0136108040/](http://www.amazon.com/dp/0136108040/)
Thanks Bachstelze, these will be very helpful for me to understand the process once a function call is executed.
But will you be able to help me with what calling display(); does , not at system level, but at programming language(C language) level.
As in, are we passing a pointer to a function, but then why do we add the (); at the end.
As in why can't we just do (*display) instead of (*display)(); .
Is it just syntax or is there more meaning to it.

---

### Post by Tony Flury on 2012-11-13
> **IAMTubby said:**
> Thanks Bachstelze, these will be very helpful for me to understand the process once a function call is executed.
But will you be able to help me with what calling display(); does , not at system level, but at programming language(C language) level.
As in, are we passing a pointer to a function, but then why do we add the (); at the end.
As in why can't we just do (*display) instead of (*display)(); .
Is it just syntax or is there more meaning to it.

To be exact display(); does not do anything at a system level. display(); is translated by the compiler into a set of assembly language instructions to set registers, push arguments if any onto the stack, record return addresses and then pass control to a new memory location which is the tanslation of the display function. When you execute your program - it does not execute display(), it executes that sequence of assembly language instructions.

The reason that display() translates to those assembly instructions and *display doesn't is down to the syntax accepted by the compiler. it would be possible to create a compiler such that *display called the display function with no arguments, but then it wouldn't be the C language - it would be something different.

---

### Post by IAMTubby on 2012-11-13
> **Tony Flury said:**
> it would be possible to create a compiler such that *display called the display function with no arguments, but then it wouldn't be the C language - it would be something different.
Thanks a lot Tony, this almost cleared my question.
The only reason I was confused was because, I know 
```

printf("%p",display);

```
gives the address, which means *display should kind of dereference it and call the function. So why do we need (*display)**();** ?
The **()** at the end was what kept confusing me.

So can I conclude that this is 
1)just syntax and nothing else.
2)Or maybe, I could convince myself as follows
"The same reason why we write display(); and not display; to call a function."

Thanks. :)

---

### Post by Bachstelze on 2012-11-13
> **IAMTubby said:**
> Thanks Bachstelze, these will be very helpful for me to understand the process once a function call is executed.
But will you be able to help me with what calling display(); does , not at system level, but at programming language(C language) level.
As in, are we passing a pointer to a function, but then why do we add the (); at the end.
As in why can't we just do (*display) instead of (*display)(); .
Is it just syntax or is there more meaning to it.

It is just syntax. Functions calls in C are expressions that do not resemble any other kind of expression (because functions in C are not objects, unlike in, say, Python). Function call expressions are described in section 6.5.2.2 of the C99 standard.

---

### Post by IAMTubby on 2012-11-13
> **Bachstelze said:**
> It is just syntax.
Thanks a lot Bachstelze.

---

### Post by ofnuts on 2012-11-14
> **IAMTubby said:**
> Thanks a lot Tony, this almost cleared my question.
The only reason I was confused was because, I know 
```

printf("%p",display);

```gives the address, which means *display should kind of dereference it and call the function. So why do we need (*display)**();** ?
The **()** at the end was what kept confusing me.

So can I conclude that this is 
1)just syntax and nothing else.
2)Or maybe, I could convince myself as follows
"The same reason why we write display(); and not display; to call a function."

Thanks. :)

Because you can use "display" in context where you don't want to call it right now but merely pass a pointer to it (see "callback"). So in C, it's "display" when considering it's a mere pointer, and "display()" when called. Which makes the syntax with 0 args ("display()") coherent with the syntax for one ore more args ("display(message)").

---

### Post by IAMTubby on 2012-11-14
> **ofnuts said:**
> Because you can use "display" in context where you don't want to call it right now but merely pass a pointer to it (see "callback"). So in C, it's "display" when considering it's a mere pointer, and "display()" when called. Which makes the syntax with 0 args ("display()") coherent with the syntax for one ore more args ("display(message)").
Thanks ofnuts, very useful. :)
(); is for calling, I get it!

---

