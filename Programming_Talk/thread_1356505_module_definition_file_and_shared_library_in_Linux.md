---
title: "module definition file and shared library in Linux"
date: 2009-12-16
forum: Programming Talk
---

### Post by vgokul on 2009-12-16
Hello all,
            Can you please let me know how to use a module defition file for creation of shared lib(.so) using gcc in Ubuntu?
            I am sorry if this has already been discussed but I did search and did not get some leads.
 
Regards
V.Gokul

---

### Post by nvteighen on 2009-12-16
> **vgokul said:**
> Hello all,
            Can you please let me know how to use a module defition file for creation of shared lib(.so) using gcc in Ubuntu?
            I am sorry if this has already been discussed but I did search and did not get some leads.
 
Regards
V.Gokul

There's no need for that :)

You just code your library... and write your header. Compile using:
```

gcc -fpic -c module1.c -Wall
# so on with all modules your library has been written in
gcc -shared -o libwhatever.so module1.o module2.o ... -Wall

```

All functions are accessible by default. But, the ones declared in the header will allow the compiler to do type-checking and catch some errors at compile-time. If you want to hide a function, you have to declare it **static** in the library's source.

Look at: [http://crasseux.com/books/ctutorial/Building-a-library.html#Building%20a%20library](http://crasseux.com/books/ctutorial/Building-a-library.html#Building%20a%20library)

EDIT: The -fpic or -fPIC flag is needed just for creating dynamic libraries. That flag makes your code Position Independent Code (PIC) which is needed for this stuff. Executables should not be PIC.

---

### Post by vgokul on 2009-12-16
Hello,
        Thanks.
 
I have a bunch of files  most of which I am not the owner out of which I create a library. I have a function which controls the other function calls.  I want to export only this function and not the rest of the functions. Any suggestions how to do it? 
 
All the files are c files.
 
Regards
V.Gokul

---

### Post by dwhitney67 on 2009-12-16
> **vgokul said:**
> 
I have a function which controls the other function calls.

This is referred to as a "wrapper" function.

> 
I want to export only this function and not the rest of the functions. Any suggestions how to do it? 

Unless you have permissions to write to these other files, there is nothing you can do to prevent someone from accessing the other library functions... other than strategically omitting describing these functions from any documentation that you may produce.

---

### Post by nvteighen on 2009-12-16
dwhitney67 is right. The only method that effectively hides a function definition from being introduced in the symbol table is the static declaration. So, if you can't modify the sources, you're lost.

Now, why can't you modify them? Is it a UNIX permissions issue (no write permissions... in that case you can copy the file)? A licensing issue? Or that you don't have access to the source?

---

### Post by vgokul on 2009-12-17
Hello ,
I found an option to selectively exports symbols here [http://www.gnu.org/software/hello/manual/gnulib/Exported-Symbols-of-Shared-Libraries.html](http://www.gnu.org/software/hello/manual/gnulib/Exported-Symbols-of-Shared-Libraries.html)
 
Since I use gcc v > 4.0 it works for me.
 
 As for the files I am not allowed to change them
 
 
Thank you for all your help
V.Gokul

---

### Post by dwhitney67 on 2009-12-17
> **vgokul said:**
> Hello ,
I found an option to selectively exports symbols here [http://www.gnu.org/software/hello/manual/gnulib/Exported-Symbols-of-Shared-Libraries.html](http://www.gnu.org/software/hello/manual/gnulib/Exported-Symbols-of-Shared-Libraries.html)
 
Since I use gcc v > 4.0 it works for me.
 
 As for the files I am not allowed to change them
 
 
Thank you for all your help
V.Gokul

I do not how you are going to get this feature to work.  It is necessary to specify -fvisibility=hidden when compiling the library, whether it be one you can edit or not.  Since you have indicated that you cannot edit the 'other' library, including possibly the Makefile that is used to build it, how are you going to invoke this GCC option?

If you are able to recompile the "untouchable" library with the -fvisibility=hidden option, then all functions will be hidden, unless otherwise specified.  But alas, since you cannot edit the header files of this library, I don't understand how you will make certain functions visible (whereas the others will remain invisible).

With all functions in the "untouchable" library invisible, your second library will not be able to reference them.

In summary, from what I have read, and I may be wrong on this, unless you have full-access to each and every library that you are dealing with, the -fvisibility=hidden option is not suitable.

Good luck with your endeavor.

P.S.  Here's a tar-ball with a simple test.  Assume that you cannot edit the library containing One.h/.cpp.

You can edit Main.cpp, Two.h/.cpp, and the Makefile (I'm being liberal here).

---

### Post by vgokul on 2009-12-17
Hello ,
     In the make file what I do is to compile all the files with the -fvisibility=hidden option while to my wrapper function (which I have control over) I add [SIZE=2][COLOR=#808080][SIZE=2][COLOR=#808080]
__attribute__((visibility("default")))
 
That way only the my wrapper function symbol gets exported (nm -D -C my_lib.so also shows this)
 
Am I missing something here?
 
Regards
V.Gokul
[/COLOR][/SIZE][/COLOR][/SIZE]

---

### Post by dwhitney67 on 2009-12-17
When you state that you compiled all the files with the -fvisibility=hidden, does this include the files in the library that you do not want to export?

Have you tried building an application that links to your library, which in turn must reference the other library (with the hidden functions)??

---

### Post by vgokul on 2009-12-17
I dont have any extra library. What I have is a number of C files and what I do is to provide a wrapper function to control the call to the functions in these C files. I want to create a shared dll of all these files with my wrapper function providing the only interface for an external application. 
 
So what I have done is to create a make file to create the dll but without the -fvisibility option ,along with my wrapper function, other functions were also getting exported. This option seems to let me export only the symbols I want to. I created a small exe to load this dll and symbol and it seems to work.

---

### Post by dwhitney67 on 2009-12-17
> **vgokul said:**
> I dont have any extra library. What I have is a number of C files and what I do is to provide a wrapper function to control the call to the functions in these C files. I want to create a shared dll of all these files with my wrapper function providing the only interface for an external application. 
 
So what I have done is to create a make file to create the dll but without the -fvisibility option ,along with my wrapper function, other functions were also getting exported. This option seems to let me export only the symbols I want to. I created a small exe to load this dll and symbol and it seems to work.

Ok, I understand.  Earlier you indicated that you had a library, presumably containing one or more C files, that you *could not* edit.

So, I gather you have something like:

Hidden.c:
```

void hiddenFunction1()
{
}

void hiddenFunction2()
{
}

```

Wrapper.c:
```

__attribute__((visibility("default")))
void userFunction()
{
   hiddenFunction1();
   hiddenFunction2();
}

```

You then compile these modules using the -fvisibility=hidden, and you are satisfied that only the 'userFunction' is available.

Well, as long as all of these functions, hidden or not, are in the same library, then you will be ok.  If you create separate libraries, then you will have issues.  Your earlier posts seemed to indicate that you were dealing with an additional library of which you were unable to modify.

---

### Post by nvteighen on 2009-12-17
> **vgokul said:**
> I dont have any extra library. What I have is a number of C files and what I do is to provide a wrapper function to control the call to the functions in these C files. I want to create a shared dll of all these files with my wrapper function providing the only interface for an external application. 
 
So what I have done is to create a make file to create the dll but without the -fvisibility option ,along with my wrapper function, other functions were also getting exported. This option seems to let me export only the symbols I want to. I created a small exe to load this dll and symbol and it seems to work.

Isn't then easier to use the static keyword in all those functions you don't want to export??

---

### Post by dwhitney67 on 2009-12-17
> **nvteighen said:**
> Isn't then easier to use the static keyword in all those functions you don't want to export??

(yes!)

---

