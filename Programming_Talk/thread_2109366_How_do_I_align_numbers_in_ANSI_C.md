---
title: "How do I align numbers in ANSI C?"
date: 2013-01-27
forum: Programming Talk
---

### Post by s3a on 2013-01-27
I'm attempting to code the Binary Division by Shift and Subtract algorithm ( [http://courses.cs.vt.edu/~cs1104/Division/ShiftSubtract/Shift.Subtract.html](http://courses.cs.vt.edu/~cs1104/Division/ShiftSubtract/Shift.Subtract.html) ) but, I do not understand how to “align [the] leftmost digits in [the] dividend and [the] divisor”.

If more information is needed/wanted, tell me and, I will give it to you.

Any help in figuring this out would be greatly appreciated!

---

### Post by Bachstelze on 2013-01-27
In which language?

---

### Post by s3a on 2013-01-27
ANSI C (as the title suggests).

---

### Post by Bachstelze on 2013-01-27
Sorry, I forgot the title after I read the link. :p

One way to do this would be to find out the position of the leading 1-bit in both numbers (Google will give you some algorithms to do that), compute the difference between them and switch the one whose leftmost 1-bit is furthest to the right by that amount.

---

### Post by ofnuts on 2013-01-27
> **bachstelze said:**
>  and switch the one whose leftmost bid 

iyswim :)

---

### Post by s3a on 2013-01-27
Sorry for the dumb question(s) but, I am very confused.

Is this comparison supposed to happen in a data structure or with a print statement or what?

Could you give me a mini-example please?

---

### Post by steeldriver on 2013-01-27
Well if you're actually implementing the division then you would need to do it on the variables that are holding the values

You should probably do some reading up on arithmetic shifts

[http://en.wikipedia.org/wiki/Arithmetic_shift](http://en.wikipedia.org/wiki/Arithmetic_shift)

In C, the operator you're going to need is the bitwise left shift  '<<' e.g.

```

  unsigned int divisor = 3;
  .
  .
  .
    divisor = divisor << n;

```

---

### Post by s3a on 2013-01-27
Is the following well done?:
```
// Shift and Subtract Algorithm
quotient = 0;

	while(dividend < divisor)
	{
		if(dividend >= divisor)
		{
			dividend = dividend - divisor;
			quotient = quotient << 1;
		}
		else
		{
			quotient = quotient << 0;
		}
		
		divisor = divisor >> 1;
	}
}
```

---

### Post by s3a on 2013-01-27
Wait, something is wrong since the inner if statement will never get executed since it is the negation of the while loop's boolean statement.

Could someone please help me out? I'm trying to implement the algorithm here ( [http://courses.cs.vt.edu/~cs1104/Division/ShiftSubtract/Shift.Subtract.html](http://courses.cs.vt.edu/~cs1104/Division/ShiftSubtract/Shift.Subtract.html) ).

---

### Post by Bachstelze on 2013-01-27
> **s3a said:**
> Is the following well done?:


Maybe. Does it give correct results?

---

