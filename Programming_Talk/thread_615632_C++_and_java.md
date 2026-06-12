---
title: "C++ and java"
date: 2007-11-17
forum: Programming Talk
---

### Post by nickoli on 2007-11-17
I was hoping to get a few opinions.I have registered to take c++ and intro to java this semester. I don't know if its a good idea to take them both at the same time. I need c++ as a prerequisite for several classes and I want to have an emphasis on java. Any opinion is appreciated thanks.

---

### Post by Arkainium on 2007-11-17
I think you'll find that both classes are going to cover a lot of the same material, especially if they're intro classes.  Java's syntax was heavily influenced by C++ so they're syntactically similar.  If C++ is a prerequisite for other classes you'll be better of taking C++ and learning Java on the side on your own.  I'm assuming the Java class will just be covering Java as a language, and not delving too much into the APIs and class libraries, which is arguably the heart of Java.

---

### Post by LaRoza on 2007-11-17
You should have no trouble.

Java and C++ by themselves can be learned in an hour, if you already understand basic programming concepts.

The standard libraries are what matter, along with algorithm design and data structures.

---

### Post by CptPicard on 2007-11-17
It really depends on your skill level. If you're a  beginning programmer, you would probably benefit more of an intro course in Java, and C++ can be tougher going. On the other hand, if you're OK with the C++ class, the Java class is useless; you'd be able to learn Java on your own, essentially.

> **LaRoza said:**
> 
Java and C++ by themselves can be learned in an hour, if you already understand basic programming concepts.


I for one did not learn C++ in an hour. ;) It's got a lot of stuff that you need to consider that is not present in a memory-managed language like Java, and if you're new to OOP, some more...

---

### Post by LaRoza on 2007-11-17
> **CptPicard said:**
> 
I for one did not learn C++ in an hour. ;) It's got a lot of stuff that you need to consider that is not present in a memory-managed language like Java, and if you're new to OOP, some more...

Most people do not. I didn't either.

The point was, a language class like C++ or Java is probably going to be a waste of money. Taking classes on more important programming concepts, like Algorithms, OO Design, Data structures, and how to program in general would be more benificial.

---

### Post by nickoli on 2007-11-17
Thanks for your help in this matter. Both courses are requirements for my degree at the college I am attending I was just curious if it would be too overwhelming to take them both at the same time. From what you all have said I would take that as a no. It wouldn't be. Once again thanks.

---

### Post by LaRoza on 2007-11-17
> **nickoli said:**
> Thanks for your help in this matter. Both courses are requirements for my degree at the college I am attending I was just curious if it would be too overwhelming to take them both at the same time. From what you all have said I would take that as a no. It wouldn't be. Once again thanks.

Requirements are requirements...

They are very similar at first glance, so syntax and most concepts will be the same. There are differences, so I suggest you get familiar with them. At least write and compile and run a few C++ and Java programs before classes start.

My wiki may help in this.

---

### Post by dumbsnake on 2007-11-17
I have to say that I think c++ and java are very different languages.  The syntax is similar, but many keywords work totally differently.  In general, I'd say C++ is a much, much more challenging language to learn.  I learned java in a couple hours.... C++ (by far my favorite language) I have been learning for years and I still have plenty to learn.  I'd say I know way more about C++ than most people, but the advanced features that are part of C++ and the design patterns possible are truly extensive and many of them are NOT simple.  Fortunately for you, I doubt you will really learn any of the more advanced features of the C++ language.  But writing templates that pass templated arguments for instance and inherit from multiple templated classes are things you just won't see in java.

Just a few words of caution...  Don't assume that similar looking sytax means the same thing.  A couple important points here:

1) C++ has 3 basic ways of passing around an object (reference, value and pointer) while java only has one (reference).  When you pass an object in C++, you must use & to pass by reference.

2) The new operator means different things in those languages.  In C++ it returns a pointer, java returns a refernce.

