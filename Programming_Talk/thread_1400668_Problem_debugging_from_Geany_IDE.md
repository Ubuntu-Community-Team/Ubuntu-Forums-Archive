---
title: "Problem debugging from Geany IDE"
date: 2010-02-07
forum: Programming Talk
---

### Post by resander on 2010-02-07
On Ubuntu 8.10 using Geany 0.18 and geanygdb 0.0.2.

I am totally new to Geany and Geanygdb (want to see what they can do) and have just downloaded and built these from sources. 

Geany 0.18 works and I can see the debugging sidebar in the side panel.

On startup only the Load and Options are active in the debugging sidebar, all other entries are inactive/greyed. When I give the program executable name to Load, the Unload, Run, Watches, Break and Environ functions also become active.

On click of Run the program runs to completion with the following appearing in the compiler messages area:

Starting gdb (pid=24814)
This GDB was configured as "i486-linux-gnu".
"gnome-terminal"  "--title"  "Debug terminal"  "-x"  "/usr/local/bin/geanygdb_ttyhelper"  "/home/ken/.config/geany/plugins/debugger/24712.tty"
Attaching to terminal /dev/pts/1
Current language:  auto; currently asm
Started target process. (pid=24822)
Program exited normally.
Target process exited. (pid=24822; code=0)

The output from the test program in /home/ken/projects/geanytest/main.c

```

int main(int argc, char** argv)
   {
   int a = 1 ;
   int b = 2 ;
   int c = a+b ;
   printf ( "c=%d\nPress any key\n" , c ) ; 
   int ch= getchar ( ) ;  
   return 0;
   }     

```

to the gnome-terminal (selected this from geanygdb Options) was correct.

But I could not set breakpoints. When I placed the caret/cursor on line 26 (int b=2;) and clicked Breaks then an Add BreakPoints dialog popped up with /home/ken/projects/geanytest/main.c preset for Filename and 26 preset for Line number. On clicking OK I get error 'No source file named /home/ken/projects/geanytest/main.c'.

I don't know what is causing this.
Would be grateful for advice.

---

### Post by SigmaSanti on 2010-02-07
Have you set the debugging flag when you compile?
I had similar problems, but I'm running windows right now, i will try and respond with more info when I find what I did to get it to work.

btw Geany dbg is not that good, its very sensitive about commands and lacks options that more advanced debuggers included in codeblocks (c/c++), netbeans, and eclipse.
However, you probably enjoy geany for its speed, small size, and compatibility. Which could explain why its debugger is not so good right now.

Geany rocks, dont get me wrong, I love using it, but its debugger is still a plugin, an extra that needs work.

---

### Post by SigmaSanti on 2010-02-07
Here are the steps I went through to make it work:

1. go to Build->Set Includes/Arguments and change it so that there is the -g flag on build and compile, ex.
```
gcc -g -o "%e" "%f"
```
2. Build/compile code
3. Go to debugger and select load
4. Select compiled file
5. Then press "Breaks" and add a line number (I used line 3 of your example code)
6. Press "Run" on the debugging panel
7. The code should run, and then display "breakpoint hit" at the top of the panel
8. At this point you can add a watch for a variable, just press watch, and then enter the variable name.
9. add another breakpoint in order to see if the variable gets modified. (or use the step button to go line by line)

Notes:
1. You can only add watches while its running.
2. You can only add watches in the current function where a breakpoint is set.

These two problems are deal-breakers for me, so I use codeblocks when I want to debug a program. Otherwise I use geany for coding everything else.

Since I am writing small programs I usually use print statements to debug, some consider this bad practice, but its necessary if you want to debug easily with geany right now.

Hopefully they will develop a better dbg plugin for geany in the future.

---

### Post by resander on 2010-02-08
SigmaSanti:
Many thanks.
The problem was I had put the -g option into the compile step 'gcc -Wall -g -c "%f"'. Debugging worked when I moved it into the build step 'gcc -Wall -g -o "%e" "%f"'.

Geany is neat, but it does not support multi-file projects like codeblocks, VC6, Visual Studio Express etc and the debugging is not working as well as it could, for example during my very brief test-drive noticed that:

  - current position is lost in source code following a context switch to the Stack
  - displaying data in a stack frame is tedious; it is not possible to step
    while stack/frame window is displayed. Better if all data in
    the current stackframe is displayed modelessly. 
  - could not Run-to a line in another source module. Also Run-to button is not
    active until a breakpoint is hit. 

These affect the useability of the debugger, but are probably easy to fix.
The real show-stopper is lack of support for multiple source files a la codeblocks etc, so I will stick to codeblocks. 

However, with multiple source files & library project support and improved debugging Geany will be a very strong contender.   

I did a bit of googling on 'gdb' and found useful documents. In a GDB wiki there were references to stand-alone GUI front-ends for GDB. I installed KDbg via Ubuntu Synaptic. It is designed for Kubuntu, but works well on Ubuntu too with the executable generated by geany and gcc. There is a user manual at [www.kdbg.org](www.kdbg.org).


Sigma Santi:
I really enjoyed your prophetic quotes!

---

