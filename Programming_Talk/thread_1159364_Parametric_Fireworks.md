---
title: "Parametric Fireworks?"
date: 2009-05-14
forum: Programming Talk
---

### Post by djbushido on 2009-05-14
Does anybody know of a java/cross-platform (able to run on windows as well) applet/program that can simulate projectile motion using parametric equations? Or can give me a general overview of how to do as such? I would expect to use a "for" loop (in whatever language - preferably python) to stand in for "t", but don't know what I would show the motion on. Or a "trace" feature. Any help would be appreciated, I know I'm being kind of vague but don't really know how to elaborate. Thanks!

---

### Post by kjohansen on 2009-05-14
Processing is a cross platform language that makes for easy visualization...  There are some good tutorials at processing.org.

---

### Post by djbushido on 2009-05-24
Decided in the end to make it my first java program. Will post it if someone wants, otherwise it's just taking up space.

---

### Post by soltanis on 2009-05-24
x(t) = v0 * cos(theta) * t
y(t) = v0 * sin(theta) * t + 1/2 * accel * t^2

Now iterate from t = 0 ... t = t(final) in a for loop, with some t-step (any stepping value will do, common ones are tstep = 0.1 or 0.01). Plugging this into those equations will give you the x and y values of the projectile's position in cartesian space.

```

for (double t = 0.0; t < tmax; t += tstep) {
  plot(x(t), y(t));
}

```

To visualize, plot the values as points on a canvas. You have to apply two transformations before you can plot the points: first, account for the fact that in cartesian coordinates, the origin is located (in quadrant I) at the bottom-left, not the top-left, and second, account for the fact that in applet programming, y coordinates move further down the screen as they increase (therefore, you must invert the value of the y(t) coordinate to plot it on the screen).

So what I'm saying is your plot function probably looks like this

```

void plot(double x, double y)
{
        some.java.graphics.system.point(x, height - y);
}

```

Which as you can see does the whole move the origin and invert the y coordinate thing in one go.

Sorry if I misunderstood your question, it sounds like you wanted to write the visualizer, if you just want an applet that visualizes arbitrary equations, there are loads of "projectile motion" applets on the net.

---

### Post by djbushido on 2009-05-25
Yeah, my friend helped me with a simple cartesian graph area - graphics drawLine(x,y,x,y) plots a point - there's actually no point-plotting method. Be careful with the equations though - saying x(t) will make it an incorrect variable, and I believe that there is one thing wrong with the "y(t)" equation - you forgot to add the initial height in. What I meant is that I'll post the jar or the applet if anybody wanted it.

---

