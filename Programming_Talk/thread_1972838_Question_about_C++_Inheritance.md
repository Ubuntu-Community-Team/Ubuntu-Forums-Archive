---
title: "Question about C++ Inheritance"
date: 2012-05-03
forum: Programming Talk
---

### Post by Kentucky88 on 2012-05-03
[PHP]
#include <iostream>
#include <map>

using namespace std;

class base {
protected:
    int number;

public:
    base() { number = 3; }
    virtual void printNum() { cout << "Not the one class" << endl; }
};

class one : public base { 
public:
    one() { number = 1; }
    void printNum() { cout << number << endl; }
};

int main()
{
    base bse;
    one uno;

    bse = uno;
    one* oneptr = dynamic_cast<one*>(&uno);
    one* baseptr = dynamic_cast<one*>(&bse);

    if(oneptr != NULL) cout << "Test 1 worked" << endl;
    if(baseptr != NULL) cout << "Test 2 worked" << endl;
    oneptr->printNum();
    baseptr->printNum();
    return 1;
}
[/PHP]

Output:

[PHP]
Scratch.exe
Test 1 worked
1
[/PHP]

Can someone explain why "Test 2 worked" was not printed in the output above?  I know that if I had the instantiated the 'uno' object on the heap and was working with pointers instead of objects on the stack, the second dynamic cast would have worked.  However, when I copy the uno object into bse, is the upcast necessitated by the need to make the superclass (one) fit in the space allocated for the base class (base)?  If so, that would make sense (even though in this case, both objects should consume the same amount of space since the subclass does not introduce any new member variables).  I still expected to see "Not the one class" print on the last line.  Does anyone know why it did not print?

---

### Post by dwhitney67 on 2012-05-04
I'm not 100% sure what is going on... it's too late for me to whip out the debugger... but I see one issue.

In this statement, you are calling the copy-constructor for base (which you have not defined):
```

bse = uno;

```

Then here, you are attempting to cast a base object into a one object, when in fact the base object is NOT a one object; it is a base object:
```

one* baseptr = dynamic_cast<one*>(&bse);

```
Thus baseptr above will be NULL; not a valid pointer to an object as you were expecting.

---

### Post by 11jmb on 2012-05-04
if you compile this -Wall you should a warning about the second cast.

I'm curious how this program didn't segfault, actually.

---

### Post by cgroza on 2012-05-04
> **11jmb said:**
> if you compile this -Wall you should a warning about the second cast.

I'm curious how this program didn't segfault, actually.
I guess the pointer was still valid in some way.

---

### Post by dwhitney67 on 2012-05-04
> **cgroza said:**
> I guess the pointer was still valid in some way.

A failed dynamic_cast will return NULL.  The OP probably didn't mention that the segfault occurred.  Also, he did not mention that g++ returned a warning similar to the following:
```

warning: dynamic_cast of ‘base bse’ to ‘class one*’ can never succeed [enabled by default]

```
IMO, this thread is done.

---

### Post by Kentucky88 on 2012-05-04
> **dwhitney67 said:**
> A failed dynamic_cast will return NULL.  The OP probably didn't mention that the segfault occurred.  Also, he did not mention that g++ returned a warning similar to the following:
```

warning: dynamic_cast of ‘base bse’ to ‘class one*’ can never succeed [enabled by default]

```IMO, this thread is done.

I compiled in Visual Studio and it did run without reporting a segfault.  

This thread is done, I'll mark it as solved.  The issue was that I was treating copying an object allocated on  the stack the same as copying the pointer of an object.   Is there no  default copy constructor in C++? I figured that by default, the member  variables of the base object would be copied over, essentially  downcasting the object into a base object.  If that's true, then there would be no segfault.

---

### Post by dwhitney67 on 2012-05-04
> **Kentucky88 said:**
> I compiled in Visual Studio and it did run without reporting a segfault.  

This thread is done, I'll mark it as solved.  The issue was that I was treating copying an object allocated on  the stack the same as copying the pointer of an object.   Is there no  default copy constructor in C++? I figured that by default, the member  variables of the base object would be copied over, essentially  downcasting the object into a base object.  If that's true, then there would be no segfault.

I'm not sure if I understand your question.  Every class is provided a default copy-constructor, unless the programmer declares one, but doesn't implement it.  For example:
```

class HasCopyConstructor
{
};

class HasNoCopyConstructor
{
private:
    // Copy-constructor declared, but will not be implemented.
    HasNoCopyConstructor(const HasNoCopyConstructor& other);
};

```

As for inheritance, a class derived from another is considered to have an "is-a" relationship with that base class; a base-class has NO relationship to a class that derives from it.

---

