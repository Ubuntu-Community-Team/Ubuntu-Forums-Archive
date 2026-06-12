---
title: "Problem with g++?"
date: 2007-09-25
forum: Programming Talk
---

### Post by thangola on 2007-09-25
I have just met a problem with my C++ Compiler: g++. When I compile my file with this command:

[INDENT]**[FONT="Courier New"]g++ cout.cpp -o cout[/FONT]**[/INDENT]

I met these errors:
> 
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/c++locale.h:55: error: &#8216;uselocale&#8217; was not declared in this scope
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/c++locale.h:55: error: invalid type in declaration before &#8216;;&#8217; token
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/c++locale.h: In function &#8216;int std::__convert_from_v(char*, int, const char*, _Tv, __locale_struct* const&, int)&#8217;:
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/c++locale.h:75: error: &#8216;__gnu_cxx::__uselocale&#8217; cannot be used as a function
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/c++locale.h:92: error: &#8216;__gnu_cxx::__uselocale&#8217; cannot be used as a function
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/time.h: At global scope:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/time.h:186: error: expected constructor, destructor, or type conversion before &#8216;char&#8217;
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/cwchar:148: error: &#8216;::fgetws&#8217; has not been declared
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/cwchar:150: error: &#8216;::fputws&#8217; has not been declared
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/cwchar:154: error: &#8216;::getwc&#8217; has not been declared
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/cwchar:155: error: &#8216;::getwchar&#8217; has not been declared
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/cwchar:160: error: &#8216;::putwc&#8217; has not been declared
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/cwchar:161: error: &#8216;::putwchar&#8217; has not been declared
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/cstdlib:192: error: &#8216;::atoll&#8217; has not been declared
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/cstdlib:212: error: &#8216;__gnu_cxx::atoll&#8217; has not been declared
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/cwctype:89: error: &#8216;::iswblank&#8217; has not been declared
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/ctype_base.h:51: error: &#8216;_ISupper&#8217; was not declared in this scope
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/ctype_base.h:52: error: &#8216;_ISlower&#8217; was not declared in this scope
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/ctype_base.h:53: error: &#8216;_ISalpha&#8217; was not declared in this scope
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/ctype_base.h:54: error: &#8216;_ISdigit&#8217; was not declared in this scope
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/ctype_base.h:55: error: &#8216;_ISxdigit&#8217; was not declared in this scope
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/ctype_base.h:56: error: &#8216;_ISspace&#8217; was not declared in this scope
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/ctype_base.h:57: error: &#8216;_ISprint&#8217; was not declared in this scope
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/ctype_base.h:58: error: &#8216;_ISalpha&#8217; was not declared in this scope
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/ctype_base.h:58: error: &#8216;_ISdigit&#8217; was not declared in this scope
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/ctype_base.h:58: error: &#8216;_ISpunct&#8217; was not declared in this scope
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/ctype_base.h:59: error: &#8216;_IScntrl&#8217; was not declared in this scope
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/ctype_base.h:60: error: &#8216;_ISpunct&#8217; was not declared in this scope
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/ctype_base.h:61: error: &#8216;_ISalpha&#8217; was not declared in this scope
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/ctype_base.h:61: error: &#8216;_ISdigit&#8217; was not declared in this scope

And this is the content of my file cout.cpp:

> 
#include <iostream>

using namespace std;

int main () {
        cout << "Print successfully!";
        return 0;
}


Can someone tell me what happens with my compiler and what am I to do to program with C++ now?

---

### Post by LaRoza on 2007-09-25
Try:
```

sudo aptitude install build-essential

```

It looks like headers are missing.

Tip: don't use "using namespace ....", if you must, use "using std::cout", namespaces are a good thing.

---

### Post by thangola on 2007-09-25
> **LaRoza said:**
> Try:
```

sudo aptitude install build-essential

```

It looks like headers are missing.

Tip: don't use "using namespace ....", if you must, use "using std::cout", namespaces are a good thing.
Thanks for your answer. I've just do these thing but nothing happened, I still receive those errors.

---

### Post by LaRoza on 2007-09-25
It looks like there are errors in the headers, usually an indication something is missing.

Was this working before? If so, what happened between now and then.

---

### Post by thangola on 2007-09-25
No! I have never used it before. But I have met some similar errors with gcc command when I compiled a .c file. I removed the gcc packaged and reinstall it and then it worked.

---

### Post by LaRoza on 2007-09-25
I hear things like this happen if packages are install one-by-one.

I would try a complete reinstallation. From what you said, you reinstalled gcc, which may have changed something.

---

### Post by thangola on 2007-09-25
I also installed following packages: gcc-4.1, cpp, g77 and g++-4.1, but nothing happened.

