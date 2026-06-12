---
title: "cant even get cout to work"
date: 2008-01-22
forum: Programming Talk
---

### Post by cgkades on 2008-01-22
i did a search the only  thing close it the thread "undefined reference to `std::cout'  	" which is NOT the problem.  i install build essential, and i'm using eclipse (though i tried on geany too).
i'm using ubuntu 7.1

code:
```

#include <iostream>

using namespace std;

int main()
{

     cout >> "hello world. /n";
     return 0;
}

```

the error in eclipse (which is almost exactly the same error in geany and in the console with i use g++)

error: no match for 'operator>>' helloworld.cp

---

### Post by insineratehymn on 2008-01-22
Syntactical error on line 8.

Have fun. =)

---

### Post by cgkades on 2008-01-22
you have to be kidding me. i even looked at old code. i have no excuses for this retardedness... thanks :)

---

### Post by Lster on 2008-01-22
[http://www.cplusplus.com/doc/tutorial/program_structure.html](http://www.cplusplus.com/doc/tutorial/program_structure.html)

HTH

---

### Post by insineratehymn on 2008-01-22
> **Lster said:**
> [PHP]// my first program in C++

#include <iostream>
using namespace std;

int main ()
{
  cout << "Hello World!";
  return 0;
}
[/PHP]

That is an example program from CPlusPlus.com. The link is here:

[http://www.cplusplus.com/doc/tutorial/program_structure.html](http://www.cplusplus.com/doc/tutorial/program_structure.html)

HTH

Yeah, but what does he learn in just giving him the program? ):P

---

### Post by Lster on 2008-01-22
Well more than if I just did nothing. I gave him a site that he may well learn from (it has a full description of what everything does in that program over there) - there is also whole learning resource there. I don't agree with doing homework but this is not that (I don't think), just an honest attempt to learn.

To cgkades, I recommend you find the difference between your posted code and that sites code so as to learn your errors.

---

