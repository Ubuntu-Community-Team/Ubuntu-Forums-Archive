---
title: "Standard Includes for C++ TR1 with g++"
date: 2006-12-20
forum: Programming Talk
---

### Post by cyberslayer on 2006-12-20
Anyone know how to get g++ (I am using g++ 4.1) to use standard includes for the TR1 stuff it has so you don't have to prefix everything with tr1/ (which is non-standard)?  So you can write:

```
#include <type_traits>
```

instead of

```
#include <tr1/type_traits>
```

which is the way it works by default in g++?  I tried creating headers with the same names as the TR1 headers that #included the TR1 headers g++ style and edited the environment variables so they were in the include path for g++ but when I attempted to compile a program like:

```
#include <type_traits> // Uses the standard include path, not the one g++ uses by default.

 int main() {}
```

I got a ton of errors from g++.  I also tried moving the TR1 headers out of the /usr/include/c++/4.1.2/tr1 folder into the standard include path but this also resulted in compile errors from g++.

Thanks

---

### Post by hod139 on 2006-12-20
Too the best of my knowledge, the TR1 additions are not yet a standard.  I believe the goal is to get the TR1 functionallity standard in C++0x (the next version of the C++ standard). G++ 4 implements some (not all) of the TR1 additions.  I would stick with using 
```

#include <tr1/type_traits>

```
for now, or if you really don't want to, you can use 
```
g++ -I/usr/include/c++/4.0.3/tr1/
```

Also, these functions are not defined in the std namespace (since they are not standard) they are defined in the std::tr1 namespace.

---

### Post by lnostdal on 2006-12-20
> **hod139 said:**
> Also, these functions are not defined in the std namespace (since they are not standard) they are defined in the std::tr1 namespace.

..to "fix" this one could do: ```
namespace std { using namespace std::tr1; }
``` ..if i'm not mistaken

---

### Post by cyberslayer on 2006-12-20
Yes I know TR1 isn't standard yet.

> ..to "fix" this one could do:
Code:

```
namespace std { using namespace std::tr1; }
```

..if i'm not mistaken

That will work but the results are technically undefined (according to the standard).

It turns out that the reason creating fake TR1 headers that #include the actual tr1 header didn't work because of the order I had the TR1 #includes in my test program.

```
#include <array>
#include <functional>
#include <memory>
#include <tuple>
#include <type_traits>
#include <unordered_map>
#include <unordered_set>
#include <utility>

int main() {}
```

Generates errors when compiled from the command line with g++ but

```
#include <memory>
#include <array>
#include <functional>
#include <tuple>
#include <type_traits>
#include <unordered_map>
#include <unordered_set>
#include <utility>

int main() {}
```

compiles for some reason.  Anyway I have CPLUS_INCLUDE_PATH set to a directory that has fake TR1 headers that #include the real TR1 headers and I don't have to prefix things with tr1/ anymore when I compile from the command line but it doesn't work when I use KDevelop.  Anyone how to get KDevelop to use the CPLUS_INCLUDE_PATH variable for g++?

Thanks

---

### Post by thumper on 2006-12-20
Actually TR1 is standard.  It was unanimously accepted at the last standards meeting.

However it is not yet part of the std namespace. 

```
#include <tr1/type_traits>
```
is the correct way to include it.  The header files assume that that are in the tr1 directory, so that may be why your fake ones create errors.

Just don't fight it. OK?

---

### Post by hod139 on 2006-12-20
Will they merge TR1 additions into the std namespace, or will they leave it in the std::tr1 namespace; leaving room for std::tr2, std::tr3 ... additions?

---

### Post by cyberslayer on 2006-12-20
>  Actually TR1 is standard. It was unanimously accepted at the last standards meeting.

It won't be part of a standard until C++0x though.

> The header files assume that that are in the tr1 directory, so that may be why your fake ones create errors.

Actually my fake headers just #include the real ones so my type_traits one looks like this:

```
#include <tr1/type_traits>
```

And they don't generate errors from the command line just from KDevelop (because it apparently doesn't load the environment variables in .bashrc).  Also, in TR1 the headers are not prefixed with tr1/ (at least I didn't see anything about this in TR1).

---

### Post by thumper on 2006-12-20
> **cyberslayer said:**
> It won't be part of a standard until C++0x though.
Actually you caused me to reread my emails.

You are right, they aren't considered part of the "standard" until C++09 (the committee has committed to 2009).  Also, not all of TR1 will be moved into the C++09 standard.  The TR has been accepted, but apparently the "standardization" of these depends on some of the other newer language features that hare being added.

Personally, I'd still use std::tr1, but then again, that's just me.

---