3) all objects are created on the heap in java...  so you don't have lots of the complexity and possibility you have in C++.


My overall point: Java is essentially C++ with most of the hard stuff taken out.  With that comes a loss of possibilities, but you do gain simplicity.  If you are serious about being a good programmer, learn how to use those more advanced features of C++ and you will see an improvement in your designs and productivity.  
In my opinion, syntax aside, java is more similar to visual basic than to C++.  I wish they had used a syntax that made more sense for their language instead of confusing people by making it similar to C++.

Goodluck

---

### Post by LaRoza on 2007-11-17
> **dumbsnake said:**
> 
Just a few words of caution...  Don't assume that similar looking sytax means the same thing.  A couple important points here:

1) C++ has 3 basic ways of passing around an object (reference, value and pointer) while java only has one (reference).  When you pass an object in C++, you must use & to pass by reference.

2) The new operator means different things in those languages.  In C++ it returns a pointer, java returns a refernce.

3) all objects are created on the heap in java...  so you don't have lots of the complexity and possibility you have in C++.


0. Java can pass "by reference", although it works differently

1. Pointers do not exist in Java, that is a difference

2. Memory allocation differences are the biggest difference between Java and C++

Java and C++ are very similar, when you take into account other non C style languages and non imperative languages.

---

### Post by pmasiar on 2007-11-17
> **nickoli said:**
> Both courses are requirements for my degree at the college I am attending I was just curious if it would be too overwhelming to take them both at the same time. From what you all have said I would take that as a no. It wouldn't be. Once again thanks.

I do not know about overwhelming, but certainly it could be confusing - Java and C++ are similar, but not exact equivalents.

So answer also depends on your previous programming experience, and on exact steps you need to take after any of these courses.

I would suggest take one where more basic stuff is done, then switch to the other one, but not jump between them, if you can arrange for that. It needs some advanced skill level to be proficient simultaneously in multiple languages, especially in closely related ones. Little differences and quirks might drive you crazy.

In real life this mixing does not happen, if one project is in Java, only is very strange coincidence will require large part of it in C++ later.

IMHO, YMMV.

---

### Post by CptPicard on 2007-11-17
Snake, you're forgetting about primitives. They are passed by value, and are allocated on stack in Java.

---

### Post by dumbsnake on 2007-11-17
> **CptPicard said:**
> Snake, you're forgetting about primitives. They are passed by value, and are allocated on stack in Java.

My bad... you are totally correct on that count.  With the exception of primitives though, everything in java is an object created on the heap and passed by reference.  And I really don't buy that they are similar at all.  Sorry...

A common construct you would see with a good C++ programmer is something like the following:

```

template<typename orderby_type, typename second_column_type> void sort_2_columns(std::vector<orderby_type> &c1, std::vector<second_column_type> &c2){
  // implementation
}

```

A Java programmer thinking they are programming in C++ perfectly well might write this code:

```

void sort_2_columns(std::vector<unsigned int> &c1, std::vector<std::string> &c2){
  // implementation
}

void sort_2_columns(std::vector<unsigned int> &c1, std::vector<float> &c2){
   // implementation
 }

```

A really good C++ programmer might write something even more advanced like the following:

```

template<typename orderby_it_type, typename second_column_it_type> void sort_2_columns(orderby_it_type ob_begin, orderby_it_type ob_end, second_column_it_type sc_begin, second_column_it_type sc_end ){
  // implementation
}

```

The only way to get that kind of flexibility with Java is with polymorphism, but there are many cases where you just can't get that same level of flexibility and furthermore, you can't use primitives in there or make use of operators...  So really it is just not going to work.

Note: this is just a dumb example I came up with in 5 minutes.  But, if you would opt for that second option in your code, you are not really programming in C++... you are using a subset of C++.  Sure, it will compile under a C++ compiler, but you aren't doing it the way it was meant to be done.

---

