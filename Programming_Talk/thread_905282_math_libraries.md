---
title: "math libraries"
date: 2008-08-30
forum: Programming Talk
---

### Post by mkartic on 2008-08-30
hey guys, i need some suggestions for powerful and [hopefully] simple libraries like boost for mathematical calculations.
[specifically] what am looking for is a function that returns the slope of a line when i pass the co ordinates [and other problems]!

thanks

---

### Post by Claus7 on 2008-08-30
Hello,

in intel's site there is a package with a lot of mathematical libraries. It comes with the fortran and c++ compiler. That might help you, yet I 'm not sure if this is what you are looking for.

Regards!

---

### Post by monkeyking on 2008-08-30
For what language, are you looking for libs.

If you are using c/c++ there are gsl gnu science library

---

### Post by jimi_hendrix on 2008-08-30
> **mkartic said:**
> [specifically] what am looking for is a function that returns the slope of a line when i pass the co ordinates [and other problems]!

thanks

homemade slope function...i think this works...its in C++ but you can get the general idea and put it in your language (also you probably should replace the ints with something that supports decimal places)

[PHP]int slope(int firstX, int firstY, int secondX, int secondY)
{
	int Slope = ((secondY-firstY) / (secondX - firstX));
	
	return Slope;
}[/PHP]

---

### Post by mike_g on 2008-08-30
> int slope(int firstX, int firstY, int secondX, int secondY)
{
    int Slope = ((secondY-firstY) / (secondX - firstX));
    
    return Slope;
}  
What happens when secondX-firstX == 0?

---

### Post by jimi_hendrix on 2008-08-30
> **mike_g said:**
> What happens when secondX-firstX == 0?

[IMG]http://ceworks.frih.net/i_divided_by_zero.jpg[/IMG]

i just gave a basic example but you have a point

---

### Post by monkeyking on 2008-08-30
lol

---

### Post by dwhitney67 on 2008-08-30
> **jimi_hendrix said:**
> homemade slope function...i think this works...its in C++ but you can get the general idea and put it in your language (also you probably should replace the ints with something that supports decimal places)

[PHP]int slope(int firstX, int firstY, int secondX, int secondY)
{
	int Slope = ((secondY-firstY) / (secondX - firstX));
	
	return Slope;
}[/PHP]
Thanks for pointing out the obvious to the OP; if I had done it I probably would have been chastised.

As mike_g pointed out, you need to guard against your x-coordinates being the same, thus leading to a division by zero.

Here's some mods to your code:
[PHP]
double slope(double firstX, double firstY, double secondX, double secondY)
{
  if ( firstX == secondX )
  {
    throw std::runtime_error( "x1 == x2; cannot determine slope!" );
  }
  
  return ((secondY-firstY) / (secondX - firstX));
}
[/PHP]

---

### Post by fredscripts on 2008-08-30
> **dwhitney67 said:**
> Thanks for pointing out the obvious to the OP; if I had done it I probably would have been chastised.

As mike_g pointed out, you need to guard against your x-coordinates being the same, thus leading to a division by zero.

Here's some mods to your code:
[PHP]
double slope(double firstX, double firstY, double secondX, double secondY)
{
  if ( firstX == secondX )
  {
    throw std::runtime_error( "x1 == x2; cannot determine slope!" );
  }
  
  return ((secondY-firstY) / (secondX - firstX));
}
[/PHP]

comparing double? nope, must check if abs(firstX - secondX) < tol, where tol is the tolerance you admit like zero.

---

### Post by generalguy on 2008-08-30
Just use Boost's math library. It has all the tolerance stuff done for you, and has loads of math functions. GSL may be faster, but it looks like you've used Boost.

---

### Post by hod139 on 2008-08-30
If boost and GSL do not have what you need, then [CGAL]("http://www.cgal.org/") probably has it.  Though it contains a ton of algorithms, it tends to be not very user friendly.

---

