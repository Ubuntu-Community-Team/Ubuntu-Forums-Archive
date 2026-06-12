---
title: "[SOLVED] Scripting and Coding in Python"
date: 2008-07-08
forum: Programming Talk
---

### Post by thornmastr on 2008-07-08
About three weeks ago I began investigating Python and found it to be not only fascinating to learn, but really a lot of fun to use. I would never give up C++, but Python can be used for most of what I do, and solutions, I think, can be implemented easier, faster, with many more solution paths to choose.

I am using the Challenge-You page, as a Python learning tool along with a number of available Python tutorials. One of the challenges 
available in Challenge You is called "lower case". It is described as:
"Create a script, that deletes all lowercase characters from a 
file. "
To say the least it is pithy, concise, and more than a tad obtuse; in short a perfect programming learning tool. The first question this generated in my mind is even more vague than the challenge. Will someone please tell me what, in Python, is a script. Is it a program, ie, coding expressed as line by line instructions to accomplish a logical task. I am assuming (ouch) that both scripts and Python programs are both interpreted and not compiled in the sense that a file is run through a compiler; ie, Python does not produce an object file. I do not need to build a Make file. 
I use the Python program to run a python (script or program ending in py). So now, please, a concise definition of a Python script.

Thanks for the edification.

Robert

---

### Post by tamoneya on 2008-07-08
within the scope of a python learning challenge they are the same thing.  Honestly the only thing I would do different if I was writing a script instead of a program in python is I would add this at the start of the file:```
#!/usr/bin/python
```

[http://en.wikipedia.org/wiki/Scripting_language](http://en.wikipedia.org/wiki/Scripting_language)

---

### Post by pmasiar on 2008-07-08
script is a program with shebang #! in first line, so shell 'knows' which program to use to interpret it. Usually it processes std input according to flags to generate std output, so it can be piped with other programs. 

But for your purposes, script == program

---

### Post by thornmastr on 2008-07-09
> **pmasiar said:**
> script is a program with shebang #! in first line, so shell 'knows' which program to use to interpret it. Usually it processes std input according to flags to generate std output, so it can be piped with other programs. 

But for your purposes, script == program

Thank you both for the quick replies. Especially for the exact statement, that in this particular instance, script==program. 
Since my question is obviously answered, I should not extend it,
but (isn't there always a but?)are there any circumstances specific to python, in which a script is not a program; something like a collection of system commands.

Thanks again,

Robert

---

