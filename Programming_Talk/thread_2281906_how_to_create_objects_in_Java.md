---
title: "how to create objects in Java?"
date: 2015-06-10
forum: Programming Talk
---

### Post by sypher2 on 2015-06-10
Im getting an error when i try to create an object. It keeps saying Sniper can not be resolved to a type. Can anyone explain how to create an object? Here is what im writing out...

Sniper s1;

public void startFireFight() {

s1 = new Sniper;
}

---

### Post by ofnuts on 2015-06-11
If you are not in the Sniper class, you must import Sniper (import some.package.path.Sniper). Furthermore to create a Sniper, you are calling one of the constructors so you need parentheses (new Sniper()) even assuming that the constructor takes no parameters.

---

### Post by Gustaf_Alhll on 2015-06-12
Have you created a class for it yet?
If you haven't, create one and put this inside:
```
class Sniper
{
    public Sniper
    {
        // TODO: Add initialization code here
    }
}
```

If you don't know the concept of a class, it's techincally a source file that stores data or run code. If you want to know how I work, I stick to many but small classes. It's usually easier to find what you're looking for if you have many small files instead of a really big one.

If you have, make sure that both the Sniper class and the main class is inside the same package, something like this:
```
package SniperExample;
```
SniperExample could be something else, but the important thing is that both files has the same package name.

If that still isn't enough, make sure that the class is included in the compiler and linked correctly. Otherwise, the file either doesn't exist because it never got compiled in the program or could not be found due to the linker not connecting the files correctly. If you're using and IDE, however, it's very unlikely that this is the issue.

I hope this helps. It was a long time ago I worked with Java, but I still hope this helped.

---

### Post by ofnuts on 2015-06-12
> **Gustaf_Alhll said:**
> Have you created a class for it yet?
If you haven't, create one and put this inside:
```
class Sniper
{
    public Sniper
    {
        // TODO: Add initialization code here
    }
}
```

If you don't know the concept of a class, it's techincally a source file that stores data or run code. If you want to know how I work, I stick to many but small classes. It's usually easier to find what you're looking for if you have many small files instead of a really big one.

Make that 
```

class Sniper
{
    public Sniper() // Don't forget the parenthese, even if you have no parameters
    {
        // TODO: Add initialization code here
    }
}

```

> **Gustaf_Alhll said:**
>  If you have, make sure that both the Sniper class and the main class is inside the same package, something like this:
```
package SniperExample;
```
SniperExample could be something else, but the important thing is that both files has the same package name.


By convention, Java package names are lowercase:
```
package sniperexample;
```

---

