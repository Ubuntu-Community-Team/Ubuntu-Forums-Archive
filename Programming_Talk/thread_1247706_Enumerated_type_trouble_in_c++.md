---
title: "Enumerated type trouble in c++"
date: 2009-08-23
forum: Programming Talk
---

### Post by nite owl on 2009-08-23
I am really stumped on a question I have got, cut a long story short we were asked to create an enumerated data type and use it to set a certain value i.e.

```
enum xType{aaa, ccc, ddd, rrr};
```

My question is during runtime how could the user set say 'ccc' as there value of choice.

I know the compiler views 'aaa, ccc, ddd, ..' as '0, 1, 2, ..' respectively. In tutorials on the internet they never have the end user set the value its always hard coded i.e.

```
xType myType;
myType = ccc;
```

Once I figured out what an enumerated type was I though it would be as simple as:

```
cin >> myType; 
```

but obviously I was way off, I would greatly appreciate even just a hint in the right direction

---

### Post by Brandon Williams on 2009-08-23
An enum is really just a specialized type of int with symbols that represent various numbers. The user would not be able to give you "ccc" as the input value. They would have to give you an appropriate number, just like when you take values from the user to fill in an int variable. Alternatively, you could take string input and convert it manually into the correct numeric value.

---

