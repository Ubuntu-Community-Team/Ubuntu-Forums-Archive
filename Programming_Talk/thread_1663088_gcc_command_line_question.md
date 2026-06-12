---
title: "gcc command line question"
date: 2011-01-09
forum: Programming Talk
---

### Post by azrael2000 on 2011-01-09
Hi All.
 
I the process of learning objective c I have found with linux I have to use the following command line to build my program.
 
```
 
gcc `gnustep-config --objc-flags` -lgnustep-base hello.m -o hello

```
 
and to run the program use
 
```
 
./hello

```
 
I have read the man gcc to try and find out what all the flags mean, but can't seem to find them... or more accurately, a good description of them.
 
Can you tell me what the flags mean, and why I have to use ./<program name> to run the program?
 
Even when I am in the graphic interface, and see the .exe, I can't run it.
 
Any help is greatly appreciated.
 
Regards

---

### Post by cipherboy_loc on 2011-01-09
> **azrael2000 said:**
> 
```
 
gcc `gnustep-config --objc-flags` -lgnustep-base hello.m -o hello

```
 

I don't know everything, but it breaks down to something like this:

gcc -- Run the main GCC program from the bash command line.

`gnustep-config --objc-flags` -- This (because of the back ticks (`)) runs gnustep-config, with an argument of --objc-flags, and what ever the output is gets added to GCC as arguments.

-lgnustep-base -- Probably an argument to include the gnustep-base library.

hello.m -- Which file (source code) you want to compile.

-o hello -- -o is the output flag, so -o makes it write to hello rather than a.out.

> **azrael2000 said:**
> 
```
 
./hello

```
--snip--
Can you tell me what the flags mean, and why I have to use ./<program name> to run the program?


Bash (your command prompt) is set up such that it has a couple of places that it searches for programs, and that is it. These places are stored in the $PATH variable:

```
echo $PATH
```
will print the $PATH variable to the screen.

If you notice, you don't see ./ as a directory in $PATH. To make it a place that Bash searches:
```
echo -e '\n\nPATH="$PATH:./"'
```

Now you can (on any project) type the name of the program (without the leading ./) and it will run, though first it needs to be executable:

```
chmod +x ./name_of_program
```

> **azrael2000 said:**
> 
Even when I am in the graphic interface, and see the .exe, I can't run it.
Any help is greatly appreciated.
Regards

Two possible reasons for this:

1) It is not marked as executable:
```
chmod +x ./path_to_program
```
from the terminal.

2) Your program runs, but because it is such a short program, that it doesn't stay open long enough for you to see it. Add a sleep, with a long enough pause, at the end of your program.


Hope this clears some things up,
Cipherboy

---

### Post by azrael2000 on 2011-01-09
Hi Cypher.
 
It is a start.  <smile>
 
Thank you very much.
 
Regards

---

### Post by cipherboy_loc on 2011-01-09
I ran `gnustep-config --objc-flags` from the terminal and got:

> -MMD -MP -DGNU_RUNTIME=1 -DGNUSTEP_BASE_LIBRARY=1 -D_REENTRANT -fPIC -Wall -DGSWARN -DGSDIAGNOSE -Wno-import -g -O2 -fno-strict-aliasing -fexceptions -fobjc-exceptions -D_NATIVE_OBJC_EXCEPTIONS -fgnu-runtime -I. -I/home/username/GNUstep/Library/Headers -I/usr/local/include/GNUstep -I/usr/include/GNUstep

For a few more flags:

-I -- Makes GCC search in the following directory (~/GNUstep/Library/Headers, etc) for headers.

-O[0-3] -- Different levels of optimization. -O2 is the highest stable optimization (and hence default). -O3 on Gentoo when emerging packages tend to be unstable (at least on my computer). 

And thats all I know about this batch of GCC flags,
Cipherboy

---

