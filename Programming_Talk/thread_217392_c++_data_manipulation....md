---
title: "c++ data manipulation..."
date: 2006-07-17
forum: Programming Talk
---

### Post by Lster on 2006-07-17
Hi,

...

What's wrong?

Thanks for your time!:)

---

### Post by thumper on 2006-07-17
Firstly, which are you learning C or C++?  They really are different languages.  Your example is C, so I'll give a C answer.

Firstly your variable a isn't able to be the destination for strcat for two reasons:
  - firstly it is only 6 bytes long (5 for hello, plus null terminator)
  - secondly it is in the constant memory space.

try
```

#include <stdio.h>

int main()
{
  char a[20];
  char* b;

  strcpy(a, "hello ");
  b = "world\n";

  printf(strcat(a,b));
  return 0;
}

```

---

### Post by Lster on 2006-07-17
Thanks Thumper :D!

Edit: I am using C.

---

### Post by thumper on 2006-07-17
malloc or calloc and free are your friends in C.  Personally I prefer calloc as it zero's the memory and you get less surprises if you have stuffed up as it is normally obvious.

*Caveat: untested and perhaps not the most efficient*
```
/* strdup allocates space that you need to free */
char* a, *b, *temp; /* damn C and variables at the top */
a = strdup("Hello ");
b = "World\n";
/* resize */
/* don't forget to allocate space for null terminator */
/* temp = (char*)calloc(sizeof(char), strlen(a) + strlen(b) + 1); */
temp = (char*)malloc(strlen(a) + strlen(b) + 1);
strcpy(temp, a);
free(a);
a = temp;
strcpy(a, b);

```
Look at the length limiting functions as well: strncpy et al.

You could also use realloc.

---

### Post by thumper on 2006-07-17
C++ is much nicer...

---

### Post by LordHunter317 on 2006-07-17
And would also mean your code would be correct in the face of errors.  Like most C, your code as written doesn't properly handle NULL or OOM conditions.

---

### Post by Lster on 2006-07-17
If i used C++ (and g++ to compile) how would I parse from a string to a double and from a double to a string?

Thanks for your time you are being REALLY helpful to a newbie!

---

### Post by Harleen on 2006-07-17
You can use almost all C functions in C++. For converting numbers to strings and back again I usually use C functions, as it's easier than doing it the C++ way using stringstreams. But I prefer sscanf/sprintf over atof/gcvt, because you can never tell, whether atof or gcvt were successful or not, because they don't give an error code.

In C++ I'd do it that way (untested)

```

#include <string>
#include <iostream>
#include <cstdio>

int main(void)
{
  std::string text = "1.23"; // string containing a number
  double number;
  int status = sscanf(text.c_str(), "%lf", &number);
  if (status != 1)
  {
    std::cerr << "Error converting string->number" << std::endl;
  }
  else
  {
    std::cout << "read the following number: " << number << std::endl;
  }
  return 0;
}
```

Edit: If you are questioning, why C++ is claimed to be better for string handling, here's an example for concatenation of strings in C++:


```
#include <string>
#include <iostream>

int main(void)
{
  std::string a = "Hello";
  std::string b = "World";
  
  a = a + std::string(" ") + b;

  // this should print out "Hello World"
  std::cout << a << std::endl;
  return 0;
}
```

---

### Post by thumper on 2006-07-17
Look at using the [boost](http://www.boost.org) libraries (it is in the repositories).

```
std::string s = "12.5";
double d = boost::lexical_cast<double>(s);
std::string another = "Something " + boost::lexical_cast<std::string>(d);

```

---

### Post by thumper on 2006-07-17
BTW boost::lexical_cast throws an exception if it doesn't work.

Any C++ programmer worth their salt uses boost (not just for lexical_cast).

---

### Post by LordHunter317 on 2006-07-17
> **Harleen said:**
>  But I prefer sscanf/sprintf over atof/gcvt, because you can never tell, whether atof or gcvt were successful or not, because they don't give an error code.Which is why you use strtol directly and correctly.

---

### Post by Lster on 2006-07-18
Wow... thanks guys you've all been REALLY helpful!

Happy Ubuntu user #1 000 000 000:-D

---

### Post by Lster on 2006-07-19
Another question though;). Sprintf and Scanf are really slow how could I speed things up. Would boost be faster and how would I get that?

Thanks for helping a n00b!:-D

---

### Post by thumper on 2006-07-19
libboost-dev is in the repositories.

define slow?

use it like
```

#include <boost/lexical_cast.hpp>

```

---

### Post by Lster on 2006-07-19
I searched for "boost" in synaptic but I didnt find anything. I havent got internet for Ubuntu (I am gonna set it up soon). Would I be able to download it on windows?

---

