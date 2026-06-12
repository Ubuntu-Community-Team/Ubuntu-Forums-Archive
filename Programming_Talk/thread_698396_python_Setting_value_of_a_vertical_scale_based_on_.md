---
title: "python: Setting value of a vertical scale based on another"
date: 2008-02-16
forum: Programming Talk
---

### Post by gorilla_au on 2008-02-16
Hi All,

I haven't been able to find a tutorial on how to acheive this scenario.

Basically, when you move a vertical Scale Control, the other one moves also. It would be helpful to know how to determine which control has been manipulated by the user.

I have attached my test code which has just two sliders in the window.

Sorry if the code is badly written as I have just getting started in pygtk programming.

---

### Post by lnostdal on 2008-02-16
ok, just a quick thought

at any point in time we have these states:

§1 no sliders are moving

§2 one slider is moved by the user

§3 the other sliders move because a slider is moved by the user

these things never happen at the same time .. this means that you can detect when state §2 is happening and store information about that state (what slider did it "happen to" etc.) before state §3 starts happening .. (edit: closures are nice when storing states btw.)

---

### Post by gorilla_au on 2008-02-16
> **lnostdal said:**
> ok, just a quick thought

at any point in time we have these states:

§1 no sliders are moving

§2 one slider is moved by the user

§3 the other sliders move because a slider is moved by the user

these things never happen at the same time .. this means that you can detect when state §2 is happening and store information about that state (what slider did it "happen to" etc.) before state §3 starts happening .. (edit: closures are nice when storing states btw.)

That makes sense, I guess the part I don't understand is how to obtain the other instances of the other sliders. 

I imagine that it is possible to walk the array of sliders untill you find the one that you are interested in or the one that triggered the event.

Sorry if you is a bit vague but this is my first pygtk example that I am trying to tackle. Perhasp I'll throw this into the pygtk wikibook as this question doesn't seem to be documented as a tutorial.

---

