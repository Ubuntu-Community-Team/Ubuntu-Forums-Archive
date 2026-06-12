---
title: "Java: Infinite For Loop {For()}"
date: 2009-10-09
forum: Programming Talk
---

### Post by Dark Aspect on 2009-10-09
How do I create an infinite for loop? I know that

```
for ( int x = 1; x<= 10; x++)
```

Counts to 10 but how I represent the highest (Infinite) number in Java?

Thanks for a clarity on this. Oh and while I am at it I need to know how to do a do while loop that loops for 10 times?

Yes this is homework related if someone is getting suspicions, but its for an open lob that I can get outside help for.

---

### Post by PaulM1985 on 2009-10-09
If you want an infinite loop you could use:

while (true)
{

}



If you insist on it being a for loop:

int y = 1;

for (int x=0; y<10; x++)
{

}


Paul

---

### Post by wojox on 2009-10-09
```

var i = 0;
while(i < 10)
{
   document.writeln("Inside loop number " + i + "<br>"); 
   i++;
}

```

For an infinite loop just take your for loop and make x > 0

---

### Post by Dark Aspect on 2009-10-09
> **PaulM1985 said:**
> If you want an infinite loop you could use:

while (true)
{

}



If you insist on it being a for loop:

int y = 1;

for (int x=0; y<10; x++)
{

}


Paul

Thanks Paul, Yes it has to be a for loop. I had already done the other assignments the same as the first part since its a little easier to understand IMO.

Edit: Whats left on my assignment if your wondering is

Write a for loop that loops 50 times?
 
I believe that the code for this would be

```
for ( int x = 1; x<= 50; x++)
```

Print the alphabet backwards?

My current answer:

```
        {

        char x = 'z';

        while (x >= 'a')

	  {

	   System.out.println(x);

           x++;

	  }

```

Use a do while() loop to loop 10 times?

Haven't got this far, it would be helpful if you just showed me what a do while looks like.

---

### Post by jeremyswalker on 2009-10-09
Couldn't you use the following for an infinite loop:
```
for(;;)
{

}
```
or if you need to have a variable
```
for(i=0;;i++)
{

}
```

---

### Post by PaulM1985 on 2009-10-09
> **Dark Aspect said:**
> Thanks Paul, Yes it has to be a for loop. I had already done the other assignments the same as the first part since its a little easier to understand IMO.

Just need to understand that in the for() case, condition is always true because in the example y will always be less than 10.  Just in the same way that 

while(true)

the case for the while loop is always true.

I guess for (int i=0; true; i++)  may be used, or even for (; true; ).

Not sure if they would compile though.  Just ideas.

Paul

---

### Post by PaulM1985 on 2009-10-09
> **jeremyswalker said:**
> Couldn't you use the following for an infinite loop:
```
for(;;)
{

}
```
or if you need to have a variable
```
for(i=0;;i++)
{

}
```

Does no condition count as a true condition?

---

### Post by Dark Aspect on 2009-10-09
> **PaulM1985 said:**
> Does no condition count as a true condition?

I don't think that would compile, I am going to try it since I am a Java newbie.

---

### Post by jeremyswalker on 2009-10-09
I am 95% positive I've used "for( ; ; ){ }" as an infinite loop before.

---

### Post by Npl on 2009-10-09
> **PaulM1985 said:**
> Does no condition count as a true condition?Yep, atleast does for C/C++. Actually many compilers warn for an useless conditional statement (always true) if you use other constructs than "for (;;)".

---

### Post by PaulM1985 on 2009-10-09
Cool, I didn't know that.

---

### Post by Gwasanaethau on 2009-10-09
Hi DarkAspect,

I'd compile and run this to make sure it does what the question asks. Something tells me you might get different results to what you expect&#8230;
> **Dark Aspect said:**
> &#8230;
Print the alphabet backwards?

My current answer:

```
        {

        char x = 'z';

        while (x >= 'a')

	  {

	   System.out.println(x);

           x++;

	  }

```

&#8230;
Just thought I'd let you know! ;)

EDIT & HINT: If you're running from the terminal, Ctrl-C might be useful in case you need to stop your programme!

---

### Post by Dark Aspect on 2009-10-09
> **Gwasanaethau said:**
> Hi DarkAspect,

I'd compile and run this to make sure it does what the question asks. Something tells me you might get different results to what you expect…

