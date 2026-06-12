---
title: "external member function implementation in local class"
date: 2008-08-12
forum: Programming Talk
---

### Post by arkangel on 2008-08-12
I was reading the std and i can't figure out if this is possible at all . I want to have a local class in a function , one of the member functions is rather long so I want to implement it outside of the function.


```


#include <iostream> 

using namespace std;
 
int foo(){
    class intClass{ 
          int a, b; 
      public:
      intClass() {a=1; b=1;} 
      int doSome_over_a_b(){/* doSome_over_a_b */} 
    }; 
   
   intClass X; 
   int y=X.doSome_over_a_b(); 
   /*some other foo stuff*/ 
}


/* I want to put intClass::doSome_over_a_b here or in a *.C file */


int main (void) { 

foo(); 

}


```


How can I implement doSome_over_a_b outside of foo keeping the declaration in intClass as if it were a normal class ?

---

### Post by Zugzwang on 2008-08-12
> **arkangel said:**
> 
How can I implement doSome_over_a_b outside of foo keeping the declaration in intClass as if it were a normal class ?

You normally don't do it that way. In your case, you would define the class outside of the function in order to get it working. If it is your purpose to "hide away" that class from all other parts of the program, simply put its declaration into a special header file that is not included by the parts of the program you don't want it to see (you might also want to use namespaces).

[PHP]
#include <iostream> 

using namespace std;

class intClass{ 
      int a, b; 
public:
      intClass() {a=1; b=1;} 
      int doSome_over_a_b();
}; 
 
int foo(){
   intClass X; 
   int y=X.doSome_over_a_b(); 
   /*some other foo stuff*/ 
}


/* I want to put intClass::doSome_over_a_b here or in a *.C file */
int intClass::doSome_over_a_b() {
    std::cout << "I'm here!\n";
    return 42;
}


int main (void) { 
    foo(); 
}
[/PHP]

BTW: Why are you trying to perform this task in any other way than as stated above?

---

### Post by arkangel on 2008-08-12
I know normally should be a normal class ,  I  have a very special foo ,  with nested classes is not a problem

---

### Post by Zugzwang on 2008-08-12
> **arkangel said:**
> [...],  I  have a very special foo ,  with nested classes is not a problem

I'm afraid that this is incomprehensible. Could you elaborate on that?

---

### Post by arkangel on 2008-08-12
:lolflag:  I have a good reason to have a local class...

---

### Post by Zugzwang on 2008-08-12
> **arkangel said:**
> I have a good reason to have a local class...

...which is....?

---

### Post by nvteighen on 2008-08-12
If I were to declare a class it's usually to allow some other code to use it.

---

