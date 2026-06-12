---
title: "maple plot two functions from one variable"
date: 2010-04-22
forum: Programming Talk
---

### Post by Xender1 on 2010-04-22
I need to plot x(t) and y(t) on the same graph using a parametric curve. I have been looking at [http://www.maplesoft.com/support/help/Maple/view.aspx?path=plot/parametric](http://www.maplesoft.com/support/help/Maple/view.aspx?path=plot/parametric) but it is missing what I am trying to do.

I have my ans which holds both x(t) and y(t) in form like:
```

ans := {x(t) = exp(-1/10*t)*(-11/2*sin(2*t)+10*cos(2*t)), y(t) = -5*exp(-1/10*t)*sin(2*t)}

```
Now trying to plot this i run in to trouble. Is there anyway to assign just x(t) and y(t) to two separate variables? or is it actually possible to plot by passing in ans (now i keep getting incorrect first argument error)

Thanks!

---

### Post by MadCow108 on 2010-04-22
its been quite a while since I last used maple, so excuse if I'm completely of

how is x(t) defined?
if this is the definition it is wrong (unless something changed since I last used maple)
delayed functions in maple are defined by:
f:=(arg1,arg2)->arg1*arg2;

if you cannot change the format use rhs to extract the righthand side:
plot([rhs(ans[1], rhs(ans[2]), t=0..20])

---

