---
title: "What is wrong with my Java source code?"
date: 2007-06-22
forum: Programming Talk
---

### Post by reidms on 2007-06-22
Hello-
I recently made a program for a banking simulation- I am to make a program that:
Starts off with 14000 in the bank
First year I get 40 percent interest on the 14000
Second year I loose 1500
Third year I get 12 percent interest.

Here is my banking.java source code
```
public class banking {                                                          
    public static void main(string[] arguments) {                               
        int inv = 14000;                                                        
        int x;                                                                  
        int y;                                                                  
        System.out.printIn("Balance is" + inv);                                 
        x = inv * .4;                                                           
        inv = inv + x;                                                          
        System.out.printIn("First Year" + inv);                                 
        inv = inv - 1500;                                                       
        System.out.printIn("Second Year" + inv);                                
        y = inv * .12;                                                          
        inv = inv + y;                                                          
        System.out.printIn("Third Year" + inv);                                 
        }                                                                       
} 
```

Here is the error I receive after compiling it:
```
bash-3.00$ javac banking.java
banking.java:2: cannot find symbol
symbol  : class string
location: class banking
    public static void main(string[] arguments) {
                            ^
banking.java:6: cannot find symbol
symbol  : method printIn(java.lang.String)
location: class java.io.PrintStream
        System.out.printIn("Balance is" + inv);
                  ^
banking.java:7: possible loss of precision
found   : double
required: int
        x = inv * .4;
                ^
banking.java:9: cannot find symbol
symbol  : method printIn(java.lang.String)
location: class java.io.PrintStream
        System.out.printIn("First Year" + inv);
                  ^
banking.java:11: cannot find symbol
symbol  : method printIn(java.lang.String)
location: class java.io.PrintStream
        System.out.printIn("Second Year" + inv);
                  ^
banking.java:12: possible loss of precision
found   : double
required: int
        y = inv * .12;
                ^
banking.java:14: cannot find symbol
symbol  : method printIn(java.lang.String)
location: class java.io.PrintStream
        System.out.printIn("Third Year" + inv);
                  ^
7 errors

```

Sorry for being a Java newb 
Thanks for your time!

---

### Post by betamike on 2007-06-22
> **reidms said:**
> 
```
public class banking {                                                          
    public static void main(string[] arguments) {                               
        int inv = 14000;                                                        
        int x;                                                                  
        int y;                                                                  
        System.out.printIn("Balance is" + inv);                                 
        x = inv * .4;                                                           
        inv = inv + x;                                                          
        System.out.printIn("First Year" + inv);                                 
        inv = inv - 1500;                                                       
        System.out.printIn("Second Year" + inv);                                
        y = inv * .12;                                                          
        inv = inv + y;                                                          
        System.out.printIn("Third Year" + inv);                                 
        }                                                                       
} 
```


Your problem is that you declared x and y as ints and are assigning them doubles.  to fix this, declare x and y as doubles.  Secondly, you used 
```
 
System.out.printIn(...);

```
but its actually:
```

System.out.print**ln**(..);

```

'println' = print line.

Lets see, simple mistake; **S**tring[] must be capitalized.

Also, just as an aside, you could condense the whole thing by declaring inv as a double, and then doing your calculations in one line, like
```

inv = inv * 1.4;

```
or even
```

inv *= 1.4;

```

---

### Post by raul_ on 2007-06-22
javac is the stupidest compiler i've worked with

you should use the suggestion above of using inv as an absolute value. Let's imagine that later in the code, in another method, you want to know how much money there is. You won't know whether to call x or y. Of course this isn't necessary, but it's just good programming :) it may help you later, in other programs

---

### Post by betamike on 2007-06-22
Well, he was just using x and y as temp variables.  inv always held the total amount.

---

### Post by raul_ on 2007-06-22
Oh indeed. I only looked to the code you posted so I missed it :) nevertheless, it's less 8 bytes xD

---

### Post by reidms on 2007-06-22
Wow- thanks for the informative posts guys!

I only used the temp variables because I did not think about multiplying by 1.X to get a percent :P
Good idea :D

I have fixed my code best to my knowlege- but I do not know what you mean betamike when you say to declare inv as double

Could you explain?

Here is banking.java now
```
public class banking {                                                          
    public static void main(String[] arguments) {                               
        int inv = 14000;                                                        
        System.out.println("Balance is" + inv);                                 
        inv = inv * 1.4;                                                        
        System.out.println("First Year" + inv);                                 
        inv = inv - 1500;                                                       
        System.out.println("Second Year" + inv);                                
        inv = inv * 1.12;                                                       
        System.out.println("Third Year" + inv);                                 
        }                                                                       
} 
```

Also- do I need a class for this?(I think it is a class- a "template" of a program-)

Thanks for your time and help!

---

### Post by raul_ on 2007-06-22
double inv = 14000;

---

### Post by Catsworth on 2007-06-22
You will also want to put a space at the end of your string to be concatenated:

```

System.out.println("Balance is" + inv);

```

Will print:

```
Balance is14000
```

Whereas:

```

System.out.println("Balance is " + inv);

```

Will print:

```

Balance is 14000

```

Note the space between the "is" and int :D

---

### Post by reidms on 2007-06-22
Excellent- and thanks Catsworth on the heads up about my strings--

```
java banking
Balance is 14000.0
First Year 19600.0
Second Year 18100.0
Third Year 20272.000000000004
```


So double is a type of variable- like byte, short, in, long, float etc?

Also- the reason why I am using javac is that it is basic, and I am on SPARC(not many other options).

Thanks,
             Reid

---

### Post by jespdj on 2007-06-22
Yes, 'double' is a variable type.

Have a look at [The Java Tutorial](http://java.sun.com/docs/books/tutorial/).
Do you have a book to learn Java from?

---

### Post by kknd on 2007-06-22
Some advices:

- Replace var = var + 2 with var += 2 (for example). Its faster (and clearer in my opinion).

- Class names are supposed to begin with a capitalized letter like "Bank";

- After do that tests, try to make a separate class that deals with Bank thing (like an Account, that have deposit, print the account status, to begin to learn Object Orientation.

Sorry for my bad english =S.

---

### Post by reidms on 2007-06-22
> Do you have a book to learn Java from?
The book I am learning from is called *Java 6 in 21* Days by Sams
I think it is the newest Java book out there- since it was release in late May.

> - Replace var = var + 2 with var += 2 (for example). Its faster (and clearer in my opinion).

The book did inform me of that- but I plan to keep it basic right now until I get a bit better



> - After do that tests, try to make a separate class that deals with Bank thing (like an Account, that have deposit, print the account status, to begin to learn Object Orientation.

Yes I am familiar with a class-  It would be a template-
So something like this-
```
public class Banking {
    public static void main(String[] arguments) {
	double inv =  amnt;
	System.out.println("Balance is " + inv);
	inv = inv * f;
	System.out.println("First Year " + inv);
	inv = inv - s;
	System.out.println("Second Year " + inv);
        inv = inv * t;
	System.out.println("Third Year " + inv);
	}
}

```


Also, your English is better than some native speakers :p

Thanks for your time

---

