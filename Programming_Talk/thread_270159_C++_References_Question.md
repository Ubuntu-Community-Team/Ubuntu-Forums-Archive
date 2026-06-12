---
title: "C++ References Question"
date: 2006-10-02
forum: Programming Talk
---

### Post by fatsheep on 2006-10-02
I'm having this compile error:

> test.cpp: In function ‘int main()’:
test.cpp:17: error: invalid conversion from ‘int*’ to ‘int’


With this source code (line 17 is bolded).




```
#include <iostream>
using namespace std;

int main ()
{
	//declared variables
	
	int Andy;
	int Fred;
	int Ted;
	int &rAndy = Andy; 
	
	//little reference test...
	
	Andy = 25;	//assign value of 25 to int Andy
	Fred = Andy;	//assign value of Andy to Fred
	**Ted = &rAndy;**//assign value of Andy to Ted through reference
	
	//print values
	
	cout << "Andy: " << Andy << endl;
	cout << "Fred: " << Fred << endl;
	cout << "Ted: " << Ted << endl;
}
```

I've commented my code so you can see what I was trying to do.  Any help would be appreciated. :)

---

### Post by fatsheep on 2006-10-02
I think I found a solution...  The bolded text should be without the "&":

> Ted = rAndy;

Correct me if I'm wrong but it looks like it's working fine.

---

### Post by po0f on 2006-10-02
fatsheep,

You're thinking about references as if they were pointers.  Don't do that.  References are basically a copy of an object (an integer in this case).  After a reference is declared, you don't need to do anything to "dereference" it like you have to do with pointers:
```
#include <iostream>
using namespace std;

int main() {
    int a = 25;
    int b;
    int &c = a;

    b = c;

    cout << "Value of b is " << b << endl;

    return 0;
}
```

References are what's called "syntactic sugar".  They make the code easier to follow.  Also, they get rid of some of the nastiness of pointers since they cease to exist after they go out of scope.  Here's an example:
```
#include <iostream>
using namespace std;

void my_func(int& x) {
    x = 25;
}

int main() {
    int a = 17;

    cout << "Value of a before my_func(): " << a << endl;

    myfunc(a);

    cout << "Value of a after my_func(): " << a << endl;

    return 0;
}
```

Notice in my_func() that you don't have to do anything to "x" inside the function.  A reference is created, pointing to "a" (by calling the function with "a" as an argument), but inside my_func(), it looks like "x".  When my_func() returns, "a" changed via the "x" reference inside the function.

References are good to use when you want to avoid the use of pointers, but don't want to pass-by-value (especially when you have big objects).

One more example:
```
#include <iostream>
using namespace std;

void my_func(int& x) {
    x += 5;
}

int main() {
    int a = 1;
    int b = 5;

    cout << "Value of a before my_func(): " << a << endl;
    cout << "Value of b before my_func(): " << b << endl;

    my_func(a);
    my_func(b);

    cout << "Value of a after my_func(): " << a << endl;
    cout << "Value of b after my_func(): " << b << endl;

    return 0;
}
```

Inside my_func(), "a" and "b" appear to the function as "x", but only for the duration of the function call.  And since the reference is directly referring (clever!) to the variable it points to, the outside values of each are changed.

Your small example was kind of confusing, because you don't see the benefit of references when all the code fits on one page.  I can see where you would get confused with them.

Another place references are useful is when you start doing objects that inherit from other objects.  You can have a generic function do the same thing to objects of different types, but that have the same base class.  Ok, I lied, one more example:
```
#include <iostream>
using namespace std;

class Animal {
public:
    virtual void speak() = 0;
};

class Dog : public Animal {
public:
    void speak() { cout << "Woof!" << endl; }
};

class Cat : public Animal {
public:
    void speak() { cout << "Meow!" << endl; }
};

void say_something(Animal& a) {
    a.speak();
}

int main() {
    Dog dog;
    Cat cat;

    say_something(dog);
    say_something(cat);

    return 0;
}
```

