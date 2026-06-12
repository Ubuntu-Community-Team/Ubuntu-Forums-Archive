---
title: "Fraction class operations C++"
date: 2010-02-27
forum: Programming Talk
---

### Post by druca on 2010-02-27
Hi all! 

I was wondering about some standard practice c++ stuff. If I make a class Fraction and operations like plus and minus etc, is it standard to return a new stack based object or modify *this to return the new value?  

returning new stack based object 
```


Fraction Fraction::operator+( const Fraction& t ) {

  Fraction A ;

  A.denominator = denominator * t.denominator ;

  A.numerator = ( ( A.denominator / denominator ) * numerator ) +

    ( ( A.denominator / t.denominator ) * t.numerator ) ;


  if( equal_rational( A , reduced( A ) ) == FALSE ) return ( A );

  return A ;
}

```

It just gave me an undefined reference to its destructor...so does that mean I cannot do the above? I have done something similar in C

---

### Post by dwhitney67 on 2010-02-27
It is really up to you, but typically non-friend methods alter the state of the class object (ie. 'this').  You defined a method that does not alter the class object.

If you want to create/return a new Fraction object, consider declaring something like this in your class:
```

class Fraction
{
public:
   Fraction(int num = 0, int den = 1);

   ...

   friend Fraction operator+(const Fraction& lhs, const Fraction& rhs);

   ...

```
The friend method will allow for you to create a new Fraction object using the information about the left-hand and right-hand side Fractions in an operation such as:
```

Fraction f1 = Fraction(1, 2);
Fraction f2 = Fraction(1, 3);
Fraction f3 = f1 + f2;

```
In the example above, f1 and f2 are not altered; f3 contains the sum of f1 and f2.

If you want to do it your way, then the same as shown above would apply.  Nevertheless, you need to ensure that you do not alter the 'this' Fraction object.  From the code you posted, it appears that you are already following this advice, but you could/should go further and declare your method with a const qualifier:
```

Fraction operator+(const Fraction& other) **const**;

```


P.S.  You need to check for the case when both fractions have the same denominator; in such an event, addition of the Fractions only involves adding one numerator to the other.


P.S. #2   I understand what you are doing here, but why do you need two return points if they are returning the same object?
```

  ...

  if( equal_rational( A , reduced( A ) ) == FALSE ) return ( A );

  return A ;

```

---

