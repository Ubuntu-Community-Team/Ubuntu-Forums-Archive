---
title: "copy constructor for a class with an abstract member"
date: 2018-01-02
forum: Programming Talk
---

### Post by chuchi on 2018-01-02
Hi everyone!


This question is related to how implement a copy constructor for a class that has a pointer to an abstract type. Here is an example:


```

class MyAbstract
{
public:    
    virtual void abstractMethod() const = 0;


};


class UseAbstract
{
public:
    UseAbstract (MyAbstract *abstract, int b)
    {
        abstract_ = abstract;
        b_ = b;
    }
    
    UseAbstract (const UseAbstract &other)
    {
        b_ = other.b_;
        //abstract_ = new ??
    }
    
private:
    MyAbstract *abstract_;
    int b_;
};

```




How can I implement the copy constructor for UseAbstract? I can't create an object for 'MyAbstract'.


Thanks a lot!

---

### Post by spjackson on 2018-01-02
You cannot copy an object whose type you don't know. C++ does not have virtual copy constructors. The usual way to handle this is via a virtual clone method. See [https://www.geeksforgeeks.org/advanced-c-virtual-copy-constructor/](https://www.geeksforgeeks.org/advanced-c-virtual-copy-constructor/) 


However, I'm puzzled about your policy on object ownership and lifetimes. Which object owns (and is responsible for deleting) MyAbstract objects which are passed in via the main constructor for UseAbstract? Is this still the case for MyAbstract objects that are to be cloned during UseAbstract's copy constructor?



[URL="https://www.geeksforgeeks.org/advanced-c-virtual-copy-constructor/"]
[/URL]

---

### Post by chuchi on 2018-01-03
Hi spjackson,


I am sorry I did not specify who owns and free the memory. Here is an example code


```

#include <iostream>


class MyAbstract
{
public:


    MyAbstract()
    {
    }


    MyAbstract& operator=(const MyAbstract & other)
    {
        if (this != &other)
        {
            copy(other); //invoke the subclass copy method
        }
        return *this;
    }


    virtual void copy(const MyAbstract & other) = 0;
    virtual void abstractMethod() const = 0;


};


class Implement : public MyAbstract
{
public:
    int a_;


    Implement(int a)
    {
        a_ = a;
    }


    Implement(const Implement &other)
    {
        copy(other);
    }
    
    /*!
     * This method is called from the parent operator=
     */
    void copy(const MyAbstract & other)
    {
        const Implement *aux = (const Implement *) & other;
        a_ = aux->a_;
    }


    void abstractMethod() const
    {
        std::cout << "value of a_ = " << a_ << std::endl;
    }
};


class UseAbstract
{
public:


    UseAbstract(MyAbstract *abstract)
    {
        abstract_ = abstract;
    }


    UseAbstract& operator=(const UseAbstract &other)
    {
        if (this != &other)
        {
            *abstract_ = *(other.abstract_);
        }
        return *this;
    }


    void useAbstractMethod()
    {
        abstract_->abstractMethod();
    }


private:


    //private because abstract_ is uninitialized
    UseAbstract(const UseAbstract &other)
    {
        //this causes a crash
        //*abstract_ = *(other.abstract_);
    }
    
    MyAbstract *abstract_;


};


int main()
{
    Implement * abstract1 = new Implement(1);
    Implement * abstract2 = new Implement(2);


    UseAbstract useabstract1(abstract1);
    UseAbstract useabstract2(abstract2);


    useabstract2.useAbstractMethod();
    useabstract2 = useabstract1;
    useabstract2.useAbstractMethod();


    delete abstract1;
    delete abstract2;
    return 1;
}

```




The management of the memory is done by the client code, in this case 'main'.


What are your thoughts about this code?


Be aware that the copy constructor is private in UseAbstract. Because I do not want the client code to do something like this


```

UseAbstract useabstract3 = useabstract2; //crash because abstract_ is not initialized

```


Thanks a lot!

---

### Post by spjackson on 2018-01-04
> **chuchi said:**
> 
The management of the memory is done by the client code, in this case 'main'.

So what will own (and delete) any copy MyAbstract object that may be created in UseAbstract's copy constructor?

Since memory management is done by the client code, does UseAbstract need to copy its MyAbstract? Is it enough just to copy the pointer, i.e.
```

  abstract_ = other.abstract_;

```

---

