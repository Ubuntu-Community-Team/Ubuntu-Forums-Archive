---
title: "Java: Squares less than n"
date: 2012-10-08
forum: Programming Talk
---

### Post by Litost on 2012-10-08
I have to write a program which prints all squares less than a value of n. I have this:

```
    int n = 0;
    int x = 0;
        while (x < 100)
        {
            x = n*n;
            System.out.print(x + " ");
            n = (n + 1);
        }
```
My problem is the output includes 100. Where did I go wrong? Is this just a fluke because 100 happens to be a perfect square? Is there anyway to fix it?

---

### Post by Litost on 2012-10-08
I fixed a flaw so it makes more sense to the goal of the program:

```
        Scanner in = new Scanner(System.in);
    System.out.print("Please enter an integer: ");
    int i = 0;
    int x = 0;
    int n = in.nextInt();
        while (i < n)
        {
            i = x*x;
            System.out.print(i + " ");
            x = (x + 1);
        }

```
but still the same problem as it will output 100 if I enter 100.
*Apparently if I enter 90 for n it still outputs 100. I see the problem is after 9x9 it goes to 10x10, but I see no way to fix this problem.

---

### Post by Some Penguin on 2012-10-08
while() loops test *before* executing each iteration, only.  They don't get magically retested during the execution of the loop itself. 

In your case, the fix is as simple as moving one line...

---

### Post by lisati on 2012-10-08
@Litost: I've added [noparse]```
 and 
```[/noparse] tags to your program listings. This can help readability. As well as this, *some* (but by no means all) language processors can alter their "understanding" of code if indentation is off by just one column.

---

### Post by r-senior on 2012-10-08
An alternative way to do this is to use the square root as the limit:

```
for (int i = 1; i < Math.sqrt(n); i++) {
    System.out.printf("%d ", i * i);
}

```

---

### Post by trent.josephsen on 2012-10-08
Math.sqrt() is susceptible to floating-point rounding errors for some values of n.

---

### Post by Vaphell on 2012-10-08
on the other hand i*i < n is not :)

---

### Post by Litost on 2012-10-08
Thanks everyone for your responses!
> **Some Penguin said:**
> while() loops test *before* executing each  iteration, only.  They don't get magically retested during the execution  of the loop itself. 

In your case, the fix is as simple as moving one line...
Yes, I am aware that it wouldn't "magically" get retested mid-execution. I did mention that I see the problem is that it will go to 10x10 because i has not yet reached the value of n. Please remember that I am posting here with such a basic question because I am in the basic stages of learning! I have been learning Java for not even a month yet.  I understand it's hard to relate to a beginner at this point for you but keep that in mind.

I'd like to further question what everyone meant about indentation and moving a line? My solution was influenced by Vaphell's post. I didn't think that I could change the while loop to be
```
while ((x*x) < n)
```
without getting a syntax error! However I'm still curious as to what the alternative solution was you guys were hinting to?

---

### Post by Vaphell on 2012-10-08
you are at n=9
x < 100 so
x=81, print x, n=10
now you test x < 100 again, but x still fits (81 from the earlier run). You update the value later, inside the loop body but that means that you will print it, no matter the value. Long story short x lags n by 1 iteration.
If you reordered code to:
while x<100
- print x (starting value or value(n) carried from last iteration)
- update the value of n
- update the value of x
there would be no lag and condition would react with no delay, never allowing 100 to be printed out
(n=9/x=81: print 81; n=10; x=100; while 100<100 -> end)


and yes, you can write conditions as complicated as you wish, as long as both sides of the comparison evaluate to the same type... and you can chain these true/false elements  according to rules of boolean logic.

---

### Post by Litost on 2012-10-08
Thank you so much! I'll keep order in mind in the future.

---

