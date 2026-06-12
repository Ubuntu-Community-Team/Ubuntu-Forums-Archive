---
title: "bash parser"
date: 2004-12-09
forum: Programming Talk
---

### Post by bob k on 2004-12-09
is there a bash parser to flag basic syntax errors and possibly a testing environment to single step through a script without executing the commands but showing the results.

I want to automate a few things and want to bullet proof my scripts.

---

### Post by robotboy on 2004-12-09
If you invoke bash with the -n argument, it does a syntax check on a file without executing it. AFAIK, debugging support is weak under bash in terms of tracing a scripts execution, but you can get a 3rd party debugger if you google for bash debugger.

---

### Post by bob k on 2004-12-09
[QUOTE=robotboy]If you invoke bash with the -n argument, it does a syntax check on a file without executing it. AFAIK, debugging support is weak under bash in terms of tracing a scripts execution, but you can get a 3rd party debugger if you google for bash debugger.[/QUOTE]
 Well I found a debugger bashdb but it's going to be a bugger to install. It looks like i'm going to have to find the bash sources and recompile with the bashdb hooks for debugging. I'm hoping that I can recompile it to a local directory where I will be doing most of my coding and not mess with the system bash.

---

### Post by robotboy on 2004-12-09
[QUOTE=bob k]Well I found a debugger bashdb but it's going to be a bugger to install. It looks like i'm going to have to find the bash sources and recompile with the bashdb hooks for debugging. I'm hoping that I can recompile it to a local directory where I will be doing most of my coding and not mess with the system bash.[/QUOTE]

This may sound obtuse, but why not use a scripting language like Perl, Python or Ruby. I know they're primarly for "real programming", but I've used all of them for automating system administration over the years, and it always makes the job easier.

---

### Post by robotboy on 2004-12-09
Also, if you do bash -x script.sh, it will print a stack trace when the script executes, which can be pretty handy. Pipe that into more, and you have some kind of bastardized poorman's debugger. You can also put set -x on the line you want to start tracing and put set +x on the line you want to stop if your script is long and you don't feel like wading through tons of output. My comment above still stands though...

---

### Post by bob k on 2004-12-09
[QUOTE=robotboy]This may sound obtuse, but why not use a scripting language like Perl, Python or Ruby. I know they're primarily for "real programming", but I've used all of them for automating system administration over the years, and it always makes the job easier.[/QUOTE]

Thats what I was thinking. I can learn a new language faster than I can compile and test bash and basdb and with bash being so widely used and looking at the source, it's best left alone.

It looks like I'm going to python. It looks like it has every thing that I will use and some. It looks to be a stright foward language and should be easy to pickup. Plus it is loaded as part of the install, so that means that it is Ubuntu maintained, and I found a plugin for eclipse that has a lint and debugger.

Thanks for your help
Bob

---

