---
title: "string help"
date: 2010-04-19
forum: Programming Talk
---

### Post by savagetwinky on 2010-04-19
This is probably the stupidest question ever but i don't know how to add a number onto a char

All i want to do, is with opencv save images and give them char name + int number

so

image1.jpeg
image2.jpeg
image3.jpeg

simple and for some reason i can't find an easy way to do this, and it makes me feel pretty stupid atm

this is in c++ btw

---

### Post by azagaros on 2010-04-19
which method of c++

```

std::string strTmp;
int nFileIndex = 1;

strTmp = "Image";
char strNum[5];
sprintf("%l", strNum, nFileIndex);  // part of the c-lang libs
strTmp += strNum;
strTmp += ".img"


```

This is the way I do it when needed...

---

### Post by MadCow108 on 2010-04-19
above way is the C way, not recommended (use snprintf not sprintf if you have to)

c++ way:
```

#include <sstream>
std::stringstream s;
std::string str("string");
int number = 5;
s << str << number;
cout << s.str() << endl;

```

you can wrap this in a very simple function for almost arbitrary types, see boost::lexical_cast

---

### Post by Ravenshade on 2010-04-19
I assume s could be replaced by image?

---

### Post by MadCow108 on 2010-04-19
yes you can write:
stringstream s("image");
s << number;

---

### Post by MindSz on 2010-04-19
> **MadCow108 said:**
> above way is the C way, not recommended (use snprintf not sprintf if you have to)

Well, I believe that the real C way would have more strcat() and strncpy() calls and stuff...

---

### Post by MadCow108 on 2010-04-19
snprintf does the same (and more) as strcat/strcpy, the performance difference is negligible in almost all cases.
Just because C overs a "high" level and a "low" level variant does not mean one of them is not C

---

