---
title: "C++ Boost threading - Can anybody figure out this error?"
date: 2010-09-06
forum: Programming Talk
---

### Post by Swiftslide on 2010-09-06
I'm pretty new to C++, like many I was a Java man. I'm trying to use boost to create some threads within a class constructor. I have seen examples of thread creation as pertaining to a single .cpp file (with a main method and a single other function which is the subject of the new thread), but none dealing with how to create threads for class methods.

The class in question is called "HarbourMaster" (it is a ship simulation). I am using separate header and cpp files. The functions are called passTime(), checkLoadingBays() and checkUnloadingBays(), respectively. The statements I am using to create the threads are as follows:

```
boost::thread timeThread(&HarbourMaster::passTime);
boost::thread lBaysThread(&HarbourMaster::checkLoadingBays);
boost::thread uBaysThread(&HarbourMaster::checkUnloadingBays);
```

The error that arises is as follows:

[I]In file included from /usr/include/boost/thread/thread.hpp:22,
/usr/include/boost/thread/detail/thread.hpp:56: error: must use ‘.*’ or ‘->*’ to call pointer-to-member function in ‘((boost::detail::thread_data<void (HarbourMaster::*)()>*)this)->boost::detail::thread_data<void (HarbourMaster::*)()>::f (...)’, e.g. ‘(... ->* ((boost::detail::thread_data<void (HarbourMaster::*)()>*)this)->boost::detail::thread_data<void (HarbourMaster::*)()>::f) (...)’[/I]

Can anybody explain what this means and/or how to fix it? I'm sure it's something to do with pointers but my knowledge of them is too slim as to be able to decipher it...

Note that originally I tried using the following, as per the examples I have seen:

```
boost::thread timeThread(&HarbourMaster::passTime);
boost::thread lBaysThread(&HarbourMaster::checkLoadingBays);
boost::thread uBaysThread(&HarbourMaster::checkUnloadingBays);
```

However, this produced errors which instructed me to put the class name ahead of the function name, which would seem to make sense according to my limited knowledge.


I would greatly appreciate any help anybody can give me.

---

### Post by dwhitney67 on 2010-09-06
Swiftslide, your namesake is demanding an explanation.

I replied to another thread you posted yesterday (or was it Saturday); please find, and more importantly, read it here:
[http://ubuntuforums.org/showthread.php?t=1568418](http://ubuntuforums.org/showthread.php?t=1568418)

---

### Post by Swiftslide on 2010-09-07
I feel a bit embarrased. I was literally so tired that I forgot I created that first topic when I created this one.

Btw I've taken your advice from the other topic on board now, and it works! Much more complex way than I was taught, but hey, as long as it works

Thanks mate

---

### Post by dwhitney67 on 2010-09-07
Actually, now I think I understand why you had initial issues with compiling your code; your thread methods were not declared as "static".

Consider the following:
```

#include <boost/thread.hpp>
#include <iostream>

class HarbourMaster
{
public:
   HarbourMaster() {}
   **static** void passTime()           { std::cout << "passing time." << std::endl; }
   **static** void checkLoadingBays()   { std::cout << "checking loading bays." << std::endl; }
   **static** void checkUnloadingBays() { std::cout << "checking unloading bays." << std::endl; }
};

int main()
{
   boost::thread* bt1 = new boost::thread(HarbourMaster::passTime);
   boost::thread* bt2 = new boost::thread(HarbourMaster::checkLoadingBays);
   boost::thread* bt3 = new boost::thread(HarbourMaster::checkUnloadingBays);

   boost::thread_group tg;
   tg.add_thread(bt1);
   tg.add_thread(bt2);
   tg.add_thread(bt3);

   tg.join_all();

   return 0;
}

```

P.S.  If you need to pass an instance of a HarbourMaster object to the thread function, do something like:
```

class HarbourMaster
{
   ...

   static void passTime(**HarbourMaster* hm**)
   {
      ...
   }

   ...
};

int main()
{
   **HarbourMaster hm;**

   boost::thread* bt1 = new boost::thread(HarbourMaster::passTime, **&hm**);

   ...
}

```

---

