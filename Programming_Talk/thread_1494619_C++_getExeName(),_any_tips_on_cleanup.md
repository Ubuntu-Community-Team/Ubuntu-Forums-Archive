---
title: "C++: getExeName(), any tips on cleanup?"
date: 2010-05-27
forum: Programming Talk
---

### Post by James78 on 2010-05-27
Hi, I just wrote a pretty inelegant function, that returns the exe's name, and only it, no path whatsoever. I finally got it to work after a stupid buffer overflow error (I forgot to account for increasing the size of char when I used strncat).

Anyways, from me looking at this code, it's not exactly elegant lmao, do you guys have any tips on cleaning it up, perhaps making it more efficient and readable? I followed the C++ standard guidelines, but the guidelines are less prominent here because of what I was doing and where I was doing it. This took me quite about 8 hours to finally figure out how to do this, as /proc/self/exe, or /proc/<pid>/exe, argv[0] and other 'solutions' weren't exactly very good considering they either didn't work or returned the full path, and I only wanted the exe name. I'm new to C++ right now so... :)
```
// Kludgy.. Gets the exe's filename
string getExeName()
{
    stringstream szBuffer;
    szBuffer << getpid() << " c";
    string szExePid = szBuffer.str();
    char szPsCommand[30] = "ps -o command= -p ";
    strncat(szPsCommand, szExePid.c_str(), sizeof(szExePid.c_str()));
    FILE* fPsOutput = popen(szPsCommand, "r");
    char szPsOut[50];
    fgets(szPsOut, 50, fPsOutput);
    string szPsOutput = string(szPsOut);
    return szPsOutput;
}
```

---

### Post by dwhitney67 on 2010-05-27
Here's what I think is a better solution:
```

#include <unistd.h>    // for readlink
#include <cstdlib>     // for atoi
#include <cerrno>      // for errno
#include <cstring>     // for strerror

#include <sstream>
#include <iostream>


int main(int argc, char** argv)
{
   const pid_t pid = static_cast<const pid_t>(atoi(argv[1]));

   std::stringstream oss;
   oss << "/proc/" << pid << "/exe";

   char actual[1024] = {0};

   ssize_t size = readlink(oss.str().c_str(), actual, sizeof(actual) - 1);

   if (size != -1)
   {
      actual[size] = '\0';
      std::cout << "Process with pid " << pid << " is located at: " << actual << std::endl;
   }
   else
   {
      std::cerr << strerror(errno) << std::endl;
   }

   return 0;
}

```

---

### Post by trent.josephsen on 2010-05-27
> **James78 said:**
> 
```
strncat(szPsCommand, szExePid.c_str(), sizeof(szExePid.c_str()));
```
Does this even work?  sizeof is a compile time operator and the size of the string can't be determined until run time.  Doesn't std::string have a size() or length() method to save you allocating new memory for a C string which you then immediately count the bytes in and then discard?

*EDIT:  Whoops, didn't realize that C++ sizeof is apparently not evaluated until run time.  Guess it's not a bug.  Nevertheless, it's still poor practice.*

That aside, what's wrong with taking argv[0] and splitting it on "/"?

---

### Post by James78 on 2010-05-27
> **trent.josephsen said:**
> Does this even work?  sizeof is a compile time operator and the size of the string can't be determined until run time.  Doesn't std::string have a size() or length() method to save you allocating new memory for a C string which you then immediately count the bytes in and then discard?

*EDIT:  Whoops, didn't realize that C++ sizeof is apparently not evaluated until run time.  Guess it's not a bug.  Nevertheless, it's still poor practice.*

That aside, what's wrong with taking argv[0] and splitting it on "/"?
I heard argv[0] was very unreliable, it just makes the code easier to assume it's always (at least) the exe name OR the full path and nothing else. Point taken from using sizeof, from looking at some documentation on it, you're right, I'll look for something more reliable and better. :P

Take this for example.. Say another process initializes my program, which uses argv[0], I've seen that some processes actually change argv[0]'s contents, which results in undefined behavior. But I don't believe the problem should be there if I use say, a constant symlink like /proc/self/exe to get the path and name (and I'm not currently expecting the code to go to another type of system where that doesn't exist.. At least not yet).