---

### Post by LaRoza on 2007-09-25
> **thangola said:**
> I also installed following packages: gcc-4.1, cpp, g77 and g++-4.1, but nothing happened.

What do you mean, you can't use g77 either?

---

### Post by thangola on 2007-09-25
One of my friends advised me that installed those packages to fix this bug, but I receiced no result. I also reinstalls my Ubuntu and g++, but those errors still happened :(.

---

### Post by LaRoza on 2007-09-25
> **thangola said:**
> One of my friends advised me that installed those packages to fix this bug, but I receiced no result. I also reinstalls my Ubuntu and g++, but those errors still happened :(.

Remove everything, and do a reinstall, using this command only:

```

sudo aptitude install build-essential

```

---

### Post by thangola on 2007-09-25
Hix! I also did that :(

---

### Post by dwhitney67 on 2007-09-25
Can you confirm if the following succeeds:

[FONT="Courier New"]$ sudo apt-get remove build-essential

$ sudo apt-get install build-essential

$ cat > dummy.cpp << "EOF"
#include <iostream>
int main() { std::cout << "it works." << std::endl; }
EOF

$ g++ dummy.cpp

$ ./a.out[/FONT]

---

### Post by thangola on 2007-09-25
> **dwhitney67 said:**
> Can you confirm if the following succeeds:

[FONT="Courier New"]$ sudo apt-get remove build-essentials

$ sudo apt-get install build-essentials

$ cat > dummy.cpp << "EOF"
#include <iostream>
int main() { std::cout << "it works." << std::endl; }
EOF

$ g++ dummy.cpp

$ ./a.out[/FONT]
I still receive those error and there is no .out file.

---

### Post by dwhitney67 on 2007-09-25
What were the error messages or other "useful" information displayed when you ran the "apt-get" commands?

---

### Post by thangola on 2007-09-25
when I rum two above apt-get command, the terminal showed me the error:

>   **E: Couldn't find package build-essentials**

What is the command *"apt-get remove build-essentials"* affected?

---

### Post by dwhitney67 on 2007-09-25
What version of Ubuntu are you running?

Can you post the contents of your /etc/apt/sources.list file?  (Please enclose the contents of this file within PHP tags!).

---

### Post by thangola on 2007-09-25
I'm using Ubuntu 7.04 (feisty). And this is the content of my source.list:

> 

deb [http://vn.archive.ubuntu.com/ubuntu/](http://vn.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://vn.archive.ubuntu.com/ubuntu/](http://vn.archive.ubuntu.com/ubuntu/) feisty main restricted

deb [http://vn.archive.ubuntu.com/ubuntu/](http://vn.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://vn.archive.ubuntu.com/ubuntu/](http://vn.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

deb [http://vn.archive.ubuntu.com/ubuntu/](http://vn.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://vn.archive.ubuntu.com/ubuntu/](http://vn.archive.ubuntu.com/ubuntu/) feisty universe

deb [http://vn.archive.ubuntu.com/ubuntu/](http://vn.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://vn.archive.ubuntu.com/ubuntu/](http://vn.archive.ubuntu.com/ubuntu/) feisty multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

deb [http://vn.archive.ubuntu.com/ubuntu](http://vn.archive.ubuntu.com/ubuntu) feisty main restricted
deb [http://vn.archive.ubuntu.com/ubuntu](http://vn.archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

deb [http://vn.archive.ubuntu.com/ubuntu](http://vn.archive.ubuntu.com/ubuntu) feisty universe multiverse
deb [http://vn.archive.ubuntu.com/ubuntu](http://vn.archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse

deb [http://mirror.ubuntulinux.nl/](http://mirror.ubuntulinux.nl/) feisty-seveas all

deb [http://vn.archive.ubuntu.com/ubuntu](http://vn.archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main

deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free


---

### Post by dwhitney67 on 2007-09-25
I now understand why the other command gave you an error... it is stating that build-essentials is not installed.

Please run this command and report back if you receive an error:

[FONT="Courier New"]$ sudo apt-get install build-essential[/FONT]

Your /etc/apt/sources.list looks fine, although I found an entry in my list that is not in yours:

[FONT="Courier New"]deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted[/FONT]

---

### Post by thangola on 2007-09-25
That entry is the source from the Ubuntu Live CD. So U don't need use it if you have an internet connection.

---

### Post by dwhitney67 on 2007-09-26
Alright, this is becoming more of an issue than I can take.

_Please run this command, and report back the results_:

[FONT="Courier New"]$ sudo apt-get install build-essential[/FONT]

If you get an error, then the solution to the problem you are having is beyond my capabilities to solve.  The only thing I could recommend is that in lieu of using Ubuntu, perhaps consider a Linux distro like Fedora 7 where the tools you need  are included with the distro.

P.S. It appears that I made typos in my earlier posts, for which I am sorry.  The package you need to install is "build-essential", not "build-essentials".

---

### Post by Lux Perpetua on 2007-09-26
> **thangola said:**
> That entry is the source from the Ubuntu Live CD. So U don't need use it if you have an internet connection.I'm not sure why your sources.list doesn't have that entry. Do you not have the CD-ROM? I recall needing the CD-ROM when I was installing the compilers.

---

### Post by gnusci on 2007-09-26
Try first update the internal database:

**> sudo apt-get update**

also:

**> apt-get --fix-missung upgrade**

and then:

**> sudo apt-get install build-essential**

if does not work try installing all corrected packages:

**> apt-get upgrade**

also try removing build-essential first:

**> sudo apt-get remove build-essential**

---

### Post by Kadrus on 2007-09-26
[http://gcc.gnu.org/](http://gcc.gnu.org/)

download 

c++ program that always work with me

# include<iostream>
using namespace std;
int main()
{
cout <<"Hello World"<<endl;
return 0;
}

save as :example.cpp

in terminal write
 g++ example.cpp

if it compile wihout error type

./a.out

Hope it helped:)

---

### Post by Lord Illidan on 2007-09-26
> **gnusci said:**
> Try first update the internal database:

**> sudo apt-get update**

also:

**> apt-get --fix-missung upgrade**

and then:

**> sudo apt-get install build-essential**

if does not work try installing all corrected packages:

**> apt-get upgrade**

also try removing build-essential first:

**> sudo apt-get remove build-essential**

That should be apt-get --fix-missing upgrade

---

### Post by thangola on 2007-09-26
> **gnusci said:**
> Try first update the internal database:

**> sudo apt-get update**

also:

**> apt-get --fix-missung upgrade**

and then:

**> sudo apt-get install build-essential**

if does not work try installing all corrected packages:

**> apt-get upgrade**

also try removing build-essential first:

**> sudo apt-get remove build-essential**

Tks to all you for comments. I tried these steps but these wann't any better result. :(

---

### Post by dwhitney67 on 2007-09-26
What was the error message (if any) when you ran:

$ sudo apt-get install build-essential


????????

---

### Post by thangola on 2007-09-26
> **dwhitney67 said:**
> What was the error message (if any) when you ran:

$ sudo apt-get install build-essential


????????
There wasn't any error.

---

### Post by dwhitney67 on 2007-09-27
Ok, there was no error.

Please confirm that gcc and g++ are installed on your system using this command:

[FONT="Courier New"]$ which gcc g++[/FONT]

What is the output?


P.S.  The output should be:
[FONT="Courier New"]/usr/bin/gcc
/usr/bin/g++[/FONT]

---

### Post by thangola on 2007-09-27
> **dwhitney67 said:**
> 
P.S.  The output should be:
[FONT="Courier New"]/usr/bin/gcc
/usr/bin/g++[/FONT]
Right! The output was that.

---

### Post by dwhitney67 on 2007-09-27
Good.

Let's try a programming example.  Please _copy/paste_ the following from your web-browser to the terminal (exactly as shown):

```
cat > dummy.cpp << "EOF"
#include <iostream>
int main() { std::cout << "it works." << std::endl; }
EOF
```

Then press the enter key.  A file named "dummy.cpp" should have been created.

To compile this file, use this command:

```
g++ dummy.cpp -o dummy
```

Are any errors reported?

If not, then run the binary:

```
./dummy
```

Are any errors reported?

---

### Post by thangola on 2007-09-27
Hmm. There was errors. But if I use command:
```
g++-3.4 dummy.cpp -o dummy
```
it's ok and when I run the dummy file, it's work. So I think there are some problem with my package g++-4.1

---

### Post by ryno519 on 2007-09-27
> **LaRoza said:**
> Try:
```

sudo aptitude install build-essential

```

It looks like headers are missing.

Tip: don't use "using namespace ....", if you must, use "using std::cout", namespaces are a good thing.

It is perfectly acceptable to use a 'using namespace' statement in the implementation, it is not considered good practise to add one to a header file.

---

### Post by dwhitney67 on 2007-09-27
I agree, but one should also refrain from specifying the "using namespace" statement until _after_ all of the header files have been included.

Thus, this is an example of poor programming:

```
using namespace std;

#include "MyProject.h"
#include <iostream>
```

However, this is acceptable:

```
#include "MyProject.h"
#include <iostream>

using namespace std;
```

---

### Post by dwhitney67 on 2007-09-27
> **thangola said:**
> Hmm. There was errors. But if I use command:
```
g++-3.4 dummy.cpp -o dummy
```
it's ok and when I run the dummy file, it's work. So I think there are some problem with my package g++-4.1

I feel like the only way to "help" you is to stick bamboo sticks up your finger to get an answer.  You need to learn to be more explicit when you state that you got an error.

When you ran the "g++ dummy.cpp" command, what were the errors you received?

Also, why do you have gcc-3.4 installed?  Are you doing legacy programming?

---

### Post by thangola on 2007-09-27
I'm sorry. My English is not good :(.
> **dwhitney67 said:**
> 
When you ran the "g++ dummy.cpp" command, what were the errors you received?

```
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/c++locale.h:55: error: ‘uselocale’ was not declared in this scope
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/c++locale.h:55: error: invalid type in declaration before ‘;’ token
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/c++locale.h: In function ‘int std::__convert_from_v(char*, int, const char*, _Tv, __locale_struct* const&, int)’:
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/c++locale.h:75: error: ‘__gnu_cxx::__uselocale’ cannot be used as a function
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/c++locale.h:92: error: ‘__gnu_cxx::__uselocale’ cannot be used as a function
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/time.h: At global scope:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/time.h:186: error: expected constructor, destructor, or type conversion before ‘char’
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/cwchar:148: error: ‘::fgetws’ has not been declared
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/cwchar:150: error: ‘::fputws’ has not been declared
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/cwchar:154: error: ‘::getwc’ has not been declared
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/cwchar:155: error: ‘::getwchar’ has not been declared
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/cwchar:160: error: ‘::putwc’ has not been declared
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/cwchar:161: error: ‘::putwchar’ has not been declared
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/cstdlib:192: error: ‘::atoll’ has not been declared
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/cstdlib:212: error: ‘__gnu_cxx::atoll’ has not been declared
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/cwctype:89: error: ‘::iswblank’ has not been declared
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/ctype_base.h:51: error: ‘_ISupper’ was not declared in this scope
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/ctype_base.h:52: error: ‘_ISlower’ was not declared in this scope
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/ctype_base.h:53: error: ‘_ISalpha’ was not declared in this scope
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/ctype_base.h:54: error: ‘_ISdigit’ was not declared in this scope
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/ctype_base.h:55: error: ‘_ISxdigit’ was not declared in this scope
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/ctype_base.h:56: error: ‘_ISspace’ was not declared in this scope
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/ctype_base.h:57: error: ‘_ISprint’ was not declared in this scope
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/ctype_base.h:58: error: ‘_ISalpha’ was not declared in this scope
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/ctype_base.h:58: error: ‘_ISdigit’ was not declared in this scope
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/ctype_base.h:58: error: ‘_ISpunct’ was not declared in this scope
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/ctype_base.h:59: error: ‘_IScntrl’ was not declared in this scope
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/ctype_base.h:60: error: ‘_ISpunct’ was not declared in this scope
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/ctype_base.h:61: error: ‘_ISalpha’ was not declared in this scope
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/i486-linux-gnu/bits/ctype_base.h:61: error: ‘_ISdigit’ was not declared in this scope

```
I posted these errors in my first post in this topic.

> Also, why do you have gcc-3.4 installed? Are you doing legacy programming?
I think my gcc-3.4, g++-3.3, g++-3.4 was installed when I installed Ubuntu.

---

### Post by dwhitney67 on 2007-09-27
From the output, it does appear that you are back to where you started.  It could possible be a problem with your version of glibc (GNU C Library), but I can't really tell.

When I installed Ubuntu 7.04, I did not have any GCC (gcc/g++) development tools on my system... none whatsoever.

Generally for any Linux system to run, the C (and possibly) C++ runtime libraries must be installed, but these cannot be used to compile source.  So these are included in the base Ubuntu installation.

If I were you, I would do either one of the following:

1)  Find a way to remove all development tools from your system using apt-get.  Then when done, re-attempt the "sudo apt-get install build-essential".

or

2) Rebuild your system from scratch.  This is always fun!

Sorry I cannot be of more help.  But there is something seriously wrong with the installation on your system.  Getting the C and C++ development tools installed should not be this difficult.

---

### Post by LaRoza on 2007-09-27
> **ryno519 said:**
> It is perfectly acceptable to use a 'using namespace' statement in the implementation, it is not considered good practise to add one to a header file.

In small programs, true, in larger ones, it is better to specify which members of the namespace you are using.

Many books and courses for beginners, sticky that line their, and don't explain what it means, and when such learners see "std::cout" or "std::endl", they are lost.

---

