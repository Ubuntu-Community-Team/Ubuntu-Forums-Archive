---
title: "Using overloaded operator=  with copy constructor &amp; std::swap function crashes (C++)"
date: 2019-04-15
forum: Programming Talk
---

### Post by s3a on 2019-04-15
Hello, everyone. :)

I just wanted to ask: Why is the following code crashing, and how do I make it not crash?:
```
#include <iostream>
#include <algorithm>
#include <utility>

class MyClass {
    
    public:
        
        int* myInt = new int(3);
        
        MyClass() {
            std::cout << "MyClass!" << std::endl;
        }
        
        MyClass(const MyClass& otherObj) { // copy constructor has to take other MyClass object as a reference, but it does not have to take it as a const variable
            *(this->myInt) = *(otherObj.myInt);
        }
        
        MyClass& operator=(MyClass otherObj) {
            
            std::swap(*this,otherObj);return *this; // Why isn't this working?
        }
};


int main() {
    MyClass m1;
    MyClass m2 = m1;
    m2 = m1;
    
    std::cout << *(m1.myInt) << std::endl;
    std::cout << *(m2.myInt) << std::endl;
    *(m1.myInt) = 6;
    std::cout << *(m1.myInt) << std::endl;
    std::cout << *(m2.myInt) << std::endl;
    return 0;
}
```

Any input would be GREATLY appreciated!

P.S.
I'm trying to do what is said [here]("https://stackoverflow.com/questions/3279543/what-is-the-copy-and-swap-idiom/3279550#3279550").

---

### Post by norobro on 2019-04-16
[FONT=arial][SIZE=2]From your link:[/SIZE]> We might be tempted to use std::swap instead of providing our own, but this would be impossible; std::swap uses the copy-constructor and copy-assignment operator within its implementation, and we'd ultimately be trying to define the assignment operator in terms of itself!
[SIZE=2]Put a cout statement in your operator=() and you'll see that your code is stuck in an infinite loop.  [/SIZE]

[SIZE=2]For this simple class you could use the same statement used in  your copy ctor in operator=(): [/SIZE][/FONT]```
MyClass& operator=(const MyClass& otherObj) {
    *myInt = *(otherObj.myInt); 
    return *this;
}
```
[FONT=arial]
[SIZE=2]For more complex classes, to avoid duplicate code, it is useful to define a function that swaps each member of the two objects and call it from the copy ctor and operator=().

HTH[/SIZE][/FONT]

---

