---
title: "Package and Object Creation"
date: 2009-04-22
forum: Programming Talk
---

### Post by JohnSearle on 2009-04-22
I have a package that contains two classes, one of which I would like to instantiate as an object in the other (Create Date object in Dog class, which both reside in Pet). 

I've been searching for the answer, but have so far turned up nothing. What am I doing wrong here?

From Dog.java:
```
package pet;  

public class Dog{
   private String breed, sex;
   private float weight;
   private Date bDay;   // gives error on compilation
...
```

From Date.java:
```
package pet;

public class Date{
   private int day;
   private int year;
   private String month;

   public Date(int newDay, String newMonth, int newYear){ 		
      day = newDay;
      year = newYear;
      month = newMonth;	}

...
```

Error in Geany:
```
Dog.java:26: cannot find symbol
symbol: class Date
location: pet.Dog
private Date BDay;
```

Date.java compiles fine, and works just fine if I try to instantiate it through main; but it fails to work if attempted through its sibling package member.

Any help would be appreciated.

Note: This is for a homework assignment, but I'm only asking to be pointed in the right direction.

Thanks,

- John

---

### Post by eye208 on 2009-04-23
By default the Java compiler writes all class files to the current directory. If you organize your classes in packages, you should use the -d option to make javac create a subfolder structure according to the package names.

For example, this...
```
javac Date.java
javac Dog.java
```
... will not work because at the time you compile Dog.java, the compiler will search the current directory and the classpath for a file "pet/Date.class" which does not exist. However, this...
```
javac -d . Date.java
javac -d . Dog.java
```
... will work fine because both classes will be written to a "pet" subfolder in the current directory.

---

### Post by JohnSearle on 2009-04-23
> **eye208 said:**
> By default the Java compiler writes all class files to the current directory. If you organize your classes in packages, you should use the -d option to make javac create a subfolder structure according to the package names.

For example, this...
```
javac Date.java
javac Dog.java
```
... will not work because at the time you compile Dog.java, the compiler will search the current directory and the classpath for a file "pet/Date.class" which does not exist. However, this...
```
javac -d . Date.java
javac -d . Dog.java
```
... will work fine because both classes will be written to a "pet" subfolder in the current directory.

Thank you!

I just tried it using this method, and it worked. I then went back into the IDE (Geany) and attempted to compile it through it, and it worked as well. I tried deleting all the class files, restarting the IDE and compiling, and it worked yet again.

I have **no** idea what just occurred. I'm more confused then every, but at least its working :)

Thanks again.

- John

---

