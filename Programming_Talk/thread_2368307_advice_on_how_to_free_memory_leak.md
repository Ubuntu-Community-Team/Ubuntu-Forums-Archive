---
title: "advice on how to free memory leak"
date: 2017-08-09
forum: Programming Talk
---

### Post by chuchi on 2017-08-09
Hi everyone!


I have to deal with a memory leak in a code that is not mine, and I want to ask for advice on what is an elegant way to free the memory leak. The code looks like this:


```



#include <iostream>
#include <vector>
using namespace std;


class A
{
public:


    int a;


    A(int a_) : a(a_)
    {}
};


class B
{
public:


    B(A * a) : a_(a)
    {
    }
private:
    A *a_;


};


class Example
{
public:


    void createElements(int count)
    {
        vectorB.clear();
        for (int i = 0; i < count; i++)
        {
            A * a = new A(i);
            B b(a);
            vectorB.push_back(b);
        }
    }


private:
    std::vector <B> vectorB;
};




int main()
{
    Example example;
    example.createElements(3);
}









```




The memory leak comes from the line :


```

A * a = new A(i);

```


I thought that maybe I could maintain a vector<A*> and add the objects to this vector. Then, when deleting Example (or when calling createElements again) I would iterate through that vector, free its elements and clear the vector.


What do you think about this approach?


Thanks a lot!

---

### Post by norobro on 2017-08-09
> **chuchi said:**
> ... advice on what is an elegant way to free the memory leak. ...Use std::shared_ptr  [http://en.cppreference.com/w/cpp/memory/shared_ptr](http://en.cppreference.com/w/cpp/memory/shared_ptr) 
Like this:```
    //A * a = new A(i);
    std::shared_ptr<A> a(new A(i));
```


You'll need to make changes in class B also.

---

### Post by chuchi on 2017-08-11
Hi norobro, thank you for your response!




If I use a shared pointer, once the method is done all the pointers are freed, and I need to maintain such pointers for later use. This is an example :


```

#include <iostream>
#include <vector>
#include <memory>
using namespace std;


class A
{
public:


    int a;


    A(int a_) : a(a_)
    {
    }
};


class B
{
public:


    A *a_;


    B(A * a) : a_(a)
    {
    }
};


class Example
{
public:


    void createElements(int count)
    {
        vectorB.clear();
        for (int i = 0; i < count; i++)
        {
            //A * a = new A(i);
            std::shared_ptr<A> a(new A(i));
            B b(a.get());
            vectorB.push_back(b);
        }
    }


    void printElements()
    {
        for (int i = 0; i < vectorB.size(); i++)
        {
            printf("value = %d\n", vectorB[i].a_->a);
        }
    }


private:
    std::vector <B> vectorB;
};


int main()
{
    Example example;
    example.createElements(3);
    example.printElements();
}

```


Besides, I can't make changes in class B, because there is another client code which uses this class in this way :


```



A *a = new A;


B b(a);
//do some stuff with b
delete a;



```




So I can not delete a_ within B destructor...

---

### Post by dwhitney67 on 2017-08-23
> **chuchi said:**
> 
Besides, I can't make changes in class B, because there is another client code which uses this class in this way :


You can't make changes, or you just don't want to???  Are the coding police preventing you from making code changes?

My advice is to use a shared pointer (per the advice that was given to you earlier), or redesign your project in a different way.  If you do not want to use a shared pointer, then class B should *own* the A object, and should be responsible for deleting it.  The client code that you supposedly can't change should be changed.  It is that simple.

---

### Post by james222 on 2017-09-06
Shared pointer will be the best approach in this case.

---

