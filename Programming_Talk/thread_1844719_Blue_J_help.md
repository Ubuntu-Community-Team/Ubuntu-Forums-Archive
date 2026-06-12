---
title: "Blue J help"
date: 2011-09-15
forum: Programming Talk
---

### Post by guber on 2011-09-15
Okay so Im new to this stuff but say I have this (short thing to get to the point)


public class test
{public static void main(String args[])
{int x = 1;
if (x == 1)
{int q = 5;
}
int g = q + 1;
}
}
    

Why do I get a error message saying cant find int q. how would I get int q to be part of the main script...or whatever its called

---

### Post by karlson on 2011-09-15
> **guber said:**
> Okay so Im new to this stuff but say I have this (short thing to get to the point)


public class test
{public static void main(String args[])
{int x = 1;
if (x == 1)
{int q = 5;
}
int g = q + 1;
}
}
    

Why do I get a error message saying cant find int q. how would I get int q to be part of the main script...or whatever its called

You might want to use indentation along with curly braces it's easier to read the code that way.

The problem is that by the time you use q it's out of scope.  Namely:
```

public class test
{
    public static void main(String args[])
    {
       int x = 1;
       if (x == 1)
       {
           int q = 5;
       }
       int g = q + 1;
    }
}

```

In Java/C++ the variable exists only in the code block where it is defined.  So by the time you exit from the "then" clause of the if statement "q" no longer exists.

So to solve it you need:
```

public class test
{
    public static void main(String args[])
    {
       int x = 1;
       int q = 0;
       if (x == 1)
       {
           q = 5;
       }
       int g = q + 1;
    }
}

```

---