> **dwhitney67 said:**
> Here's what I think is a better solution:
```

#include <unistd.h>    // for readlink
#include <cstdlib>     // for atoi
#include <cerrno>      // for errno
#include <cstring>     // for strerror

#include <sstream>
#include <iostream>


int main(int argc, char** argv)
{
   const pid_t pid = static_cast<const pid_t>(atoi(argv[1]));

   std::stringstream oss;
   oss << "/proc/" << pid << "/exe";

   char actual[1024] = {0};

   ssize_t size = readlink(**oss.str().c_str()**, actual, sizeof(actual) - 1);

   if (size != -1)
   {
      actual[size] = '\0';
      std::cout << "Process with pid " << pid << " is located at: " << actual << std::endl;
   }
   else
   {
      std::cerr << strerror(errno) << std::endl;
   }

   return 0;
}

```
Haa, I didn't know you could do that (bolded), I could've saved me a variable lol. Anyways, thanks, I'll take a look at it. :)

---

### Post by MadCow108 on 2010-05-27
> **trent.josephsen said:**
> 

*EDIT:  Whoops, didn't realize that C++ sizeof is apparently not evaluated until run time.  Guess it's not a bug.  Nevertheless, it's still poor practice.*

this is not correct. sizeof in C++ is the same as in C, evaluated at compile time, even when dealing with polymorphic types (-> take care of slicing)
It is a bug.

I recommend using strings all the way, saves you all these buffering issues.
e.g. instead of strcat just do this with two strings:
str1 += str2;

---

### Post by James78 on 2010-05-27
> **MadCow108 said:**
> this is not correct. sizeof in C++ is the same as in C, evaluated at compile time.
It is a bug.

I recommend using strings all the way, saves you all these buffering issues.
e.g. instead of strcat just do this with two strings:
str1 += str2;
Thankss. Criticism is very helpful, it helps us fix the problems and make things better in the future. I would've used strings all the way, but most of the C functions (and many others too) require a char* type.. Heh, no one noticed that I didn't use pclose to close the FILE*.

---

### Post by MadCow108 on 2010-05-27
thats what c_str() is for
it returns a cstring compatible with all C functions expecting standard cstrings

maybe you don't know, also C++ vectors are fully compatible with C.
To pass them into functions use this:
some_c_function(&vec[0])

---

### Post by James78 on 2010-05-27
> **MadCow108 said:**
> thats what c_str() is for
it returns a cstring compatible with all C functions expecting standard cstrings

