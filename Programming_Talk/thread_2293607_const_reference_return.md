---
title: "const reference return"
date: 2015-09-06
forum: Programming Talk
---

### Post by chuchi on 2015-09-06
Hi there!!
 

 I am just wondering what is the difference between returning a non-const object and a const reference.
 

 For example, this code outputs the same result regardless of the return type in the assignment operator.
 

 ```

 

 class Test
 {
 public:
   int *ptr;
 

   Test(int i = 0)
   {
     ptr = new int(i);
   }
 

   const Test& operator=(const Test &t)
   {
     *ptr = *(t.ptr);
     return *this;
   }
    
   /**
    * the same result  
    */
 //  Test operator=(const Test &t)
 //  {
 //    *ptr = *(t.ptr);
 //    return *this;
 //  }
 };
 

 int main()
 {
 

   Test t1(5);
   Test t2;
   t2 = t1;
   t1.ptr = new int(10);
   cout << "t2 = " << *(t2.ptr) << endl;
 

   return 0;
 }
 

 
```
 

 Could someone explain to me the differences? Thank you so much!!

---

### Post by patlkli on 2015-09-07
Well, first of all, I think you should do some reading about [the rule of three]("http://en.cppreference.com/w/cpp/language/rule_of_three").

There are several problems in your code which I will address before I explain, why you'd use one assignment operator over the other:

You are leaking memory. If you are using dynamically allocated memory in your class, you almost certainly need a destructor, a copy constructor **and** an assignment operator. (see: rule of three)

Here's why: Your constructor is allocating heap memory. When the object(s) of your class are destroyed at the end of the scope, nobody will free the memory you have allocated. The pointer value will be lost and the referenced memory will leak.

Now, if you were to copy construct an object of your class using another object (example follows), the default copy constructor (which the compiler will generate for you), will simply copy the pointer value into the new class.
You now have two objects, which both reference the same memory location in their ptr pointers. If you now had a destructor (to fix your memory leak I described), the destructor of the first object would free the memory pointed to by ptr. When the second object is destroyed, it will also try to free its ptr pointer (which is identical to the already free'd one), and you will get an error from the runtime stating a "double-free".

Copy Construct: ```
Test t3(t2);
```

Now, if you have implemented both your destructor and copy constructor properly, you try to use the default assignment operator, which will pretty much try the same as the copy constructor: copy each member, including the pointer. This will lead to the same double-free problem, so you also need your own (copy) assignment operator.

This leads to the following:
```

class Test
 {       
     public:
         int *ptr;
         
         
         Test(int i = 0)
         {
             ptr = new int(i);
         }
         
         ~Test()
         {       
             if(ptr)
                 delete ptr;
         }
         
         const Test& operator=(const Test &t)
         {       
             if (ptr)
                 delete ptr;
                 
             if (t.ptr)
                 ptr = new int(*t.ptr);
         
             return *this;
         }
         
         Test(const Test &t)
         {       
             if (t.ptr)
                 ptr = new int(*t.ptr);
         }
};

```

In your main function you now try your code:
```

 int main()
 {
     Test t1(5);                             // calls default constructor
     Test t2;                                // calls default constructor
     t2 = t1;                                // calls assignment operator
     t1.ptr = new int(10);                   // this will leak memory!
     cout << "t2 = " << *(t2.ptr) << endl;
 
     return 0;
 }

```

Since your member ptr is public, you can work around the well-oiled machine of your rule of three and directly overwrite the pointer like you do in your main.
You don't free the old t1.ptr, but only allocate a new pointer and assign it. The memory of the old t1.ptr is lost.
So you should make your member private and use a getter method to obtain the stored value.

Additionally, the fact that you seperated the declaration of t2 and the assignment on two lines instead of just one, you will unnecessarily call the constructor and assignment operator, instead of just the copy constructor:
```

Test t2; // calls default constructor
t2 = t1; // calls assignment operator

// -- vs. --

Test t2 = t1; // calls copy constructor

```

So, now to your question. ;)

What's the difference when the return value of the assignment operator is **Test** instead of **const Test&**?

Considering your main code:
```

Test t2;
t2 = t1;

```

The first line calls the default constructor. The second line will first call the assignment operator, which will operate on the object t2 and copy the value from t1.
Then however, since you're returning by value, the object t2 will be copied using the copy constructor. Directly after, the copy of t2 will be assigned to t2, which then triggers the destruction of the original t2.
This is by no means illegal, but it costs performance because it's copying and duplicating the objects just to destroy the identical copies directly after.

This answer was definitely longer than I anticipated, but I hope I could explain to you, why your code is quite a bit flawed.
Just some basic reading on the rule of three would be enough to understand, why this is important.

Feel free to ask, if you have more questions concerning this example.

---

### Post by dwhitney67 on 2015-09-15
Regarding the previous post, it is recommended that class member data be initialized *prior* to entering the body of the constructor.  For example:
```

Test(int i = 0)
    : ptr(new int(i))
{
}

~Test()
{
    delete ptr;     // there's no need to check if the pointer is non-null; it will always be a legit pointer.
}

```

Taking this a step further, it also recommended that std::unique_ptr be used whenever appropriate.  For example:
```

#include <memory>

class Test
{
public:
    Test(int i = 0)
        : ptr(new int(i))
    {
    }

    ~Test()
    {
        // heap memory in ptr is automatically freed
    }

    int get() const
    {
        return *ptr;
    }

private:
    std::unique_ptr<int> ptr;
};

```

---

### Post by chuchi on 2015-09-20
Hi patlkli!!

Thank you very much for your great answer!! I have understood everything clearly!!

You are a great C++ developer!

All the best[B][COLOR=#000000]

[/COLOR][/B]

---

