---
title: "The reason that I prefer C++ instead of Java"
date: 2009-11-01
forum: Programming Talk
---

### Post by miklcct on 2009-11-01
1. In C++, everything is an object. Compare the following code segment (Foo is a class):

C++
```

int a;
char b;
Foo *c;

```

Java
```

int a;
char b;
Foo c;

```

In the C++ example, a, b, c are objects but, in Java, they are not objects. Therefore, in Java, you cannot make pointers point to a, b and c.

2. There are references in C++ but not in Java. For example, the following C++ code is not possible in Java:

```

void swap(int &a,int &b) {
  int c=a;
  a=b;
  b=c;
}

```

3. C++ has pointer arithmetic but not in Java. For example, the following C++ code segment is not possible in Java:

```

int *p=new int[10];
int *q=p + 3;

```

4. (deleted)

5. In C++, you are free to allocate objects in the program image, in the heap or on the stack. In Java, you can only allocate objects in the heap and primitives and pointers on the stack. The following C++ code is not possible in Java. (Foo is a class)

```

class Blah {
public:
  void method() {
    Foo a; // a is allocated on the stack and is destructed automatically when a goes out of scope.
  }
};

```

6. In C++, object are values. In Java, object are not values. Therefore, in combination of the fact that Java has no references, you cannot pass an object into a function or return an object, only their pointers can be passed around. In Java, you must also manually write a clone function to copy an object but in C++, a simple assignment copies an object. The following C++ code is not possible in Java.
```

class Foo {
};

void func(Foo x) {
}

int main() {
  const Foo x;
}

```

7. In Java, objects cannot be made read-only (although pointer that points to the object can). See the above code for example.

8. In Java, there is no operator overloading. Therefore, it is impossible to write generics that applies to both primitives and objects. Here is a bubble sort algorithm written in C++, which is not possible in Java:
```

template <class T> void sort(T *begin, T *end) {
  for(T* i=end; i > begin; --i) {
    for(T* j=begin; j + 1 < i; ++j) {
      if(j[1] < j) {
        swap(j, j[1]);
      }
    }
  }
}

```

9. In C++, there is full multiple inheritance. In Java, a class can implement more than one interface but can only extend one class. For example, the following is not possible in Java:
```

class BaseOne {
public:
  void aa()=0;
  void ab() {
    // implemented
  }
};

class BaseTwo {
public:
  void xa()=0;
  void xb() {
    // implemented
  }
};

class Derived: public BaseOne, BaseTwo {
};

```

---

### Post by dwhitney67 on 2009-11-01
Your inexperience in C++ and Java shines through quite well with your post.  There are countless holes in your arguments.

I will respond to numbers 5 and 6, and let others have fun with your other items.

For item 5:
Objects in Java are allocated on the heap because that is the way the language was designed.  Java has automatic garbage-collection, thus once an object is allocated, one does not need to dispose of it as in C++.

If in C++, you attempt to construct a 1GB object on the stack, you may be SOL, regardless of how much system memory you have.  In such case you would allocate the object on the heap.  How does this differ from Java?



For item 6:
In C++, you would need the equivalent of a "clone" method to copy an object; it is called a copy-constructor.  For simple objects, one does not necessarily need to implement this type of constructor, but when the objects become more complex, it is essential to have (or at least defined as private if you wish to prevent cloning).

When passing an object to a function (in C++), never pass it by value.  Always pass it by reference.  If you want to provide the callee a warm-fuzzy-feelin' that the object will not be modified by the function, then preface the parameter declaration with the 'const' qualifier.

---

### Post by MadCow108 on 2009-11-01
I do not quite see the point of this post besides trying to start a flamewar. Both languages have their benefits and drawbacks and should be used where appropriate.
but I would like to comment on 2 points:
> **miklcct said:**
> 1. In C++, everything is an object. Compare the following code segment (Foo is a class):

C++
```

int a;
char b;
Foo *c;

```

Java
```

int a;
char b;
Foo c;

```

