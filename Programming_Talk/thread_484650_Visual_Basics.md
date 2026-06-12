---
title: "Visual Basics?"
date: 2007-06-26
forum: Programming Talk
---

### Post by phizikal on 2007-06-26
Ok, I used to work with visual basics on XP. Now that I am on wonderful Ubuntu, is there any languages or programs that are simular to VB? Is there a working module that I can use to make apps and such easier? Please and thank you!

---

### Post by phizikal on 2007-06-26
No suggestions?

---

### Post by PlatinumPlus on 2007-06-26
There is Gambas and you can import your VB6.0 programs save for some extra components.

---

### Post by phizikal on 2007-06-26
That didn't help.

---

### Post by PlatinumPlus on 2007-06-26
> **phizikal said:**
> That didn't help.

Gambas didn't help :(

---

### Post by phizikal on 2007-06-26
One I can't find it. Two, I am sure I need wine. ANd wine wont let me install due to missing repositories or something,

---

### Post by phizikal on 2007-06-26
ok i have wine installed. how do i run it?
and for tat gambas?

---

### Post by Rui Pais on 2007-06-26
```
sudo apt-get install gambas
```
don't need wine.

With wine you may try to install original MS-VB, but it's complicated... Check wine site for info (and success/failure reports).

Edit:
You can too use Mono. It has a [MonoBasic]("http://www.mono-project.com/VisualBasic.NET_support") (equivalent of Basic from .NET)

---

### Post by phizikal on 2007-06-26
I didn't get it installed, any alternatives. Or you know the problem?

```

root@admin:/home/admin# sudo apt-get install gambas
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gambas

```

---

### Post by Rui Pais on 2007-06-26
> **phizikal said:**
> I didn't get it installed, any alternatives. Or you know the problem?

```

root@admin:/home/admin# sudo apt-get install gambas
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gambas

```

You need to have universe repository enabled. 

I see now you report to use dapper, under your avatar. I think Dapper don't have that enabled by default...
Use synaptic (Settings-> Repositories) or edit your /etc/apt/sources.list, uncommenting (remove symbol # from the beginning of line) of the lines started with 'deb' and that have the word 'universe' on it.

hth

---

### Post by phizikal on 2007-06-26
Ok, gambas installed correctly. But there is alot of errors and it freezes alot.
I also downloaded mono, but I cant find the run. I tried using shell "mono".

```

root@admin:/home/admin# mono
Usage is: mono [options] program [program-options]

Development:
    --aot                  Compiles the assembly to native code
    --debug                Enable debugging support
    --profile[=profiler]   Runs in profiling mode with the specified profiler module
    --trace[=EXPR]         Enable tracing, use --help-trace for details
    --help-devel           Shows more options available to developers

Runtime:
    --config FILE          Loads FILE as the Mono config
    --verbose, -v          Increases the verbosity level
    --help, -h             Show usage information
    --version, -V          Show version information
    --optimize=OPT         Turns on or off a specific optimization
                           Use --list-opt to get a list of optimizations
    --security             Turns on the security manager (unsupported, default is off)

```

---

### Post by PlatinumPlus on 2007-06-26
I think you may also need monodevelop ;)

---

### Post by Rui Pais on 2007-06-26
> **phizikal said:**
> Ok, gambas installed correctly. But there is alot of errors and it freezes alot.

well... thats the universe...
apps there are not very updated, and bugs sometimes stays there "for ever", special for scientific or more technical apps. I usually end up by compiling my one versions that at least are up-to-date and running less buggy. 
If you liked Gambas interface (it's very qt look and feel...) give at look at [Gambas site]("http://gambas.sourceforge.net/") and try to download and compile the last version. When i tried Gambas i remember it run more stable with that than the official ones (it was a long time ago, i use debian then). Instructions on compile are [here]("http://gambas.sourceforge.net/compilation.html").

> 
I also downloaded mono, but I cant find the run. I tried using shell "mono".

mono is made of the compiler and libraries. Compiler is a command line app. It's suppose you make your code with a text editor or some semi-IDE that offers some extras to make work easier. You can try to compile your VB code with a line command... something from mono called mb i think... not sure. 
If you want something like a full IDE you may want to check monodevelop (available using apt-get)... but i don't know it works for basic or just for c#/gtk#. Check mono site for more info/documentation.


Your main problem is that Basic it's not taken much serioulsy under Linux... 
You will have to adapt a lot, and learn new procedures too. 
Most people would tell you that the effort needed would make enough for you to learn something easy and better like python. It's not hard and you can get (for free) an easy way to do GUI apps with a language that it's considered to be more serious and mature then VisualBasic... It's a question on how much you want to do new and how much you may want to port (from your existing applications)

---

### Post by phizikal on 2007-06-26
Thanks, basic gets old and not very many options.
I'll just go ahead and learn python. thanks for the help. :)

---

### Post by Rui Pais on 2007-06-26
No problem :)

Theres a lot of IDE for python too. Check at least boa and eric... there plenty of others, do a search on google or at synaptic.


Good luck 
:)

---

### Post by PlatinumPlus on 2007-06-26
> **phizikal said:**
> Ok, gambas installed correctly. But there is alot of errors and it freezes alot.


You might have to edit your xorg file in /etc/X11 to get rid of some of the errors you see soon after installing Gambas. I think it's a matter of editting out some entries with wacom or something like that. Do a search with the error message and you will get the solution in seconds ;)

---

### Post by pmasiar on 2007-06-26
For python links, check wiki in my sig

---

### Post by hsweet on 2007-06-26
It might be easier to learn a new language than struggle getting VB to work..  Doesn't it have to compile .exe's?  These wouldn't work either without wine or virtualization.  So even if you get the IDE working you still can only write Windows programs.

There are a pile of languages that will run and at least one will probably do what you need + most are cross platform.  Perl, Python, Ruby, Java, C are some off the top of my head. Gambas was mentioned already.

Good luck either way.

---

### Post by Smygis on 2007-06-26
I'd say Python. 
Its a great language. 
And you alredy got it installed.

[www.python.org](www.python.org)

---

