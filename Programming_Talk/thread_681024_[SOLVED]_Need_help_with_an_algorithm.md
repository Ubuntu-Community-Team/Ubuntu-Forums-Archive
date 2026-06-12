---
title: "[SOLVED] Need help with an algorithm"
date: 2008-01-28
forum: Programming Talk
---

### Post by mssever on 2008-01-28
After reading a couple of threads here, I got inspired to write my own unit converter. I know that there are many better tools available, but by writing my own I get to learn something. :-)

I've attached the current incarnation of my converter. If you look through the code, you'll notice that I have a ton of methods to define each conversion supported (92 plus a few supporting methods). This strikes me as a terrible way to code it. It's repetitive and bug-prone.

What I would like to do is define a few key conversions and then let Ruby's method_missing magic derive the proper conversion on the fly. For example, 1 in is 2.54 cm and 1 ft is 12 in. Based on that, the program should be able to figure out how to convert 2 ft to cm without my having to explicitly write that conversion.

My problem is that I haven't been able to figure out an algorithm to accomplish such a task. Perhaps it's because I'm not very good at math, or maybe I'm just a lousy programmer. My code is written in Ruby, but since this is an algorithm question, it's largely language-independent.

Any suggestions?

---

### Post by stroyan on 2008-01-28
It seems that the simplest structure is to have a single master unit for each category of measurement. Then the conversion from one mass unit to another would always consist of scaling the input unit to grams and then scaling grams to the output unit.  You need to make it clear which group each unit belongs to.  You can't convert weight to length.  (But you can convert mass to energy!)

---

### Post by mssever on 2008-01-28
> **stroyan said:**
> It seems that the simplest structure is to have a single master unit for each category of measurement. Then the conversion from one mass unit to another would always consist of scaling the input unit to grams and then scaling grams to the output unit.  You need to make it clear which group each unit belongs to.  You can't convert weight to length.  (But you can convert mass to energy!)

Right. And if I were using solely metric units, that would be trivial. However, if I didn't have to use US customary usits, there would be no need for such a program.

The part that I'm having trouble wrapping my head around is how to make the program determine the steps to take to convert from, e.g., feet to cm. To make matters worse, the conversion factors for US units are anything but consistent.

---

### Post by popch on 2008-01-28
I solved this once in Smalltalk. I trust that the solution would work in other languages just as well.

The solution consisted of a hierarchy of classes:

Magnitude
.. Length
....Meter
....Mile
....Furlong
.. Speed
....Kph
....FurlongPerFortnight
..Time
....Hour
....Fortnight
.. (and so on)

I also added some methods which allowed oddball units to be generated on the fly. Thus, the FurlongPerFortnight class in the above list is spurious as I could generate that unit when required as a particular unit of speed.

The logic to generate between units of the same dimension (say, times, distances, volumes and so on) was straight forward. Select an arbitrary unit to be the 'normal' one, and overload the conversionFactor method for each unit.

The logic to recognize 'valid' dimensions (i.e. dimensions for which there was a class defined) was also straight forward. I think I used both for the nominator and the denominator a bag holding each 'elementary' dimension. Thus, Speed was expressed as [Distance]/[Time], while Acceleration was [Distance]/[Time, Time] or some such.

I do not know any more how I did the decimal factors (kilo, Mega and so on), but I think I used the exception mechanism of the language to trap those expressions, removed the prefix if known and retried to process the unit name.

Pitfall: you have to know when to process a Magnitude as difference or as a point on a scale. This is especially visible when converting between Fahrenheit and Celsius, where there is an offset between the origins: 0 Fahrenheit is not 0 Celsius, while a difference of 0 is in all units the same.

---

### Post by stroyan on 2008-01-28
It doesn't really matter whether you are converting from feet to cm or meters to kilometers.  All lengths would be mapped to the same master unit and then to the desired unit.  For each unit you need two functions.  One function mapping to the master unit of that measurement and one function mapping from the master unit to the desired unit.

If you would like to see a very strong implementation of this kind of program you can install the 'units' package (and its source code).
The /usr/share/misc/units.dat data file has over 4000 lines of conversions.

---

### Post by a9bejo on 2008-01-28
I guess you could also solve this with a "general problem solver"-type recursive logic: 

1. start with the target conversion and search all methods you already know that convert to these units. 
2. check the source units for these methods.
3. take these source units as target units and continue with step 1  
4  if a source unit matches the original unit,  apply all the methods that lead to these method.

---

### Post by pmasiar on 2008-01-28
There is yet another flexible system of measures: [http://en.wikipedia.org/wiki/Potrzebie](http://en.wikipedia.org/wiki/Potrzebie)

But sadly, not so many converters can handle it, yours might be the one :-)

---

### Post by mssever on 2008-01-29
Thanks for the pointers, everyone. I've got that sorted out, now. The only major thing remaining is to allow the user to enter units in various standard forms, instead of requiring the abbreviation I use internally. I haven't had time to write that yet.

And pmasiar, I added the potrzebie just for you, :) although I didn't include the rest of the system.

One final, off-topic, question: does anyone know how to work around floating-point errors in Ruby?

---

