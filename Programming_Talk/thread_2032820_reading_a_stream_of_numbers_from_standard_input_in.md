---
title: "reading a stream of numbers from standard input in java"
date: 2012-07-24
forum: Programming Talk
---

### Post by Mia_tech on 2012-07-24
guys, I'm trying to read a stream of numbers from standard input like: 2 3 -3 10 44 9 -1. The line ends once it read -1, but for some reason I have an endless loop... how could I read this stream of numbers one number at a time?

```
int num[] = new int[5];
        char ch;
 
        BufferedReader bf = new BufferedReader(new InputStreamReader(System.in));
        System.out.println("enter series of number: ");         
        int i = 0;
         do{ 
             num[i] = bf.read();
             i++;                     
        }while(num[i] != -1);
 
         int j = 0;
         while(j < num.length) {
             System.out.println(num[j]);
             j++;
         }
```

---

### Post by dwhitney67 on 2012-07-24
It sure would have been nice if you had posted all of your code, so that I could copy it, compile it, and then run it for myself.

Frankly, just doing a static analysis of your code, I would have expected it to throw an exception if it were to attempt to read more than 5 int values, as you have shown in your example input data.

But as for the crux of the problem, you are incrementing the variable 'i' in the do-while loop and *then* you are checking for the -1.  Try using 'i - 1' in the conditional statement in the do-while loop.


P.S.  The BufferReader's read() method can throw an IOException, yet I do not see in your code where you are handling that.

P.S #2  I just realized... read() returns a single character; not an int value as you have assumed.  You may want to consider using Scanner (w/ the System.in as its arg) for reading numbers.  The alternative is to call readLine() method of BufferReader and then convert the string to an int using Integer.parseInt().

---

### Post by Mia_tech on 2012-07-24
> **dwhitney67 said:**
> It sure would have been nice if you had posted all of your code, so that I could copy it, compile it, and then run it for myself.

Frankly, just doing a static analysis of your code, I would have expected it to throw an exception if it were to attempt to read more than 5 int values, as you have shown in your example input data.

But as for the crux of the problem, you are incrementing the variable 'i' in the do-while loop and *then* you are checking for the -1.  Try using 'i - 1' in the conditional statement in the do-while loop.


P.S.  The BufferReader's read() method can throw an IOException, yet I do not see in your code where you are handling that.

P.S #2  I just realized... read() returns a single character; not an int value as you have assumed.  You may want to consider using Scanner (w/ the System.in as its arg) for reading numbers.  The alternative is to call readLine() method of BufferReader and then convert the string to an int using Integer.parseInt().

I used an scanner in my original code.. I guess I posted wrong line of code

---

### Post by PaulM1985 on 2012-07-25
So do you want to post all of your code?  Did you solve your problem?

---

