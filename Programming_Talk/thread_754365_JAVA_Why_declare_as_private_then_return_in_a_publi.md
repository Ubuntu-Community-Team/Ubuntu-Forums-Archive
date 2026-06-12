---
title: "JAVA: Why declare as private then return in a public method?"
date: 2008-04-13
forum: Programming Talk
---

### Post by Aeph on 2008-04-13
I have found that one of the best ways (for me) to learn a language is by reading code. In doing so, I have begun to wonder why a variable is declared as private...

[SIZE="1"]example:[/SIZE]
```
private JPanel panel;
```

...then used in a local method and finally returned as public in a method in this manner:

[SIZE="1"]example:[/SIZE]
```
public JPanel getPanel() {
     return panel;
}
```

Is this more efficient than just declaring the variable as public initially, or is there some other reason to do this?

---

### Post by tamoneya on 2008-04-13
This is so that the panel cant be modified or altered without the permission of the class or object to which it belongs.  For example you may want to count the number of times that it is accessed in which case you would need to force people to use the getPanel() method.  Also you may not want people altering the panel from outside of the class.  While you may not see the benefit immediately when working with smaller code segments it starts to pay off when you are managing large code and is overall considered a good practice.

---

### Post by themusicwave on 2008-04-13
It really has to do with Visibility and information hiding.

How useful it is varies on a case by case basis, but the basic idea is that In Java you often don't want to give users access to the underlying variables.  Also, you often don't want users to care about the underlying variables.

It really depends on the situation.  Also in some cases, you can add in error checking/ exception throwing to the function.  Like for example if I had a Calendar class with a setDay function.  I could check to make sure the day sent was valid for that month and throw an error if it wasn't.

With a simple public variable you throw this responsibility to the user.  It is up to them to sent good data.

Also one thing I kind of like about Java is when I use and IDE to look at functions associated with an object, in Java I can always just hit g and look at the get functions to see what properties the thing has for me to use.

It is useful and is a convention throughout Java.

---

### Post by Tuna-Fish on 2008-04-13
Also, one additional point: If the enemy, I mean the other developers, cannot directly touch your data, you can later change how you store that data without having to modify anything but the class itself. If you ever make anything really big, you'll start to appreciate this a lot. It's actually such a good feature, that some programming languages make it easier to use by so-called properties.

For example, in delphi pascal, you can do:
[php]
 property Color: Integer read GetColor write SetColor; 
// then when you type
x.Color = y.Color; // it really turns into
x.SetColor(y.GetColor()); // in the compiler.
[/php]

This feature is used at least in dephi, c#, and can be implemented with some hoops in python. I **so** wish they'd have removed the property() madness in p3000 and made def __set_variablename(self, a): turn variablename into a property. But no.

---

