---
title: "Is my c++ code following good practise ?"
date: 2009-10-11
forum: Programming Talk
---

### Post by ShaolinF on 2009-10-11
Hi Guys,

I am working on a c++ project and need to know whether what I am doing is good or bad practise. 
My questions followed by the code:

1. I have included myThread.cc into the project.cc file. I was told that its good practise ONLY to include headers and not other .cc files. Is this true ?

2. What are the name standards for c++ ? In java when creating a new class the first letter must be capitalise (of the filename) and the same for the class e.g. class is called MyClass.java and the class begins Class MyClass { .. } - Is this the same for Java ?


```
// project.cc
#include <iostream>
#include "myThread.cc"

using namespace std;

int main(int argc, char* argv[])
{
	// do something
}
```

```
//myThread.cc
#include "fileThread.h"

using namespace std;

MyThread::MyThread() {
	// do something
}

MyThread::find() {
	// do something
}

MyThread::print() {
	// do something
}
```

```
//myThread.h
#ifndef _myThread_h_included_
#define _myThread_h_included_

#include <iostream>
using namespace std;

class MyThread
{
	private:
	string filename;
	string searchstr;

	public:
	MyThread();
	void find();
	void print();
};
#endif
```

---

### Post by Tony Flury on 2009-10-12
> **ShaolinF said:**
> Hi Guys,

I am working on a c++ project and need to know whether what I am doing is good or bad practise. 
My questions followed by the code:

1. I have included myThread.cc into the project.cc file. I was told that its good practise ONLY to include headers and not other .cc files. Is this true ?

You are correct, it is not considered good practice to include a ".cc" file into another ".cc" file - make the linker do the work to reconcile the links between the compiled ".cc" files.

> 
2. What are the name standards for c++ ? In java when creating a new class the first letter must be capitalise (of the filename) and the same for the class e.g. class is called MyClass.java and the class begins Class MyClass { .. } - Is this the same for Java ?

To the best of my knowledge, there are no Standards for c++, unless the project you are working on imposes them - you could define class "a" in file "b.cc" and define class "b" in file "a.cc" and the compiler wont stop you - common sense will though. If you are comfortable with the Java naming convention then continue to use it.

---

### Post by Bad Sector on 2009-10-12
1. Yes it is true, but nobody will come out and hit you if you do so :-P. What you are doing is giving to the compiler both source code files as a single source file. In practice the difference is mostly that it takes longer for the compiler to compile your code and everything will be recompiled if you modify a single file. Given how slow G++ is, you probably want to split your code to several files and let the linker do the linking job :-P.

2. There aren't really any "C++ naming standards" but most people use names LikeThis or likeThis (some also use names like_this, but these are usually found in C code). The Java naming is used a lot (and this is what i use in my own C++ code) so if you know that, use that.

---

### Post by lisati on 2009-10-12
As others have said, it's sometimes easier to compile files separately rather than include them. As for naming conventions go, my $0.02 is that unless you have reason to do otherwise avoid using the same name for your own routine as one which comes with the programming environment you're using.

---

### Post by hessiess on 2009-10-12
Regarding naming conventions, it does not matter as long as you stick with one throughout the code:)

---

### Post by jespdj on 2009-10-12
Have a look at the [Google C++ Style Guide](http://google-styleguide.googlecode.com/svn/trunk/cppguide.xml).

---

### Post by dwhitney67 on 2009-10-12
Programming "good practices" many times weigh down to programming "preferences".

A few things I noted in your code of which _I_ consider bad programming practice are 1) the inclusion of unnecessary header files in a particular .h or .cpp module, 2) the usage of a "using namespace" directive in a header file, and finally 3) including project header files *after* system header files.

Not everyone shares my opinion with respect to the last item.  I've worked on a project once where everything compiled great.  However, one day, when cleaning up a particular header file of unnecessary #include statements, everything became unglued.  Apparently many modules did not include all of the header file(s) necessary to make themselves standalone/compilable modules, and were heavily dependent on another header to do that.

Anyhow, what looked like a trivial cleanup exercise took hours to fix.  So my stance is to include local header files first, then project header files, followed by system header files.

See other notes in the code below...
```

//myThread.h
#ifndef _myThread_h_included_
#define _myThread_h_included_

#include <iostream>     <---- Not needed!
using namespace std;    <---- Never do this in a header file

class MyThread
{
...

```
```

// project.cc
#include <iostream>
#include "myThread.cc"   // as discussed earlier, this should be a .h file
                         // this file should also be included before <iostream>

...

```

---

### Post by ShaolinF on 2009-10-12
Thanks guys! Great responses.

> You are correct, it is not considered good practice to include a ".cc" file into another ".cc" file - make the linker do the work to reconcile the links between the compiled ".cc" filesHow do I do this ?


