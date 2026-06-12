---
title: "How do I make a plot with 3 dimensions (Octave?)"
date: 2011-04-12
forum: Programming Talk
---

### Post by Kimm on 2011-04-12
For my bachelor thesis in biology (a mix of plant physiology and evolutionary biology in this case) I have developed a model that describes a linear function when you provide it with two variables:

y=-5.41z/x+1.01

Simple enough, but I'm wondering if its possible to plot this as a 3D graph, with a y, z and x axis? I'm using R for statistics, but I don't know if this is possible to do there. So what I'm asking for is, how would I do this in Octave (or R if that is possible)?

---

### Post by visitron on 2011-04-12
> **Kimm said:**
> 
y=-5.41z/x+1.01



I don't know R or Octave, but most programs will allow you to plot it as z = f ( x,y ).

Just solve the equation for z after that you can use any plotting program.


z = ( xy-1.01x ) / 5.41

---

### Post by Vox754 on 2011-04-12
> **visitron said:**
> I don't know R or Octave, but most programs will allow you to plot it as z = f ( x,y ).

Just solve the equation for z after that you can use any plotting program.


z = ( xy-1.01x ) / 5.41



Lol. This is stupid. You don't "need" to solve for the "z" variable. You just need to use the "y" variable as the "z" variable in your example. That is,
```

y = f(x,z)
f(x,z) = -5.41z/x+1.01

```

But, anyways... check out "pyplot". It is a module for Python, that provides graphic capabilities similar to Matlab. It has an interface with functions that are named and work the same as Matlab plotting functions, so it is easy to use if you are familiar with Matlab syntax.

Pyplot also has an object oriented interface, that is more powerful, and which I recommend once you are comfortable with the basics.

---

### Post by visitron on 2011-04-12
> **Vox754 said:**
> Lol. This is stupid. You don't "need" to solve for the "z" variable. You just need to use the "y" variable as the "z" variable in your example. 

I only mentioned it because the poster asked about using Octave.

As far as I know Octave still uses Gnuplot for plotting.

Gnuplot only supports cartesian coordinates for 3d plotting, surfaces of the type z=f(x,y).

Therefore if he wants a 3d plot with Octave he will have to have it in that form and solve for the z variable.

But I'm sure some other software can do it the way you set it up.

---

### Post by Vox754 on 2011-04-13
> **visitron said:**
> I only mentioned it because the poster asked about using Octave.

As far as I know Octave still uses Gnuplot for plotting.

Gnuplot only supports cartesian coordinates for 3d plotting, surfaces of the type z=f(x,y).

Therefore if he wants a 3d plot with Octave he will have to have it in that form and solve for the z variable.

But I'm sure some other software can do it the way you set it up.

You don't get it.

Just pretend "y" is "z".
```

y=-5.41z/x+1.01

z=-5.41y/x+1.01

```

See? Magic.

Variables are variables, just symbols, just labels, they don't have a fixed meaning regarding space coordinates. You could just use other names for them.

Sigh...

---

### Post by visitron on 2011-04-13
> **Vox754 said:**
> You don't get it.

Just pretend "y" is "z".
```

y=-5.41z/x+1.01

z=-5.41y/x+1.01

```See? Magic.

Variables are variables, just symbols, just labels, they don't have a fixed meaning regarding space coordinates. You could just use other names for them.

Sigh...


I understand quite well about variables in space not having a fixed meaning thank you.

However by convention we usually call them x,y,z you can call them whatever you like.

The trouble is plotting software will expect a certain order.  If you simply switch around you have to take into account that in the final plot your points may not match how your axes were drawn, for some functions it may not matter for others it will.  In the least in could be confusing or even misleading.

But I really don't wish to continue discussing anything with you.  I don't like your derisive attitude or scoffing remarks.

---

