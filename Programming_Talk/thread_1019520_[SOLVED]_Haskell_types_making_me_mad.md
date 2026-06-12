---
title: "[SOLVED] Haskell types making me mad"
date: 2008-12-23
forum: Programming Talk
---

### Post by amityak on 2008-12-23
Hello dear people


my task is to draw a line, and in order to do that i though i'd use the help of trigonometry. so given the type Pixel (Int,Int) i would like to have from two given Pixel the angle (rad) between them.
so i scribbled something like this:

```
getAngle :: Pixel -> Pixel -> Float
getAngle (a,b) (c,d) = atan (y/x)

        where   y = d-b
                x = c-a
```

surprise surprise its not working...

i tried several types instead of the FLoat but i always get pretty much the same error:

```
Prelude> :r
[3 of 3] Compiling Main             ( ./aufgabe3.hs, interpreted )

./aufgabe3.hs:11:23:
    Couldn't match expected type `Float' against inferred type `Int'
    In the expression: atan (y / x)
    In the definition of `getAngle':
        getAngle (a, b) (c, d)
                   = atan (y / x)
                   where
                       y = d - b
                       x = c - a

```

I understand that the problem is that im giving in Int and want to get out FLoat, but how can I solve it without having to change my type Pixel because i would like it to stay (Int,Int)

Thank you all!

---

### Post by Reiger on 2008-12-23
3 Remarks:
a) trivial compiler error; your inability to see the fix is probably due to your course focusing on interpreted Haskell (which automates it for you) first...
b) Homework. I can read that much German to know what aufgabe3.hs means :P
c) Would you really be surprised if you defined in Java:

```

public class ErrorApp {

public static void main (String [] args) {
 int i=args.length;
 System.out.println("Test "+(new Foo(i)));
}
}

class Foo {
public double bar=0.0;
Foo(double d) {
this.bar=d;
}
public String toString() {
return "Foo: "+bar;
}
}

```

the compiler would refuse to compile with exactly the same error type (a missing cast)?

You need to convert your Int's to Float's in Haskell using the function:
```

fromInteger :: Num a => Integer -> a

```
which will work out as:
```

fromInteger :: Integer -> Float

```

---

### Post by amityak on 2008-12-23
Thank you Reiger for your reply (:

I think i'm basically not getting the usage of fromInteger. I've tried several variation always trying keeping it as simple as it goes. and i think nothing is simpler then that:

```
makeFloat :: Int -> Float
makeFloat x = fromInteger x :: Float

```

which also leads to the same error:

```
   Couldn't match expected type `Integer' against inferred type `Int'
    In the first argument of `fromInteger', namely `x'
    In the expression: fromInteger x :: Float
    In the definition of `makeFloat':
        makeFloat x = fromInteger x :: Float

```

actually the way i want it to function is the following:

```
getAngle :: Pixel -> Pixel -> Float
getAngle (a,b) (c,d) =  atan z
          where z= (((fromInteger d)-(fromInteger b)) / ((fromInteger c)-(fromInteger a)))

```

which produces the following error:

```
aufgabe3.hs:12:34:
    Couldn't match expected type `Integer' against inferred type `Int'
    In the first argument of `fromInteger', namely `d'
    In the first argument of `(-)', namely `(fromInteger d)'
    In the first argument of `(/)', namely
        `((fromInteger d) - (fromInteger b))'
Failed, modules loaded: PNG, PNGInternal.

```

any idea how am I using the fromInteger wrong??

and yes it is for my homework, but since the project is much larger then this small problem that gets in my way i figured it's okay to ask for help. I can present the bigger problem if it's in the interest of any.

Great christmas and Holidays for all

Amít

---

### Post by Alasdair on 2008-12-23
fromInteger won't work because you are using the Int type rather than the Integer type. Integer supports arbitrary precision, while Int does not. The function you want to use is the slightly more general fromIntegral which has the type '(Num b, Integral a) => a -> b'.

In the original function you need y and x to be floats in order for the (/) function to work (check it's type and see if you can work out why it won't work for ints), why don't you try something like 'y = fromIntegral (d-b)' in your original where clause?

---

### Post by amityak on 2008-12-23
Thank you, it worked.
i just changed fromInteger to fromIntegral and that did the work.
is it really just beacause i was using Int and not Integer ?
I thought they were pretty much the same.

oh well.... thank you all very much :KS
and happy Chrishanukkha

---

### Post by Reiger on 2008-12-23
No they're not the same because of the precision thing. Also: Integer supports larger values (Int is pretty much the C/Java int type).

---