so far I know java has objects for primitive types they just have non-abbreviated uppercase names (e.g. Integer).

> 
2. There are references in C++ but not in Java. For example, the following C++ code is not possible in Java:

```

void swap(int &a,int &b) {
  int c=a;
  a=b;
  b=c;
}

```


I consider this a disadvantage of C++, there are not rvalue references
So the swap is not very efficient as it needs to create a temporary
(this is fixed in C++0x where rvalue references exist)

---

### Post by Reiger on 2009-11-01
1) really ought to be rewritten to: in C++ there is but one type and it is the byte array. Everything else is void. Cast away. :p

---

### Post by issih on 2009-11-01
1. In C++, everything is an object. Compare the following code segment (Foo is a class):

Cobblers - not everything in c++ is an object, and the definition of an object is NOT that you can make a pointer to it. An int in c++ is no more an object than in java. 

2. There are references in C++ but not in Java. For example, the following C++ code is not possible in Java:

Wrong again - all objects are passed by value in java, primitives are passed by value, but if you wish to pass them by reference you can box them into an object such as the Integer class. - Frankly you don't understand primitives and objects properly

3. C++ has pointer arithmetic but not in Java. For example, the following C++ code segment is not possible in Java:

```

int *p=new int[10];
int *q=p + 3;

```

indeed it doesn't have pointer arithmetic, but that does not mean  there is one single thing I can think of that c++ could do that java couldn't

4. In Java, there are classes and interfaces. The C++ equivalent of interfaces is abstract classes. The following C++ code is not possible in Java:

100% wrong.. java does have abstract classes and they work exactly as in c++, interfaces are a way of doing a kludged but safe form of multiple inheritance.

5. In C++, you are free to allocate objects in the program image, in the heap or on the stack. In Java, you can only allocate objects in the heap and primitives and pointers on the stack. The following C++ code is not possible in Java. (Foo is a class)

Java manages the memory for you, and collects up your garbage...it is vastly simpler to code for because of this - how is this a plus for c++? It does mean certain patterns are easier to code in c++, but as a general rule, java's techniques are what nearly all modern languages have adopted, and there is a reason for that.

6. In C++, object are values. In Java, object are not values. Therefore, in combination of the fact that Java has no references, you cannot pass an object into a function or return an object, only their pointers can be passed around. In Java, you must also manually write a clone function to copy an object but in C++, a simple assignment copies an object. The following C++ code is not possible in Java.

Having read this twice - I see you mean that you can't pass objects by value in java - true, and not an issue, passing objects by value is generally a bad thing, and if you want a copy, just clone it.


7. In Java, objects cannot be made read-only (although pointer that points to the object can). See the above code for example.

Not 100% sure about that, but assuming you mean what I think you do, the final operator pins a method or field so sub classes can't override it, if you mean const pointers and the like, well I admit I don't actually know, I haven't used java extensively for a few years.

8. In Java, there is no operator overloading. Therefore, it is impossible to write generics that applies to both primitives and objects. Here is a bubble sort algorithm written in C++, which is not possible in Java:

There is no operator overloading, but regardless of that, java has generics, and the general rule is that in java the operator you want to overload becomes a method - e.g. the ".equals" method


You are quite allowed to prefer c++, no problem from me whatsoever, but I'm afraid that nearly every single thing you mention in this list of reasons is entirely bogus.

I suggest you go look at java again, and actually spend enough time to learn how to use it.

Sorry to be somewhat confrontational

---

### Post by miklcct on 2009-11-01
> **MadCow108 said:**
> I consider this a disadvantage of C++, there are not rvalue references
So the swap is not very efficient as it needs to create a temporary
(this is fixed in C++0x where rvalue references exist)
How can I swap 2 l-values in C++0x without using a temporary?

---

### Post by MadCow108 on 2009-11-01
by telling the object to use the data of the other objects and vice versa.
This is used in the vector member function specialization swap where it swaps the pointer to the buffer instead of the buffer.
but not every object has a pointer to all its data which it can swap, this is where rvalue references come in.
Internally it will probably create some kind of temporary but of a primitive and not a complex type.

