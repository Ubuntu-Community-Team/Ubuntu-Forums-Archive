---
title: "Boost C++ libraries"
date: 2007-11-20
forum: Programming Talk
---

### Post by Rij on 2007-11-20
Hello,

I am trying to use Boost Thread libraries. I followed the usual download and build instructions. 

So now I have all my Thread header files in:  
.../boost_1_34_1/boost/thread/

I have the following libraries in .../boost_1_34_1/stage/lib:
libboost_thread-gcc34-mt-1_34_1.a     libboost_thread-gcc34-mt-d.a
libboost_thread-gcc34-mt-d-1_34_1.a   libboost_thread-gcc34-mt.a

Now I am trying to compile the standard hello world which looks like this:
#include <boost/thread/thread.hpp>
#include <iostream>

void hello() {
  std::cout << "Hello world, I'm a thread!" << std::endl;
}

int main(int argc, char* argv[]) {
  boost::thread thrd(&hello);
  thrd.join();
  return 0;
}

I compile with gcc 3.4.1 on SunOS. I specified the header files with -I option and the libraries with -L option.

But ld is unable to resolve the thread symbols. So I get the error:

Undefined                       first referenced
 symbol                             in file
boost::thread::join()               /var/tmp//ccrK5p0W.o
boost::thread::~thread()            /var/tmp//ccrK5p0W.o
boost::thread::thread(boost::function0<void, std::allocator<boost::function_base> > const&)/var/tmp//ccrK5p0W.o
ld: fatal: Symbol referencing errors. No output written to a.out
collect2: ld returned 1 exit status

Can someone please help?

Thanks, Rij

---

### Post by aks44 on 2007-11-20
What is the *exact* command line you use? IIRC g++ uses -I (upper-case i) for include paths and -l (lower-case L) for library paths.

Better post your command line inside [ code ] tags to avoid any confusion...

---

### Post by iharrold on 2007-11-20
[I'm assuming Ubuntu]first type:
```
sudo apt-get install libboost*
```

To ensure you have all components of the library.  Then, this should be the command line g++ compile procedure.  Use [-l] boost_thread for the library.

```
g++ boostthreadtest.cpp -o boostthreadtest -lboost_thread
$ ./boostthreadtest
```

---

### Post by aks44 on 2007-11-20
> **iharrold said:**
> I'm assuming Ubuntu

> **Rij said:**
> I compile with gcc 3.4.1 on SunOS.

Morality: never assume anything, and always read the posts thoroughly... ;)

---

### Post by Rij on 2007-11-20
I used -I and tried with -L for the above mentioned error
> 
g++ -I/home/research/code/boost_1_34_1 -L /home/research/code/boost_1_34_1/stage/lib/libboost_thread-gcc34-mt.a main.cc


But if I use -l, then I get the error:
ld: fatal: library -l/home/research/code/boost_1_34_1/stage/lib/libboost_thread-gcc34-mt.a: not found

I DO have the library in that location.

---

### Post by aks44 on 2007-11-20
> **Rij said:**
> g++ -I/home/research/code/boost_1_34_1 -L /home/research/code/boost_1_34_1/stage/lib/libboost_thread-gcc34-mt.a main.cc

-L should be a path (directory), use -l (lower-case L) to specify the library name (without "lib" prefix and without ".a"/".so" postfix).


If I'm not mistaken, this should work:

```
g++ -I/home/research/code/boost_1_34_1 -L/home/research/code/boost_1_34_1/stage/lib/ -lboost_thread-gcc34-mt main.cc
```

---

### Post by iharrold on 2007-11-20
Are you sure you have the library?  Here's the install help from boost.

