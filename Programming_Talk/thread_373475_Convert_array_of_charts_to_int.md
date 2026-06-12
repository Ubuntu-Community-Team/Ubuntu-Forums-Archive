---
title: "Convert array of charts to int"
date: 2007-03-01
forum: Programming Talk
---

### Post by Kimm on 2007-03-01
I'm trying to write a program that would read every line of a file to an array of integers (1 line to 1 position in the integer).

My Program reads the file but as a list of charts.

How do I write char temp[3] = "342" to int x?

---

### Post by Tomosaur on 2007-03-01
Well, it depends on which language you're writing it in :P

---

### Post by Wybiral on 2007-03-01
Assuming it's C/C++, use the "atoi" function.

Here's an example in C:
```

#include <stdio.h>

int main()
{
   char* strValue = "1004";
   int intValue = atoi(strValue);
   intValue *= 2;
   printf("%s * 2 = %i \n", strValue, intValue);
}

```

In C++:
```

#include <iostream>
#include <string>

using namespace std;

int main()
{
   string strValue = "1004";
   int intValue = atoi(strValue.c_str());
   intValue *= 2;
   cout << strValue << " * 2 = " << intValue << endl;
}

```

In python:
```

strValue = "1004"
intValue = int(strValue)
intValue *= 2
print strValue, " * 2 = ", intValue

```

---

### Post by Kimm on 2007-03-01
> **Wybiral said:**
> Assuming it's C/C++, use the "atoi" function.

Here's an example in C:
```

#include <stdio.h>

int main()
{
   char* strValue = "1004";
   int intValue = atoi(strValue);
   intValue *= 2;
   printf("%s * 2 = %i \n", strValue, intValue);
}

```

In C++:
```

#include <iostream>
#include <string>

using namespace std;

int main()
{
   string strValue = "1004";
   int intValue = atoi(strValue.c_str());
   intValue *= 2;
   cout << strValue << " * 2 = " << intValue << endl;
}

```

In python:
```

strValue = "1004"
intValue = int(strValue)
intValue *= 2
print strValue, " * 2 = ", intValue

```

Oops, sorry. Forgot to say what language I was  writing it in. But I was using C++ so thanks for the advice! :D

---

