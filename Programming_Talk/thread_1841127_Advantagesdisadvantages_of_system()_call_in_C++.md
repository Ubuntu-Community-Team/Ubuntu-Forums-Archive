---
title: "Advantages/disadvantages of system() call in C++"
date: 2011-09-08
forum: Programming Talk
---

### Post by MG&amp;TL on 2011-09-08
Recently, I was reliably informed that the system() call in C++ (from #include <stdlib.h>), was not necessary. And it was implicated that almost all programming could be done in bash.

Thoughts/feelings on this, please.

---

### Post by Longinus00 on 2011-09-08
> **MG&TL said:**
> Recently, I was reliably informed that the system() call in C++ (from #include <stdlib.h>), was not necessary. And it was implicated that almost all programming could be done in bash.

Thoughts/feelings on this, please.

That wasn't what I said.

You said "Most of my code at the moment is based around [calling system()]" and in this context it meant c++ calling bash scripts. I was trying to point out that system should be a uncommon thing and that it's possible you might be able do your whole program in either language without all the system() calls.

From your replies in the original thread it sounds like you use system() as a crutch because you don't know how to do some things in c++ that you can otherwise do easily in the shell (moving files around, etc.) which is not a good reason to use the system() call.

Is your post what you got out of our discussion or are you just misrepresenting me for fun?

---

### Post by MG&amp;TL on 2011-09-08
It was what I got out of our conversation.

OK, so if you're not suggesting that I code in bash, and you say that system is not necessary, what's the [other] convenient way of say, copying a file in C++? (Actually, I'm using grub-mkfont, but it's the same difference.) Initially, I started out with minimal system() calls, simply writing to a script in /tmp, then executing that at the end with system(), but then I realised it was much easier simply to use system() all the way through, and it has been cited as 'the way to use bash in C++' by many experienced forum members (found via an internet trawl), hence I have been using system()...

Please don't take this the wrong way, I'm not the agressive type, I just feel that there is no actual problem with system().

If everyone used bash to write their programs with, I would take your point, but 90% of programs I see are C-language based. If you want the source code for my project, you're very welcome to it (I'm not porting it, the maintainer of grub-customizer is), but it will be in the morning. It is not perfect, nor even what most normal people (I daresay) would have done, as it was an iterative process, designed to run without bugs first, and be elegant and efficient later.

Thanks for the tips. Sorry I seem to have alienated(?) you.

---

### Post by dwhitney67 on 2011-09-09
> **MG&TL said:**
> ... what's the [other] convenient way of say, copying a file in C++? 

Using the Boost library:
```

// File:  CopyFile.cpp
//
// To build this program:
//
//    g++ CopyFile.cpp -lboost_filesystem
//
#include <boost/filesystem.hpp>
#include <iostream>

int main(int argc, char** argv)
{
   // assume argv[1] is the source file, and argv[2] the destination file.

   try {
      boost::filesystem::copy_file(argv[1], argv[2]);
   }
   catch (std::exception& e) {
      std::cerr << e.what() << std::endl;
   }
}

```

---

### Post by MG&amp;TL on 2011-09-09
Is there a manpage for boost() somewhere? :) Looks good, is the boost library 'heavy' or not?

---

### Post by nvteighen on 2011-09-09
> **MG&TL said:**
> Recently, I was reliably informed that the system() call in C++ (from #include <stdlib.h>), was not necessary. And it was implicated that almost all programming could be done in bash.

Thoughts/feelings on this, please.

First, that would be cstdlib in C++, not stdlib.h (which is C). Yes, both define the same interface, but the former is designed to work with C++, while the latter might not. For the C Standard header xxxx.h, its C++ equivalent is cxxxx.

Second. The problem with system() is that it makes your program delegate functionality to another program without letting you control anything of it, save for specifying command line arguments to alter its behavior. This renders your C++ program just a shell script... so if you're going for these route, you better use a language meant for shell scripting, like bash.

But in C++ or general programming languages you don't want that. You usually want to control functionality to some extent. So, the ideal thing is to use libraries, because they allow you communication through data structures. Of course, libraries don't give you 100% control (if you want 100% control, implement everything yourself... from the BIOS to your program), but they do give you a lot of control over the information flow of your program. When you're given an API, you're given a whole new catalogue semantic units you can use in your program as if they were defined by you according to the language's parameters. All of this is valid for both proprietary and Free Software libraries.

In UNIX and Unix-like OSs, almost every single program is written as a shared library and a separate interface executable... Check the repos and you'll usually find the library you need. And if not, use Google.

When you don't have a library available, the best thing to try is popen(). popen() works by allowing you to control the program's I/O... only if it supports POSIX pipes. But of course, this is very limited, but it gives you some way to interact with the other program. So, only use system() when libraries and popen() aren't available.

(Though sometimes, in that case, you should think whether you shouldn't develop that missing library yourself...).

> **MG&TL said:**
> Is there a manpage for boost() somewhere? :) Looks good, is the boost library 'heavy' or not?

Boost is not 'heavy' because it's a template library. It will slow down compiling a lot, though.

I don't think it has a manpage, but Google for the API docs. It's a pretty well-known library.

---

### Post by Bachstelze on 2011-09-09
[http://www.cplusplus.com/articles/j3wTURfi/](http://www.cplusplus.com/articles/j3wTURfi/)

---

### Post by karlson on 2011-09-09
> **MG&TL said:**
> Is there a manpage for boost() somewhere? :) Looks good, is the boost library 'heavy' or not?

[http://www.boost.org](http://www.boost.org)

---

### Post by karlson on 2011-09-09
> **MG&TL said:**
> It was what I got out of our conversation.

OK, so if you're not suggesting that I code in bash, and you say that system is not necessary, what's the [other] convenient way of say, copying a file in C++?


Example 1 (no bashing I know it's all sorts of problematic)
```

pid_t pid = fork();
if( !pid )
{
    execlp("/bin/cp", "fname1", "fname2", NULL);
}

```

Example 2
```

FILE *src = fopen("source_file", "rb");
FILE *dst = fopen("source_file", "wb");
char buffer[65536];

while(!feof(src))
{
    int num_read = fread(buffer, sizeof(char), sizeof(buffer), src);
    int num_written = fwrite(buffer, sizeof(char), sizeof(buffer), dst);
}

```

Checking for errors and generally making code safe would be up to you.

> 
Initially, I started out with minimal system() calls, simply writing to a script in /tmp, then executing that at the end with system(), but then I realised it was much easier simply to use system() all the way through, and it has been cited as 'the way to use bash in C++' by many experienced forum members (found via an internet trawl), hence I have been using system()...


And they were correct although may not necessarily be bash that is being called.  system() simply calls your shell and executes the text you pass in as a script.


> 
If everyone used bash to write their programs with, I would take your point

Anyone want to enlighten people about the history of the discussion that seem to be happening?

---

### Post by MG&amp;TL on 2011-09-11
OK, thanks people! I've looked at all the links and things, and they're awesome. Some of the stufff is WAY over my head, but isn't everything?

Thread solved.

---

