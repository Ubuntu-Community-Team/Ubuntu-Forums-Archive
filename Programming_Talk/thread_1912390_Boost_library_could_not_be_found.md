---
title: "Boost library could not be found"
date: 2012-01-20
forum: Programming Talk
---

### Post by alfa_80 on 2012-01-20
I was trying to compile and build one of Boost-related source code that was found here:
[http://en.highscore.de/cpp/boost/](http://en.highscore.de/cpp/boost/) (refer to part 6.2)

The code is as follows:
```

#include <boost/thread.hpp>  
#include <iostream>   

void wait(int seconds)  
{    
    boost::this_thread::sleep(boost::posix_time::seconds(seconds));  
}   

void thread()  
{    
    for (int i = 0; i < 5; ++i)    
    {      
        wait(1);      
        std::cout << i << std::endl;    
     }  
}   

int main()  
{    
    boost::thread t(thread);    
    t.join();  
} 


```I've compiled it with the command like below:
```
g++ -Wall -I/usr/include/boost/ try_boost.cpp -lboost1.40 -L/usr/share/lintian/overrides/libboost-thread1.40.0 -o try_boost
```However, I got an error message like below:
```
/usr/bin/ld: cannot find -lboost1.40

```It seems that the library couldn't be found. Can someone suggest me about where it is normally located or perhaps you can try with some changes on the above command to compile the code.

---

### Post by Arndt on 2012-01-20
> **alfa_80 said:**
> I was trying to compile and build one of Boost-related source code that was found here:
[http://en.highscore.de/cpp/boost/](http://en.highscore.de/cpp/boost/) (refer to part 6.2)

The code is as follows:
```

#include <boost/thread.hpp>  
#include <iostream>   

void wait(int seconds)  
{    
    boost::this_thread::sleep(boost::posix_time::seconds(seconds));  
}   

void thread()  
{    
    for (int i = 0; i < 5; ++i)    
    {      
        wait(1);      
        std::cout << i << std::endl;    
     }  
}   

int main()  
{    
    boost::thread t(thread);    
    t.join();  
} 


```I've compiled it with the command like below:
```
g++ -Wall -I/usr/include/boost/ try_boost.cpp -lboost1.40 -L/usr/share/lintian/overrides/libboost-thread1.40.0 -o try_boost
```However, I got an error message like below:
```
/usr/bin/ld: cannot find -lboost1.40

```It seems that the library couldn't be found. Can someone suggest me about where it is normally located or perhaps you can try with some changes on the above command to compile the code.

Try using

```
-L/usr/share/lintian/overrides
```

---

### Post by MadCow108 on 2012-01-20
> **Arndt said:**
> Try using

```
-L/usr/share/lintian/overrides
```

wtf what would boost to in the lintian override directory?
thats for something completely different (a package quality assurance tool before you ask)

package installed libraries are located in /usr/lib or /usr/lib/<arch-triplet> though you never have to (nor should you) specify these paths when compiling. -L is for the non default paths.

@op:
do you have boost1.40 and the appropriate -dev packages installed?
different ubuntu versions have different versions available.
Plaese first tell us which version you are using.
if 1.40 is available in your ubuntu version do
```
sudo apt-get install libboost1.40-dev
```

---

### Post by alfa_80 on 2012-01-20
> **Arndt said:**
> Try using

```
-L/usr/share/lintian/overrides
```

Thanks for your idea, nevertheless i still received an error message of "/usr/bin/ld: cannot find -lboost1.40
collect2: ld returned 1 exit status"

---

### Post by alfa_80 on 2012-01-20
> **MadCow108 said:**
> wtf what would boost to in the lintian override directory?
thats for something completely different (a package quality assurance tool before you ask)

package installed libraries are located in /usr/lib or /usr/lib/<arch-triplet> though you never have to (nor should you) specify these paths when compiling. -L is for the non default paths.

@op:
do you have boost1.40 and the appropriate -dev packages installed?
different ubuntu versions have different versions available.
Plaese first tell us which version you are using.
if 1.40 is available in your ubuntu version do
```
sudo apt-get install libboost1.40-dev
```

Yes, from synaptic manager and using "locate" command I can see, there are boost1.40(including dev) related stuff.

I am Lucid(10.04 LTS) anyway.

Thanks in advance.

---

### Post by MadCow108 on 2012-01-20
is there even supposed to be a libboost in existence?
boost libraries are usually named libboost_*somefeature*

there is no libboost available in my current distribution (precise)

---

### Post by alfa_80 on 2012-01-20
> **MadCow108 said:**
> is there even supposed to be a libboost in existence?
boost libraries are usually named libboost_*somefeature*

there is no libboost available in my current distribution (precise)

Thanks a lot MadCow, your hint works!

The exact one that is currently working is like below:
```
 g++ -Wall -I/usr/include/boost/ try_boost.cpp -lboost_thread -L/usr/share/lintian/overrides/libboost-thread1.40.0 -o try_boost
```

Can anyone refactor my command, because I think I mess it up, which one actually better comes first -L or -I, and -I and -L should or not be coupled with /, or should there be a space between them.

---

### Post by dwhitney67 on 2012-01-20
> **alfa_80 said:**
> 
Can anyone refactor my command...

The following would have sufficed:
```

g++ -Wall thread.cpp -lboost_thread -o try_boost

```
I'm not sure what the "lintian" thing is, but it is not necessary on a 32-bit 10.04 system.  Are you compiling on a 64-bit system?

---

### Post by alfa_80 on 2012-01-20
If some of you want to contribute on my follow-up question regarding Eclipse IDE, you can go here: [http://ubuntuforums.org/showthread.php?p=11627020#post11627020](http://ubuntuforums.org/showthread.php?p=11627020#post11627020).

Thanks in advance.

---

### Post by alfa_80 on 2012-01-20
> **dwhitney67 said:**
> The following would have sufficed:
```

g++ -Wall thread.cpp -lboost_thread -o try_boost

```I'm not sure what the "lintian" thing is, but it is not necessary on a 32-bit 10.04 system.  Are you compiling on a 64-bit system?

Cool! It also works, even I'm on 64-bit machine. Why a friend of mine suggested that I should include -I and -L? Why in this case, we don't need it? Any idea?

---

### Post by MadCow108 on 2012-01-20
-L is used to tell the linker an additional path where it should search for libraries.
Several paths are searched by default and must not be added to the commandline explicitly (gcc --print-search-dirs in newer gcc's)
Similary -I tells it additional paths to look for headers.

packages install libraries into the paths that are searched by default so you don't have to use these flags when you use those versions.

---

### Post by dwhitney67 on 2012-01-20
> **alfa_80 said:**
> Why a friend of mine suggested that I should include -I and -L? Why in this case, we don't need it? Any idea?

Typically the -I option is used when the need arises to specify a directory that is not directly under /usr/include and /usr/include/c++/<someversion>.

In the program you posted earlier, you included <boost/thread.hpp>, and thus there's no need to specify the -I/usr/include/boost as a search directory since 'boost/'  falls under /usr/include.

Similarly, for the -L option, there's no need to specify it if the directory you are interested in is stored within the "ldconfig" cache.  Use -L only when specifying the directory of a library that is not in this cache.

P.S.  You can view the ldconfig cache using the following command:
```

ldconfig -p

```

---

### Post by Arndt on 2012-01-20
> **MadCow108 said:**
> wtf what would boost to in the lintian override directory?
thats for something completely different (a package quality assurance tool before you ask)



Use polite language, dude.

The original question had -L/usr/share/lintian/overrides/libboost-thread1.40.0 in the command line, so I thought it might be involved.

---

