---
title: "[Java] Provlem with toUpperCase(char ch)"
date: 2009-11-14
forum: Programming Talk
---

### Post by SpinningAround on 2009-11-14
Having some problem with getting this part to work, don't understand why it wont compile.

```

char CH = toUpperCase(ch);

```

Error Message
```

cannot find symbol
symbol  : method toUpperCase(char)
location: class isVowelTest
		char CH = toUpperCase(ch);
		          ^
1 error

```

---

### Post by squaregoldfish on 2009-11-14
Use Character.toUpperCase(ch)

In Java, you can't call a method without the context of an object, or (for static methods) a class. In this case, you have to specify that you want to call the static toUpperCase method from the Character class.

Steve.

---

### Post by fiddler616 on 2009-11-14
squaregoldfish is right, but to expand on that:

You can't call a method from any of the four primitive types (int, double, boolean, char), instead you have to use the wrapper classes: Integer, Double, Boolean and Character. For another example, instead of
```
String x = "2.4";
double y;
y = y.parseString(x);
```
or similar nonsense, you have:
```
String x = "2.4";
double y = Double.parseString(x);
```

For more fun, refer to the API.

And adding to my List of Things I Hate About Java, the above code is kind of weak when compared to a language like Python with ONE function to convert ANYTHING to a double/insert-primitive-type-here.

---

### Post by SpinningAround on 2009-11-15
Thanks :) made it make a little more sense ;)

---

### Post by fiddler616 on 2009-11-15
> **SpinningAround said:**
> Thanks :) made it make a little more sense ;)
Anytime.

*Psst! Mark the thread as solved!*

---

