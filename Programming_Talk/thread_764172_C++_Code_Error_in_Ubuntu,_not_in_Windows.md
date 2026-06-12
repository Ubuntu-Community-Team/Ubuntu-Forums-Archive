---
title: "C++ Code Error in Ubuntu, not in Windows"
date: 2008-04-23
forum: Programming Talk
---

### Post by seuzy13 on 2008-04-23
I've only very recently begun C++, and I began in a Windows environment. After switching to Ubuntu and compiling one of my programs, I got an error that did not exist in Windows. All of my other programs appeared to be running fine. 

Anyway when I run the very simple [_[COLOR="Blue"]hangman[/COLOR]_]("http://www.mediafire.com/?7ylz2mxw9m4") program I wrote, and after going through the first few prompts, I get this error:
[COLOR="Red"]terminate called after throwing an instance of 'std::bad_alloc'
  what():  std::bad_alloc
Aborted (core dumped)[/COLOR]

Anyone know a fix for this? Is there a subtle difference between Ubuntu and Windows' handling of C++ that I'm not aware of?

Thanks all.

EDIT--I should also include the [[COLOR="Blue"]_sortsearch.h_[/COLOR]]("http://www.mediafire.com/?ztmzokxag2s") header file which contains the "resize" function, just in case.

---

### Post by Npl on 2008-04-23
well, i dunno if the resize-function is doing what you intended, ever used a debugger?
Hint: you have 2 definitions of i, and resize is called with an uninitialized variable.

but regarding differences Windows/UNIX - its more of a difference in compiler-settings. If an allocation fails, there are 2 possibilities
1) either the function that failed to (re-)allocate returns NULL. (Or just silently fails if it has no return value)
2) or it throws an exception.

I guess your Windows compiler does 1, your Unix compiler does 2. there should be option for the compilers to change that behaviour.

---

### Post by hod139 on 2008-04-23
Without seeing the code, there isn't much help I can offer.  Try compiling the code with debug flags enabled:
```
g++ -g foo.cpp
```

and running it in the debugger
```
gdb ./a.out
```

In the debugger prompt type 'r' (without the quotes) for run and press enter.  When it crashes, type 'bt' for backtrace.  This will tell you where the crash happens.  If it's a pesky memory bug, you can also try running it in valgrind to find out of bounds and other memory errors.  Install valgrind (and alleyoop for a nice gui frontend)  and run it as 
```
 alleyoop ./a.out 
```

---

### Post by seuzy13 on 2008-04-24
After using backtrace, I get this message.
[COLOR="Red"]
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7cf8875 in raise () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7cfa201 in abort () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7f046e0 in __gnu_cxx::__verbose_terminate_handler ()
   from /usr/lib/libstdc++.so.6
#4  0xb7f01f65 in ?? () from /usr/lib/libstdc++.so.6
#5  0xb7f01fa2 in std::terminate () from /usr/lib/libstdc++.so.6
#6  0xb7f020ca in __cxa_throw () from /usr/lib/libstdc++.so.6[/COLOR]

If I'm reading this correctly, it looks like a library problem. Perhaps I don't have a library file on ubuntu that I had on Windows? That's about all I can make of it.

> Without seeing the code, there isn't much help I can offer.
I included links to the code in my original post. :-)

Also, Npl, only two of my functions are something other than void, and they both return a value. So that should not be a problem.

Thank you!

---

### Post by lnostdal on 2008-04-24
i haven't looked at you code at all(#1), but i'd say one of your destructors is throwing an exception .. or something .. 

[http://yosefk.com/c++fqa/exceptions.html#fqa-17.3](http://yosefk.com/c++fqa/exceptions.html#fqa-17.3)


#1: there are less annoying pastebins out there .. specifically made for code, this for instance: [http://paste.lisp.org/](http://paste.lisp.org/)

---

### Post by Npl on 2008-04-24
> **seuzy13 said:**
> After using backtrace, I get this message.
[COLOR="Red"]
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7cf8875 in raise () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7cfa201 in abort () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7f046e0 in __gnu_cxx::__verbose_terminate_handler ()
   from /usr/lib/libstdc++.so.6
#4  0xb7f01f65 in ?? () from /usr/lib/libstdc++.so.6
#5  0xb7f01fa2 in std::terminate () from /usr/lib/libstdc++.so.6
#6  0xb7f020ca in __cxa_throw () from /usr/lib/libstdc++.so.6[/COLOR]

If I'm reading this correctly, it looks like a library problem. Perhaps I don't have a library file on ubuntu that I had on Windows? That's about all I can make of it.


I included links to the code in my original post. :-)