[QUOTE=dwhitney67]2) the usage of a "using namespace" directive in a header file[/QUOTE]The thing is I have some string variables in my header file and they won't compile unless I either specify std::string or use the using namespace std; derective. What should I do ?


EDIT: How would I define a vector in a header file ? I was reading up on this and it looks like I need to use typedef e.g

```

//MyClass.h
#include <vector>;
typedef std::vector<std::string> StrVector;

class MyClass {
     private:
     StrVector MyVector;
}
```

Why cant I do something like:

```

//MyClass.h
#include <vector>;

class MyClass {
     private:
     std::vector<std::string> MyVector;
}
```

---

### Post by dwhitney67 on 2009-10-12
As I stated earlier, it is bad practise to use the "using namespace" directive in a header file.  Thus in the example code you provided, you are correct in that the only remaining alternative is to specify the scope operator, or std::.

Using a typedef is not required, although for some, it can make code more readable, and for obvious reasons, require less typing at the keyboard when coding.

The reason why your example code, without the typedef, failed to compile is that you neglected to include <string>.

The proper code would look like:
```

#ifndef MYCLASS_H   // to prevent multiple inclusion of this header file within the same module
#define MYCLASS_H

//MyClass.h

#include <vector>    // a semi-colon is not required
#include <string>

class MyClass
{
private:
     std::vector<std::string> MyVector;
};   // added missing semi-colon

#endif

```

---

### Post by ShaolinF on 2009-10-12
Thanks dwhitney67 for the informative reply.

I have removed #include myThread.cc from the project.cc file and instead placed myThread.h in its place - This has resulted in compile errors. See error msg followed by src code:

```
/usr/include/c++/4.3/bits/stl_vector.h: In destructor &#8216;std::_Vector_base<_Tp, _Alloc>::~_Vector_base() [with _Tp = Word, _Alloc = std::allocator<Word>]&#8217;:
/usr/include/c++/4.3/bits/stl_vector.h:301:   instantiated from &#8216;std::vector<_Tp, _Alloc>::~vector() [with _Tp = Word, _Alloc = std::allocator<Word>]&#8217;
myThread.h:17:   instantiated from here
/usr/include/c++/4.3/bits/stl_vector.h:136: error: invalid use of incomplete type &#8216;struct Word&#8217;
myThread.h:13: error: forward declaration of &#8216;struct Word&#8217;
/usr/include/c++/4.3/bits/stl_construct.h: In function &#8216;void std::_Destroy(_ForwardIterator, _ForwardIterator) [with _ForwardIterator = Word*]&#8217;:
/usr/include/c++/4.3/bits/stl_construct.h:128:   instantiated from &#8216;void std::_Destroy(_ForwardIterator, _ForwardIterator, std::allocator<_T2>&) [with _ForwardIterator = Word*, _Tp = Word]&#8217;
/usr/include/c++/4.3/bits/stl_vector.h:300:   instantiated from &#8216;std::vector<_Tp, _Alloc>::~vector() [with _Tp = Word, _Alloc = std::allocator<Word>]&#8217;
myThread.h:17:   instantiated from here
/usr/include/c++/4.3/bits/stl_construct.h:102: error: cannot increment a pointer to incomplete type &#8216;Word&#8217;
/usr/include/c++/4.3/bits/stl_construct.h: In function &#8216;void std::_Destroy(_Tp*) [with _Tp = Word]&#8217;:
/usr/include/c++/4.3/bits/stl_construct.h:103:   instantiated from &#8216;void std::_Destroy(_ForwardIterator, _ForwardIterator) [with _ForwardIterator = Word*]&#8217;
/usr/include/c++/4.3/bits/stl_construct.h:128:   instantiated from &#8216;void std::_Destroy(_ForwardIterator, _ForwardIterator, std::allocator<_T2>&) [with _ForwardIterator = Word*, _Tp = Word]&#8217;
/usr/include/c++/4.3/bits/stl_vector.h:300:   instantiated from &#8216;std::vector<_Tp, _Alloc>::~vector() [with _Tp = Word, _Alloc = std::allocator<Word>]&#8217;
myThread.h:17:   instantiated from here
/usr/include/c++/4.3/bits/stl_construct.h:88: error: invalid use of incomplete type &#8216;struct Word&#8217;
myThread.h:13: error: forward declaration of &#8216;struct Word&#8217;
shaid@shaid-desktop:~/Desktop/filereader/src$ 
```

The lines which are causing the error:

```
Line 13 of myThread.h: struct Word;
line 17 of myThread.h: std::vector<Word> words;
```

The full src:

