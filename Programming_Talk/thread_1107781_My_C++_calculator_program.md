---
title: "My C++ calculator program"
date: 2009-03-27
forum: Programming Talk
---

### Post by gralco on 2009-03-27
I still want to add more code but here's the C++ calculator program I wrote so far, read the instructions I put on how to use it, tell me what you think, give me some ideas:

[http://paste.ubuntu.com/138813/](http://paste.ubuntu.com/138813/)

I also have another build of one with more instructions after entering a value and/or an arithmetic operator:

[http://paste.ubuntu.com/138817/](http://paste.ubuntu.com/138817/)

I've attached the build of the code for amd64 architectures.

---

### Post by simeon87 on 2009-03-27
goto should not be used, it's better to rewrite it without goto as goto will turn your code into [spaghetti code](http://en.wikipedia.org/wiki/Spaghetti_code) (it already does on this small scale). It's better to use functions to control the flow of the program.

Also see [Go To Statement Considered Harmful](http://www.u.arizona.edu/~rubinson/copyright_violations/Go_To_Considered_Harmful.html) from Edsger W. Dijkstra.

---

### Post by gralco on 2009-03-27
> **simeon87 said:**
> goto should not be used, it's better to rewrite it without goto as goto will turn your code into [spaghetti code](http://en.wikipedia.org/wiki/Spaghetti_code) (it already does on this small scale). It's better to use functions to control the flow of the program.

Also see [Go To Statement Considered Harmful](http://www.u.arizona.edu/~rubinson/copyright_violations/Go_To_Considered_Harmful.html) from Edsger W. Dijkstra.

Right, spaghetti code, I forgot that goto statements get sloppy, I'll fix it up and post a build without any. Thanks for the help.

---

### Post by benj1 on 2009-03-27
looks good, i did one a few months ago.
i would suggest using 

getline(cin,string); instead of cin

brackets would also be useful and pretty easy to implement

---

### Post by dwhitney67 on 2009-03-27
I took a peek at both of your code samples.  They are both valiant starts to C++ coding, but unfortunately not very impressive.

For starters, aside from the usage of cout/cin, the code resembles a BASIC application that has been translated into C/C++ syntax.  The 'goto' statements are very inappropriate for either C or C++ applications.

Secondly, I would have expected the calculator to handle more complex operations, even something as simple as 5 + 4 * 3 (which should yield 17).  Typically one would employ the use of a stack container (maybe two containers) to store values an operators so that operations can be performed in the appropriate order.  Using the example equation above, the stack would contain values such as: 5 4 3 * +

These values are obtained from converting an infix-notation equation into postfix-notation (research Google concerning these topics).

Once the stack has been populated, you then just pop an operator from the stack, looking for two values on which to perform the operation.  This procedure may involve recursion, because there is no guarantee that the item item in the stack that is after the operator is a value; it may be another operator.

The whole procedure get slightly more complicated if the use of parenthesis () are allowed.

Anyhow, I'm sure there are countless code examples for calculators that are available on the web.  Just make sure they are employing a stack.  Without a stack, the application perhaps only employs the most basic of operations.

Btw, when dividing two values, make sure that the divisor is NOT zero.  You failed to check this in your application.

---

### Post by darthmob on 2009-03-27
I have to post it.

[IMG]http://imgs.xkcd.com/comics/goto.png[/IMG]

---

### Post by benj1 on 2009-03-27
@ dwhitney67
i implemented mine as a string expanding the brackets then iterating over the sum till i had one number, i agree not the best way technically, but it works, and in that case would be quite easy to implement brackets

@darthmob
lol its annoying when that happens :)

---

### Post by gralco on 2009-03-27
> **dwhitney67 said:**
> I took a peek at both of your code samples.  They are both valiant starts to C++ coding, but unfortunately not very impressive.

For starters, aside from the usage of cout/cin, the code resembles a BASIC application that has been translated into C/C++ syntax.  The 'goto' statements are very inappropriate for either C or C++ applications.

Secondly, I would have expected the calculator to handle more complex operations, even something as simple as 5 + 4 * 3 (which should yield 17).  Typically one would employ the use of a stack container (maybe two containers) to store values an operators so that operations can be performed in the appropriate order.  Using the example equation above, the stack would contain values such as: 5 4 3 * +

These values are obtained from converting an infix-notation equation into postfix-notation (research Google concerning these topics).

Once the stack has been populated, you then just pop an operator from the stack, looking for two values on which to perform the operation.  This procedure may involve recursion, because there is no guarantee that the item item in the stack that is after the operator is a value; it may be another operator.

The whole procedure get slightly more complicated if the use of parenthesis () are allowed.

Anyhow, I'm sure there are countless code examples for calculators that are available on the web.  Just make sure they are employing a stack.  Without a stack, the application perhaps only employs the most basic of operations.

Btw, when dividing two values, make sure that the divisor is NOT zero.  You failed to check this in your application.

I haven't learn of LIFO stack yet, I'm studying how they operate now, thanks for your advice. The program still out puts an error if the divisor is in fact a zero by default in C++, though I could still place my own error. Thank you once again.

---

