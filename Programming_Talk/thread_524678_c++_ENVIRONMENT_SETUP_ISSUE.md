---
title: "c++ ENVIRONMENT SETUP ISSUE ?"
date: 2007-08-13
forum: Programming Talk
---

### Post by jnorthr on 2007-08-13
Here is an attempt at a c++ example after apt-get build-essential and others. Can't get c compiler to see the include files.
```
jim@Tiny:~/Desktop/workspace/C_Test/src$ gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)


jim@Tiny:~/Desktop/workspace/C_Test/src$ gcc -o xxx myfirst.cpp
myfirst.cpp: In function ‘int main()’:
myfirst.cpp:8: error: ‘cout’ was not declared in this scope


~/Desktop/workspace/C_Test/src/myfirst.cpp text -------------------------------------------------------
// display a message
#include <stdio.h>
#include <iostream>


int main (void)
{
        cout << "myfirst.c output";
        cout << "\n";
        return 0;
}
--------------------------------------------------------
```


i found /usr/include/c++/4.1/iostream looks like a  header file with method cout defined but i can't get the compiler to 'see' this header. How can i do it ? So then i tried #include <iostream.h> and recompiled giving:

```
jim@Tiny:~/Desktop/workspace/C_Test/src$ gcc -o xxx myfirst.cpp
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/backward/iostream.h:31,
                 from myfirst.cpp:3:
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.
/tmp/ccMEVZEn.o: In function `__static_initialization_and_destruction_0(int, int)':
myfirst.cpp:(.text+0x23): undefined reference to `std::ios_base::Init::Init()'
/tmp/ccMEVZEn.o: In function `__tcf_0':
myfirst.cpp:(.text+0x6c): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccMEVZEn.o: In function `main':
myfirst.cpp:(.text+0x8e): undefined reference to `std::cout'
myfirst.cpp:(.text+0x93): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
myfirst.cpp:(.text+0xa2): undefined reference to `std::cout'
myfirst.cpp:(.text+0xa7): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
/tmp/ccMEVZEn.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status
```

jeeezzzz - what does all this mean ??? I only want to compile a c++ sample program. Guess my compiler setup is not correct yet but dunno what.

---

### Post by Damanther on 2007-08-13
Missed part of the post. lemme look again

OK, you might try g++ instead of gcc. gcc is more of a traditional C language compiler where g++ is for C++ apps

---

### Post by jnorthr on 2007-08-13
Yes, true but then added it as shown in the second example.

---

### Post by Damanther on 2007-08-13
Edited previous post. Try using g++ instead.

---

### Post by jnorthr on 2007-08-13
excellent idea - thx :)

---

### Post by aks44 on 2007-08-13
Short answer:

1. Use g++ as already mentionned.
2. #include **<iostream>**
3. Use **std::cout** rather that plain **cout**


Long answer:
The compiler has no problem "seeing" the include file... but **cout** is part of the **std** namespace. Using the unqualified name makes the compiler look in the global namespace, where obviously **cout** doesn't exist.

So either qualify **cout** with **std::** (which I recommend) or put somewhere in your file (after #include <iostream>): ```
using std::cout;
```
Both will allow the compiler to look for **cout** in the **std** namespace, which is where it resides.

IOW your compiler environment is fine, it's only a problem in your code. ;)

---

### Post by mgoblue on 2007-08-13
> **aks44 said:**
> Short answer:

1. Use g++ as already mentionned.
2. #include **<iostream>**
3. Use **std::cout** rather that plain **cout**


Long answer:
The compiler has no problem "seeing" the include file... but **cout** is part of the **std** namespace. Using the unqualified name makes the compiler look in the global namespace, where obviously **cout** doesn't exist.

So either qualify **cout** with **std::** (which I recommend) or put somewhere in your file (after #include <iostream>): ```
using std::cout;
```
Both will allow the compiler to look for **cout** in the **std** namespace, which is where it resides.

IOW your compiler environment is fine, it's only a problem in your code. ;)


I'd recommend to just always add "using namespace std;" since you're a beginner.

```

using namespace std;

```

You won't have to worry about doing using std::cout/cin or whatever that way.

---

### Post by aks44 on 2007-08-13
> **mgoblue said:**
> You won't have to worry about doing using std::cout/cin or whatever that way.

And you won't learn proper programming practices either... (granted, that's a flamebait ;))

---

### Post by LaRoza on 2007-08-13
> **aks44 said:**
> And you won't learn proper programming practices either... (granted, that's a flamebait ;))

Or you can use:

```

using std::cin

```

That way, you don't pollute the namespace and you don't have to type std:: for what you are using.

---

### Post by aks44 on 2007-08-13
> **LaRoza said:**
> Or you can use:
```

using std::cin

```

Which is the other alternative I proposed before mgoblue went "bersek" using namespace std; ;)

---

### Post by LaRoza on 2007-08-13
> **aks44 said:**
> Which is the other alternative I proposed before mgoblue went "bersek" using namespace std; ;)

Ah, I see, I should have kept up with the thread before replying.

Although "using namespace std" warrents another reply.

---

### Post by aks44 on 2007-08-13
> **LaRoza said:**
> Although "using namespace std" warrents another reply.

Napalm eradication? :p (ok, I'll stop now... you all already know my position about the **using** directive ;))

:lolflag:

---

### Post by jnorthr on 2007-08-19
merci beaucoup, guys ;
this feature reminds me of the java syntax where you can say something like system.out.println (for example) to fully qualify a function location or just println if you are lazy and want the compiler to do the hard work as long as you have an includes to tell the compiler which packages to look in. As always you may run the risk of the compiler choosing a function version you did not intend.

So where does this using namespace std; go ?

int main(void)
{
cout << "hi kids\n";
} using namespace std;

ok so i don't think i shall make it into writing device drivers, but i like to be able to read the code just to assist other debugging tasks 
:rolleyes:

---

### Post by slavik on 2007-08-19
```
#include <iostream>
using namespace std;

int main () {
 return 0;
}
```

Also, please don't use void main() ... ever.

---

### Post by Wybiral on 2007-08-19
> **slavik said:**
> Also, please don't use void main() ... ever.

I agree, _**EVER!**_

EDIT:

Just noticed he used int "main( void )" which is acceptable since older compilers expect it that way... But these days I don't think you need to (I don't).

---

