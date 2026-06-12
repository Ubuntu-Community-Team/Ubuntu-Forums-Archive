---
title: "Python Rounding"
date: 2011-09-18
forum: Programming Talk
---

### Post by noodleman999 on 2011-09-18
So, i need to round a number, but the number can't be a decimal number.
So it can't be fx 40.0, it must be 40
And it's rounding to a precision of 1, so 40.1 would be rounded to 40.
Thanks ahead.

---

### Post by JDShu on 2011-09-18
I would use the round function and then cast the result as an int.

---

### Post by noodleman999 on 2011-09-19
I tried, but it didn't work in this case of some reason. Well, it worked, but not fully.
Trying to find out if the problem is something else, which is what I really DON'T hope.

---

### Post by ofnuts on 2011-09-19
> **noodleman999 said:**
> Well, it worked, but not fully.Cana you elaborate on that (input and expected/effective results)? And what is your definition of "round"?

---

### Post by noodleman999 on 2011-09-19
Okay, i'm currently making a PyGame program, and i want the background to slowly change from black to green, and back.
Therefore, i can't use +1, as it goes too quick
I need to use 0.1
But the pygame.Color function can't take decimals.
After that, i tried:
```

rgc = round(rgc)
rgc = int(rgc)

```
And it went to green, fine. But as soon as it tried backwards: Error saying invalid color arguement.

---

### Post by JDShu on 2011-09-19
Without seeing the code, I can't tell what in particular is wrong with, but your approach seems to use floats needlessly. It seems better to use integers throughout, for example only incrementing the color value every 10 passes of the loop.

---

### Post by noodleman999 on 2011-09-19
> **JDShu said:**
> Without seeing the code, I can't tell what in particular is wrong with, but your approach seems to use floats needlessly. It seems better to use integers throughout, for example only incrementing the color value every 10 passes of the loop.
I'll try. Thanks for the tip :D

---

