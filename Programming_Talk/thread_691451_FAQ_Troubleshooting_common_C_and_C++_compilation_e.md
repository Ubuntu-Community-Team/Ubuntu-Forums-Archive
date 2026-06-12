---
title: "FAQ: Troubleshooting common C and C++ compilation errors"
date: 2008-02-08
forum: Programming Talk
---

### Post by aks44 on 2008-02-08
You have problems compiling a C or C++ program? Here are the most common ones, and their solution...

This FAQ assumes you're trying to compile *error-free* code. To actually learn the C or C++ languages, see the [How to start programming](http://ubuntuforums.org/showthread.php?t=333867) thread.
If your problem is not covered here, please [post a new question](http://ubuntuforums.org/newthread.php?do=newthread&f=39).
Complete beginners may also want to read this thread: [Compiling your first C or C++ programs](http://ubuntuforums.org/showthread.php?t=689635).

**Important:** whenever command line examples are given, I'll use **gcc** (the C compiler) but if you're compiling C++ code you should use **g++** instead. The rest is identical for both languages.




[SIZE="5"]**0. Make sure the build-essential package is installed**[/SIZE]


[SIZE="3"]**Symptom: [COLOR="Blue"]stdio.h: No such file or directory.[/COLOR]**[/SIZE] (or any other **[COLOR="Blue"]standard[/COLOR]** header, eg. **[COLOR="Blue"]iostream[/COLOR]**)
**Cause:** the build-essential package is likely not to be installed.
**Solution:** install the build-essential package:
```
sudo apt-get install build-essential
```



[SIZE="3"]**Symptom: [COLOR="Blue"]installing the build-essential package yields an error.[/COLOR]**[/SIZE]
**Cause:** should not happen unless you screwed something up...
**Solution:** [did you mess with your sources.list](http://ubuntuforums.org/showthread.php?t=314578)?




[SIZE="5"]**1. Include problems**[/SIZE]


[SIZE="3"]**Symptom: [COLOR="Blue"]whateverThirdPartyHeader.h: No such file or directory.[/COLOR]**[/SIZE]
**Cause:** you didn't install the **-dev** package corresponding to the library you're trying to use.
**Solution:** search for the library's development package that ends with **-dev** and install it.
**Hint:** the tool **apt-file** may come in handy to find which **-dev** package a file belongs to.



[SIZE="3"]**Symptom: [COLOR="Blue"]I know that this include file is on my disk, but I still get the same error.[/COLOR]**[/SIZE]
**Cause:** the compiler doesn't know where to find that file.
**Solution:** use the **-I** (uppercase **i**) compiler flag to tell the compiler where the include file is located:
```
gcc main.cpp -o test -I/path/to/the/library/includes/
```
**Explanation:** **-I/path/to/the/library/includes/** (uppercase **i**) tells the compiler to look in **/path/to/the/library/includes/** (in addition to the default include search path) when it looks for a file included using angle brackets <>.
_Note:_ there can be several such switches on a command line.



[SIZE="3"]**Symptom: [COLOR="Blue"]I still get the same error despite previous advices.[/COLOR]**[/SIZE]
**Cause:** the compiler still can't find that file.
**Solution:** make sure you're using angle brackets to include it, rather than quotes:
```
#include <whateverThirdPartyHeader.h> // <...> NOT "..."
```
**Explanation:** angle brackets **<...>** tell the compiler to look for include files in every directory that is in the include path. When you use quotes **"..."** the compiler only looks in the directory where the compiled file resides.




[SIZE="5"]**2. Linking problems**[/SIZE]


[SIZE="3"]**Symptom: [COLOR="Blue"]undefined reference to 'function_prototype(whatever)'[/COLOR]**[/SIZE]
**Cause:** the compiler can't guess which library contains that function.
**Solution:** tell the compiler what library it should link your program against:
```
gcc main.cpp -o test -lfoo
```
**Explanation:** **-l[COLOR="Blue"]foo[/color]** (lowercase L) instructs the compiler to link your program against **lib[COLOR="Blue"]foo[/color].so**
_Note:_ there can be several such switches on a commmand line.



[SIZE="3"]**Symptom: [COLOR="Blue"]undefined reference to 'acos'[/COLOR]**[/SIZE] (or to any other function defined in **[COLOR="Blue"]math.h[/COLOR]**)
**Cause:** you must link your program against the math library.
**Solution:** use the **-lm** command line switch (lowercase L).
**Explanation:** [see Compyx's post]("http://ubuntuforums.org/showpost.php?p=4298292&postcount=6").



[SIZE="3"]**Symptom: [COLOR="Blue"]/usr/bin/ld: cannot find -lfoo[/COLOR]**[/SIZE]
**Cause:** looks like **lib[COLOR="Blue"]foo[/COLOR].so** is not in the compiler's library search path.
**Solution:** tell the compiler where this library is located:
```
gcc main.cpp -o test -L/path/to/the/library/ -lfoo
```
**Explanation:** **-L/path/to/the/library/** tells the compiler to look in **/path/to/the/library/** (in addition to the default library search path) when it looks for a library.
_Note:_ there can be several such switches on a command line.






Thanks to so many people @UF for their very useful help, this FAQ wouldn't be the same without them (you know who you are ;)).

---

### Post by Majorix on 2008-02-08
Looks nice!

I hope this gives birth to similar Python, Ruby, Perl and Java FAQs ;)

---

### Post by pmasiar on 2008-02-08
If you have nothing of substance to add, and want to thank aks44 for his excellent work, don't comment here. Comment just adds noise. Instead, **click on the little "medal" icon next to "Quote" button**, it adds aks44 thank without adding noise to thread. Thanks.

---

### Post by Compyx on 2008-02-09
Perhaps a few additions would be nice:

* The infamous -lm switch when using functions from <math.h>. And maybe a little note on why this behaviour is there in the first place.

* Sometimes when trying to resolve the 'no such file or directory: foo.h' problem, tools such as 'apt-file' might come in handy. And when running into a lot of these, 'apt-get build-dep'.

For example when I try to build 'vice' (the commodore 8-bit emulator suite), I could just try to look for all -dev packages I need. There are however a lot of these packages, so in this case I would run:
```

sudo apt-get build-dep vice

```
this trick may not always help, since the dependencies are those of the version in the repos, not the ones for the version you're trying to install.

* pkg-config is another invaluable tool for finding out the right switches to pass to the compiler and linker.


Any, nice stab at trying to get some decent information together :)

---

### Post by aks44 on 2008-02-09
> **Compyx said:**
> * The infamous -lm switch when using functions from <math.h>. And maybe a little note on why this behaviour is there in the first place.

Could you please expand on that? My knowledge of the GNU toolchain is still a bit limited (I've been seriously fiddling with it for less than a year, and never ran into this issue yet).


Thanks for the other suggestions, I'll be looking into them and update the FAQ ASAP. :)

---

### Post by Compyx on 2008-02-09
Historically, the math library didn't get linked in by default because of the limitations off the hardware of the time. Not linking in the math library parts in an executable reduces the size of such an executable and considering the limited memory and drive-space available at the time (early seventies) this was a 'good thing'.

These days, we have a little more memory and drive-space, but to be consistent with the old behaviour you still need to provide the '-lm' switch when using <math.h>. This at least holds true for gcc.

Some people consider the need to explicitly state '-lm' a bug, other consider it to be consistent with early behaviour. Doesn't matter much, we're stuck with it and have to deal with it. ;)

---

### Post by aks44 on 2008-02-10
@Compyx:

Regarding **apt-file**, **build-dep** and **pkg-config**: I have thought a bit about that, and I'd tend to say that's a bit too much of an advanced topic for a "common errors FAQ". TBH since I hang out here (about 10 months) I don't remember having seen questions on that topic (at least in "Programming Talk", perhaps more in "Packaging and Compiling Programs" where I don't go often?).

Maybe a separate FAQ along the lines of "Solving complex build dependencies" would be more appropriate? Just my 0.02.

---

### Post by amingv on 2008-03-03
I found this page half by chance. Decided to post it here since I didn't see it in the sticky; in case it can be of any use to anyone:
[http://www.cs.umbc.edu/courses/undergraduate/202/fall04/Projects/CommonErrors.shtml](http://www.cs.umbc.edu/courses/undergraduate/202/fall04/Projects/CommonErrors.shtml)

Compiler errors are often so cryptic, this page gives a brief description of some.

---

### Post by dwhitney67 on 2008-03-03
> **aks44 said:**
> 
[SIZE="3"]**Symptom: [COLOR="Blue"]I still get the same error despite previous advices.[/COLOR]**[/SIZE]
**Cause:** the compiler still can't find that file.
**Solution:** make sure you're using angle brackets to include it, rather than quotes:
```
#include <whateverThirdPartyHeader.h> // <...> NOT "..."
```
**Explanation:** angle brackets **<...>** tell the compiler to look for include files in every directory that is in the include path. When you use quotes **"..."** the compiler only looks in the directory where the compiled file resides.

Overall, I good post for all newbies.  However, I feel the need to clarify something...

The angle-brackets tell the compiler to search the standard system directories (e.g. /usr/include) for the location of the header file.  When opting to use the -I compiler flag to manually specify the location of header files, it does not matter if using the angle-brackets or double-quotes.  However, convention is to use the angle-brackets for system header files and the double-quotes for project header files.

When using double-quotes, you are correct in stating that only the current directory is searched, but when -I is used, then the additional paths are also searched.  When compiling, a de facto -I./ is included by default, along with the include paths of the standard system directories.

I tried compiling the program below, and I was successful in doing so (bear in mind that foo.h is in a directory called 'temp', which is a different directory than the source code that was compiled):

[PHP]#include "stdio.h"    // not done to convention, but still legal.
#include "foo.h"

int main() { return 0; }[/PHP]

The command used to compile was:
```
gcc myFile.c -Itemp
```

---

### Post by ruy_lopez on 2008-03-03
2. Linking Problems++

Occasionally, after installing a source lib dependency, the build process bitches about "shared libfoo.so error". Manually running "sudo ldconfig" updates the links.

---

### Post by Coos Yellowknife on 2008-03-10
Symptom: stdio.h: No such file or directory. (or any other standard header, eg. iostream)
Cause: the build-essential package is likely not to be installed.
Solution: install the build-essential package:
Code:

sudo apt-get install build-essential

Great info but where do I find this so I can install it? Not having these nothing will ever compile using gcc stdio.h is the most common #include 

Thank you for any help you can give on this

---

### Post by LaRoza on 2008-03-10
> **Coos Yellowknife said:**
> Symptom: stdio.h: No such file or directory. (or any other standard header, eg. iostream)
Cause: the build-essential package is likely not to be installed.
Solution: install the build-essential package:
Code:

sudo apt-get install build-essential

Great info but where do I find this so I can install it? Not having these nothing will ever compile using gcc stdio.h is the most common #include 

Thank you for any help you can give on this

Run the command...

The build-essential package is on the CD, so even without an internet connection you can installed it.

---

### Post by ruy_lopez on 2008-03-10
> **LaRoza said:**
> The build-essential package is on the CD

I've seen some comments reporting the package isn't on the CD. Are you sure it is on all CD's?

---

### Post by LaRoza on 2008-03-10
> **ruy_lopez said:**
> I've seen some comments reporting the package isn't on the CD. Are you sure it is on all CD's?

It has been on all disks I have used (Ubuntu Live + Ubuntu Alternative).

Even if it isn't on the disk, the poster seems to be connected to the internet.

---

### Post by ruy_lopez on 2008-03-10
> **LaRoza said:**
> Even if it isn't on the disk, the poster seems to be connected to the internet.

I don't mean any posts in this thread. I saw a post the other day. A guy needed build-essential to set up a dsl modem. He didn't have an internet connection.

---

### Post by LaRoza on 2008-03-10
> **ruy_lopez said:**
> I don't mean any posts in this thread. I saw a post the other day. A guy needed build-essential to set up a dsl modem. He didn't have an internet connection.

The CD may not have been listed as a repository, that can be changed in System->Administration->Software Sources.

---

### Post by ruy_lopez on 2008-03-10
> **LaRoza said:**
> The CD may not have been listed as a repository, that can be changed in System->Administration->Software Sources.

Whether or not the sources were setup correctly, I don't know. But the poster said they were.

That's why I asked if all the CD's have "build-essential". 

You are saying the same thing that I thought myself at the time. All the CD's *should* have "build-essential".

But, like you, I haven't tried them all.

---

### Post by jeneverboy on 2009-09-15
He

I am trying to compile a .cpp file, there is also a header file in it which I made myself. I was able to compile in windows. In ubuntu however I did this;

```
g++ main.cpp -o test
```

And get the following error:

```
/tmp/ccKxRBSO.o: In function `main':
main.cpp:(.text+0xb4): undefined reference to `Point::Point(double, double)'
collect2: ld returned 1 exit status

```

Can anybody tell me, what the proper way is of compiling .cpp files with headers in the same directory.

Thanks, Alex.

---

### Post by dwhitney67 on 2009-09-15
You are compiling just fine.  However your source code is missing the implementation for the Point object's constructor that accepts two double values.

Perhaps you implemented the constructor outside the class, but forgot to specify the scope operator?
```

**Point::**Point(double val1, double val2)
{
   // ...
}

```

P.S.  I assumed your class Point and its implementation are defined in main.cpp.  If this is not the case, then you need to compile the additional source code file and link it with main.cpp.  Something like:
```

g++ main.cpp Point.cpp -o myapp

```
Never name your executable "test"; there already is an app with that name in /usr/bin, which if your PATH is not set up correctly, will be invoked before your local executable file is ever found.

---

### Post by jeneverboy on 2009-09-15
ok

I had to compile the additional source code file. Now it works just fine. 
Thanks.

---

### Post by HaXoR7Om on 2010-03-06
I'm having trouble with gtkmm, I create a button and click it but I can only use it once it's not reusable please help.

---