[http://www.boost.org/more/getting_started/unix-variants.html](http://www.boost.org/more/getting_started/unix-variants.html)

---

### Post by Rij on 2007-11-20
> **aks44 said:**
> 
If I'm not mistaken, this should work:

```
g++ -I/home/research/code/boost_1_34_1 -L/home/research/code/boost_1_34_1/stage/lib/ -lboost_thread-gcc34-mt main.cc
```

I tried that. Now it finds the libraries, but still throws the same error: undefined symbol ... blah ... blah ... blah

Incidentally, there seems to be a mismatch between my g++ and ld. 
/usr/ccs/bin/ld
/opt/gcc-3.4.1/bin/g++

Can that be an issue?

---

### Post by Rij on 2007-11-20
> **iharrold said:**
> Are you sure you have the library?  Here's the install help from boost.

[http://www.boost.org/more/getting_started/unix-variants.html](http://www.boost.org/more/getting_started/unix-variants.html)

I do have the library. If you see my first message, I listed the libraries that I have. Is there any missing?

---

### Post by aks44 on 2007-11-20
> **Rij said:**
> I tried that. Now it finds the libraries, but still throws the same error: undefined symbol ... blah ... blah ... blah

Did you try linking (-l switch, lower-case L) with other libraries than **boost_thread-gcc34-mt**, and/or linking with several of them at the same time?

What comes to my mind is:
- both **boost_thread-gcc34-mt-d-1_34_1** and **boost_thread-gcc34-mt-d** if you're building a debug binary, or
- both **boost_thread-gcc34-mt-1_34_1** and **boost_thread-gcc34-mt** if you're building a release binary


Not sure this helps though... linking to **boost_thread-*** should *theoretically* have gotten rid of boost::thread* missing references, even though it may have given new missing references.
As it seems this is not the case, so maybe we're just heading the wrong way?


> **Rij said:**
> Incidentally, there seems to be a mismatch between my g++ and ld. 
/usr/ccs/bin/ld
/opt/gcc-3.4.1/bin/g++

Can that be an issue?
Now I must admit, I have not the slightest clue about that. :oops:

---

### Post by dwhitney67 on 2007-11-20
I've looked into the program you wrote, and it works on my system, however that system is Fedora 8; not the SunOS (Solaris) that you are using.

I compiled using this statement:

```
g++ SimpleThread.cpp -L/usr/lib -lboost_thread-mt -o simple
```

Of course, on Fedora, the boost libraries are installed in /usr/lib, thus I do not have to specifically provide the -L option above, but nevertheless I did so for the OP's benefit.

By the way, I have this version of Boost:  1.34.1-5.fc8.i386.  It would appear that the OP has a very similar version.  And I am running gcc-4.1.2.

---

### Post by mdwhite76 on 2009-03-13
Hello, I'm getting the following error when I'm attempting to build my project.  I'm using eclipse on linux.  

/usr/includ/boost/date_time/date_parsing.hpp undefined refenrece to 'boost::gregorian::greg_month::get_month_map_ptr()'

I have the following included:
#include <boost/date_time/posix_time/posix_time.hpp>
using namespace boost::posix_time;

Any help would be appreciated..

---

### Post by dwhitney67 on 2009-03-13
I need to see your code, and also what library (or libraries) you are specifying on the command line when invoking g++.

P.S.  Did you link with '-lboost_date_time'??

---

### Post by moma on 2009-03-13
Hello,

Study the **Examples 1 and 2** of this thread: 
[http://ubuntuforums.org/showthread.php?p=5164645#post5164645](http://ubuntuforums.org/showthread.php?p=5164645#post5164645)

It should work on Linux. Do not know about SunOS.
---
ps. I will release version 0.2 of [Gscreendump...]("http://linux1.no/blogg/moma/3632/utrolig-video-om-gscreendump-v02") tomorrow 14.th mars.2009 (or 15.th if problems occur). It is amazing! Look for announcement on Ubuntuforums.org.

[COLOR="Red"]EDIT:[/COLOR] Gscreendump v0.2 is now ready.
Read [http://ubuntuforums.org/showthread.php?t=1096860](http://ubuntuforums.org/showthread.php?t=1096860)

---

