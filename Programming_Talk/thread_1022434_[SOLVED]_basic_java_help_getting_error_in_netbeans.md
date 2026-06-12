---
title: "[SOLVED] basic java help getting error in netbeans and at commandline"
date: 2008-12-26
forum: Programming Talk
---

### Post by aszxcv on 2008-12-26
[HTML]public class math {
 
    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
    int x = (int) Math.PI * 20.0;
    System.out.println(x);
 
    }
 
}
[/HTML]



```
found   : double
required: int
    int x = (int) Math.PI * 20.0;
1 error
BUILD FAILED (total time: 0 seconds)

```


the code is suppose to round math pi to 3 and then multiple by 20 and produce the answer 60. but i keep getting the error above when i try to build this project:confused:

---

### Post by achelis on 2008-12-26
20.0 is explicitly a double.

That means you're casting the Math.PI constant to an int then multiplying it by a double which results in a double.

Changing x to a double would give you the result you're after as a double.

Changing 20.0 to 20 (which is an int) would give the result you're after as an int.

Hope that made sense, otherwise feel free to ask again :)

Edit:
Quick note on literals in Java:
```

Literal  Type
10       integer
10l      long
10f      float
10.0     double
10d      double 

```

---

### Post by aszxcv on 2008-12-26
gotcha thanks for explanation .

---

### Post by meanburrito920 on 2008-12-26
It is often useful to just throw a pair of parenthesis around the entire expression that is being cast, which takes care of any ambiguities in order of operations. 
So for example the line 

```

int x = (int) Math.PI * 20.0;

```

would become

```

int x = (int) ( Math.PI * 20.0 );

```

and would work just fine.

---

