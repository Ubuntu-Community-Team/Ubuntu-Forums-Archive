---
title: "C++ class syntax (public shared function)"
date: 2009-06-06
forum: Programming Talk
---

### Post by WitchCraft on 2009-06-06
Hi, I've a question:
 
In most object-oriented programming languages, you can access math functions by typing for example 
```

math.acoth(x)

```
 
Now, the interesting thing is you don't have to derive the math class from it's definition, i mean:
```

Cmath math = new Cmath();

```
 
 
Now VB.net has this interesting modifier: shared
So if you declare 
```

Public Shared Function acoth(byref x as double) as double

```
in a class, you can call math.acoth(x) without defining a math object.
 
How is the corresponding C++ syntax to achieve the same?

---

### Post by simeon87 on 2009-06-06
Is this the same as static methods? If so, you can simply use the keyword static in C++.

---

### Post by WitchCraft on 2009-06-06
> **simeon87 said:**
> Is this the same as static methods? If so, you can simply use the keyword static in C++.
 
 
It sure as hell looks like that - but i'm not 100% sure, that's why I ask.
 
Actually public static :-)))
 
//C#
```

public class Foo
{
    public static void Bar()
    {
        Interaction.msgbox("Hello");
    }
}
 
 
'VB.NET
Public Class Foo
    Public Shared Sub Bar()
        Interaction.msgbox("Hello")
    End Sub
End Class

```

---

### Post by simeon87 on 2009-06-06
> **WitchCraft said:**
> It sure as hell looks like that - but i'm not 100% sure, that's why I ask.

I don't know Shared but with static in Java/C++, you can write ClassName.method() to execute a method of a class. That matches your description of running a method from a class without creating an object.

---

### Post by WitchCraft on 2009-06-08
> **simeon87 said:**
> I don't know Shared but with static in Java/C++, you can write ClassName.method() to execute a method of a class. That matches your description of running a method from a class without creating an object.

Yes it does, I solved my own thread the moment I put the VB.NET code in a VB to C Sharp converter.

Sometimes it's funny, you used to program in C/C++, and then you discover some feature while you're using Basic ;-))

---

