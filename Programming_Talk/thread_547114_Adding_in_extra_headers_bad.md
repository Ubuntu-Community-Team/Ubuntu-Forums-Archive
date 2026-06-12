---
title: "Adding in extra headers bad?"
date: 2007-09-09
forum: Programming Talk
---

### Post by happysmileman on 2007-09-09
I just started to learn QT (doing quite well, considering how boring I found WinAPI and wxWidgets).

I have a question. My files all begin with something like

```
#include <QApplication>
#include <QWidget>
#include <QVBoxLayout>
#include <QFont>
#include <QPushButton>
#include <QLCDNumber>
#include <QSlider>
```

What i want to know is if I don't need "<QSlider>" but keep it in anyway, including an extra header, what effect will that have:

On compilation time?
On File Size?
On program speed?
On debugging?

I know I'll obviously take the unneeded ones out anyway, but how bad is it to keep them in if I forget or something

---

### Post by -Rick- on 2007-09-09
AFAIK, it only adds compile time. Object files (.o) will also be bigger, but this is optimized away in your binary.

---

### Post by gnusci on 2007-09-09
On compilation time? [COLOR="Red"]Yes, it will take more time to compile it.[/COLOR]

On File Size? [COLOR="Red"]Yes, it will increase the final size of your binary (in debugging mode).[/COLOR]

On program speed? [COLOR="Red"]No, it does no change to program performance, it is just a piece of program that will be never used.[/COLOR]

On debugging? [COLOR="Red"]Yes, it will take more time during debugging.[/COLOR]

---

### Post by aks44 on 2007-09-09
> **gnusci said:**
> On File Size? [COLOR="Red"]Yes, it will increase the final size of your binary.[/COLOR]

Only if the code is compiled for debug (in which case additional debug symbols are stored) AND the compiler stores debug symbols inside the binary itself (which g++ does BTW).

For release builds, there won't be a single byte of overhead.


IOW it only affects you because of the increased build time (increased debug time is technically true but totally negligible). The size of the debug builds is kinda irrelevant since that's not what users will get in the end.

---

### Post by dwhitney67 on 2007-09-10
The previous post are correct:  you will experience slower compilation times, the binary size will not be affected, etc.

The bottom line though is that it's bad programming practice to include header files that are not used.

The other practice that is overlooked by many developers is the ordering of the header files.  Local (project) header files should be included first, followed by header files for tools (e.g. Qt), then followed by system include files.

If one of your project header files cannot compile because of the ordering rules described above, then your header file has a deficiency that needs to be corrected.  Shuffling the ordering of the header files to satisfy a deficiency is _not_ the answer.

---

### Post by the_unforgiven on 2007-09-10
> **dwhitney67 said:**
> The previous post are correct:  you will experience slower compilation times, the binary size will not be affected, etc.

The bottom line though is that it's bad programming practice to include header files that are not used.

The other practice that is overlooked by many developers is the ordering of the header files.  Local (project) header files should be included first, followed by header files for tools (e.g. Qt), then followed by system include files.

If one of your project header files cannot compile because of the ordering rules described above, then your header file has a deficiency that needs to be corrected.  Shuffling the ordering of the header files to satisfy a deficiency is _not_ the answer.
I think the general practice is to try and make this dependency as minimal as possible - i.e. the sequence in which the headers are included should not matter - that should be the aim while writing the headers.

Also, I have never read anything that states that the practice is to include local headers before system headers. On the contrary, almost all the renowned books include system headers before local ones (from the top of my head, I know for sure about W. Richard Stevens' "Advanced programming in UNIX environment" - I'm referring to it for some work.)

Can you please point out where this best-practice is described?

Thank you.

To the OP, as aks44 said, the only overhead will be slower compile times, but the binary should not be bloated at all - the headers should only include the declarations of classes/methods/functions and if they're not actually used (e.g. a class not instantiated or a function not called) then there is no reason for the corresponding code to be generated.

---

### Post by aks44 on 2007-09-10
Regarding header inclusions, the only best practice I can think of is to migrate as many as possible #includes from headers to source files, to reduce dependencies. Use forward declarations whenever you can, instead of #including in a header.

Ever dealed with that almighty header that ends up included in almost every single other header, and that makes your whole project being fully recompiled because you just made a trivial change in it (eg. adding a comment)? ;)

---

