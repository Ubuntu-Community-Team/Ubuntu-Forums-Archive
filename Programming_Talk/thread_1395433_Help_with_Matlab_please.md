---
title: "Help with Matlab please"
date: 2010-01-31
forum: Programming Talk
---

### Post by smdawson on 2010-01-31
I need to figure out what command will multiple all the elements of a row or column in a matrix. (i.e  A = [ 1, 2, 1 ];  ......(command is what?)(A) = 2 )

---

### Post by TheStatsMan on 2010-01-31
It is not clear what you are asking.

If I was to guess
```


 A=ones(3,3)

   1   1   1
   1   1   1
   1   1   1

D=eye(3)

   1   0   0
   0   1   0
   0   0   1

 D(1,1)=2

   2   0   0
   0   1   0
   0   0   1

 A*D
ans =

   2   1   1
   2   1   1
   2   1   1

 D*A

   2   2   2
   1   1   1
   1   1   1


```

---

### Post by smdawson on 2010-01-31
Sorry. I need to find the product of all the numbers in one row of a matrix. But using one command to execute this.

---

### Post by ad_267 on 2010-01-31
```
octave:1> A = [1,1,1;1,1,1;1,1,1]
A =

   1   1   1
   1   1   1
   1   1   1

octave:2> A(1,:)*2
ans =

   2   2   2

octave:3> A(:,1)*2
ans =

   2
   2
   2

```

Does that answer your question, or do you need a command that will give you something like this? (Octave syntax and functions are the same as Matlab by the way.)
```
2 2 2
1 1 1
1 1 1
```

---

### Post by hanlin on 2010-01-31
prod(array,dim)

So dim=1 if you want to do columns and dim=2 for rows.

---

### Post by smdawson on 2010-01-31
Yes, that answers it. I also need to know what the operator for "e" is. i.e - 2.5e^(-j*3*pi/4) is the operator for e^x log2?...i''m not sure.

---

### Post by ve4cib on 2010-02-01
> **smdawson said:**
> Yes, that answers it. I also need to know what the operator for "e" is. i.e - 2.5e^(-j*3*pi/4) is the operator for e^x log2?...i''m not sure.

Not entirely sure what you mean there.  e (the constant) is simply e.  You can multiply/divide with it normally: 2.5*e = 6.7957

e can also be used to express a value that is multiplied by 10^x.  10e2 = 10 * 10^2 = 1000

In your example "-2.5e^..." is a syntactical error.  If you want to multiply 2.5 by e to some power you need "-2.5*e^...", and if you want to express a power of 10 you need a value after the e: "-2.5e__^..."

---

### Post by not_a_phd on 2010-02-01
Are you looking for e^x = exp(x)?

---

### Post by smdawson on 2010-02-01
ok. I wasn't putting the * between the 2.5 and the e. But I am still getting an error. Is this right?
```
l=2.5*e^(-j*3*pi/4) 
```

I am getting "??? Undefined function or variable 'e'. "

---

### Post by ve4cib on 2010-02-01
Hm.  Maybe e is only defined as a constant in Octave.  I don't have MATLAB installed, so I can't check for sure.

According to [http://amath.colorado.edu/computing/Matlab/Tutorial/Intro.html](http://amath.colorado.edu/computing/Matlab/Tutorial/Intro.html) you can calculate e with

```
e = exp(1)
```

It's not quite as elegant as having the constant pre-defined for you, but it should do the trick.

---

### Post by smdawson on 2010-02-01
Yea. That's right. Now I can just set exp(1) = e. Then use e in the previous equation I was trying to solve. Thank you.

---

### Post by ad_267 on 2010-02-02
Or just use:
```
l=2.5*exp(-j*3*pi/4)
```

The exp() function means the same thing as e^

---

### Post by smdawson on 2010-02-02
Actually I just ended up using it like that. 
```
....exp(j*3*pi/4)
```
It came out very nicely. Thanks

---

