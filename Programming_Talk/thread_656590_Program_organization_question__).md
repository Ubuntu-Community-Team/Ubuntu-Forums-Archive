---
title: "Program organization question ?? :)"
date: 2008-01-02
forum: Programming Talk
---

### Post by nathandelane on 2008-01-02
I am a relatively seasoned programmer, in that I have used many languages to accomplish many tasks, from scripting to compiling languages, from Windows to Linux and the Web, from BASIC to C++, and from Java to C#. I know how to do a lot of things, but one thing that always hangs me up is program organization.  Perhaps that isn't even the correct terminology.

Let me explain. I am trying to write a shell-like program (similar in some ways to BASH, irb, or interactive python shell) and I am wondering, should I separate a library of commands out as separate modules and make the program extensible in this way? Should I create a dictionary of keywords?  How should I go about parsing - should it be a part of the main program or should it be its own module?

If anybody out there has ever written an interactive shell-like program, could you please shed some light on how you organized it?  I have looked at the source code for BASH briefly, but came to the conclusion that I didn't need a lot of the things that were in there, and I also saw a lot of connections with the kernel api.

I have attempted to write this program in Ruby, Java, and C, and I just keep getting stumped. I want to write it in a quality that is somewhat professional at least.

Thanks,

Nathan

---

### Post by Wybiral on 2008-01-02
It would help to know more about your goal. Is this going to be some kind of interactive command line for debugging another program? Do you want it to be a valid replacement for BASH itself? Do you just want to create your own "language" to play around with?

Then you have other decisions like how you want to add new functionality to the distributed project. Do you want the commands to be actual programs (like BASH) that must exist in an executable directory? Do you want them to be dynamic libraries that can actually call functions in your program? Do you want them to be scripted in somehow?

What is your goal, what is the purpose?

---

### Post by pmasiar on 2008-01-03
Coding (writing valid syntax) is simple, but program design is complex art.

Best way to learn how parts are organized is to study existing project like you are interested, try to make changes, so you will see and experience consequences of designer's decisions.

Engineering is about balancing competing requirements. It is also art, experience is learned from past mistakes.

---

### Post by nathandelane on 2008-01-03
You have some good points. Here (hopefully it worked) is an image pertaining to the high level design of this project:

[IMG]http://i259.photobucket.com/albums/hh297/nathandelane/avshell_diagram.png[/IMG]

I want to do a couple of things in this project:

[LIST=1]
[*]Create my own language that is similar to other scripting languages
[*]Make the language interpreted by an interpreter
[*]Make the language testable in an interactive shell (like irb or interactive python shell)
[/LIST]

The system I am trying to make is a structured programming system for text-based video games. Two things I am trying to accomplish for myself are language design, and language interpretation/processing.

This the start of my system - I think that I want to make it modular in that is uses separate modules, but not necessarily separate executables, rather scripted modules.  There is still a lot of unknown I suppose. Does this help you help me a little bit?

(The diagram is just a pseudo diagram - I know it's not proper UML)

---

### Post by pmasiar on 2008-01-03
Most flexible core system for this kind of tasks IMHO is Forth: it was designed to be extended into small specialized languages, and interactive shell is its base. Another one will be Perl6 :-)

Easiest could be Python, just start Python shell and "from MyGameShell import *" which you will wrote :-)

---

### Post by popch on 2008-01-03
The main reason why you do not arrive at a clear picture of the overall structure of your program could be that you have not yet a clear understanding of the tasks it is to accomplish.

To begin just someplace, you could start designing the language your system is to process, interpret and execute.

@pmasiar: that's been a long time since someone mentioned Forth. And in keeping somewhat in the vicinity of the thread, I even designed parts of a language I whimsically decided to call 'Neuf'.

---

### Post by Wybiral on 2008-01-03
> **nathandelane said:**
> Does this help you help me a little bit?

Not really because I still don't know why you're doing this. It sounds like you need an interactive scripting language for text-based games? Why not just use Python? Writing your own interpreter (and thus, language) will be a ton of work. I would use one that already exists.

If you need a special source of input (as in, not from the command line) then you can create your own input system, but I would still use an established interpreter to actually execute the code.

Here's a simplified example of using the "code" module in Python to create a customizable version of the interactive shell:

```

import code

class Shell(code.InteractiveConsole):
    def __init__(self):
        code.InteractiveConsole.__init__(self)

    def push(self, line):
        if line.count("import"):
            code.InteractiveConsole.push(self, "raise 'Import not allowed!'\n")
        else:
            code.InteractiveConsole.push(self, line)

shell = Shell()
shell.interact(banner="Hello, welcome to my Python shell!")

```

There are better ways to filter things, but as an example, the above will prevent the use of "import".

---

