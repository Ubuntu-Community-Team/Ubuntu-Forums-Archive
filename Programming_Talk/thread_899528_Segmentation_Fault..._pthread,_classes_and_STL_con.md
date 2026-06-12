---
title: "Segmentation Fault... pthread, classes and STL container"
date: 2008-08-24
forum: Programming Talk
---

### Post by Ristar on 2008-08-24
hi

I keep getting the segmentation fault thingie and i think i know wat's causing the problem, but i dunno how to fix it.

please take a look at the code.

```

...
class AnotherClass{
    ...
};

...

class AClass{
    private:
        list<AnotherClass> listName;
        list<AnotherClass>::iterator it;
        ...
    public:
        void disp();
};
void AClass::disp(){
    cout<<"show this statement"<<endl;
    [COLOR="Red"]cout<<"size of listName = "<<listName.size()<<endl;[/COLOR]
    cout<<"XXXXXXXXXXXXXXXXXXX"<<endl;
    ...
}

int main(){
    ...
    AClass inst;
    int retVa1 = pthread_create(&thread1, NULL, func, &inst);
    ...
}

void *func(void *ptr){
    AClass *inst = (AClass *) &ptr;
    ...
    inst -> disp();
    ...
}

```



The output is

> 
show this statement
Segmentation fault


wat is wrong with my codes? please help...

---

### Post by mike_g on 2008-08-24
Wheres the constructor for AClass? From what you have posted it seems as if there isent one. It seems that you have not initialised your object and listName is just pointing to some random point in memory.

---

### Post by Ristar on 2008-08-24
> **mike_g said:**
> Wheres the constructor for AClass? From what you have posted it seems as if there isent one. It seems that you have not initialised your object and listName is just pointing to some random point in memory.

well... the constructor initialises everything except listName.

how do i initialise the STL container "list" properly? i have tried listName.clear() and i still get the "Segmentation fault" message.

is initialising STL containers a must for pthreads? i mean, i tried it from main() (using the code "inst.disp()" ) and it returns the correct value, which is 0.

---

### Post by mike_g on 2008-08-24
> how do i initialise the STL container "list" properly? i have tried listName.clear() and i still get the "Segmentation fault" message.
I havent used stl much but this might help:
[http://www.cplusplus.com/reference/stl/list/list.html](http://www.cplusplus.com/reference/stl/list/list.html)

Edit: I think what i was on about before might have been wrong. Instead, you might want to try changing this: 
```
AClass *inst = (AClass *) &ptr;
```
To this:
```
AClass *inst = (AClass *) ptr;
```
Does that work?

---

### Post by Ristar on 2008-08-24
> **mike_g said:**
> Well that should be your problem then. This might help:
[http://www.cplusplus.com/reference/stl/list/list.html](http://www.cplusplus.com/reference/stl/list/list.html)

uh... i have read it, but still do not understand how to do it.

```

list<AnotherClass> listName;

```

it looks like i called the first constructor of list from the webpage, however, since the problem is present, i tried using:

```

list<AnotherClass> listName (1,AnotherClass());

```

but was greeted with many errors upon compilation.


wats the correct way of doing it?

---

### Post by dwhitney67 on 2008-08-24
Below are two working solutions; one using the pthread functions, the other using Boost.  I recommend you consider using Boost; it is more portable.

SimpleThread.cpp:
[PHP]#include <pthread.h>
#include <list>
#include <iostream>


class AnotherClass
{
  public:
    AnotherClass() {}
};


class AClass
{
  public:
    void disp()
    {
      std::cout << "show this statement" << std::endl;
      std::cout << "size of listName = " << m_listName.size() << std::endl;
      std::cout << "XXXXXXXXXXXXXXXXXXX" << std::endl;
    }
    
  private:
    typedef std::list< AnotherClass > MyList;
    typedef MyList::iterator          MyListIterator;

    MyList m_listName;
};


void * func( void *arg );

int main()
{
  AClass aclass;

  pthread_t tid;

  pthread_create( &tid, NULL, func, &aclass );

  int *status = 0;

  pthread_join( tid, (void**)&status );

  return 0;
}

void * func( void *arg )
{
  AClass *aclass = reinterpret_cast<AClass *>(arg);

  aclass->disp();

  return NULL;
}[/PHP]
To compile the program above:
```
g++ SimpleThread.cpp -lpthread
```

SimpleThread2.cpp:
[PHP]#include <boost/thread/thread.hpp>
#include <list>
#include <iostream>


class AnotherClass
{
  public:
    AnotherClass() {}
};


class AClass
{
  public:
    void operator()(void)
    {
      disp();
    }
    
  private:
    void disp()
    {
      std::cout << "show this statement" << std::endl;
      std::cout << "size of listName = " << m_listName.size() << std::endl;
      std::cout << "XXXXXXXXXXXXXXXXXXX" << std::endl;
    }

    typedef std::list< AnotherClass > MyList;
    typedef MyList::iterator          MyListIterator;

    MyList m_listName;
};


int main()
{
  AClass aclass;

  boost::thread *aclassThread = new boost::thread( aclass );

  boost::thread_group threads;
  threads.add_thread( aclassThread );

  threads.join_all();

  return 0;
}[/PHP]
To compile the program above:
```
g++ SimpleThread2.cpp -lboost_thread-mt
```

---

### Post by Ristar on 2008-08-24
> **mike_g said:**
> I havent used stl much but this might help:
[http://www.cplusplus.com/reference/stl/list/list.html](http://www.cplusplus.com/reference/stl/list/list.html)

Edit: I think what i was on about before might have been wrong. Instead, you might want to try changing this: 
```
AClass *inst = (AClass *) &ptr;
```
To this:
```
AClass *inst = (AClass *) ptr;
```
Does that work?



that really helped!
thanks a million.

if it is not too much trouble, would u mind explaining, or referring me to a webpage that explains, why the "&" should be removed?

thanks again.

---

### Post by mike_g on 2008-08-24
If you dont remove the & then you would be assigning the adress of the pointer to **inst**. What you want to do is assign the adress that the pointer points to. I know it sounds confusing, but it becomes easier with practice.

Some more on it:
[http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?answer=1047588532&id=1043284376](http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?answer=1047588532&id=1043284376)

---

