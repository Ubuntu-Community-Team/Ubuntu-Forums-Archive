---
title: "c++ efficiency subject"
date: 2018-02-10
forum: Programming Talk
---

### Post by chuchi on 2018-02-10
Hi there! 


This is a subject related to copy constructors and efficiency in C++. The following code snippet shows three functions: 'example1', 'example2' and 'example3'. I have been discussing with a workmate which one is the most efficient :


```



#include <iostream>
#include <string>


//just an example class
class MyClass
{
public:
    std::string toString()
    {
        return "just an example";
    }
};


static MyClass myObj;




bool example1()
{
    std::string str = myObj.toString();//executing copy constructor of std::string
    
    //... some code
    std::cout << str << std::endl;
    
    //.. some other code
    std::cout << str << std::endl;
    
    return true;
}


bool example2()
{
    const std::string& str = myObj.toString();//avoid copy constructor of std::string, but more verbose.
    
    //... some code
    std::cout << str << std::endl;
    
    //.. some other code
    std::cout << str << std::endl;
    
    return true;
}


bool example3()
{
    //avoid copy constructor of std::string, but we get two call stacks .
    
    //... some code
    std::cout << myObj.toString() << std::endl;
    
    //.. some other code
    std::cout << myObj.toString() << std::endl;
    
    return true;
}




int main()
{
    for (size_t i = 0; i < 1000000; i++)
    {
        //example1();
        example2();
        //example3();
    }
}





```


In my opinion, the less efficient one is 'example1' because it implies the execution of the copy constructor which, in turn, implies a system call to allocate memory and another call to free such memory. But my workmate says 'example1' is the most efficient one, because the compiler will perform an optimization to avoid the copy constructor.


What is your opinion about that?


My opinion is that efficiency issues should not be left to the compiler, they should always be fixed in the c++ code. The code is aimed to be run on all platforms (Windows, Linux and Mac) and different compilers may behave in a different way. Even different versions of the same compiler may or may not perform optimizations.




I would choose 'example2' or even 'example3' because a call stack will always be faster than a system call to allocate memory. 


Here I used std::string as an example, but it can be with any user defined complex type.


Thanks a lot!

---

### Post by TheFu on 2018-02-10
Why not use a profiler and KNOW the answer?

Also, might be good to do it with an array of the objects, say 1,000, to see the differences better.

---

### Post by chuchi on 2018-02-11
Hi TheFu, thanks for your answer.


I could use a profiler like 'valgrind' with the program compiled under gcc which has optimizations enabled. Then 'example1' would be the best choice.


However, my main point is that we cannot be sure that the compiler will apply optimizations. What if you are compiling your code with a version of Visual Studio with optimizations disabled?

---

### Post by TheFu on 2018-02-11
Include a makefile.
Can't help with VS - stopping using that around 2000 when they broke compatibility with makefiles.  There are profilers for VS, however.  

I used Purify for years on 5 different platforms. What we found was that optimizations were pretty standard across all platforms for the most part. Only HP-UX with PA-Risc was a little different and even that wasn't much.

You can't save every foot from the gun pointed at it by the owner. In the README, tell them you did profiling using g++ and include a makefile.  It isn't like -O2 shouldn't be standard for production code.

IMHO.

---

### Post by dwhitney67 on 2018-02-15
The copy-constructor is not called in example 1, much less in any of the examples.

In fact, only the std::string constructor that accepts a const char* is ever called when the toString() is invoked.

Here's a test program that verifies such:
```

#include <iostream>
#include <string>

class String
{
public:
    String() : str() { std::cout << "no-arg constructor" << std::endl; }

    String(const std::string& s) : str(s) { std::cout << "string constructor" << std::endl; }

    String(const char* s) : str(s) { std::cout << "const char* constructor" << std::endl; }

    String(const String& s) : str(s.str) { std::cout << "copy constructor" << std::endl; }

    String& operator=(const String& other)
    {
        std::cout << "assignment operator" << std::endl;
        if (&other != this) {
            str = other.str;
        }

        return *this;
    }

    std::string str;
};

class MyClass
{
public:
    String toString() const
    {
        return "just an example";
    }
};

static MyClass myObj;

int main()
{
    // Example 1
    String s1 = myObj.toString();

    // Example 2
    const String& s2 = myObj.toString();

    // Example 3
    std::cout << myObj.toString().str << std::endl;
}

```

The output will appear as:
```

const char* constructor                                                                             
const char* constructor                                                                             
const char* constructor                                                                             
just an example

```

---

