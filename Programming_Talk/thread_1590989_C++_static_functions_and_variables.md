---
title: "C++ static functions and variables"
date: 2010-10-08
forum: Programming Talk
---

### Post by DBQ on 2010-10-08
Hi everybody,

I got a question. I have the following code.

```


#include <list>
using namespace std;

class A
{
        public:

        static A* f(int a)
        {   
                A* new_A = new A(a);
                    
                list_of_A.push_back(new_A);
                    
                return new_A;
        }   
                    
        protected:
                            
        static list<A*> list_of_A;
                            
        A(int a)
        {   
                a = 100;            
        }   
                            
};

int main()
{
   A* myA = A::f(100);
   return 0;
}


```

when I compile it, I get error: undefined reference to `A::list_of_A'. The thing is, if I remove line ```
A* myA = A::f(100);
``` from main, then everything is fine. Why is this happening? Any ideas how to fix it? Help is appreaciated.

---

### Post by worksofcraft on 2010-10-08
Yes, the reason you get no error when you remove the call to A::f(100) is because defining a method inside the class definition makes it inline code, so if it isn't used then the compiler doesn't implement it anywhere.

The reason you get the error message when you do use it, is because inside the definition of your class A you are only declaring the list. You still need to actually define it... Well you need to define it if you actually use it and that is when method f() is expanded somewhere, so simply add the following line just above main() to fix your problem:

```

list<A*> A::list_of_A;

```

---

### Post by DBQ on 2010-10-08
Thanks for the help.  Is there a way to some how declare and define this variable within the class A?  Doing it in main seems bit inelegant.

---

### Post by worksofcraft on 2010-10-08
> **DBQ said:**
> Thanks for the help.  Is there a way to some how declare and define this variable within the class A?  Doing it in main seems bit inelegant.

Oh it's not supposed to be IN main... just outside it... like you would define any other static or global Data. The declaration of your class doesn't actually generate anything and would quite often be something you put in a header file... so, no... definitions and declarations must be separate in this case.

p.s. in my mind, to tell compiler about something that can exist somewhere else (declaration) and telling it to actually make one of them right here (definition) really are very separate concepts :shock:

---

