---
title: "While loop question"
date: 2008-05-20
forum: Programming Talk
---

### Post by glolite on 2008-05-20
hi, 

I have a question that I have given some thought to and cannot come up with a suitable answer.

I am programming in Java and I have a method lets say getClick() that returns a instance of a class... I want to keep looping over this until getClick() returns null.

essentially while (getClick() != null) { some code } 

my problem is I have no way to find the value of getClick() within each loop.

Therefore I want something like

while ((Class class = getClick()) != null) { reference class here }

which I can then call "class" each time the loop iterates.. however this doesn't compile.. am I missing something, or is there an easy way to solve this problem?

thanks!

---

### Post by lisati on 2008-05-20
> **glolite said:**
> hi, 

I have a question that I have given some thought to and cannot come up with a suitable answer.

I am programming in Java and I have a method lets say getClick() that returns a instance of a class... I want to keep looping over this until getClick() returns null.

essentially while (getClick() != null) { some code } 

my problem is I have no way to find the value of getClick() within each loop.

Therefore I want something like

while ((Class class = getClick()) != null) { reference class here }

which I can then call "class" each time the loop iterates.. however this doesn't compile.. am I missing something, or is there an easy way to solve this problem?

thanks!

One option I was taught many years ago (in another programming language, can't remember which one) was to do something like this (please forgive my style, I'm not a java programmer)

```

item = getClick()
while (class != NULL)
      {
      ..... some code .....
      item = getClick()
      }

```

---

### Post by glolite on 2008-05-20
thanks for the quick reply, but I am not sure that will work.

the loop iterates over the result of getClick() which obviously can change every time it is called. so doing it the way you have shown "item" could quite possibly have a different instance in it every time?

I want to reference the result of getClick() that is used to loop on each occasion.

---

### Post by pedro_orange on 2008-05-20
```

item = getClick()
while (item != NULL)
      {
      ..... some code .....
      item = getClick()
      }

```

You are then checking the contents of item for NULL each iteration; breaking the loop when the condition is met.

I'm not a Java programmer, but I'm sure this will do.
This is probably how I'd do it in c++

EDIT: Oh hang on. Are you testing the same instance of a class each time? In which case, forget the item=getClick(). Just keep testing the same class. (As long as you're changing it in the code ofc; otherwise you'll get an infinite loop)

---

### Post by glolite on 2008-05-20
ahh yes ok, sorry I was slow on the uptake I will give it a shot now, thanks for the help!

I am testing a different instance of the class each time, how you have showed it works perfectly Thanks again!

---

### Post by Tomosaur on 2008-05-20
> **glolite said:**
> hi, 

I have a question that I have given some thought to and cannot come up with a suitable answer.

I am programming in Java and I have a method lets say getClick() that returns a instance of a class... I want to keep looping over this until getClick() returns null.

essentially while (getClick() != null) { some code } 

my problem is I have no way to find the value of getClick() within each loop.

Therefore I want something like

while ((Class class = getClick()) != null) { reference class here }

which I can then call "class" each time the loop iterates.. however this doesn't compile.. am I missing something, or is there an easy way to solve this problem?

thanks!

EDIT: Never mind, just noticed you already sorted it :P

---

