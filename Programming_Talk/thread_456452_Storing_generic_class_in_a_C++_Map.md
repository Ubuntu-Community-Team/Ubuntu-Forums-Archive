---
title: "Storing generic class in a C++ Map"
date: 2007-05-27
forum: Programming Talk
---

### Post by bluedalmatian on 2007-05-27
Is it possible to store a genric C++ class in a map, such that the type of the gernic class isnt specified when you declare the map, but can be any type.

For example, if I have the following generic class:

template <class T> class MyClass
{
...
}
can i declare a Map to hold objects of this class regardless of their type like this:

map <string,MyClass<T>> myMap;           //this line wont compile

then add instance of MyClass to the map with varying types:

MyClass<int> one;
MyClass<string two;

myMap.insert(std::make_pair(key,one));
myMap..insert(std::make_pair(key,two));

Thanks in advance
Andrew

---

### Post by hod139 on 2007-05-27
I may be wrong, but I don't think it is possible to do what you want, since the compiler cannot determine the size of your class at compile time.  You could do:
```

std::map <std::string, MyClass<int> > myMap;

```
because now the compiler can determine the size of the class, but this is obviously not what you want.  I may be wrong, and if I am hopefully someone else will know how to do it. 

 What exactly is the problem you are trying to solve, there may be alternative ways?

---

### Post by bluedalmatian on 2007-05-27
> **hod139 said:**
> 
 What exactly is the problem you are trying to solve, there may be alternative ways?

I need to store any type in a map, ints, bools, strings, doubles etc. and have a string key associated with them like this:

KEY                 VALUE
"one"                30
"two"                476.566
"three"             "hello"

I think the most exotic type I'll need to store is a byte array.  string is the only object i'll need to store

---

### Post by bluedalmatian on 2007-05-27
What if I (somehow) declare the map as storing a pointer to MyClass and create instances of MyClass on the heap using new??

---

### Post by hod139 on 2007-05-27
All of the containers in the STL are homogeneous.  See the C++ FAQ for two ways to accomplish what you want:
[http://www.parashift.com/c++-faq-lite/containers.html#faq-34.4](http://www.parashift.com/c++-faq-lite/containers.html#faq-34.4)

---

### Post by bluedalmatian on 2007-05-28
Thanks for that. Thats along the lines that I was thinking, Ive done it by declaring the map to store a pointer to MyClass like this:

map <string,MyClass<class T>*> myMap;

on a related note. How do I create instnaces of generic classses using new.

The following line doesnt work:

MyClass<std::string> *value = new MyClass();

---

### Post by hod139 on 2007-05-28
```
MyClass<std::string> *value = new MyClass<std::string>();
```

---

### Post by bluedalmatian on 2007-05-28
If a class inherits from another it does so like this doesnt it:

class MyDerivedClass : public MyClass
{

...

}

so why am I getting an error saying:

./MyDerivedClass.h:13:error: expected class-name before ‘{’ token


(I dont really name classes like this, Ive just changed the names for simplicity ;)

---

### Post by thumper on 2007-05-28
Have a look at boost::any or boost::variant to store different types in a map [www.boost.org](www.boost.org).

Also this line doesn't compile:
```
typedef std::map<foo, bar<another>> baz;
```
But this one does...
```
typedef std::map<foo, bar<another> > baz;
```
This is a hang over from C operator precedence.  The closing template > are thought of by the compiler as a shift right operator.  I understand that this is being fixed in C++09.

---

### Post by Mirrorball on 2007-05-29
> **bluedalmatian said:**
> class MyDerivedClass : public MyClass
{

...

}**;**

Notice the semicolon.

---

### Post by bluedalmatian on 2007-05-29
Thanks for all the help.  Much appreciated. I think the missing semicolon was just when I copied & pasted the code. I suspect the real casue of the problem was something to do with namespaces but im not sure what. i solved it by putting the parent and its subclasses in the same files which in this case is actually neater and easier than having them separate. although normally it wouldnt be ideal obviously.

ah well, im going in a c++ course next week :)

---

