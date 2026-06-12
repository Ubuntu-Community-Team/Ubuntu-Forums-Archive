---
title: "[SOLVED] How to install TBB in Ubuntu"
date: 2008-02-05
forum: Programming Talk
---

### Post by leileicats on 2008-02-05
Hi, I'm a novice to Linux and TBB. I am asking help for how to build TBB in Ubutu.
I have already downloaded the source file: tbb20_20070927oss_src. And then I enter the directory and 'make': ~/tbb20_20070927oss_src/$ make

After running a bunch of stuff, I still can't compile TBB sample code.
My sample code:
#include "tbb/task_scheduler_init.h"

using namespace tbb;

int main() {
    task_scheduler_init init;
    return 0;
}

When I's using g++ compile, it shows:
/tmp/cccwYHds.o: In function `tbb::task_scheduler_init::task_scheduler_init(int)':
tbbtext.cpp:(.text._ZN3tbb19task_scheduler_initC1Ei[tbb::task_scheduler_init::task_scheduler_init(int)]+0x28): undefined reference to `tbb::task_scheduler_init::initialize(int)'
/tmp/cccwYHds.o: In function `tbb::task_scheduler_init::~task_scheduler_init()':
tbbtext.cpp:(.text._ZN3tbb19task_scheduler_initD1Ev[tbb::task_scheduler_init::~task_scheduler_init()]+0x16): undefined reference to `tbb::task_scheduler_init::terminate()'
collect2: ld returned 1 exit status

I guess I failed to install TBB on my machine. Could anyone give some help?

---

### Post by aks44 on 2008-02-05
Looks like it's a linking problem. Check the -L and -l (lowercase L) flags of g++.

Your command line should look like:

g++ tesp.cpp -o test -L*/path/to/the/relevant/library/* -l*nameoflib*

where **nameoflib** would be eg. **tbb** if the actual shared library is named **libtbb.so**

---

### Post by leileicats on 2008-02-05
Thanks for your informatioin.
1)
The share library is in the directory **~/lib/libtbb.so**. TSo my command line:
**g++ tbb.cpp -o tbb -L/lib/ -ltbb**
And it works!!!

2)
I also install the tbb package ( a bunch of .deb files ). I could find the file **tbb**(there are a bunch of *.h files) in the directory as **/usr/include/tbb** which is the same as my boost libraries **/usr/include/boost**.

But now the question is:
When I am using boost libraries, 
#include "boost/dynamic_bitset.hpp"

int main() {
	boost::dynamic_bitset<> bitsetting;
	return 0;
}

the command line as: **$ g++ -o test test.cpp**. There is no error.

However when I am using TBB libraries,

#include <tbb/task_scheduler_init.h>

int main() {
	tbb::task_scheduler_init init;
	return 0;
}

It will pop out those errors when I am using **$ g++ -o test test.cpp**. I don't know why?
The only difference is that I install the boost libraries through Synaptic Package Manager, but as to the TBB libraries, I am using **dpkg --install ***tbb**.deb** to install TBB libraries. Should I modify some enviromental settings?

---

### Post by aks44 on 2008-02-05
That's not a problem of how you install the .debs (in fine, even synaptic, aptitude and apt-get all boil down to dpkg calls).

IMHO the problem is in the contents of the .debs: the boost package probably is of better quality (as far as Ubuntu integration goes) than the TBB one.

---

### Post by leileicats on 2008-02-05
It seems that TBB is a runtime library. Does it mean that I could only link to the shared library during execution? And the boost library is portable library.

---

### Post by aks44 on 2008-02-06
More on that (it just popped into my mind)...

Most of the boost library, just like the STL, consists of templates & macros, which are defined in headers and need no linking (since they get inlined into your own code).

On the contrary, TBB (whatever this library is) is more of a "classic" library, ie. the code resides in a shared library (libtbb.so).

Now I'm pretty sure (although I didn't have the occasion to test it on Linux) that if you used the few parts of boost that are not inlined then you'd have the very same problem.


I hope this sheds some light on the topic. :)

---

