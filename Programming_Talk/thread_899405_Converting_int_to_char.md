---
title: "Converting int to char"
date: 2008-08-24
forum: Programming Talk
---

### Post by J05HYYY on 2008-08-24
I want the last line of the following C code to work. What is the _standard_ way of converting an integer to string?

```

#include <stdlib.h>

int mynumasnum;
char *mynumasstr;

mynumasnum=156;
mynumasstr=mynumasnum;

```

(At the moment, it gives the following when compiled:)
```
warning: assignment makes pointer from integer without a cast
```



Whats the difference between printf, sprintf and atio? I heard atio isn't standard, is this true?

Any help would be great :)

---

### Post by kpatz on 2008-08-24
Usually in C one uses sprintf to convert numbers to strings.

```

#include <stdio.h>

int mynumasnum;
char mynumasstr[20];  /* should be long enough */

mynumasnum=156;
sprintf(mynumasstr, "%d", mynumasnum);

```

printf writes the output to standard output; fprintf writes the output to a specified FILE* stream; sprintf writes into a string.

I've never heard of atio... ???

---

### Post by winch on 2008-08-24
[http://www.cplusplus.com/reference/clibrary/cstdlib/itoa.html](http://www.cplusplus.com/reference/clibrary/cstdlib/itoa.html)
Should give you enough to get going.

Also,
char *mynumasstr;
gets you a pointer to char. Since you don't initialize it it could be pointing anywhere. You also need to allocate some memory and point mynumasstr at it.

Or just use a char array, for example.
char mynumasstr[50];

---

### Post by mujambee on 2008-08-24
> **kpatz said:**
> I've never heard of atio... ???

He probably refers to atoi.  atoi transforms a string into an integer.

---

### Post by monkeyking on 2008-08-24
> **J05HYYY said:**
> I want the last line of the following C code to work. What is the _standard_ way of converting an integer to string?

```

#include <stdlib.h>

int mynumasnum;
char *mynumasstr;

mynumasnum=156;
mynumasstr=mynumasnum;

```

(At the moment, it gives the following when compiled:)
```
warning: assignment makes pointer from integer without a cast
```



Whats the difference between printf, sprintf and atio? I heard atio isn't standard, is this true?

Any help would be great :)

What do you want?
int to char og int to string

char!=string

---

### Post by Zugzwang on 2008-08-24
> **monkeyking said:**
> What do you want?
int to char og int to string

char!=string
Huh? He/She never claimed that the int is to be converted to a char (might be too small) - The task was to "convert" the integer to a string, which is C is typically a char array. The original "code" by the OP was based on the implicit assumption that the conversion would have been done automatically, which isn't the case (Note that a pointer was overwritten with an integer, not the string it was pointing to).

---

### Post by Catalyst2Death on 2008-08-24
atoi isn't STL compatible in some implementations... When I ran into this problem, I did this in C++:

```
//number to string
template <class T>
inline std::string stringify(const T& t)
{
  std::ostringstream o;
  if (!(o << t))
    return "err";
  return o.str();
} 
```

This will run *any* number to string.  I know its not const char* but I think these are more easily interchanged?  If there's a problem, it will return "err" as your string... I modified the original version of this because I didn't feel like throwing an exception in my implementation of this code.

---

### Post by J05HYYY on 2008-08-24
**kpatz**, you have basically answered my question thank you
**winch**, well observed - the pointer is adjusted manually each time so that the field length doesn't have to be fixed (i didn't post this code, whoops)
**mujambee**, thats not what i meant
**monkeyking**, read zugwang's comment
**Zugzwang**, this is what i meant - kinda and yes the code was based on that assumption.
**Catalyst2Death**, Okay atio looks just plain annoying to me, if its not compatible on the majority of machines with the possibility of non standardization etc; maybe it's the worst of the choices. Unfortunately I can't read C++ code because I haven't learnt it.

Thank you for all your comments, I tried to ask and answer as clearly as I could (honest). I think I will try using sprintf. As suggested by kpatz... will see how it goes and post back sometime. :)

---

### Post by MarkieB on 2008-08-25
no longer participating in ubuntuforums.org

---

### Post by dwhitney67 on 2008-08-25
> **MarkieB said:**
> string handling is one of the 'reasons' for the ++ in c++:

...
Nice program, but the OP is writing in C, not C++.  If OP wanted C++, this would be easier:
[PHP]#include <boost/lexical_cast.hpp>
#include <string>
#include <iostream>

int main()
{
  int value = 10;

  std::string strValue = boost::lexical_cast<std::string>(value);

  std::cout << "strValue = " << strValue << std::endl;

  return 0;
}[/PHP]

---

### Post by generalguy on 2008-08-25
[PHP]
#include <stdio.h>

int main()
{
     /* converting int to string */
     char str[20];
     int i = 12345;
     snprintf(str,sizeof(str)/sizeof(char),"%d",i);
     
     /*casting int to char */
     char i_as_char = (char) i;
     return 0;

}
[/PHP]



Note that snprintf is only in C99. If you're using gcc, add "-std=c99" as an argument to the compiler.

---

### Post by dwhitney67 on 2008-08-25
> **generalguy said:**
> ...
Note that snprintf is only in C99. If you're using gcc, add "-std=c99" as an argument to the compiler.
Whatever gave you that idea?  The C-library snprintf() has been around for ages.

Try compiling the following code with:
```
gcc -std=c89 myprog.c
```
[PHP]#include <stdio.h>

int main()
{
  char buf[10];
  snprintf( buf, sizeof(buf)-1, "%d", 5 );
  printf( "buf = %s\n", buf );
  return 0;
}[/PHP]

---

### Post by MarkieB on 2008-08-27
no longer participating in ubuntuforums.org

---

### Post by J05HYYY on 2008-09-01
I'm not fresh from C, I just chose (and will probably continue to choose) to write in C because its lightweight, fast running and extremely portable.:)

---

