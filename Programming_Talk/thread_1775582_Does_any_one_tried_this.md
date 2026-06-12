---
title: "Does any one tried this"
date: 2011-06-04
forum: Programming Talk
---

### Post by raja.genupula on 2011-06-04
Hey Friends 
                   does any one have tried this. open python in terminal . 
                   types as follows
                  >>>~1
                                 ans:-2
                   >>>~-1
                                   ans:0

          How its going to be done as above .

---

### Post by r-senior on 2011-06-05
It's just the way [two's complement]("http://en.wikipedia.org/wiki/Two%27s_complement") signed numbers work. The ~ is a bitwise negate.

Simple example with 4 bits:

```

  1 = [COLOR="Red"]0[/COLOR]001
 ~1 = [COLOR="Red"]1[/COLOR]110 = -2

 -1 = [COLOR="Red"]1[/COLOR]111
~-1 = [COLOR="Red"]0[/COLOR]000 = 0

```

The bit in red denotes the sign: 1 means negative, 0 means positive.

The point of two's complement is that you can do the same low-level addition algorithm for positive and negative numbers, i.e. a simple long addition in binary:

```

(2 + 3 = 5):

0010 + 
0011 
----
0101    (0 + 1 = 1, 1 + 1 = 0 and 1 carried)


(2 + (-3) = -1):

0010 + 
1101 
----
1111    (0 + 1 = 1, 1 + 0 = 1, 0 + 1 = 1 and 0 + 1 = 1) 

```

---

