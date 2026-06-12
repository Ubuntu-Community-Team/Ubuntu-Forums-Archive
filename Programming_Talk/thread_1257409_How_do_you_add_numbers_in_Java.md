---
title: "How do you add numbers in Java?"
date: 2009-09-03
forum: Programming Talk
---

### Post by s3a on 2009-09-03
5 + 2 = 7

but

int pennies = kb.nextInt();
int pennies2 = kb.nextInt();

System.out.println(pennies + pennies2);

if pennies = 1 and pennies2 = 2, then I get 12 instead of 3. What is the workaround to get my desired result?

Any input would be greatly appreciated!
Thanks in advance!

---

### Post by king vash on 2009-09-03
println(1 + 2);
will print the sting "1" concatenated (added) to the string "2"
instead use println((1+2));

---

### Post by s3a on 2009-09-03
Actually println(1 + 2); gives 3 and not 12 (tested it). My problem is when the numbers are variables (ie pennies and pennies2). Adding the extra brackets has no effect on the output either.

---

### Post by Dougie187 on 2009-09-03
You could always store it as a temporary variable, and then print that. I don't think variable arithmetic is handled in a println. but i may be incorrect.

---

### Post by features on 2009-09-03
> **s3a said:**
> 5 + 2 = 7

but

int pennies = kb.nextInt();
int pennies2 = kb.nextInt();

System.out.println(pennies + pennies2);

if pennies = 1 and pennies2 = 2, then I get 12 instead of 3. What is the workaround to get my desired result?



It is Java's autoboxing of Integer objects that is doing this.  What it's doing, is thinking that those ints are really Integers, then calling toString() on them.  Surrounding the operation in parentheses anfd adding it to an empty string forces java to evaluate them as ints, and do the addition first.

```
System.out.println("" + (pennies + pennies2));
```

For more autoboxing fun, try working with an ArrayList of Integers :D

---

### Post by Volt9000 on 2009-09-03
> **features said:**
> It is Java's autoboxing of Integer objects that is doing this.  What it's doing, is thinking that those ints are really Integers, then calling toString() on them.  Surrounding the operation in parentheses anfd adding it to an empty string forces java to evaluate them as ints, and do the addition first.

```
System.out.println("" + (pennies + pennies2));
```

For more autoboxing fun, try working with an ArrayList of Integers :D

Although that will work, it's a big kludgy IMHO. I prefer

```

int total = pennies + pennies2;
System.out.println(total);

```

---

### Post by features on 2009-09-03
> **Volt9000 said:**
> Although that will work, it's a big kludgy IMHO. I prefer

```

int total = pennies + pennies2;
System.out.println(total);

```

Yeah go for that solution :D ... far more elegant.  Though my one stands as an illustration of what Java thinks it's doing in a out.println...

---

### Post by abhilashm86 on 2009-09-04
> **s3a said:**
> 5 + 2 = 7

but

int pennies = kb.nextInt();
int pennies2 = kb.nextInt();

System.out.println(pennies + pennies2);

if pennies = 1 and pennies2 = 2, then I get 12 instead of 3. What is the workaround to get my desired result?

Any input would be greatly appreciated!
Thanks in advance!

Actually when you use kb.nextInt(), are you using Random number generator? I don't see you initializing values......
what is kb's ,main class, what is inherited by kb, i guess its random number genrator?

---

### Post by Reiger on 2009-09-04
> **abhilashm86 said:**
> Actually when you use kb.nextInt(), are you using Random number generator? I don't see you initializing values......
what is kb's ,main class, what is inherited by kb, i guess its random number genrator?
He's been posting other threads with homework problems had: kb consistently featured as a Scanner object there (I presume it stands for keyboard). But anyways, nextInt() etc. are Scanner methods -- not random number generating ones. (Which would be static calls to a Math method.)

---

### Post by pbrockway2 on 2009-09-04
String concatenation?  Autoboxing?  Argument expression not being evaluated?

```

public class PrintlnTest {
    public static void main(String[] args) {
        int pennies = 1;
        int pennies2 = 2;
        System.out.println(pennies + pennies2);
    }
}

```

Output:
> 
3


Just saying.

---

### Post by s3a on 2009-09-04
I solved it by doing something like:

comb = pennies + pennies2

System.out.println(comb);

---

### Post by defacto on 2009-09-04
```
int var1 = 5;
int var2 = 8;

System.out.println("The result is " + (var1 + var2));

```

Basically, if you want to do arithmetic operations in println function, you need to enclose them into brackets.

---

### Post by PandaGoat on 2009-09-04
*Another* case of not showing all of the code.

As pbrockway2 verfied, you cleary did not show everything.

To be explicit on what I think your code actually is and why it is wrong, I wager that you have System.out.println("Some string" + pennies + pennies2);

In java, the concatination operator, +, is overloaded to take more than just a string.  How + is interpreted is based on context.  If the first occuring object is a string, then the following +'s will be interpreted as concatination (with the exception of +'s within parenthases where the same process is (recursively) followed from the beginning).

Hence, if you have "Some string" + pennies + pennies2, the +'s will be interpreted as concatination and not addition.  However, to exemplify, if you have pennies + pennies2 + "some string" the first + will be interpreted as addition and the second will be interpreted as concatination (since it has no other interpretation--int + string must be concatination).

You can solve all ambiguities by including parenthasese.  (pennies + pennies2) is interpretted as addition no matter where this expression is placed.

Hopefully this helped and remember next time to post ***ALL*** of your code if you want help.

---

### Post by wmcbrine on 2009-09-04
From some of the answers given in this thread, I can only conclude that programming in Java drives people to madness. :o

---

### Post by socool274 on 2009-09-04
Print takes a string, when you added them, java assumed string. When using string concatenation, it is seen as saying "1"+"2" (12). Another way of going about adding them, and printing the output, would be to say:
System.out.println("%i", 1+2)

This takes the output of 1+2 (assumed int), and puts it in (replacing) for %i. %i determines the variable type to be put in i is for int.

---

### Post by pbrockway2 on 2009-09-04
> **socool274 said:**
> Print takes a string, when you added them, java assumed string.

No, it does not.  The [API docs]("http://java.sun.com/javase/6/docs/api/java/io/PrintStream.html") for PrintStream's println() lists umpteen versions of this method: it will print whatever you throw at it.

If you want to print strings - concatenation and all - pass it a reference to a String (or some other reference where String's valueOf() will be called to provide the String).  But if you want to print an integer value that results from some expression, just use that expression as the argument: println() will do the right thing as documented in the link given above.

I would underline the point implicit in what PandaGoat said: parentheses aside, Java is strictly a left-to-right affair.  This helps make sense of

```

System.out.println(pennies + pennies2 + " is the answer");
    // vs
System.out.println("The answer is " + pennies + pennies2);

```

> Another way of going about adding them, and printing the output, would be to say:
System.out.println("%i", 1+2)

This takes the output of 1+2 (assumed int), and puts it in (replacing) for %i. %i determines the variable type to be put in i is for int.

I think you mean

```

System.out.printf("%d", pennies + pennies2);

```

---

### Post by socool274 on 2009-09-06
Yeah, I didn't know whether it would be i, or d. i seemed logical.

---

### Post by pbrockway2 on 2009-09-06
> **socool274 said:**
> Yeah, I didn't know whether it would be i, or d. i seemed logical.

It's d for "**d**ecimal".  With *numerals* (strings representing numeric values) there is a concept of "base" that plays no part in the numeric value.  What I mean is that half a dozen eggs are always half a dozen - the numeric value doesn't change.  But the numerals used to represent this value can be as different as "6", "110" and "VI".

---

