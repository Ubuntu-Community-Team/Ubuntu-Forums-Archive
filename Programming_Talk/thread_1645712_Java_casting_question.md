---
title: "Java casting question"
date: 2010-12-14
forum: Programming Talk
---

### Post by kwyto on 2010-12-14
Hi guys, 
Here is my problem 
```

Interface B {
  Factory {
     returns an instance of A
  }
}

class A implements B {
}

A a = (A) b;

```
Gives an error saying that b cannot be cast to A. I confirm that b is an instanceof B. Can anyone clarify?

---

### Post by shadylookin on 2010-12-15
Think of it this way a cat is a mammal, but a mammal is not necessarily a cat. 

It wouldn't make any sense to try to cast B into A because an interface B is not necessary an instance of Class A even if A implements it. 

I don't recall whether that's legally valid casting, but even if it is I would avoid doing so.

---

### Post by kwyto on 2010-12-15
Thank you for the response. You might have answered the question, but I'm still a little confused. I will work around it, to find a diff solution which doesn't involve doing the casting.

---

### Post by shadylookin on 2010-12-15
let me try it this way. 

if you have a parent interface

interface Mammal{
.....
}

2 classes that implement it

Class Cat implements mammal{

}

class Dog implements mammal{

}


a function that takes an instance of the interface

public static void blah(Mammal m){
    Cat c = (Cat) m;
    //you're making an assumption that every mammal that
    // get's passed to this function will be a Cat
}

and a main function that calls said function

public static void main(string args[]){
    Mammal m = new Dog();
    blah(m);
}


like in the above example there is a possibility that the actual class won't be a Cat it's a bad idea to try and cast a parent into a subclass.

---

### Post by kwyto on 2010-12-15
Ok, I saw a similar explanation, but I believe now it makes more sense. Thank you all for your help.

---

### Post by KdotJ on 2010-12-15
As a side note, and to avoid ClassCastExceptions, you can use the instanceof operator. So for the blah method above...

```

public static void blah(Mammal m) {
    if (m instanceof Cat) {
        //Can cast m to a Cat object
    } else { 
        //m is not a Cat
    }
}

```

---

