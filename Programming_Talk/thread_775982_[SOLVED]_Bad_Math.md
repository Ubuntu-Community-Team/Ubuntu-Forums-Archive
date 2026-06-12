---
title: "[SOLVED] Bad Math"
date: 2008-04-30
forum: Programming Talk
---

### Post by Zeotronic on 2008-04-30
C++: I have written some code to keep a rotational value between 0 and 360 degrees... that way I can use the value to access the corrisponding image... however, my math seems to be flawed, because my program crashes with a segmentation fault when I rotate in about 400 degrees in one direction, and my image I'm rendering keeps dissappearing when I'm at specific rotations in the other direction (like 90 - 270)... my math is rusty, so this is no suprise.
```
//Bring up from below 0
if (rotation<0){rotation+=round((rotation-360)/360.0)*-1*360.0;}
//Bring down from above 360
else if (rotation>360){rotation-=round(rotation/360.0)*360.0;}
```
The code is *supposed* to bring any value to between 0 and 360, but this doesn't seem to be the case.

Does anyone know whats wrong with my math?

---

### Post by mike_g on 2008-04-30
It looks like you are calculating in degrees, but not converting to radians, which is what C++ uses. Unless you are doing that elsewhere you could try multiplying it by: 0.0174532925

Dont know if thats going to fix your problem.

---

### Post by kebes on 2008-04-30
You should just be able to use the [modulus operator]("http://www.cprogramming.com/tutorial/modulus.html"):

```

// Force rotation value to be between 0 and 360
rotation = rotation % 360;

```

---

### Post by Zeotronic on 2008-04-30
> It looks like you are calculating in degrees, but not converting to radians, which is what C++ uses. Unless you are doing that elsewhere you could try multiplying it by: 0.0174532925
I am calculating in degrees... my entire program handles it in radians untill the graphical part... when it gets to rotation it is converted to degrees, but that is before this point. Just so that you can know that my conversion is correct, I'm multiplying by 57.295779513, thus converting it into degrees, from radians.
> You should just be able to use the modulus operator:
I was not aware of the modulus operator... I will look into that.

Edit:

Wait, your code wouldn't handle negatives would it? I would have to do something else wouldn't I?

Edit:

When I try to use the operator, I get this error:
> main.cpp:1338: error: invalid operands of types ‘double’ and ‘double’ to binary ‘operator%’

Edit:

Ahh, I see, it doesn't support floating values.

---

### Post by mike_g on 2008-04-30
Yeah the modulus operator is very useful for integer maths. fmod will handle doubles:

[http://www.codecogs.com/reference/math.h/fmod.php?alias=fmod](http://www.codecogs.com/reference/math.h/fmod.php?alias=fmod)

but it would be faster to use an if statement and adjust the value if it overflows or underflows.

Edit: your orignal code might be wrong. I never checked it properly before. Maybe something like this would work:
```
if(degree > 359) 
    degree -= 360;
else if(degree < 0)
    degree += 360;

```
Also, is it possible for the degrees to be incremented more than 360 in one go? That could cause problems.

---

### Post by kebes on 2008-04-30
> **Zeotronic said:**
> Ahh, I see, it doesn't support floating values.
Yes. Sorry, I didn't catch that "rotation" was a float. I think you can use "[fmod]("http://www.cplusplus.com/reference/clibrary/cmath/fmod.html")" from <cmath> to do the equivalent of a modulus on floats and doubles. (I think it works for negative numbers, too.)

Hope that helps.

---

### Post by kebes on 2008-04-30
> **mike_g said:**
> Also, is it possible for the degrees to be incremented more than 360 in one go? That could cause problems.
I think his code needs to allow for arbitrary increments... Also note that your code has the comparison ">359" which won't work for floating point (for instance, a value of 359.6 doesn't need to be changed).

---

### Post by mike_g on 2008-04-30
Oh yeah, I forgot it was floating point.

---

### Post by Zeotronic on 2008-04-30
> I think you can use "fmod" from <cmath> to do the equivalent of a modulus on floats and doubles. (I think it works for negative numbers, too.)
While it works for negatives, it leaves them negative, and I don't know a quick way to make them positive... if I just use abs(), it would make the object just start rotating backwards suddenly.

---

### Post by aks44 on 2008-04-30
```
while (degree < 0.0)
  degree += 360.0;
while (degree >= 360.0)
  degree -= 360.0;
```

---

### Post by Zeotronic on 2008-04-30
> Code: ...
While your code would work, wouldn't it take more and more processing power the further you got from 0? There is no code in place in my program, to keep it from getting as far from 0 as it wants.

---

### Post by aks44 on 2008-04-30
> **Zeotronic said:**
> While your code would work, wouldn't it take more and more processing power the further you got from 0? There is no code in place in my program, to keep it from getting as far from 0 as it wants.

Well, then just use **fmod** followed by
```
if (degree < 0.0)
  degree += 360.0;
```

---

### Post by Zeotronic on 2008-04-30
Theres not a cheaper way to do it? Then I guess I have to.

---

### Post by mike_g on 2008-04-30
Well if you really want a cheaper way to do then you may be best off looking to limit your range and do what aks44 originally suggested.

---

### Post by Lux Perpetua on 2008-04-30
The "true" modulus x mod y (x is an arbitrary real, y is a nonnegative real) can be computed as ```
x - y*floor(x/y)
```It is the unique value between 0 and y (including 0, not including y) that can be achieved from x by adding or subtracting whole multiples of y. In your case: 
```
rotation -= 360*floor(rotation/360);
```I would be interested to know whether that is slower or faster than aks44's second suggestion. I guess the answer would depend on the implementations of fmod and floor, among other things.

---

