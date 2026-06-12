---
title: "Overhead of local variables in Java"
date: 2012-01-16
forum: Programming Talk
---

### Post by Kentucky88 on 2012-01-16
Is there any overhead in using local variables in Java in an effort to enhance readability?  For example, is the following function:

[PHP]public static void main(String args[])
{
    System.out.println(getNumber());
}

public int getNumber()
{
    return 1;
}[/PHP]any more efficient than:

[PHP]public static void main(String args[])
{
    int somenumber = getNumber();
    System.out.println(somenumber);
}

(using same getNumber() as defined above.)[/PHP]I would think that the Oracle or OpenJDK Java compilers would be smart enough to realize that the local variable "somenumber" in the function above is only used as a holder for the result of calling getNumber().  So that if the result of getNumber() as well as the variables used by getNumber() are not changed by the code, then the optimized compiled code would not have a local variable and simply pull the result from getNumber().  Is that what really happens?

---

### Post by Simian Man on 2012-01-16
That will make no difference in the runtime of the program.  However it's not necessarily a question of Java realizing that the second version doesn't need a local variable, but of Java realizing that the first version *does* need a local variable.  When compilers compile code they generate temporary values for things like this all of the time.

However, whether the temporary is a local on the actual stack, a value in the JVM or a register on the machine depends on the implementation and the architecture.

---

### Post by ofnuts on 2012-01-16
> **Simian Man said:**
> That will make no difference in the runtime of the program.  However it's not necessarily a question of Java realizing that the second version doesn't need a local variable, but of Java realizing that the first version *does* need a local variable.  When compilers compile code they generate temporary values for things like this all of the time..
The compiler may have to compile a method in many cases:

```

class MyClass {
  void printNumber() {
     System.out.println(getNumber())
 }

 int getNumber() {
    return 1;
 }
}

```
So far, so good.

Now add this code in the picture:
```

class MyDerivedClass extends MyClass {
 int getNumber() {
   return 2;
 }
}

// ... elsewhere...

obj1=new MyClass();
obj1.printNumber();

obj2=new MyDerivedClass();
obj2.printNumber();

```

I'll let you test with the various qualifiers (public/protected/private) and with or without "final".

---

### Post by Simian Man on 2012-01-16
You seem to be talking about dynamic function binding which has nothing to do with code generation for individual functions.  I didn't say that the Java compiler would automatically inline the getNumber function, just that it wouldn't matter if he used an explicit temporary or not.

---