maybe you don't know, also C++ vectors are fully compatible with C.
To pass them into functions use this:
some_c_function(&vec[0])
You got a point there. :) Using that, I saved a few variables and conversions.. Too bad that if it's gonna be writing it to the c_str() it can't work though... :(

---

### Post by dwhitney67 on 2010-05-27
> **James78 said:**
> Too bad that if it's gonna be writing it to the c_str() it can't work though... :(

Stick to the API when calling a function; if it requires a "char*", then of course you cannot pass it an STL string's c_str() pointer.  The c_str() returns a "const char*".

The STL string supports many types of constructors, allowing you freely to convert a C-style string (ie "char*" or "const char*") to an STL string.  Thus in the example I provided earlier, this would work:
```

std::string getProcessName()
{
   std::stringstream oss;
   char actual[1024] = {0};

   oss << "/proc/" << getpid() << "/exe";

   // from the C library API:
   //
   //        ssize_t readlink(const char *path, char *buf, size_t bufsiz);
   //
   ssize_t size = readlink(oss.str().c_str(), actual, sizeof(actual) - 1);

   // need to null-terminate the string, because the API says so.
   //
   actual[size] = '\0';

   // this will be converted to an STL string.
   //
   return actual;
}


int main()
{
   std::string procFullName = getProcessName();

   // ...
}

```

---

### Post by James78 on 2010-05-27
Awesome, thanks. I was trying to figure out how to use the STL, then I thought, just read the entire documentation for it. DOH! Either way, you showed me some useful stuff, like making a char* and returning it with the function defined as returning string, and it works great. Anything that can remove all the clutter I had is good. I significantly reduced my clutter already! Thanks. :)

Could you explain why:

You set char actual to all 0?

---

### Post by trent.josephsen on 2010-05-28
> **James78 said:**
> I heard argv[0] was very unreliable, it just makes the code easier to assume it's always (at least) the exe name OR the full path and nothing else. Point taken from using sizeof, from looking at some documentation on it, you're right, I'll look for something more reliable and better. :P

Take this for example.. Say another process initializes my program, which uses argv[0], I've seen that some processes actually change argv[0]'s contents, which results in undefined behavior. But I don't believe the problem should be there if I use say, a constant symlink like /proc/self/exe to get the path and name (and I'm not currently expecting the code to go to another type of system where that doesn't exist.. At least not yet).

My question would be, so what if the parent process calls your program with a different name?  Shouldn't you be making accommodations for that anyway?  Good practice dictates that a program shouldn't break just because you change the name of the executable.  For that matter, if you're trying to get the executable name at run time, aren't you assuming that it's not necessarily going to be the same every run?  And how is a user supposed to pass your program a different name if argv[0] doesn't work?

I'm considering something like busybox, which is a single binary but acts differently depending on the name it's called with -- ls, mv, sh, etc.  Is this what you're aiming for or are you doing something weird?

---

### Post by James78 on 2010-05-28
Actually, the binary name is not dependent on the program working. It was just a little nice thing I thought would be cool for the printing of my usage statement (the program name). Still the method used would still have to be reliable of course, and from reading around people said that argv[0] wasn't the most reliable method around. I suppose there's still no point in bothering though lol, except that it DOES give me more practice.

And you're right, programming in such a manner that the program working would be dependent on knowing the binary name _would_ be bad practice (in general, I'm sure there's exceptions to everything).

> My question would be, so what if the parent process calls your program with a different name? Shouldn't you be making accommodations for that anyway?For one, I actually do plan to create a special argument that's 'hidden' from the users eye or printUsage() statement, that allows me to control the program through a GTK/QT4 interface. I'm gonna be creating a GUI later on for it. If a parent process does call my program on the command line (parent process being the GTK/QT4 interface), it wouldn't matter if argv[0] was wrong in that case, because the instance of the program on the command line isn't going to be used or seen from the users perspective anyways (and my program doesn't care to print the usage because it can't comprehend anything), this was more for the user operating it on the command line, still though, I wanted a pretty reliable way to get the information, and this was the best way I could find considering I didn't want to (or know how to really) find the LAST / in the string and cut off everything past it (I suppose there IS strchr, but still don't have any idea how to cut off everything before it...), otherwise I might consider argv[0], as it would work just as well for me in this case.

> For that matter, if you're trying to get the executable name at run time, aren't you assuming that it's not necessarily going to be the same every run? And how is a user supposed to pass your program a different name if argv[0] doesn't work?Actually yes, that would be the assumption, it's sorta stupid I know, since that wouldn't be the case here anyways, I just wanted my printUsage to always be right. Well, I suppose the user COULD pass a different name by calling the CLI mode of my GUI app, but that'd just be silly considering you won't ever see a single output statement from my complete CLI app from the CLI mode of the GUI app, so there'd be no point in worrying about that. As for sending a different name on the CLI of the main CLIj app, we all know that wouldn't be needed. :)

Ya. it doesn't make sense, I just wanted a "always right" printUsage.

---

### Post by trent.josephsen on 2010-05-28
> **James78 said:**
> Ya. it doesn't make sense, I just wanted a "always right" printUsage.

The point of my post was, what is the "right" name of the executable?  If /proc/self/exe doesn't point to the same binary as argv[0], who's to say which one is "right"?  Keep in mind that someone could just 'cp bin/yourscript bin/otherscript' and voila, you'd have a different name in /proc/self/exe.  Then suppose he performs 'ln -s otherscript bin/yetanother' and the end user calls yetanother.  argv[0] would contain "yetanother", /proc/self/exe would point to "bin/otherscript", and neither one would be the name you first gave it.  In that case, what would be "right"?

Plus, argv[0] is portable.

---

### Post by dwhitney67 on 2010-05-28
> **James78 said:**
> ... I just wanted my printUsage to always be right.
You wasted my time for this ****??

---

### Post by James78 on 2010-05-29
> **trent.josephsen said:**
> The point of my post was, what is the "right" name of the executable?  If /proc/self/exe doesn't point to the same binary as argv[0], who's to say which one is "right"?  Keep in mind that someone could just 'cp bin/yourscript bin/otherscript' and voila, you'd have a different name in /proc/self/exe.  Then suppose he performs 'ln -s otherscript bin/yetanother' and the end user calls yetanother.  argv[0] would contain "yetanother", /proc/self/exe would point to "bin/otherscript", and neither one would be the name you first gave it.  In that case, what would be "right"?

Plus, argv[0] is portable.Yea. I guess as I said earlier, I wouldn't be so against using it if I could only figure out how to find / and strip everything, and I'd prefer to use strings so.. Guess it's time to do some researching!

> **dwhitney67 said:**
> You wasted my time for this ****??Sorry. :( It wasn't a waste though, trust me, it gives me better practice and insight on how to code better. It may be "pointless", but these "pointless" skills become useful when you are learning, and thus become useful and not pointless at all.

---

