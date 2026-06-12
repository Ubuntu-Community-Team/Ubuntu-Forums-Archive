---
title: "try catch program"
date: 2015-01-23
forum: Programming Talk
---

### Post by vijay9 on 2015-01-23
how use try catch block with method
----------------------------------------------------------------

it show me error
```
javac exp.java
exp.java:12: error: 'try' without 'catch', 'finally' or resource declarations
        try
        ^
exp.java:18: error: illegal start of type
    catch(ArithmeticException e)
------------------------------------------------------------------------
                  code is here


class exp
{
    int a,b;
    exp(int a, int b)
    {
        this.a = a;
        this.b = b;
    }
    
    void getExp()
    {
        try
           {
            int c = a/b;
            System.out.println("statement not print");
           }    
    }
    catch(ArithmeticException e)
    {
        System.out.println("not divided by 0");
    }
    public static void main(String args[])
    {
        exp a1 = new exp(10,0);
        a1.getExp();
    }
}
```

---

### Post by kpatz on 2015-01-23
Your brackets aren't matched correctly.  In particular, one closing bracket needs to be moved.  I'll leave it as an exercise for you to figure it out.  (hint: indenting the code correctly will make it jump out)

Also, it's best to put code in [noparse]```
...
```[/noparse] tags so it gets indented properly.

---

### Post by slickymaster on 2015-01-23
*Moved to the ***Programming Talk*** sub-forum.*

Without further info on the rest of your code, I'll just correct your code format:
```
int a, b;

    exp(int a, int b) {
        this.a = a;
        this.b = b;
    }

    void getExp() {
        try {
            int c = a / b;
            System.out.println("statement not print");
        } catch (ArithmeticException e) {
            System.out.println("not divided by 0");
        }
    }

    public static void main(String args[]) {
        exp a1 = new exp(10, 0);
        a1.getExp();
    }
```

---

### Post by vijay9 on 2015-01-23
ya i got answer catch outside of method body. catch always followed by try

---

