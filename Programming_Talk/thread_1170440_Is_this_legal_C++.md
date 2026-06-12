---
title: "Is this legal C++?"
date: 2009-05-26
forum: Programming Talk
---

### Post by Habbit on 2009-05-26
Hello there everyone. I'd like to know whether using data from a temporary object which is constructed in a function call as an argument to that function is valid C++. In other words, I have a function that returns a heap-allocated char* that I should delete[], and I'd like to do the trick in one line, but I don't know if my way is actually legal or it's just that I've been lucky until now. An example: (consider auto_array a class akin to auto_ptr, just invoking delete[] on destruction)
```
cout << auto_array<char>(func_returning_heapalloced_str()).get() << endl;

// With auto_array being (skeletal implementation)
template<typename T> class auto_array {
    T* res;
public:
    explicit auto_array(T* ptr) : res(ptr) {}
    ~auto_array() { if (res) delete[] res); }
    T* get() { return res; }
};
```
Thus, when is the temporary auto_array object destroyed? If it is killed the moment after its get() function is evaluated - thus before operator<<(ostream&, char*) is called - I could get a very nasty surprise on another compiler or platform. So long, both g++ 4.x and MSVC++ 9.0 seem to destroy the temporary object only after the whole statement, but I want to be on safe ground because the code in question might leave my hands soon.

---

### Post by hod139 on 2009-05-26
I believe that what you are doing is portable.  I think the scope of the tempory object is defined by the output stream's "<<" operator.  If you are uncertain, why not introduce a temporary?

```

auto_array<char> temp(func_returning_heapalloced_str());
cout << temp.get() << endl;

```

---

### Post by Habbit on 2009-05-26
If by "introduce a temporary" you mean what your code does, that is, introduce a local, non-temporary variable, I'd rather have it in one line as in my snippet. The code that receives the data is more like this:```
myobj.setfoo(i) = auto_array<char>(xmlstr::transcode(xmldata)).get()
```
Where the return type of setfoo is std::string&, so the function actually using the temporary data would be "string::operator=(const char*)". Thus, I'd like to know which one of those two execution paths, if any, is mandated by the standard. Is is this one?
[LIST=1]
[*]myobj.setfoo(i) returns a string&
[*]xmlstr::transcode executes "new char[]" and returns a char*
[*]auto_array(T*) initializes the temporary
[*]T* auto_array::get() returns the original pointer
[*]string::operator=(const char*) is executed, COPYING the data in the temporary buffer
[*]The statement in which the temporary was used ends. ~auto_array() is executed, delete[]'ing the temporary buffer
[*]All is fine
[/LIST]
Or this one?
[LIST=1]
[*]myobj.setfoo(i) returns a string&
[*]xmlstr::transcode executes "new char[]" and returns a char*
[*]auto_array(T*) initializes the temporary
[*]T* auto_array::get() returns the original pointer
[*]The narrow usage scope of the temporary (the evaluation of a function argument) ends. ~auto_array() is executed, delete[]'ing the temporary buffer
[*]string::operator=(const char*) is executed, trying to copy data from a delete[]'d buffer
[*]BOOM!
[/LIST]

---

### Post by hod139 on 2009-05-26
I believe your first execution path is the one that gets executed.  But again, why not create a temporary local-scope variable to remove all ambiguity?  

```

auto_array<char> temp(xmlstr::transcode(xmldata));
myobj.setfoo(i) = temp.get();
// temp cleaned up when function exits

```


This way there is no possible confusion, and there will not be any performance differences.

---

### Post by ibuclaw on 2009-05-26
It is my understanding that, with ISO C/C++ at least, that things such as order of execution is undefined, and generally left up to the compiler.

It is also to my understanding that GCC (and possibly many other compilers) choose to have left-to-right evaluation. So you may be in the green on this one...

Regards
Iain

---

### Post by Habbit on 2009-05-26
Well, I finally found out the Standard... oh joy! According to section 12.2 "Temporary objects",

*When an implementation introduces a temporary object of a class that has a non-trivial constructor (12.1, 12.8), it shall ensure that a constructor is called for the temporary object. Similarly, the destructor shall be called for a temporary with a non-trivial destructor (12.4). **Temporary objects are destroyed as the last step in evaluating the full-expression (1.9) that (lexically) contains the point where they were created.** This is true even if that evaluation ends in throwing an exception.*

AKA, I was not writing a crapload of code and my temporary auto_array will be destroyed after operator= copies its data out of delete[]s ground zero. Phew... Well, it still is a crap since it performs dozens of new[]s and delete[]s within loops, but that would have been so even with the temporary string approach because strings perform copies, not moves. Thank you everybody!

---