Also, Npl, only two of my functions are something other than void, and they both return a value. So that should not be a problem.

Thank you!First, its not called **back**trace for a no reason, the offending code is typically way down. 

And secondly, atleast 1 horrible bug is in the resize-method

```
    int i;
    for (int i=words.size(); words[i-1]==""; i--) {
    }
    words.resize(i);
```

Note you have 2 definitions **int i** here, the one used in the for-loop only is dead when you call words.resize(i). Read up about scopes in C++.
In the end you call resize i with a uninitialized (means as good as random) value. Which will just silently do nothing if it fails (some MS-Compilers default to this) or throw the bad_alloc-Exception you are seeing (Standard C++).

Also words[i-1] might get called with negative indexes.

---

### Post by samjh on 2008-04-24
> **Npl said:**
> And secondly, atleast 1 horrible bug is in the resize-method

```
    int i;
    for (int i=words.size(); words[i-1]==""; i--) {
    }
    words.resize(i);
```

Note you have 2 definitions **int i** here, the one used in the for-loop only is dead when you call words.resize(i). Read up about scopes in C++.
In the end you call resize i with a uninitialized (means as good as random) value. Which will just silently do nothing if it fails (some MS-Compilers default to this) or throw the bad_alloc-Exception you are seeing (Standard C++).

Also words[i-1] might get called with negative indexes.

Sounds like this problem:

[http://www.wesnoth.org/wiki/CodingStandards#Respect_for_loop_scoping_of_different_platforms](http://www.wesnoth.org/wiki/CodingStandards#Respect_for_loop_scoping_of_different_platforms)

---

### Post by Npl on 2008-04-24
> **samjh said:**
> Sounds like this problem:

[http://www.wesnoth.org/wiki/CodingStandards#Respect_for_loop_scoping_of_different_platforms](http://www.wesnoth.org/wiki/CodingStandards#Respect_for_loop_scoping_of_different_platforms)Nope, that would just throw errors when trying to compile with a misunderstanding compiler =)
Its simply a scope problem - the compiler needs to figure out which variable you mean with "i", as in the for loop there are 2 defined variables called "i"
It will pick the "most recently defined" so to speak, any decent compiler will do so while warning you about having 2 variables with the same name.

---

### Post by seuzy13 on 2008-04-24
> And secondly, atleast 1 horrible bug is in the resize-method

Code:

    int i;
    for (int i=words.size(); words[i-1]==""; i--) {
    }
    words.resize(i);

Note you have 2 definitions int i here, the one used in the for-loop only is dead when you call words.resize(i). Read up about scopes in C++.

I understand what you're saying, and that is something I overlooked and need to fix (Thanks), but it's not the problem here. The resize function I'm calling in the program is for character vectors. You referenced to the string vector resize function, which I'm not using in this instance. However, I did make a few changes that you mentioned which, in the end, fixed the problem at hand. (Changes are in blue)

[COLOR="Red"]void resize(vector<char>& chars) { //resizes vector with blank spots on the end

    int i[COLOR="Blue"]=0[/COLOR];

    for (i=chars.size(); !chars[i]; i--) {

    }

   [COLOR="Blue"] if (i>0)[/COLOR]
       chars.resize(i);

}
[/COLOR]

The program compiles and runs now, but it exits before it's supposed to, and when I run a debug it says "Program exited normally."

Here is what happens in debug mode:

[COLOR="Red"]Would you like the computer to randomly generate a word for you to guess? y
[/COLOR] [COLOR="Blue"]//Before the error was here[/COLOR]
[COLOR="Red"]INCORRECT GUESSES: 
____________
|           |
|           |
|___________|
                         _____
                        |    |
                             |
                             |
                             |
                          ___|___
_ _ _ _ 

What is your guess? a

Program exited normally.
[/COLOR]

Note that the forum is not displaying the box, hook, and spaces like it does when you actually run the program.

At any rate, this doesn't make sense, because even if it exited the while loop in main() for some unforeseen reason, it would have gone on to either print "YOU WON!" or "GAME OVER, YOU LOSE!"

---

