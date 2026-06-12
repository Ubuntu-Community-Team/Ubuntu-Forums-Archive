---
title: "Math.random() in java"
date: 2008-07-24
forum: Programming Talk
---

### Post by ogwilson on 2008-07-24
I can't use Math.random() to initialize an integer array with random numbers? Its saying my array can only be of type double. Why would this be?

heres my netbeans error:

> found   : double
required: int
            numbers[i] = Math.random();
                                    ^
1 error
BUILD FAILED (total time: 0 seconds)

---

### Post by scragar on 2008-07-24
cast it to int?
```
numbers[i] = (int) Math.random();
```

---

### Post by hod139 on 2008-07-24
> **scragar said:**
> cast it to int?
```
numbers[i] = (int) Math.random();
```

Math.random() returns a random float between 0 and 1.  Casting that to an int is always going to be a 0 (not very random).  You need to use Java's Random class.

```

Random rng = new Random (seed);
rng.nextInt(n); // produces random number between 0 and n-1

```

---

### Post by scragar on 2008-07-24
I've never used java before, so my guess was based on a quick google search and my experience with PHP(why does it say double instead of float in the error though? Double in all languages I know is for large numbers, float is for fractions and numbers larger than that...)

---

### Post by ogwilson on 2008-07-24
> **hod139 said:**
> Math.random() returns a random float between 0 and 1.  Casting that to an int is always going to be a 0 (not very random).  You need to use Java's Random class.

```

Random rng = new Random (seed);
rng.nextInt(n); // produces random number between 0 and n-1

```

Hi Im not sure how to use your code in my context. Here's my method thus far:

```
    public static void initArray(int[] numbers)
    {
         for(int i = 0; i < numbers.length; i++)
        {
             numbers[i] = Math.random();
        }
    }
```

---

### Post by ogwilson on 2008-07-24
Ok thanks I looked at java documentation and see how to use it now. Weird that math.random() only supports doubles between .01 and .09.

---

### Post by hod139 on 2008-07-24
I don't have a java compiler on my laptop, but something like
```
    
public static void initArray(int[] numbers)
{
    Random rng = new Random (seed); // seed is an int to seed the random number generator
    for(int i = 0; i < numbers.length; i++)
    {
         numbers[i] = rng.nextInt(n); // produces random int between 0 and n-1            
    }
}
```

---

### Post by Zugzwang on 2008-07-25
> **ogwilson said:**
> Weird that math.random() only supports doubles between .01 and .09.

Huh? It returns a number between 0 (including) and 1 (excluding), which makes perfectly sense.

---

### Post by ogwilson on 2008-07-25
I don't think it makes perfect sense. How so?

---

### Post by hod139 on 2008-07-25
> **ogwilson said:**
> I don't think it makes perfect sense. How so?
In the real number system, there are as many numbers in the range [0, 1) as there is in the range [0, \inf).   Therefore, when generating a floating point number, it is sufficient to generate a number between [0, 1) and scale it to the range of floating point numbers you want.  
x = Math.random()*M; // x is a random floating point number between [0, M), that is not including M

---

