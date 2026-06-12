---
title: "Copied a C++ class but my version fails to compile"
date: 2009-08-15
forum: Packaging and Compiling Programs
---

### Post by trilobite on 2009-08-15
Hi all - 
 I've been playing around with this simple C++ class that creates a couple of simple functions and pushes them onto a vector. 
( I'm running g++ 4.4.1 on Ubuntu Jaunty ). 

This is the original code that I copied-

*** start of code *** 
#include <vector> 
#include <iostream> 

using namespace std ; 

class Movie
{
    typedef void (Movie::*MovieFunc)();
public:
    Movie()
    {
        f.push_back(&Movie::heHe);
        f.push_back(&Movie::haHa);
    }
    void show(int part) { (this->*f[part])(); }
private:
    void heHe() { cout << "He he" << endl; }
    void haHa() { cout << "Ha ha" << endl; }

    vector<MovieFunc> f;
};

//  Main function 
int main() 
{
    Movie m;
    m.show(0);
    m.show(1);
return 0 ; 
} 
*** end of code *** 

Ok, now that code above compiles and runs fine.

Now, in order to see if I could do a very similar class, I created the following code - 

*** start of code *** 
#include <vector> 
#include <iostream> 

using namespace std ; 

class Myclass 
{   
   typedef void (Myclass::*Myfunc)();
    
public:
    Myclass()
    {
        f.push_back(&Myclass::func1);
        f.push_back(&Myclass::func2);
    }
    
  void run(int part) { (this->*f[part])(); }
    
private:  
    void func1(int arg) 
    { 
       cout << (arg * arg) << "\n" ;  
    }       
        
    void func2(int arg) 
    { 
       cout << (arg * 3) << "\n" ; 
    }         
        
    vector<Myfunc> f;
};


int main()  
{ 

  Myclass a;
  a.run(0);
  a.run(1);

return 0; 
} 
 
*** end of code *** 

However, this code fails with the following error - 

g++ -Wall -o "templates3" "templates3.cpp" -I "/home/andy/boost-trunk/:/home/andy/file_parsers/"  (in directory: /home/andy/file_parsers)
templates3.cpp: In constructor ‘Myclass::Myclass()’:
Compilation failed.
templates3.cpp:29: error: no matching function for call to ‘std::vector<void (Myclass::*)(), std::allocator<void (Myclass::*)()> >::push_back(void (Myclass::*)(int))’
/usr/local/lib/gcc/i686-pc-linux-gnu/4.4.1/../../../../include/c++/4.4.1/bits/stl_vector.h:733: note: candidates are: void std::vector<_Tp, _Alloc>::push_back(const _Tp&) [with _Tp = void (Myclass::*)(), _Alloc = std::allocator<void (Myclass::*)()>]
templates3.cpp:30: error: no matching function for call to ‘std::vector<void (Myclass::*)(), std::allocator<void (Myclass::*)()> >::push_back(void (Myclass::*)(int))’
/usr/local/lib/gcc/i686-pc-linux-gnu/4.4.1/../../../../include/c++/4.4.1/bits/stl_vector.h:733: note: candidates are: void std::vector<_Tp, _Alloc>::push_back(const _Tp&) [with _Tp = void (Myclass::*)(), _Alloc = std::allocator<void (Myclass::*)()>]
*** End of error message *** 

 Seems very odd.  About all that I've changed is that I've created another couple of simple functions, yet the program fails. So, can anyone see how I can fix this?  

 Very many thanks in advance! Bye for now - 
- trilobite

---

### Post by Kazade on 2009-08-15
In the second version, your methods take integer params, your function pointer typedef doesn't match. Try:

typedef void (Myclass::*Myfunc)(int);

instead.

---

### Post by TrueTom on 2009-08-15
```

typedef void (Movie::*MovieFunc)();

void func1(int arg)
{
    cout << (arg * arg) << "\n" ;
} 

```

Where is the difference? :)

---

### Post by trilobite on 2009-08-15
> **Kazade said:**
> In the second version, your methods take integer params, your function pointer typedef doesn't match. Try:

typedef void (Myclass::*Myfunc)(int);

instead.

Ahhh.... Thanks *very much*, Kazade!  That's great - much appreciated! 
Bye for now - 
- trilobite

---

### Post by trilobite on 2009-08-15
> **TrueTom said:**
> ```

typedef void (Movie::*MovieFunc)();

void func1(int arg)
{
    cout << (arg * arg) << "\n" ;
} 

```

Where is the difference? :)
Good question, TrueTom! 
I think Kazade "hit the nail on the head" by adding the "int" after the typedef. Anyway, this has been a *very* helpful thread! It's good for me to become more familiar with typedefs (among many other things... :)  ). 

( Update ) - I've added the (int) after the typedef, ann that has indeed removed the above errors. The only error I get now is this one, for this statement -
 void run(int part) { (this->*f[part])(); }

templates3.cpp: In member function &#8216;void Myclass::run(int)&#8217;:
templates3.cpp:35: error: too few arguments to function 

So, just wondering how this can be fixed? Many thanks in advance - 
- trilobite

---

### Post by TrueTom on 2009-08-16
The error message is actually pretty clear: If the function expects an int parameter you have to provide one if you call the function.

---

### Post by trilobite on 2009-08-16
> **TrueTom said:**
> The error message is actually pretty clear: If the function expects an int parameter you have to provide one if you call the function.
Thanks, TrueTom! I've just had another go at this, and at last, I've made the code compile. 
I made the statement look like this - 
(this->*f[part])(part);   
 - and got success at last! 
At first, it didn't seem to "look right", having "part" twice, but there's no arguing when it works and gives the expected results. I apologise for my being a bit dense ;) . 
( Update ) - I've made the code even better by changing it to - 
void run(int part, int param) 
    {             
      (this->*f[part])(param);                
    }

- so you specify the index of the function, and the integer argument to the function. The calls now look like - 
Myclass a;
a.run(0, 3);
a.run(1, 7); 

Much better! I've learned *heaps* in the last day or so - many thanks again...
- trilobite

---