### Post by the_unforgiven on 2007-09-10
> **aks44 said:**
> Regarding header inclusions, the only best practice I can think of is to migrate as many as possible #includes from headers to source files, to reduce dependencies. Use forward declarations whenever you can, instead of #including in a header.
Indeed.. very true.
> **aks44 said:**
> Ever dealed with that almighty header that ends up included in almost every single other header, and that makes your whole project being fully recompiled because you just made a trivial change in it (eg. adding a comment)? ;)
Many a times - while starting to code moderately large/complex projects (anything more than college assignments would qualify :p) :D
Unfortunately, nobody taught us how to write headers - learnt it the hard way :(.

---

### Post by dwhitney67 on 2007-09-10
> **the_unforgiven said:**
> 
Also, I have never read anything that states that the practice is to include local headers before system headers. On the contrary, almost all the renowned books include system headers before local ones (from the top of my head, I know for sure about W. Richard Stevens' "Advanced programming in UNIX environment" - I'm referring to it for some work.)

Can you please point out where this best-practice is described?

Thank you.
I can't quote you a book title.  And I for one am not an author.  However my personal experience has taught me that the ordering of header files is relevant.  The books you have read probably never covered the subject because either they were demonstrating simple applications or the authors didn't have experience working in large projects with many collaborators.

I've seen countless times where naive (inexperience) software developers would include more into their header files than is needed.  Some advanced developers also do the same on occasion.

So here's an example:

```
#ifndef FILE1_H
#define FILE1_H

#include <string>
#include <iostream>
using namespace std;

class File1
{
  public:
    File1( int value ) : val( value ) {}

    void printValue() const { cout << "val = " << val << endl; }

  private:
    int value;
};

#endif

```

Then another collaborator comes along and writes this file:

```
#ifndef FILE2_H
#define FILE2_H

class File2
{
  public:
    File2( const string& str ) : strValue( str ) {}
    string getString() const { return strValue; }
  private:
    string strValue;
};
#endif
```

Then something like this for File2.cpp:

```
#include "File1.h"
#include "File2.h"

int main( int argc, char** argv )
{
...
}
```

Everything compiles fine, right?  Yep, up until the point where a Peer Review is held on File1.h and someone points out that 1) there is no need to include <string>, and 2) that a "using namespace std" should _never_ be inserted into a header file.

Later File1.h is corrected... and then all of the sudden File2.cpp (and File2.h) doesn't compile, along with perhaps hundreds of other files, depending on how far down the road is the project.

The moral of this example is to ensure that 1) unnecessary components are not included in a header file (which is difficult to enforce because people make mistakes or change designs), and 2) always declare header files in the proper order.

Had File2.h been included before File1.h in the above example implementation for File2.cpp, then deficiencies within File2.h would have been caught from the first time it was compiled.  Instead its deficiencies weren't caught until a later stage in the project. 

Anyhow, don't put too much stock in the examples included in text books.  These are generally simple examples, sometimes ranging from a few lines of code to perhaps 500.  Think of a project that has 500,000 lines of code and 100 software developers (at any given time) writing code.

I will refrain from adding comments concerning "book writers", but suffice to say not all of them have real-world experience.

---

### Post by happysmileman on 2007-09-10
In QT (if any of you know) how do I stop things being included more than once. For example I currently have:
```

#include "b.h"
#include "slidewidget.h"

#include <QApplication>
#include <QGridLayout>
...

```

Where both "b.h" and "slidewidget.h" apparently need to have <QWidget> for signals and slots to work.

Would a forward declaration work, or do i just have to include it in both and hope for the best?

And some examples/tutorials on this would be incredibly useful, but I doubt anyone ever goes into much detail about headers

ALSO: The QT tutorial puts local header files after the QT ones, what's up with this, anyone know of a way they're SUPPOSED to be included or is it just dependent on circumstances?

---

### Post by dwhitney67 on 2007-09-10
> **happysmileman said:**
> In QT (if any of you know) how do I stop things being included more than once. For example I currently have:
```

#include "b.h"
#include "slidewidget.h"

#include <QApplication>
#include <QGridLayout>
...

```

Where both "b.h" and "slidewidget.h" apparently need to have <QWidget> for signals and slots to work.

Would a forward declaration work, or do i just have to include it in both and hope for the best?

And some examples/tutorials on this would be incredibly useful, but I doubt anyone ever goes into much detail about headers

Within the header files you develop, you should add the multiple-inclusion guards.  For example:

```
#ifndef B_H
#define B_H
#include <Qwidget>
...
#endif
```

and
```
#ifndef SLIDEWIDGET_H
#define SLIDEWIDGET_H
#include <Qwidget>
...
#endif
```

You can rest assured that the folks at TrollTech did the same within their Qt header files.  Thus you do not have to worry about their header files being "included" twice in a similar chain like you described.

---

### Post by happysmileman on 2007-09-10
> **dwhitney67 said:**
> Within the header files you develop, you should add the multiple-inclusion guards.  For example:

```
#ifndef B_H
#define B_H
#include <Qwidget>
...
#endif
```

and
```
#ifndef SLIDEWIDGET_H
#define SLIDEWIDGET_H
#include <Qwidget>
...
#endif
```

You can rest assured that the folks at TrollTech did the same within their Qt header files.  Thus you do not have to worry about their header files being "included" twice in a similar chain like you described.

