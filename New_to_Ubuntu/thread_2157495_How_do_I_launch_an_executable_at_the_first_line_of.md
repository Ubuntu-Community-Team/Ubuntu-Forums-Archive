---
title: "How do I launch an executable at the first line of the Terminal?"
date: 2013-06-25
forum: New to Ubuntu
---

### Post by MemoryMarc on 2013-06-25
I have an executable named "phasor" located in this sample directory: /location/of/my/exe

Just after starting up the Terminal (Ctrl + Alt + T) I would like to be able to type phasor and the program is launched.

How would I set this up?

I am familiar with moving around directories, editing files using vi, becoming root, etc etc; but I'm not sure what the steps are to set this up, any guidance would be great!

---

### Post by DeathByDenim on 2013-06-25
Sounds like you would like to have it in your path. Type this:
```
export PATH=$PATH:/location/of/my/exe
```

If that does what you want, then you can make it permanent by adding that line to your .bashrc

---

### Post by Cheesemill on 2013-06-25
The easiest method is probably to create a folder called bin in your home directory and put the executable in there.
If the ~/bin directory exists then it is automatically added to your $PATH variable meaning it gets searched every time you type in a command.

If you want to leave the executable in its current location then you need to add this location to your $PATH. The easiest way to do this is to edit your ~/.bashrc file and add the following to the bottom...
```
export PATH=$PATH:/location/of/my/exe
```

---

### Post by Dennis N on 2013-06-25
Make an alias definition and add to your **.bash_aliases** file:

**alias phasor=/full-path-to-program-executable/phasor**

Using your example path,

**alias phasor=/location/of/my/exe/phasor**

Then starting the terminal and typing **phasor** at the command prompt will run it.

---

### Post by Mark Phelps on 2013-06-25
Executables in Linux are not "exe" files; instead, they are "bin" or other such files.  IF this is a Windows ".exe" file, you are not going to be able to run it from a command line the way you want.

---

### Post by MemoryMarc on 2013-06-26
> **Mark Phelps said:**
> Executables in Linux are not "exe" files; instead, they are "bin" or other such files.  IF this is a Windows ".exe" file, you are not going to be able to run it from a command line the way you want.


I wrote "exe" as an abbreviation for the term executable, which now I see as being a little ambiguous.  Sorry about that.  But thanks for the tip!  The "export PATH..." examples above worked out great!

---

### Post by MemoryMarc on 2013-06-26
> **DeathByDenim said:**
> Sounds like you would like to have it in your path. Type this:
```
export PATH=$PATH:/location/of/my/exe
```

If that does what you want, then you can make it permanent by adding that line to your .bashrc


Great answer, thank you

-M

---

