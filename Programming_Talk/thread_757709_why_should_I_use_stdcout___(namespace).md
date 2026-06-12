---
title: "why should I use std::cout   (namespace)"
date: 2008-04-17
forum: Programming Talk
---

### Post by brijith on 2008-04-17
hai,

In my college days I used to write CPP programs as below

```
#include <iostream.h>

int main()
{
  char s[10];
  cout << "Hello World!" << std::endl;
  cin >> s;
  cout<< s<<"\n";
  return 0;
}
```

that day we were using  ReadHat 9. When I tried the same code in new Linux distribution it is not working 

for the above code to work I have to change it as below

```
#include <iostream>

int main()
{
  char s[10];
  std::cout << "Hello World!" << std::endl;
  std::cin >> s;
  std::cout<< s<<"\n";
  return 0;
}


```


Why this change? can  any body suggest a tutorial where I can get a simple note about these type of changes. 

I am refreshing C++ after a long period of time.


**[COLOR="Red"]Thanks [/COLOR]**

---

### Post by pedro_orange on 2008-04-17
You can still use cout (without the std:: )

You just need to define 

using std::cout;
or
using namespace std;

It's just including namespaces so you can use their functions.

EDIT: Also, why would you use std::endl and not std::cout?
EDIT2: Blonde moment

---

### Post by Caduceus on 2008-04-17
Another way is:

#include <iostream>
using namespace std;

[code]

---

### Post by brijith on 2008-04-17
**[COLOR="Red"]Thanks friends.               May I know more about namespaces[/COLOR]**

---

### Post by Zugzwang on 2008-04-17
> **brijith said:**
> **[COLOR="Red"]Thanks friends.               May I know more about namespaces[/COLOR]**

Sure. Read chapter 10.2 of Bruce Eckel's "Thinking in C++" (first volume). The book is available free of charge as PDF - use google to find it.

---

### Post by pedro_orange on 2008-04-17
Yes you may sir!

[http://www.cplusplus.com/doc/tutorial/namespaces.html](http://www.cplusplus.com/doc/tutorial/namespaces.html)

---

