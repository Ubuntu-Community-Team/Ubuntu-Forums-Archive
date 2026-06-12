---
title: "java method not executing......"
date: 2009-07-08
forum: Programming Talk
---

### Post by abhilashm86 on 2009-07-08
i tried a program to return a value to main function, but its not working, when i find a random value, assign to variable of int a, then say return, nothing is returning, what is problem
```

class j15 {
int a;
int randa()
{
       a= (int)(Math.rand()* 10);
       return a;
}
}

class run{
public static void main(String [] args) {
      j15 ran= new j15();
      int guess=ran.randa();
      System.out.println("number guessed is "+guess);
}
}


```

---

### Post by baizon on 2009-07-08
> **abhilashm86 said:**
> i tried a program to return a value to main function, but its not working, when i find a random value, assign to variable of int a, then say return, nothing is returning, what is problem
```

class j15 {
int a;
int randa()
{
       a= (int)(Math.rand()* 10);
       return a;
}
}

class run{
public static void main(String [] args) {
      j15 ran= new j15();
      int guess=ran.randa();
      System.out.println("number guessed is "+guess);
}
}


```

Change in line 5 Math.rand() to Math.random()

```
number guessed is 5
```

---

### Post by insilicium on 2009-07-08
also, you need to declare the class with the main method public.  So change the line

```
class run {
```

to

```
public class run {
```

and make sure that the filename and the public class have the same name.  So, if the public class is called run, make sure the filename is run.java.

Cheers!

---

### Post by Zugzwang on 2009-07-08
> **abhilashm86 said:**
> i tried a program to return a value to main function, but its not working, when i find a random value, assign to variable of int a, then say return, nothing is returning, what is problem


How did you get your code to compile? That rand() function doesn't exist. If you got an error message during the compilation process, you should state that here.

---

### Post by abhilashm86 on 2009-07-08
oh i'm really sorry, i always code c++, so i used that rand() function, simple doubt, now i got it......

---

