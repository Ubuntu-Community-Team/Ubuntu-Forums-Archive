---
title: "GoLang's Complex Number Type"
date: 2012-09-28
forum: Programming Talk
---

### Post by shawnhcorey on 2012-09-28
I was looking over the specifications for Go and I notice that it had complex numbers as a built-in type. Now, Go is suppose to be for system programming, that is, writing Linux & drivers, file systems, sockets & communication protocols, etc. But I can't for the life of me figure out why system programming would need complex numbers. Am I missing something? What part of system programming requires complex numbers?

---

### Post by Tony Flury on 2012-09-28
Off the top of my head - depending on the type of systems you are dealing with complex numbers could be very useful - for instance - a embedded system for robotics might use complex numbers as a way of calculating rotations.

---

### Post by MadCow108 on 2012-09-29
golang is suited for system programing due to its compiled nature.
that does not mean its the only purpose it can ever be used for.
The easy parallelization for example is very useful for scientific applications.

Complex numbers are required for many transformations like fourier or wavelet transformations.
These things are essential in signal processing for which there are plenty of systems out there.

---

### Post by shawnhcorey on 2012-09-29
Yes, I understand that Go can be used for many tasks but I was wondering why it had complex numbers. If it has them, then why doesn't it have matrices? They're also used a lot in computer graphics.

Most languages have complex numbers and matrices as add-ons, not part of their core.

It seems that the main reason they're there is because the designers wanted them. There is no requirement in system programming for them.

---

### Post by MadCow108 on 2012-09-29
> **shawnhcorey said:**
> Yes, I understand that Go can be used for many tasks but I was wondering why it had complex numbers. If it has them, then why doesn't it have matrices? They're also used a lot in computer graphics.

Most languages have complex numbers and matrices as add-ons, not part of their core.

computer graphics already imply another library that already does the drawing, that might as well then provide the matrices along with it.

matrices in the scientific sense are a different beasts as they need to be implemented differently depending on the task at hand.

complex numbers on the other hand are a much more basic type, it makes more sense to have them baked into the language.
There is not much debate on how to implement them properly. Also C has them so it improves compatibility.

---

### Post by shawnhcorey on 2012-09-29
> **MadCow108 said:**
> Also C has them so it improves compatibility.

Huh? Last time I looked at C, complex numbers were add-ons. Guess I'll have to take another look. :)

---

### Post by trent.josephsen on 2012-09-29
Speaking as an embedded systems programmer, I'd much rather have complex numbers built-in than matrices. Matrices are fairly straightforward to implement on my own, and if I'm using them in my application there's a good chance I'm doing that anyway. Making my own complex number implementation opens a whole can of worms, something like rolling my own floating point arithmetic... ok, probably not quite that bad.

Complex numbers pop up in the oddest of places sometimes -- it's probably easier to list the systems they *aren't* used to model.

[QUOTE=shawnhcorey]It seems that the main reason they're there is because the designers wanted them.[/QUOTE]
Maybe so. What's wrong with that?

---

### Post by shawnhcorey on 2012-09-29
> **trent.josephsen said:**
> Speaking as an embedded systems programmer, I'd much rather have complex numbers built-in than matrices. Matrices are fairly straightforward to implement on my own, and if I'm using them in my application there's a good chance I'm doing that anyway. Making my own complex number implementation opens a whole can of worms, something like rolling my own floating point arithmetic... ok, probably not quite that bad.

Complex numbers pop up in the oddest of places sometimes -- it's probably easier to list the systems they *aren't* used to model.


Maybe so. What's wrong with that?

Nothing wrong with it; I'm just trying to figure out why. After a quick review of C, I thin it's because there's no overloading of algebraic expressions, not even for add-ons.

And complex numbers are easier to implement than floating points. The biggest problem is division, which you do by multiplying by one:

```
( a + bi ) / ( c + di )
= ( a + bi ) / ( c + di ) × ( c - di ) / ( c - di )
= [ ( a + bi ) × ( c - di ) ] / ( c² + d² )
= ( ac + bd ) / ( c² + d² ) + i × [ ( bc - ad ) / ( c² + d² ) ]

```

---

### Post by trent.josephsen on 2012-09-29
> **shawnhcorey said:**
> And complex numbers are easier to implement than floating points. The biggest problem is division, which you do by multiplying by one
Don't forget exponentiation, which you're going to need for almost any analysis that involves some kind of transform. Logs and trig functions too. In fact, check out all the functions in complex.h(3) -- I don't fancy implementing any of those myself. You'll have to be careful not to accidentally introduce floating-point rounding errors, and keep it portable from one platform to another. Like I said before, it's a can of worms.

---

### Post by MadCow108 on 2012-09-29
> **shawnhcorey said:**
> Nothing wrong with it; I'm just trying to figure out why. After a quick review of C, I thin it's because there's no overloading of algebraic expressions, not even for add-ons.

And complex numbers are easier to implement than floating points. The biggest problem is division, which you do by multiplying by one:

```
( a + bi ) / ( c + di )
= ( a + bi ) / ( c + di ) × ( c - di ) / ( c - di )
= [ ( a + bi ) × ( c - di ) ] / ( c² + d² )
= ( ac + bd ) / ( c² + d² ) + i × [ ( bc - ad ) / ( c² + d² ) ]

```

and thats wrong, complex numbers are not straighforward to implement.
you need to take special care of NaN, Inf, positive and negative zero and denormals when you deal with complex numbers.
E.g. a and c are Inf when you multiply
(z*w)*z is perfectly well defined as Inf + NaN*i, but with the naive approach the result is the wrong NaN + NaN*i due to the mixing complex arithmetic implies.

and not to speak of the more complex trigonometric and transdental functions :/
there are still bugs being discovered in libc's implementation of these (though mostly only precision guarantee related)

---

### Post by shawnhcorey on 2012-09-29
> **trent.josephsen said:**
> Don't forget exponentiation, which you're going to need for almost any analysis that involves some kind of transform. Logs and trig functions too. In fact, check out all the functions in complex.h(3) -- I don't fancy implementing any of those myself. You'll have to be careful not to accidentally introduce floating-point rounding errors, and keep it portable from one platform to another. Like I said before, it's a can of worms.

Yes but like floats, you can make logs and trigs part of a library; it need not be part of your core.

---

### Post by trent.josephsen on 2012-09-29
Which is what both Go and C do.

---

### Post by shawnhcorey on 2012-09-29
If algebraic formulas are part of your core and you don't allow overloading than whatever you do for integers and floats must be paralleled with complex numbers. Since it's likely that addition, subtraction, multiplication, division, and integer exponentiation for integers and floats are part of your core, you will have to add them for complex numbers too. Since logs and trigs are likely to be in a library, they can be in one for complex numbers too.

---

### Post by trent.josephsen on 2012-09-29
I think we've begun talking at cross purposes... what was the topic again? ;)

---

