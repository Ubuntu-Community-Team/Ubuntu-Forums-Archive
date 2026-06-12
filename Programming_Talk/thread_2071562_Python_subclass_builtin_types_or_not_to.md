---
title: "Python subclass builtin types or not to?"
date: 2012-10-15
forum: Programming Talk
---

### Post by fokuslee on 2012-10-15
Hi 
I got myself into subclassing python builtin type. 
However now i read from some sources that we should not subclass the builtins but instead subclass ABC. 
However there are plenty of tutorials on how to subclass the builins.
I am pretty confused. So should this be done or not?
or should be done under certain conditions.
Thanks
Tao Li

---

### Post by trent.josephsen on 2012-10-15
Well, what you *should* do depends heavily on what you're writing, how it will be used, and how the existing code is written. It's probably something you should avoid because of the potential for surprises, but I'd be foolish to give advice on code I've never seen...

That said, I find it hard to think of a case where subclassing built-in types is a *practical* and *useful* idea, especially as compared to using composition. Especially in a duck-typed language like Python -- what problem can be more easily solved by subclassing a built-in type than by simply creating a new one?

The Zen of Python (run `python -m this` to see the whole thing) has a few lines that might speak to this practice:

"Explicit is better than implicit" -- Are you trying to subclass a built-in type so that you can (implicitly) take advantage of that class's definition of certain operators or methods? It might be better to define your own methods within the class, which makes it easier to predict the control flow for debugging. (This guideline is a big one for Python, and you may hear Python people say EIBTI like Perlers say TMTOWTDI.)

"Special cases aren't special enough to break the rules" -- How will your subclass behave differently from its parent? Will your changes surprise programmers using it, or break common idioms if it's used in place of its parent? Those are Bad Things.

"Although practicality beats purity" -- On the other hand, maybe you're using code that uses an object of built-in type and you just want to make a small change to the object's behavior. It might be more practical to extend the built-in type than to re-code the whole thing, or create your own type that acts almost exactly the same.

"If the implementation is hard to explain, it's a bad idea" -- Self-explanatory, really. Document your code concurrently with writing it; if you find your design difficult to explain in English, it's probably a bad design in Python too.

Sorry about the wall of text, I'm currently not otherwise occupied so I have lots of time to write on Internet forums ;)

---

### Post by fokuslee on 2012-10-16
Hi Trent
Thanks for your detailed answer,
Some of the Zen wisdom make sense to me right away, but others take more time to digest.
i will keep those points in mind as i learn more about programming 
Thanks
Tao

---