Notice how say_something() is declared.  A couple things are going on here actually.  The classes Dog and Cat inherit from Animal, which has one pure virtual function (if you didn't know, it means that classes derived from Animal have to override speak()).  say_something() is declared as taking a reference to an Animal, but since Dog and Cat both derive from it, they can be used as arguments to that function as well.  Inside say_something(), Dog and Cat's speak() functions are called as if they were Animal objects, which, in a way, they are.

(I actually don't know if that last example will work, just kinda pulled it from the top of my head.  ;)  If it doesn't work but you really want to see it, message back and I'll fix it.)

Hopefully you can see from that last example how references, used with other aspects of C++, would make coding easier for you.  :)

---

### Post by fatsheep on 2006-10-03
Thanks that was very helpful. :D

---

### Post by rplantz on 2006-10-03
> **po0f said:**
> fatsheep,

You're thinking about references as if they were pointers.  Don't do that.  References are basically a copy of an object (an integer in this case).

I don't think they are really a copy of an object. Otherwise, pass by reference would not change the original object. When I look at the assembly language generated by g++, the reference is implemented via pointers.

> 
References are what's called "syntactic sugar".  They make the code easier to follow.  Also, they get rid of some of the nastiness of pointers since they cease to exist after they go out of scope.  Here's an example:
```
#include <iostream>
using namespace std;

void my_func(int& x) {
    x = 25;
}

int main() {
    int a = 17;

    cout << "Value of a before my_func(): " << a << endl;

    myfunc(a);

    cout << "Value of a after my_func(): " << a << endl;

    return 0;
}
```

As with most things, "easier" depends on what you're used to. As an experienced C programmer I found the call to my_func() confusing since it changes the value in a. Internally, the call passes a pointer to a, but that does not show in the calling function. I have to read the called function in order to see that (which, of course, I really should do).
> 
Notice in my_func() that you don't have to do anything to "x" inside the function.  A reference is created, pointing to "a" (by calling the function with "a" as an argument), but inside my_func(), it looks like "x".  When my_func() returns, "a" changed via the "x" reference inside the function.

Again, the fact that you don't need to dereference "x" is confusing to an experienced C programmer.
> 
References are good to use when you want to avoid the use of pointers, but don't want to pass-by-value (especially when you have big objects).

This is confusing. Pass-by-value is used when you do NOT want to change the value of the original object. In other words, for inputs to the function.

Passing by pointer or by reference MUST be used if the function is going to change the value of the object. They CAN be used if the function is not going to change it, especially for large (compound) objects. Then, of course, you should use the const modifier, etc.

Note that calling a member function implicitly passes the object by reference.

Coming from C, it took me a while to get used to references and to learn how to use them.

---

### Post by po0f on 2006-10-03
rplantz,

[quote=rplantz]I don't think they are really a copy of an object. Otherwise, pass by reference would not change the original object. When I look at the assembly language generated by g++, the reference is implemented via pointers.
[/quote]

I said *basically* a copy of an object.  The & operator takes the address of whatever variable it points to, which is of course a pointer.  The fact that this is hidden from the programmer is helpful or not, depending on where you are coming from.  I started learning C++ before C, so I kinda have a bias towards the way C++ does things.

I'll concede that my knowledge of C++ isn't authoritive, so please pardon any misconceptions I may have presented.

---

### Post by rplantz on 2006-10-03
> **po0f said:**
> rplantz,


I'll concede that my knowledge of C++ isn't authoritive, so please pardon any misconceptions I may have presented.

I hope that my remarks did not offend you, and that you took them in the spirit of all of us helping each other to learn more.

C++ is not one of my strengths. But I know a fair amount about how it's implemented because I am strong in assembly language.

On the topic of learning more, I was a computer science professor for 21 years. I taught assembly language almost every semester. And before going into teaching I wrote a lot of assembly language working in industry. Even with my background, I learned something new every time I taught the class. Since most students come into the class with few pre-conceptions, many tend to ask "dumb" questions, which would cause me to think about things I had never thought about before. So I had to constantly learn new things, which I enjoy. Now that I'm retired, I have more time to learn new things. :)

---

### Post by po0f on 2006-10-03
rplantz,

No offense taken.  :)  I posted that mainly for the benefit of the OP, in case it raised some doubts and prompted more question asking.  Like you said, even when answering questions, I always learn something.

Oh yeah, and I'm jealous of your asm knowledge!  I am completely lacking in that respect.

---

