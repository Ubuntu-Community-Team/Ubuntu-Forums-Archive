---
title: "Is it Geany or my problem???"
date: 2008-11-09
forum: Programming Talk
---

### Post by phantomgunex on 2008-11-09
Hey! i just created a simple hello world program in Geany:
```
#include <iostream>

int main(int argc, char** argv)
{
	cout << "Hello World!" << endl;
	
	return 0;
}

```
But got this errors:
project.cpp:28: error: ‘cout’ was not declared in this scope
project.cpp:28: error: ‘endl’ was not declared in this scope

Is there something wrong with my program or is there something about Geany that is not letting me compile it?

Thanks!

---

### Post by cmay on 2008-11-09
you need to use namespace std
[php]
#include <iostream>
using namespace std;
int main(int argc, char** argv)
{
    cout << "Hello World!" << endl;
    
    return 0;
}
[/php]or
[php]
#include <iostream>
int main(int argc,char**argv)
{
std::cout<<"hello again"<<std::endl;
return 0;
}
[/php]if you do not use the namespace std.

---

### Post by phantomgunex on 2008-11-09
thanks! You saved my life
:KS

---

### Post by LaRoza on 2008-11-09
> **phantomgunex said:**
> Hey! i just created a simple hello world program in Geany:

Is there something wrong with my program or is there something about Geany that is not letting me compile it?

Thanks!

Are you just learning C++ and doing a test run or did you not know about namespaces?

---

### Post by phantomgunex on 2008-11-09
lol i am learning c++. i borrowed "C++ for dummies" from the library and it used dev-c++ but i could not compile the source i downloaded, so i used geany but apperently i cannot just copy the codes into the book just like that. The header used in the book is
```
#include <iostream>
#include <stdlib.h>
```
but i cant use it in geany.

---

### Post by LaRoza on 2008-11-09
> **phantomgunex said:**
> lol i am learning c++. i borrowed "C++ for dummies" from the library and it used dev-c++ but i could not compile the source i downloaded, so i used geany but apperently i cannot just copy the codes into the book just like that. The header used in the book is
```
#include <iostream>
#include <stdlib.h>
```
but i cant use it in geany.

That book is...weird.

iostream is a C++ like, stdlib.h is for C (cstdlib would be for C++)

If you are just starting programming, I suggest you check out the stickies, my site, and wiki. I started with C++ from a book I randomly got, I regret it.

---

### Post by phantomgunex on 2008-11-09
ya... but it worked in my Windows com. I am using dev-c++ in my windows com and it worked like a charm but i cant do it in geany...

---

### Post by phantomgunex on 2008-11-09
hmmm... anyone know any GOOD IDEs??? i wanna try them... Oh ya is there a way to install dev-c++ for linux.

---

### Post by LaRoza on 2008-11-10
> **phantomgunex said:**
> hmmm... anyone know any GOOD IDEs??? i wanna try them... Oh ya is there a way to install dev-c++ for linux.

No, there is no such thing as a good ide. See the stickies ;)

Dev C++ uses the windows port of gcc. You can actually use that to compile directly.

I suggest you learn how to use gcc and g++ with any editor.

---

### Post by samjh on 2008-11-10
As LaRoza said, just use an editor and the gcc and g++ compilers from the command line.

IDEs are quite distracting when learning a new language.

Geany is actually a very nice code editor, and can even be used as a very basic IDE.

---

