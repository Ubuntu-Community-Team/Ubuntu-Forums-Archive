---
title: "what does this function  mean in c++??"
date: 2009-07-17
forum: Programming Talk
---

### Post by abhilashm86 on 2009-07-17
here there is class port, which i need to use for GUI later, my doubt is what exactly following statement mean, that is after : symbol??
i know Port(....) is parameterzied constructor, what is after colon?? why do i require it??
Port(int _x, int _y, bool _avail=true) : x(_x), y(_y), avail(_avail) {
  Type=""; Connection=0;}

```

class Port
{
  public:
  int   x, y;
  bool  avail;
  QString Type;
  Node *Connection;
  Port() {}
  Port(int _x, int _y, bool _avail=true) : x(_x), y(_y), avail(_avail) {
  Type=""; Connection=0;}
};
```

---

### Post by typedef on 2009-07-17
That is in initialization list. It is used to initialize the members of the class at the time of construction. Using them is the preferred way of setting values in a constructor, especially for other object types. You can read more about initialization lists on this page: [http://www.cprogramming.com/tutorial/initialization-lists-c++.html](http://www.cprogramming.com/tutorial/initialization-lists-c++.html)

---

### Post by Habbit on 2009-07-17
The statements after the colon are called the class member initializers. The are effectively calls to the constructors of each member variable. If you don't insert an explicit initializer for some class variable, then C++ will call its default constructor if there is any, or error out if there is none.

So, would you say, what is the point with them when you can write "x = _x;" etcetera inside the constructor body? Well, for POD types this will not change the program meaning, though if you are using a primitive compiler, it might waste one or two CPU instructions per variable initialized in the constructor body as opposed to with initializers. This might not be the same for other classes: keep reading.

Notice that if you had a std::string variable, for example, and you "initialized" it in the constructor body, like "my_str = _some_param;", then _two_ methods have been called: the default "string()" constructor, then the "string& string::operator=(const string& other)" assignment operator. For even bigger classes, or classes whose constructors/assignment operators have side effects, this might be a problem. It is good practice to use the initializers instead of assigning to member variables in the constructor body.

PS: the initializer list is also where you can select which parent class constructors to call.

---

### Post by abhilashm86 on 2009-07-17
> **Habbit said:**
> The statements after the colon are called the class member initializers. The are effectively calls to the constructors of each member variable. If you don't insert an explicit initializer for some class variable, then C++ will call its default constructor if there is any, or error out if there is none.

So, would you say, what is the point with them when you can write "x = _x;" etcetera inside the constructor body? Well, for POD types this will not change the program meaning, though if you are using a primitive compiler, it might waste one or two CPU instructions per variable initialized in the constructor body as opposed to with initializers. This might not be the same for other classes: keep reading.

Notice that if you had a std::string variable, for example, and you "initialized" it in the constructor body, like "my_str = _some_param;", then _two_ methods have been called: the default "string()" constructor, then the "string& string::operator=(const string& other)" assignment operator. For even bigger classes, or classes whose constructors/assignment operators have side effects, this might be a problem. It is good practice to use the initializers instead of assigning to member variables in the constructor body.

PS: the initializer list is also where you can select which parent class constructors to call.

thanks a lot, i understood how it works:)

>  It is good practice to use the initializers instead of assigning to member variables in the constructor body.
yes its easy and readable form, when we initialize data memebers of class, also easy to manipulate data members, also code read ability is easy for not so great c++ coders like me!!

---

### Post by c0mput3r_n3rD on 2009-07-17
```

class Port
{
public:
  Port() 
  {}
  Port(int _x, int _y, bool _avail=true) : x(_x), y(_y), avail(_avail) 
  {
  Type=""; Connection=0;
  }
private:
  int   x, y;
  bool  avail;
  QString Type;
  Node *Connection;

};

```

I don't know if you wrote this or some else did, but the variables should be in a private section, because you don't want to users be able to directly access the information.   Instead make "getter" and "setter" functions that access this information so it's only manipulated the way the you (the programmer) wants it to be.

---

### Post by abhilashm86 on 2009-07-18
> **c0mput3r_n3rD said:**
> ```

class Port
{
public:
  Port() 
  {}
  Port(int _x, int _y, bool _avail=true) : x(_x), y(_y), avail(_avail) 
  {
  Type=""; Connection=0;
  }
private:
  int   x, y;
  bool  avail;
  QString Type;
  Node *Connection;

};

```

I don't know if you wrote this or some else did, but the variables should be in a private section, because you don't want to users be able to directly access the information.   Instead make "getter" and "setter" functions that access this information so it's only manipulated the way the you (the programmer) wants it to be.

oh yes i completely discared it, yes i should make it private, actually this code initially, had struct, i made it into class, yes i'll change those variables to private...........

---

