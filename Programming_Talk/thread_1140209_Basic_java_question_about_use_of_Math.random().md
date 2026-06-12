---
title: "Basic java question about use of Math.random()"
date: 2009-04-27
forum: Programming Talk
---

### Post by bramming on 2009-04-27
Hey :) i finally decided to start doing some tutorials on programming, and chose java for a start with the Eclipse IDE. I understand all i have read so far in the [http://www.linuxbog.dk/java/java/index.html](http://www.linuxbog.dk/java/java/index.html) tutorials (sorry it's in danish so you will probably not understand anything it says). Theres one thing that really wonders me though.

There's an example of a program throwing a dice and then displaying the value of the toss in a terminal. To calculate the side it hits the following code is used:

```
public class Terning
{
  // the current side facing upwards
  int værdi;

  // constructor
  public Terning()
  {
    kast(); // call kast() that sets the value to something reasonable
  }

  // method to throw the dice
  public void kast()
  {
    // find a random side
    double tilfældigtTal = Math.random();
    værdi = (int) (tilfældigtTal * 6 + 1);
  }

  // gives a description of the dice
  public String toString()
  {
    String svar = ""+værdi;  // value as string
    return svar;
  }
}
```

What i dont understand, is that to calculate the side, its using Math.random() * 6 + 1.

As far as i can see Math.random() gives a random double between 0.1 and 1.0. So lets say it gives 1.0 it would mean the side would be 6*1+1 = 7? when i run it, it always returns between 1 and 6 as its supposed to, and if i remove the +1 it only goes up to 5. But how can 1.0*6 give max 5? :S I hope my question is understandable as well as the code ;)

Thanks in advance :)

---

### Post by Namtabmai on 2009-04-27
> greater than or equal to 0.0 and **less than** 1.0.

The key thing here is "less than" NOT "less than or equal to".

---

### Post by stair314 on 2009-04-27
I don't do much Java programming (mainly C++) but I looked at this page:
[http://java.sun.com/j2se/1.4.2/docs/api/java/lang/Math.html](http://java.sun.com/j2se/1.4.2/docs/api/java/lang/Math.html)
and it says that the return value of the random() method is "greater than or equal to 0.0 and less than 1.0". So, the minimum value is not 0.1 like you thought, and the maximum value can never be 1.0
When you multiply by 6, this means the value will be greater than or equal to 0 and less than 6, but never equal to 6.
When you use (int) to convert the floating point number to an integer, it will always round down. Thus you want the floating point number to be greater than or equal to 1, and less than but never equal to 7.
6.999999 is fine; it will be rounded down to 6 by the (int) cast.

---

### Post by bramming on 2009-04-27
ah thanks a lot for the explanations :) now i finally understand :)


Also thanks for the fast replies, it's much appreciated ! :)

---

