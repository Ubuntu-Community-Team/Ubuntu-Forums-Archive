---
title: "Any good C++ compilers like Visual Studio?"
date: 2013-06-15
forum: Programming Talk
---

### Post by Bombtrust on 2013-06-15
Just wondering if there are any C++ compilers like Visual Studio for Ubuntu. I am learning C++, and the terminal method didn't work.

---

### Post by Vormeph on 2013-06-16
G++ is your friend. Install synaptic package manager, search g++ and you should find the relevant packages.

BTW: If you do not like using the terminal method, you could always use Codeblocks. Look that up on synaptic package manager and you should also find the relevant packages to install. If you need any more help, just shout.

---

### Post by zobayer1 on 2013-06-16
By compiler, you mean IDE, right? Well, in my opinion, there is no IDE that comes close to visual studio, may be only good product from MS, but for learning C++, this is not 
good. It is always better if you use terminal during learning period.
To install G++, simply do this: in your terminal, write

sudo apt-get update
sudo apt-get install build-essentialAlso there are lots of IDE's for ubuntu like Codeblocks, Geany, Eclipse etc. You also don't need to install any package manager to get these, just open up your software center, and look for want you want, it is quite well categorized.

---

### Post by alan9800 on 2013-06-16
since Ubuntu 12.04 comes with gcc-4.6.3, Ubuntu 12.10 comes with gcc-4.7.2 and Ubuntu 13.04 comes with gcc-4.7.3, remember that if you don't install manually gcc 4.8.1, the g++ compiler doesn't have the full support for c++11.

---

### Post by sanderj on 2013-06-16
> **Bombtrust said:**
> Just wondering if there are any C++ compilers like Visual Studio for Ubuntu. I am learning C++, and the terminal method didn't work.

Eclipse? See [http://www.eclipse.org/cdt/](http://www.eclipse.org/cdt/)

---

### Post by trent.josephsen on 2013-06-16
By "the terminal method didn't work", do you mean you had technical problems with it, or you just didn't like it, i.e. it's not working for you? If the latter, that's fine and Eclipse might be a reasonable choice. Kdevelop is the only other one that comes to mind. If you had technical problems using a terminal, well, you're not likely to have much more success with an IDE, but feel free to try out different things and see what you like best.

---

### Post by Bombtrust on 2013-06-16
By "Didn't work" I meant there was an error when i compiled the demo.
```
# include <stdio.h>
int main
{
printf("Hello World!");
return 0;
}
```
Did I do something wrong? This worked on sourcelair.

---

### Post by Bombtrust on 2013-06-16
Thanks everyone!
I will try the 2 IDEs that were suggested (Code Blocks and Eclipse)

---

### Post by r-senior on 2013-06-16
> **Bombtrust said:**
> By "Didn't work" I meant there was an error when i compiled the demo.
```
# include <stdio.h>
int main
{
printf("Hello World!");
return 0;
}
```
Did I do something wrong? This worked on sourcelair.
This a C program. (Which compiles and works OK when the extra space is removed after '#' on line 1).

If you want a comparable C++ program, it would be:

*hello.cc*
```
#include <iostream>

using namespace std;

int main()
{
	cout << "Hello World" << endl;
}

```

Compile using:

```
g++ -o hello -Wall -Wextra hello.cc
```

---

### Post by steeldriver on 2013-06-16
I don't think the space after the # is significant - however the incomplete declarator for 'main' is - it needs to be 'int main**(void)**' or at least 'int main**()**' surely?

> **Bombtrust said:**
> By "Didn't work" I meant there was an error when i compiled the demo.
```
# include <stdio.h>
int [COLOR=#ff0000]main[/COLOR]
{
printf("Hello World!");
return 0;
}
```
Did I do something wrong? This worked on sourcelair.

---

### Post by r-senior on 2013-06-16
You are quite right. It's the missing brackets.

---

