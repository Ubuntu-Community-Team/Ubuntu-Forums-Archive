---
title: "[C++]Class function operations on members"
date: 2010-10-15
forum: Programming Talk
---

### Post by xnerdx on 2010-10-15
I don't know if that title makes any sense, I don't know exactly how to describe what I'm doing. Nevertheless, here is what I'm trying to figure out. I have a Fraction class that (obviously) stores fractions. In my main function have a member function of class that is declared as follows:
```

void simpFraction(Fraction& operatingFraction);   //Declared in class Fraction

```
In order to call that function I obviously have to pass a fraction to it like so:
```

Fraction foo(1,2);
simpFraction(foo);

```

My dilema is that I want to be able to automatically simplify fractions when they're declared/operated on. This issue is that if I do this I can't pass it a fraction object because no object exists (yet), so how would I go about doing that? In summary I want to be able to just say something along the lines of:
```

//In fraction operator function
return Fraction(numerator,denominator)->simpFraction
//Or maybe?
return simpFraction->Fraction(numerator,denominator);

//In constructor??
this->simpFraction //???

```

I don't know if any of those examples are possible xD... But hopefully you understand what I'm after ^.^

---

### Post by dwhitney67 on 2010-10-15
Why are you making the simpFraction() a friend method?  That seems like a poor design choice.  Just make the method, probably more aptly named simplify(), as a class method.

---

### Post by xnerdx on 2010-10-15
:\ For some reason I couldn't get it to work with the function within the class defintion before. I don't know, nevertheless, I changed it so it's not friend anymore. Back to my initial question :P

---

