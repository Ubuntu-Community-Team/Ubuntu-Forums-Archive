---
title: "random function in java ??"
date: 2009-06-12
forum: Programming Talk
---

### Post by abhilashm86 on 2009-06-12
well if i use random numbers between an interval like in c++, javac is throwing error, this is what is did,
```

public class j4{
public static void main(String args[]){
double sum=0;
double randomize(0,100);
double x=Math.random();
sum+=x;
System.out.println("value is "+sum);
}
}


```
so when i tried, javac said needs to be double, so changed,
javac j4.java
j4.java:4: ';' expected
double randomize(0,100);
                ^
1 error

---

### Post by pokerbirch on 2009-06-12
I'm not a Java programmer, but:

Is randomize() a function? If it's a function, shouldn't you be assigning it to a variable?

---

### Post by gvoima on 2009-06-12
AFAIK there's no such method in the java Random class. Or any other like it.

---

### Post by pokerbirch on 2009-06-12
Perhaps he's thinking along the lines of VB6 which has a Randomize() function which creates a random seed. It's not required in Java. A quick Google found this:

[http://www.javapractices.com/topic/TopicAction.do?Id=62](http://www.javapractices.com/topic/TopicAction.do?Id=62)

---

### Post by rocketflame on 2009-06-12
Math.random()

gives you a random double between 0 and 1
i dont know c++, but i'm guessing you want it between 0 and 100?
if thats the case you can always use


(Math.random() * 100)

then try getting rid of 

double randomize(0,100);

and see if it works.

---

### Post by abhilashm86 on 2009-06-12
> **rocketflame said:**
> 

(Math.random() * 100)

.

yes good, it worked........

---

### Post by abhilashm86 on 2009-06-12
> **pokerbirch said:**
> I'm not a Java programmer, but:

Is randomize() a function? If it's a function, shouldn't you be assigning it to a variable?

yes true randomize is user defined function, we use srand(time(0)) and then initialize int x=rand()%100; to get interval,

---