Just thought I'd let you know! ;)

EDIT & HINT: If you're running from the terminal, Ctrl-C might be useful in case you need to stop your programme!

uh yeah, luckily I am just adding break at the end of everything right now :)

---

### Post by Gwasanaethau on 2009-10-09
I wouldn't say you need any **break** statements here, your code is very good. The only thing I'd say is to take another look at your iterator (the **x++;** bit). ;)

P.S. Well done for getting stuck in, you seem to be doing well!

---

### Post by Dark Aspect on 2009-10-09
> **Gwasanaethau said:**
> I wouldn't say you need any **break** statements here, your code is very good. The only thing I'd say is to take another look at your iterator (the **x++;** bit). ;)

P.S. Well done for getting stuck in, you seem to be doing well!

X--

........Blast, thats not the first time I've done that. I did that in class yesterday.

---

### Post by Gwasanaethau on 2009-10-09
And it won't be the last, I can guarantee you! ;) Many times I've had all kinds of madness spewing out of the console after little things like that! Problem is they're very hard to track as the compiler thinks everything's OK…

---

### Post by SecretCode on 2009-10-11
Although [FONT="Courier New"]while (true)[/FONT] is the best option, and [FONT="Courier New"]for (int i = 0;; i++)[/FONT] is best if it has to be a for loop ... technically you can put an upper bound on the loop: 

```
// if there has to be an upper bound
for (int i = 0; i < Integer.MAX_VALUE; i++) {
	System.out.println(i);
}
```

---

### Post by unknownPoster on 2009-10-11
> **SecretCode said:**
> Although [FONT=Courier New]while (true)[/FONT] is the best option, and [FONT=Courier New]for (int i = 0;; i++)[/FONT] is best if it has to be a for loop ... technically you can put an upper bound on the loop: 

```
// if there has to be an upper bound
for (int i = 0; i < Integer.MAX_VALUE; i++) {
    System.out.println(i);
}
```

I'm not convinced that this would create an infinite loop. Integer.MAX_VALUE is a constant representing 2^31-1 therefore, given a sufficient amount of time, this loop would run to completion.

---

### Post by SecretCode on 2009-10-11
True! I failed to test my code :)

This should work:
```
for (int i = 0; i <= Integer.MAX_VALUE; i++) {
    System.out.println(i);
}

```
In fact this does (produce an infinite loop, that is):
```
for (byte b = 0; b <= Byte.MAX_VALUE; b++) {
	System.out.println(b);
}
```

- because Java doesn't implement overflow/bounds checking and happily wraps the value.

---

### Post by MrStill on 2009-10-11
> **Dark Aspect said:**
> How do I create an infinite for loop? I know that

```
for ( int x = 1; x<= 10; x++)
```

Counts to 10 but how I represent the highest (Infinite) number in Java?


infinite for loop:
```

for(int x = 0; true; x++){
        // s.o.p(x) if needed
}

```

the middle expression in a for loop is a boolean expression and execution will continue until this condition returns false. Obviously, placing the boolean value true in that place will never allow it to be false. You can increment x and print if needed. Your problem is that int is a 32 bit value and so the highest int can go is 2^32 roughly divided by 2 (for 2s complement signed bit). Longs and doubles reach much higher values see: [http://java.sun.com/docs/books/tutorial/java/nutsandbolts/datatypes.html](http://java.sun.com/docs/books/tutorial/java/nutsandbolts/datatypes.html) for more information on how hight primitive types can count in Java.


count 1 to 10 with while:
```

x = 1;
while(x++ > 10){
        // s.o.p(x) if needed
}

```

---

### Post by Gwasanaethau on 2009-10-11
> **MrStill said:**
> …count 1 to 10 with while:
```

x = 1;
while(x++ > 10){
        // s.o.p(x) if needed
}

```
Sorry to stop you there, MrStill, but there's a couple of things that need to be noted here. First of all, you probably meant
```
x = 1;
**while(x++ < 10)**
        // s.o.p(x) if needed
}
```
otherwise the loop wouldn't run at all (1 &#8815; 10). Secondly, there's the problem that when the conditions for the while loop are tested for the first time, x == 1. However, by the time the loop itself runs and **s.o.p(x)** is called, **2** will be printed to the console (not 1). A suggestion on how to fix these would be:
```
x = 1;
while(x < 10)
        // s.o.p(x++) if needed
}
```

---