Thanks, I'm assuming it's ok to "#include <QWidget>" in every header (since it gives errors if you don't), and I do include inclusion guards

---

### Post by the_unforgiven on 2007-09-11
> **dwhitney67 said:**
> I can't quote you a book title.  And I for one am not an author.  However my personal experience has taught me that the ordering of header files is relevant.  The books you have read probably never covered the subject because either they were demonstrating simple applications or the authors didn't have experience working in large projects with many collaborators.

I've seen countless times where naive (inexperience) software developers would include more into their header files than is needed.  Some advanced developers also do the same on occasion.

So here's an example:

```
#ifndef FILE1_H
#define FILE1_H

#include <string>
#include <iostream>
using namespace std;

class File1
{
  public:
    File1( int value ) : val( value ) {}

    void printValue() const { cout << "val = " << val << endl; }

  private:
    int value;
};

#endif

```

Then another collaborator comes along and writes this file:

```
#ifndef FILE2_H
#define FILE2_H

class File2
{
  public:
    File2( const string& str ) : strValue( str ) {}
    string getString() const { return strValue; }
  private:
    string strValue;
};
#endif
```

Then something like this for File2.cpp:

```
#include "File1.h"
#include "File2.h"

int main( int argc, char** argv )
{
...
}
```

Everything compiles fine, right?  Yep, up until the point where a Peer Review is held on File1.h and someone points out that 1) there is no need to include <string>, and 2) that a "using namespace std" should _never_ be inserted into a header file.

Later File1.h is corrected... and then all of the sudden File2.cpp (and File2.h) doesn't compile, along with perhaps hundreds of other files, depending on how far down the road is the project.

The moral of this example is to ensure that 1) unnecessary components are not included in a header file (which is difficult to enforce because people make mistakes or change designs), and 2) always declare header files in the proper order.

Had File2.h been included before File1.h in the above example implementation for File2.cpp, then deficiencies within File2.h would have been caught from the first time it was compiled.  Instead its deficiencies weren't caught until a later stage in the project. 

Anyhow, don't put too much stock in the examples included in text books.  These are generally simple examples, sometimes ranging from a few lines of code to perhaps 500.  Think of a project that has 500,000 lines of code and 100 software developers (at any given time) writing code.

I will refrain from adding comments concerning "book writers", but suffice to say not all of them have real-world experience.

As far as the example you've shown here, that's exactly what I was saying - minimize the dependencies between the headers - that should be your goal. 

Also, including a properly-written header twice doesn't have much of a problem - it simply is ignored by the preprocessor if it's already included. That's what the include guards are for (or **#pragma once**)

So, in your example, the right way would be to #include <string> in file2.h where the string class is really needed instead of file1.h and I prefer NOT to use "using namespace.." construct anywhere - even in .cpp files to avoid pollution of the global namespace.

At times, you cannot just use forward declarations - especially when you're using references because the compiler REQUIRES the complete class definition to be seen to construct the ref. You can use forward declarations when you use pointers where only the existence of the type is sufficient.

So, if we were to adhere to your example, I'd say the devs/reviewers don't know how to write the headers properly and shouldn't be given responsibilities to define the interfaces at all - they'll invariably end up messing the whole thing.

As far as book authors and their authorities are concerned, if you doubt the experience of the likes of K&R and W. Richard Stevens, man, I really don't know what to say.

I think I should stop here.

---

### Post by aks44 on 2007-09-11
> **the_unforgiven said:**
> At times, you cannot just use forward declarations - especially when you're using references because the compiler REQUIRES the complete class definition to be seen to construct the ref.

Sorry, but this is plain wrong. The following code is perfectly valid:

```
/*--- Bar.h ---*/
class Foo;

class Bar
{
private:
  Foo& m_foo;
public:
  inline Bar(Foo& theFoo) : m_foo(theFoo) {};
  void goFoo();
};

/*--- Bar.cpp ---*/
#include "Bar.h"
#include "Foo.h" // Now you need it for doFoo()

void Bar::goFoo()
{
  m_foo.go();
}
```

WRT forward declarations, references work exactly like pointers.


That apart, I agree with the rest of your post.



> **dwhitney67 said:**
> Think of a project that has 500,000 lines of code and 100 software developers (at any given time) writing code.

100 developpers for 500 kloc? :shock: Better make it 2 to 5 mloc... ;)

---

### Post by the_unforgiven on 2007-09-13
> **aks44 said:**
> Sorry, but this is plain wrong. The following code is perfectly valid:

```
/*--- Bar.h ---*/
class Foo;

class Bar
{
private:
  Foo& m_foo;
public:
  inline Bar(Foo& theFoo) : m_foo(theFoo) {};
  void goFoo();
};

/*--- Bar.cpp ---*/
#include "Bar.h"
#include "Foo.h" // Now you need it for doFoo()

void Bar::goFoo()
{
  m_foo.go();
}
```

WRT forward declarations, references work exactly like pointers.

Yeah, you're right. Don't know what was I thinking when I wrote that :(
My bad :(
Thanks for correcting me ;)

---

