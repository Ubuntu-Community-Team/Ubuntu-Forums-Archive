---
title: "Creating an Array based on class object C++"
date: 2007-07-22
forum: Programming Talk
---

### Post by computergirl on 2007-07-22
Hi - 

 Im taking a class in C++ (normally Visual basic ) and Im wondering how I can make an Array based on 10 objects from a class.  I understand arrays, I understand Classes, this SYNTAX between the two languages is messing me up!

Also - What kind of compiler should I use for C++? Is there any on Ubuntu with a debugger? I dont like using Visual Studio 2005 in C++, on my "other OS" (dual booted).

Thank you in advance,

---

### Post by slavik on 2007-07-22
sudo apt-get build-essential

that will install (among many things) g++ (the gnu C++ compiler)
for debugger, you want gdb and ddd (ddd is a GUI front end to gdb  and I like it).

also, please post what you think a correct piece of code should (this way we can correct any mistakes you may have instead of teaching you stuff you already know).

---

### Post by djhworld on 2007-07-22
From your post I can only presume you're looking for "Vectors" 

Vectors work a little different to arrays, but you can create collections of objects easily

Look it up, C++ Vectors.

---

### Post by aks44 on 2007-07-22
> **djhworld said:**
> Look it up, C++ Vectors.

An example here: [http://ubuntuforums.org/showthread.php?t=506402#post3061963](http://ubuntuforums.org/showthread.php?t=506402#post3061963)

---

### Post by computergirl on 2007-07-22
I got it...It clicked!
This syntax thing is killing me! I noticed in C++ you do a lot of Looping to get results.
Im still a little confused about some of the stuff, but Im almost done with the class!

Thanks again!

---

### Post by Wybiral on 2007-07-22
Does it have to be a dynamically sized array? If so, then use a vector as the others have suggested, but if you can get away with using a stationary sized array, then just use the normal array syntax...

```

#include <iostream>

using namespace std;

class object
{
    private:

    string data;

    public:

    object()
    {
        data = "[None]";
    }

    ~object()
    {
        cout << data << endl;
    }

    void set_msg(string s)
    {
        data = s;
    }
};

int main()
{
    object x[10];

    x[3].set_msg("Hello");

    return 0;
}

```

Only use vectors when you need them to change in size, otherwise use compile-time sized arrays.

---

### Post by hod139 on 2007-07-22
> **Wybiral said:**
> Only use vectors when you need them to change in size, otherwise use compile-time sized arrays.
Only used vectors when you need then to change in size **and** you need random access.  If you need dynamic size but not random access use a linked list.

As for using a C-style fixed size array instead of a vector if you know the size; I personally would not suggest that.  I would suggest you still use a vector, but reserve the memory needed.  The less memory management I have to do the better, and the overhead of using a vector versus a C-style array is minimal.

---

### Post by Wybiral on 2007-07-22
> **hod139 said:**
> Only used vectors when you need then to change in size **and** you need random access.  If you need dynamic size but not random access use a linked list.

As for using a C-style fixed size array instead of a vector if you know the size; I personally would not suggest that.  I would suggest you still use a vector, but reserve the memory needed.  The less memory management I have to do the better, and the overhead of using a vector versus a C-style array is minimal.

But you don't have to manage any memory when you use fixed-size arrays. As long as you aren't dynamically allocating anything, arrays are perfectly OK. It's no harder to use, in fact just as easy... And you get the extra benefit of having the lack of overhead. I don't see a logical reason not to use C++'s arrays over vectors for non-dynamic memory.

But I also agree that you should make use of C++'s stack and queue when the situation demands it.

But seriously, if the data is a constant size, use an actual array, not an ADT... Anything else would just be wasteful.

---

### Post by hod139 on 2007-07-22
> **Wybiral said:**
> But you don't have to manage any memory when you use fixed-size arrays. As long as you aren't dynamically allocating anything, arrays are perfectly OK.  It's no harder to use, in fact just as easy... And you get the extra benefit of having the lack of overhead. I don't see a logical reason not to use C++'s arrays over vectors for non-dynamic memory.


Many fixed size arrays are not allocated on the stack, they will be allocated on the heap.   This is prone to programmer error and leaking memory.

Even fixed size arrays allocated on the stack can be harder to use.  For one example, passing a C-style array by reference with const correctness to a function is not as obvious to a new programmer as passing a std::vector. Also, the C-style array has no notion of size, the programmer has to continually pass that value around, and that is another possible error.
**C-Style**
```

template<typename T>
void myFunction(const T* const &c_array, const unsigned int size){ // pass by const reference
  // do something
}

int main(){
  int intArray[10];
  myFunction(&intArray, 10); // prone to error, could pass the wrong size
  return 0;
}

```**C++ vector**
```

template<typename T>
void myFunction(const std::vector<T> &vector){ // no need to pass size
  // do something
}

int main(){
  std::vector<int> intVector(10);
  myFunction(intVector);

  return 0;
}

```As you stated, there will be overhead, but it is negligible.


> 
But seriously, if the data is a constant size, use an actual array, not an ADT... Anything else would just be wasteful.I still suggest using a vector with a reserved size over a C-style array, because it removes the burden of memory management and cleans up the syntax. In the end I think it comes down to preference.

---

