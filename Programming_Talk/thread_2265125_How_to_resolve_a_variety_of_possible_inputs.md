---
title: "How to resolve a variety of possible inputs"
date: 2015-02-12
forum: Programming Talk
---

### Post by Erdaron on 2015-02-12
I have a kind of general question. I'm writing a function that has a sole output, but may be supplied a variety of inputs, and I'm wondering to handle this in an elegant or proper manner.

Here is the situation. The function calculates the complex beam parameter q (for Gaussian beam optics). It has a canonical definition that uses beam radius, curvature, and wavelength. However, the user might not necessarily have these handy. Instead, the user may have other variables - waist radius, divergence, distance from waist, numerical aperture, maybe a couple other ways. All of these can be combined in different ways to compute q, but only some of them need to be specified. How can I do this in a way that isn't clunky?

My current clunky idea is to define the function like this: ```
def q(L, w0 = False, w = False, z = False, NA = False, div = False, C = False)
```

(L is wavelength, and cannot be substituted for)

Then in the body of the function, repeatedly test various combinations from which I know how to calculate q. For example, ```
if w0 and z: return *calculation expression*
```

At the end, if none of the if statements resolve, raise an exception.

Is there a more elegant way to achieve this?

(If it helps, I'm working in Python.)

---

### Post by Vaphell on 2015-02-12
so what's clunky about your idea and what do you expect of an elegant solution?
Imo it's perfectly fine assuming the valid combinations are very specific and there is no way around a series of conditions.

---

### Post by Erdaron on 2015-02-12
Well, to be honest, I am not actually sure what I expect. This brute force way of just decision-treeing my way through is straightforward, and there is certainly value in that. But maybe someone has a different approach to this problem? At the very least, I wanted to see how others would approach this situation, and maybe learn something from that.

---

### Post by tgalati4 on 2015-02-13
You could create a computational state vector--which is really just a way of storing your conditionals in a single array variable.  Then define a function that gets passed the state vector [0,0,45,0.01,0,2.0] and the computations would depend on which values are non-zero.  The beginning of the function would have some simple checks to make sure you have the minimum number of values defined to perform the calculation.  With some clever ordering of the array and some clever programming, you could write a compact and robust function to handle this calculation.

I would search the web for a similar calculator and look at the code.  For example if you want to calulate the pressure of a gas using the Ideal Gas Law:

[http://www.chemicool.com/idealgas.html](http://www.chemicool.com/idealgas.html)

This tool uses a push-button for the variable that you want to solve for and the form then modifies itself depending on what is selected.

---

