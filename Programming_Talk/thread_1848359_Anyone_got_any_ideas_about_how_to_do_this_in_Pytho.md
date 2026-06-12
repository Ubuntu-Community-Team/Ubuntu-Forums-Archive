---
title: "Anyone got any ideas about how to do this in Python?"
date: 2011-09-22
forum: Programming Talk
---

### Post by x-D on 2011-09-22
Hey, does anyone know at all, how you would go about taking a string of text, that is stored in a variable, ie:

z = raw_input("Enter Text here: ")

to a Unicode Hex?

---

### Post by x-D on 2011-09-22
Actually, scrap that. Can you change that to 'convert it to anything that will produce a number value, when encoded?' ie - 23394394934

---

### Post by DangerOnTheRanger on 2011-09-22
Have you tried:
```

z = int(raw_input("Enter Text here: "))

```

If you want "z" to be a hexadecimal string, then use:
```

z = hex(int(raw_input("Enter Text here: "))

```

---

### Post by archeryguru2000 on 2011-09-22
Actually, I believe that throws an error.

```
In [1]: z = hex(int(raw_input("Enter Text here: ")))
Enter Text here: hello
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)

~/<ipython console> in <module>()

ValueError: invalid literal for int() with base 10: 'hello'

```

How about this:

```
z = raw_input("Enter Text here: ").encode('hex')
```

The output to z is:

```
In [2]: z = raw_input("Enter Text here: ").encode('hex')
Enter Text here: hello

In [3]: z
Out[3]: 68656c6c6f

```

Let us know if this is what you were wanting.
~~archery~~

---

### Post by archeryguru2000 on 2011-09-22
Also, the command I posted above will also work with numbers.

```
In [13]: z = raw_input("Enter Text here: ").encode('hex')
Enter Text here: 123

In [1]: z
Out[1]: 313233

In [2]: z = raw_input("Enter Text here: ").encode('hex')
Enter Text here: '123'

In [3]: z
Out[3]: 2731323327

In [4]: z = raw_input("Enter Text here: ").encode('hex')
Enter Text here: 1.23

In [5]: z
Out[5]: 312e3233


```

Hope this helps.

~~archery~~

---

### Post by DangerOnTheRanger on 2011-09-22
Personally, I believe if the user doesn't enter a number, an exception should be thrown anyway; in the face of ambiguity, refuse the temptation to guess, and errors should never pass silently (unless explicitly silenced). Which is why I posted the snippet I did, instead of using your approach.

---

### Post by archeryguru2000 on 2011-09-22
> **DangerOnTheRanger said:**
> Personally, I believe if the user doesn't enter a number, an exception should be thrown anyway; in the face of ambiguity, refuse the temptation to guess, and errors should never pass silently (unless explicitly silenced). Which is why I posted the snippet I did, instead of using your approach.

I suppose so, *but* the OP did ask to convert a string (not a float) to hex.  Just wanted to give what was asked for.  Even though I see your point.

Thanks,
~~archery~~

---

### Post by x-D on 2011-09-22
Cheers for both great replies. I have learnt a lot from this. :)

---

