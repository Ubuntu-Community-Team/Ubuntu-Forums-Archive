---
title: "Newbie C++ Question"
date: 2006-03-08
forum: Programming Talk
---

### Post by Nord on 2006-03-08
I am trying to compile a C++ program with GNU and am getting an error with the cout statement

cout was not declared in this scope.

I am a total newbie and am trying code out of Sams Teach Yourself C++ for Linux so I am off to a bad start.

Thanks for any insight.

Nord

---

### Post by FizDev on 2006-03-08
Hmm.. I do not know much about C++, but I believe you must include iostream.h

---

### Post by Adrian on 2006-03-08
[QUOTE=FizDev]Hmm.. I do not know much about C++, but I believe you must include iostream.h[/QUOTE]

Use

```
#include <iostream>
```

instead. That's the C++ way.

---

### Post by krypto_wizard on 2006-03-08
try #include<iostream> if you are using g++

iostream.h is deprecated I think.

[QUOTE=FizDev]Hmm.. I do not know much about C++, but I believe you must include iostream.h[/QUOTE]

---

### Post by thumper on 2006-03-08
You might find that the Sams book is pre-standard.

The header file you want is <iostream>.

cout is defined in the std namespace.

```

#include <iostream>

int main()
{
   std::cout << "Hello World\n";
   return 0;
}

```
Most books suggest something like:

```

#include <iostream>

using namespace std;

int main()
{
   cout << "Hello World" << endl;
   return 0;
}

```
That brings everything in namespace std into the local scope.  I won't get into my pet peeve of std::endl vs '\n'.

Personally I prefix with std:: most of the time, and if I do want to bring something into local scope, then only bring in what you need, like:

```

#include <iostream>

int main()
{
   using std::cout;
   cout << "Hello World\n";
   return 0;
}

```

---

### Post by Nord on 2006-03-08
Tried the code you gave me and it doesn't work either.

Maybe I didn't install GNU properly for C++.

It did work for a C program I tried earlier.

Thanks for the info.

---

### Post by Adrian on 2006-03-08
[QUOTE=Nord]Tried the code you gave me and it doesn't work either.

Maybe I didn't install GNU properly for C++.

It did work for a C program I tried earlier.

Thanks for the info.[/QUOTE]

How do you compile the code? You must use g++ to compile a C++ program.

What error messages do you get?

You get the tools you need (like g++) by installing the **build-essential** package.

---

### Post by Nord on 2006-03-08
Thanks for the help.

I was using gcc instead of g++.

I only have one Linux book, "Linux Bible" and one C++ book, "Sams Teach Yourself C++ for Linux".

Can anyone recommend a better C++ for Linux book.

Thanks to everyone that posted for their comments and patience.

Nord

---

### Post by Adrian on 2006-03-08
[QUOTE=Nord]Thanks for the help.

I was using gcc instead of g++.

I only have one Linux book, "Linux Bible" and one C++ book, "Sams Teach Yourself C++ for Linux".

Can anyone recommend a better C++ for Linux book.

Thanks to everyone that posted for their comments and patience.

Nord[/QUOTE]

Accelerated C++ by Koenig, et al. has a reputation of being good. I'd check it out if I were you.

You can also download Thinking in C++ by Bruce Eckel from the net:
[http://mindview.net/Books/TICPP/ThinkingInCPP2e.html](http://mindview.net/Books/TICPP/ThinkingInCPP2e.html)

---

### Post by Lord Illidan on 2006-03-08
[quote=Nord]Thanks for the help.

I was using gcc instead of g++.

I only have one Linux book, "Linux Bible" and one C++ book, "Sams Teach Yourself C++ for Linux".

Can anyone recommend a better C++ for Linux book.

Thanks to everyone that posted for their comments and patience.

Nord[/quote]

Probably any good c++ book is good. Read the reviews at amazon.com, and steer clear of those who are too windows oriented.
And read lots of online tutorials.

---

### Post by thumper on 2006-03-08
Nah, amazon reviews are too easy to fake.

Check out the [ACCU book review](http://www.accu.org/index.php/book_reviews) site.

---

