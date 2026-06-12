---
title: "Making a vector of func. pointers accept funcs of all types"
date: 2009-08-18
forum: Packaging and Compiling Programs
---

### Post by trilobite on 2009-08-18
Hi all - 

 This is a follow-on to this post of mine - 
[http://ubuntuforums.org/showthread.php?t=1240824](http://ubuntuforums.org/showthread.php?t=1240824)

 I've got the code to compile, so that's great!
Here's the code as it is now, for easy reference- 
*** start of code *** 
#include <vector> 
#include <string> 
#include <iostream> 

using namespace std ; 

int power(int base, int exp) 
{
    int i, result = 1;
    for (i = 0; i < exp; i++)
        result *= base;
    return result;
 }


class Myclass 
{   
    typedef void (Myclass::*Myfunc)(int);
    
public:
    Myclass()
    {
        //  The functions to push onto the vector 
        f.push_back(&Myclass::func1);
        f.push_back(&Myclass::func2);        
    }
    
    //  A method for the class. This takes two ints - the index of 
    //  the function to run, and the argument to the function. It then 
    //  executes the function in that index.  
    void run(int part, int param) 
    {             
      (this->*f[part])(param);                
    } 
            
private:
    //  The functions used are defined here 
    void func1(int arg) 
    { 
       int myresult = power(arg, 4) + (5 * arg) - 8 ; 
          
       cout << myresult << "\n" ;  
    }       
        
    void func2(int arg) 
    { 
       int result = arg * 3;                 
       cout << result << "\n" ; 
    }         
                      
    //  Create the function vector 
    vector<Myfunc> f;
};


int main()  
{ 

//  Create an instance and call the methods on it. 
     
  Myclass a;
  a.run(0, 4);
  a.run(1, 7);  
 
return 0; 
} 
*** end of code *** 

What I'm wondering is - is it possible to change this code so that the function vector can take *string* functions (as well as the current int ones)? If so, how could that be done? 

Many thanks in advance... :) 
- trilobite

---

### Post by Brandon Williams on 2009-08-22
One option would be to store the functions as objects, rather than straight function pointers. Each object would store a function pointer and its class would implement an operator() method. It could like something like this.

```
class Callback {
public:
    // one operator() method for each argument type
    virtual void operator()( int ) {
        std::cerr << "Error: no int method for this object\n";
    }
    virtual void operator()( std::string& ) {
        std::cerr << "Error: no string method for this object\n";
    }
};

class IntCallback : public Callback {
private:
    void (*cb)(int);
public:
    IntCallback( void (*_cb)(int) ) : cb = _cb { }
    void operator()( int i ) { cb(i); }
};

class StringCallback : public Callback {
private:t
    void operator()( std::string& s ) { cb(s); }
};

// building out the vector
std::vector<Callback> funcs;
funcs.push_back(IntCallback(funcThatTakesInt));
funcs.push_back(StringCallback(funcThatTakesString));

// calling functions from the vector
funcs[0](intArg);
funcs[1](stringArg);
```

---

### Post by MadCow108 on 2009-08-22
edit: read something wrong

---

### Post by trilobite on 2009-08-23
> **Brandon Williams said:**
> One option would be to store the functions as objects, rather than straight function pointers. Each object would store a function pointer and its class would implement an operator() method. It could like something like this.

```
class Callback {
public:
    // one operator() method for each argument type
    virtual void operator()( int ) {
        std::cerr << "Error: no int method for this object\n";
    }
    virtual void operator()( std::string& ) {
        std::cerr << "Error: no string method for this object\n";
    }
};

class IntCallback : public Callback {
private:
    void (*cb)(int);
public:
    IntCallback( void (*_cb)(int) ) : cb = _cb { }
    void operator()( int i ) { cb(i); }
};

class StringCallback : public Callback {
private:t
    void operator()( std::string& s ) { cb(s); }
};

// building out the vector
std::vector<Callback> funcs;
funcs.push_back(IntCallback(funcThatTakesInt));
funcs.push_back(StringCallback(funcThatTakesString));

// calling functions from the vector
funcs[0](intArg);
funcs[1](stringArg);
```

Great! Thanks **very much**, Brandon! 
Looks like a really good solution - very clean and elegant! 

(Update) - 
Ok, I've used the above code and have created several small functions to use with it. The code is now as follows - 
```
 

#include <vector> 
#include <string> 
#include <iostream> 
#include <cmath> 

using namespace std ; 

int power(int base, int exp) 
{
    int i, result = 1;
    for (i = 0; i < exp; i++)
        result *= base;
    return result;
 }


class Callback {
public:
    // one operator() method for each argument type
    virtual void operator()( int ) {
        std::cerr << "Error: no int method for this object\n";
    }
    virtual void operator()( std::string& ) {
        std::cerr << "Error: no string method for this object\n";
    }
};


class IntCallback : public Callback {
private:
    void (*cb)(int); 
    
    void func1(int arg) 
    { 
       int myresult = power(arg, 4) + (5 * arg) - 8 ;           
       cout << myresult << "\n" ;  
    }       
        
    void func2(int arg) 
    { 
       int result = arg * 3; 
       cout << result << "\n" ; 
    }         
         
public:
    IntCallback( void (*_cb)(int) ): cb ( cb = _cb ) { }; 
    void operator()( int i ) { cb(i); }
};


class StringCallback : public Callback { 
public:   
    void operator()( std::string& s ) { cb(s); }
   
   
private:  
    void (*cb)(std::string); 
     
    void func3(std::string arg) 
    { 
       cout << arg << "\n" ;          
    }                      
};


// Fill the vector with functions 
std::vector<Callback> funcs;
funcs.push_back(IntCallback(func1));
funcs.push_back(IntCallback(func2));
funcs.push_back(StringCallback(func3));
        
int main()  
{ 

// Call the functions stored in the vector. 
funcs[0](3);
funcs[1](7);
funcs[2]("Hi there!"); 
 
return 0; 
} 

``` 

However, I get these errors - 
*** start of errors *** 
g++ -Wall -o "func_vector" "func_vector.cpp" (in directory: /home/andy/file_parsers)
func_vector.cpp:79: error: expected constructor, destructor, or type conversion before &#8216;.&#8217; token
func_vector.cpp:80: error: expected constructor, destructor, or type conversion before &#8216;.&#8217; token
func_vector.cpp:81: error: expected constructor, destructor, or type conversion before &#8216;.&#8217; token
func_vector.cpp: In function &#8216;int main()&#8217;:
func_vector.cpp:90: error: invalid conversion from &#8216;const char*&#8217; to &#8216;int&#8217;
func_vector.cpp:90: error:   initializing argument 1 of &#8216;virtual void Callback::operator()(int)&#8217;
Compilation failed.
*** End of errors *** 

These look like they should be straightforward to fix, but I'm not sure how to do so, so any help is much appreciated... :)  
- trilobite

---

