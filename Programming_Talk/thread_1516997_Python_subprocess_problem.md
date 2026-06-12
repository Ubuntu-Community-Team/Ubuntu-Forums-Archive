---
title: "Python subprocess problem"
date: 2010-06-24
forum: Programming Talk
---

### Post by lykwydchykyn on 2010-06-24
For reasons I won't go into, I'm trying to replicate a win32 tool we use at my workplace (currently written in C++ and wxwidgets) in python and pyqt4.

The purpose of the tool is to simplify tech support, it basically reads a text-based config file full of macros and generates a button for each macro.

I want my python version to be compatible with config files from the current program.

Now here's the issue:

 - in the config file, a command line is specified just as you would at the windows command prompt, e.g.
```

C:\Program Files\Some Program\someprogram.exe /A /i=fizzfozz NOSNAPS

```

 - I'm trying to run these using subprocess.Popen
 - subprocess.Popen wants to see commands like this:
```

subprocess.Popen([command, argument, argument, argument])

```

In other words, I need to split the actual command from the arguments, then split the individual arguments and switches for subprocess.Popen to use it.  

The problem of course is the spaces.  

How would I go about formatting a raw command line like the above so that it would work with python's subprocess.call or subprocess.Popen?

Or, is there another way to launch this that wouldn't require me splitting up the raw command line like this?

---

### Post by DanielWaterworth on 2010-06-24
If there's no quotations then it's just string.split(). If it may have quotations, then I'd do the split first then make a list of tuples of indices of words to join. Then you can make the joins with:

```
args[s:e] = [' '.join(args[s:e])]
```

Where args is the list you get from splitting and a is the start index and e is the end index.

---

### Post by lykwydchykyn on 2010-06-24
Ok, I figured it out; doh I'm silly.

Popen will happily take the whole command, args and all, as a string instead of a list.

Thanks anyway!

---

