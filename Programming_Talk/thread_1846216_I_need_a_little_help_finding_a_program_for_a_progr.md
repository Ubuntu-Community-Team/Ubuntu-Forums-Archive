---
title: "I need a little help finding a program for a programming class."
date: 2011-09-18
forum: Programming Talk
---

### Post by Orange_Ribbon on 2011-09-18
All right,  basically when I turn in assignments,  I have input I have to test my programs with.  Well in the past I was just able to copy paste from terminal.  These last two assignments had to much so I couldn't copy paste it all.  Any way to unlimit the buffer in Terminal or  is there a simple script to just output to a simple text file?  

I tried reading the help contents for Terminal but I didn't see any.

---

### Post by Off Shore on 2011-09-18
> **Orange_Ribbon said:**
> All right,  basically when I turn in assignments,  I have input I have to test my programs with.  Well in the past I was just able to copy paste from terminal.  These last two assignments had to much so I couldn't copy paste it all.  Any way to unlimit the buffer in Terminal or  is there a simple script to just output to a simple text file?  

I tried reading the help contents for Terminal but I didn't see any.

If I understand your problem correctly I think you need to open Terminal.
Go to the edit menu
Select Profiles
Select Edit
then choose the tab called scrolling. You can change defaults there

---

### Post by nmaster on 2011-09-18
if you want to dump the output into a file just use '>' like this:
```

$ ./theProgram > outputFile

```

this will redirect standard out to 'outputFile'.  you can read more about i/o redirection here: [http://tldp.org/LDP/abs/html/io-redirection.html](http://tldp.org/LDP/abs/html/io-redirection.html)

---