implementation may look like this (probably not exactly like this):
```

template<typename T> 
void swap(T& a, T& b)
{
	T && tmp = rval(a); // rvalue bind no deep copy
	a = rval(b);
	b = rval(tmp);
}

```
rvalues will be indicated by && (hurray even more syntax to learn :( )

(it also possible to swap primitive types without temporaries by arithmetics, but then you'll have to watch out for overflows)

---

### Post by CptPicard on 2009-11-01
A couple of points I feel compelled to comment on...

The issue of pointers and pointer arithmetic (and by extension, references) pops up every now and then as a "plus" of C and C++. They are meaningful within the context of a language that specifically needs to model the computer's memory. On the other hand, they are semantically pretty much equivalent to either an array index or a more abstract "indirect reference". So when it comes to actually modeling some programming problem, a genuine pointer is rarely (if ever) actually needed.

The swap example is interesting in the sense that it can be questioned how much some external code should be altering the meaning of assigned variables in some scope ("side-effects"). It's one of the few points I'm often willing to grant in the C++ discussion -- it can be nice to be able to pass "the exact same object" to some function -- but on the other hand, after a call to "swap" your x and you have, behind the scenes, actually become exchanged... how much of that do you like in your code? :)

Operator overloading is just rather trivial syntactic sugar, and thus quite unnecessary. At worst, when the operator does not have very natural semantics for the objects in question (like, '+' for addition or concatenation), using their overloading can result obscure, tricky code.

---

### Post by shadylookin on 2009-11-01
> **miklcct said:**
> 1. In C++, everything is an object. Compare the following code segment (Foo is a class):

C++
```

int a;
char b;
Foo *c;

```

Java
```

int a;
char b;
Foo c;

```

In the C++ example, a, b, c are objects but, in Java, they are not objects. Therefore, in Java, you cannot make pointers point to a, b and c.


The definition of object is not that you can pass it by reference.

> 
2. There are references in C++ but not in Java. For example, the following C++ code is not possible in Java:

```

void swap(int &a,int &b) {
  int c=a;
  a=b;
  b=c;
}

```


You could just make variables public or use getters and setters

> 
3. C++ has pointer arithmetic but not in Java. For example, the following C++ code segment is not possible in Java:

```

int *p=new int[10];
int *q=p + 3;

```



You could use arrays and just remember the index. As for 4 java does have abstract classes.

> 
5. In C++, you are free to allocate objects in the program image, in the heap or on the stack. In Java, you can only allocate objects in the heap and primitives and pointers on the stack. The following C++ code is not possible in Java. (Foo is a class)

```

class Blah {
public:
  void method() {
    Foo a; // a is allocated on the stack and is destructed automatically when a goes out of scope.
  }
};

```


All objects in java are destructed automatically anyway so there's no benefit to adding them on the stack.

> 
6. In C++, object are values. In Java, object are not values. Therefore, in combination of the fact that Java has no references, you cannot pass an object into a function or return an object, only their pointers can be passed around. In Java, you must also manually write a clone function to copy an object but in C++, a simple assignment copies an object. The following C++ code is not possible in Java.
```

class Foo {
};

void func(Foo x) {
}

int main() {
  const Foo x;
}

```

[quote]

All objects have a clone() method in java


[quote]
9. In C++, there is full multiple inheritance. In Java, a class can implement more than one interface but can only extend one class. For example, the following is not possible in Java:
```

class BaseOne {
public:
  void aa()=0;
  void ab() {
    // implemented
  }
};

class BaseTwo {
public:
  void xa()=0;
  void xb() {
    // implemented
  }
};

class Derived: public BaseOne, BaseTwo {
};

```

It's really just a different way of doing things. I don't really see how someone could think one is superior to another.

---

### Post by 0cton on 2009-11-01
This thread was fail from the start <.<

---

### Post by Sinkingships7 on 2009-11-01
This has got to be the biggest troll post I've seen in a long time...

---