```
//myThread.h
#ifndef _myThread_h_included_
#define _myThread_h_included_

#include <string>
#include <vector>

struct Word;

class MyThread
{
	private:
	std::string filename;
	std::string searchstr;
        std::vector<Word> words;

	public:
	MyThread();
	void find();
	void print();
};
#endif

```

---

### Post by MadCow108 on 2009-10-12
struct Word;
is not enough for the vector of Word
the vector needs the complete definition of the struct Word
(indicated by this error message: /usr/include/c++/4.3/bits/stl_vector.h:136: error: invalid use of incomplete type &#8216;struct Word&#8217;)

either you define it completely in Thread.h or you include the header there Word is defined in Thread.h
the latter is probably better style because Word is probably a class that can be used separately from the MyThread Class
If this is not the case then Word should probably be a local class of MyThread

---

### Post by ShaolinF on 2009-10-12
Thanks MadCow.
Ok, so a new problem has popped up now that I try to compile the whole project. Error message followed by src:

```
project.cc:(main(int argc, char* argv[])]): undefined reference to `MyThread::print()'
collect2: ld returned 1 exit status
```

```
//project.cc
#include "myThread.h"

int main(int argc, char* argv[])
{
		MyThread object;
		object.print();
}
```

```
//myThread.h
#ifndef _myThread_h_included_
#define _myThread_h_included_

#include <string>
#include <vector>

struct Word {
        int x;
        string y;
}

class MyThread
{
	private:
	std::string filename;
	std::string searchstr;
        std::vector<Word> words;

	public:
	MyThread();
	void find();
	void print();
};
#endif

```


```

// myThread.cc
#include "myThread.h"
#include <iostream>

void MyThread::print()
{
	cout << "print data" << endl;
}
```

---

### Post by MadCow108 on 2009-10-12
you can compile each of your files (project.cc and myThread.cc) on its own now
now you have to link them together to form a program.
This compiles and links your files:
```

g++ project.cc myThread.cc -o myprogram

```

this is actually a shortcut for following:
```

#compile myThread (with -c)
g++ -c myThread.cc -o myThread.o
#compile project
g++ -c project.cc -o project.o
#link the to object files together
g++ project.o myThread.o -o myprogram

```

as your program gets bigger you should use Makefiles to simplify the compile/linking
[http://www.gnu.org/software/make/manual/make.html](http://www.gnu.org/software/make/manual/make.html)

or even autotools/cmake for platform independent builds:
[http://sourceware.org/autobook/autobook/autobook_toc.html](http://sourceware.org/autobook/autobook/autobook_toc.html)
[http://www.cmake.org/](http://www.cmake.org/)

---

### Post by ShaolinF on 2009-10-12
Thanks MadCow, its working now. I am using a makefile to compile my app. See below:

```

#makefile
all:
	g++ -c myThread.cc -o myThread.o
	g++ -I /usr/local/boost_1_39_0 project.cc myThread.o -o fr /usr/local/boost_1_39_0/boost/stage/lib/libboost_thread-gcc43-mt-1_39.a -lpthread /usr/local/boost_1_39_0/boost/stage/lib/libboost_program_options-gcc43-mt-1_39.a
```

I am using boost for multithreading and commandline args. As you can see, the dirs to the boost header files are hardcoded into the makefile. There are two problems here:

1. If another user compiles this and his boost dir isn't the same as the one specified then it wont compile. He will need to alter the makefile to make it work.

2. It isn't very portable since if someone wants to compile the app from source they will need to install the boost library.

What would be the best approach to rectify the two listed problems ?

---

### Post by grayrainbow on 2009-10-12
> Not everyone shares my opinion with respect to the last item. I've worked on a project once where everything compiled great. However, one day, when cleaning up a particular header file of unnecessary #include statements, everything became unglued. Apparently many modules did not include all of the header file(s) necessary to make themselves standalone/compilable modules, and were heavily dependent on another header to do that.

I'll suggest you next time to use precompiled header for system includes :)
 
 
> 1. If another user compiles this and his boost dir isn't the same as the one specified then it wont compile. He will need to alter the makefile to make it work.

2. It isn't very portable since if someone wants to compile the app from source they will need to install the boost library.

You can try using make variables, like:
BOOST_DIR=/boost/instal/dir
make readme where you explain about it, and how user can change it.
But in general...much better to use an IDE

---

### Post by ShaolinF on 2009-10-12
Thanks.

One more question:

Whats the difference between #include <myfile.h> and #include "myfile.h" ?

---

### Post by MadCow108 on 2009-10-13
the difference is where the compiler searches for the headers
<> means search in default include path + include paths provided as compiler flags
"" means search directory where the code is and only if nothing is found search where <> searches

this allows headers with the same name as system headers in your project directory without conflicts (given you use <> and "" correctly)

---

