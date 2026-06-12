---
title: "Geany won't compile C++"
date: 2011-03-06
forum: Programming Talk
---

### Post by acidblue on 2011-03-06
Ubuntu 10.04 64 bit.

I'm learning C++ and I made a simple program in geany, but I can't get it to compile.
It compiles fine at the command line just not in geany.
I get this error when I try to execute:
./geany_run_script.sh: 5: ./Number: not found.
Number being the name of the program.

Compile>>Build>>Execute is the process I'm using.
Can anyone help?

---

### Post by zenwalker on 2011-03-07
Does the geany build your program rather than running/executing it? Upon compilation by the GCC. A.out or program.out file is produced. That will be used for execution.

---

### Post by acidblue on 2011-03-07
No, Geany does nothing, no files are produced.

---

### Post by zenwalker on 2011-03-07
When you click BUILD option, what happens?

I guess, gcc link isnt happened properly. Was geany installed earliar to GCC?

---

### Post by acidblue on 2011-03-07
Nothing happens when I click Build.
Which is strange cause I can compile and build C programs, just not C++ ones.
GCC and g++ are installed on my system as well as build-essential.
Compiling works fine from command line, so I think this is a Geany problem.

---

### Post by acidblue on 2011-03-07
I've installed Code:Blocks and it compiles C++ just fine.
I prefer Geany as it is so simple and yet useful for beginners like me.

I have Eclipse installed but I don't use it, I find it a bit bloated and 
not as easy to use as Geany or Code Blocks.

I'll use Code Blocks for now, as it seems to be a happy medium between Geany and Eclipse.
But I would like to find a solution to Geany not compiling C++.
If anyone has any ideas please post them.

---

### Post by Milliways on 2011-03-07
> **acidblue said:**
> Ubuntu 10.04 64 bit.

I'm learning C++ and I made a simple program in geany, but I can't get it to compile.
It compiles fine at the command line just not in geany.
I get this error when I try to execute:
./geany_run_script.sh: 5: ./Number: not found.
Number being the name of the program.

Compile>>Build>>Execute is the process I'm using.
Can anyone help?

What is the content of your Build/Set Build Commands/Build commands?

This should be something like:-
```
Compile  g++ -Wall -c "%f"
Build    g++ -Wall -o "%e" "%f"
```

---

### Post by acidblue on 2011-03-07
That's exactly what there are.
But Geany just doesn't want to do it.

---

### Post by Milliways on 2011-03-07
> **acidblue said:**
> That's exactly what there are.
But Geany just doesn't want to do it.

When you execute Build (F9) you should see a message in the Compile Pane, such as (or an error message)

g++ -Wall -o "world" "world.cxx" (in directory: /home/.../Projects/WorldC)

If nothing really happens, select the Terminal pane and type "gcc"

---

### Post by acidblue on 2011-03-07
Compile pane?
I don't see a compile nor a terminal pane.
I only get the terminal when I execute a program.

---

### Post by Milliways on 2011-03-07
> **acidblue said:**
> Compile pane?
I don't see a compile nor a terminal pane.
I only get the terminal when I execute a program.

If you tick View/Show Message Window you will see a pane (which Geany calls an optional message window) at the bottom, which can show the following tabs:

    * Status - A list of status messages.
    * Compiler - The output of compiling or building programs.
    * Messages - Results of 'Find Usage', 'Find Usage' 'Find in Files' and other actions
    * Scribble - A text scratchpad for any use.
    * Terminal - An optional terminal window.

---

### Post by acidblue on 2011-03-08
Thanks for pointing that out my message window was minimized so I couldn't see it.
I can see the error messages, and others now.

I got it to compile.
I had left out [ using namespace std; ] in my program, DOH!

---

### Post by stchman on 2011-03-08
> **acidblue said:**
> Thanks for pointing that out my message window was minimized so I couldn't see it.
I can see the error messages, and others now.

I got it to compile.
I had left out [ using namespace std; ] in my program, DOH!

Also did, you install the build-essential package?

---

### Post by acidblue on 2011-03-09
Yes, of course.

---

