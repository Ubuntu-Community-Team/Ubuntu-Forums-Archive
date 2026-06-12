---
title: "How to iterate vectors in matlab?"
date: 2008-04-15
forum: Programming Talk
---

### Post by Belathor on 2008-04-15
Hi,

Is it possible to iterate through a list of vectors in matlab or octave? For example, I want to be able to prompt the user for a set of coordinates on a grid and have them stored in a way so that I can iterate over them one by one. I feel I need to do this because I want to make a dot representing a robot traverse the grid through those user specified points in order. I am really inexperienced with the language and I don't have any idea how I would do it.

Thanks for any help you could give!

---

### Post by WW on 2008-04-15
A **for** loop can do this.  If A is a matrix, and you use a **for** loop of the form **for v = A, ...**, v will iterate through the columns of A. Type **help for** or **doc for** in Matlab for more details.

For example,
```

>> A = [1 4.3; 2 91.1; 3 17]'   % Note the transpose character at the end
A =
    1.0000    2.0000    3.0000
    4.3000   91.1000   17.0000
>> for p = A, str = sprintf('x=%f y=%f',p(1),p(2)); disp(str), end
x=1.000000 y=4.300000
x=2.000000 y=91.100000
x=3.000000 y=17.000000
>> 

```

---

### Post by Belathor on 2008-04-16
Thanks so much, WW! That worked perfectly.

---

