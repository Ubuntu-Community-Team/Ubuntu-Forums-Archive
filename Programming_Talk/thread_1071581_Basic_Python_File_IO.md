---
title: "Basic Python File I/O"
date: 2009-02-16
forum: Programming Talk
---

### Post by tpg on 2009-02-16
I'm having a problem with the Python file I/O methods. Here is the offending code:

```

f = open('test.tex', 'w')
f.write(latex)
f.flush
f.close
os.system('pdflatex test.tex')

```

The idea is to write the data in the latex variable to a file 'test.tex', and then call pdflatex on that file. However, when LaTeX runs, it quits with an error. I have realised that this is because the file 'test.tex' has not been fully written before the latex command is called.

I have tried putting a long pause in after the f.close instruction, with no effect. What is interesting is that after the script quits, the file is written completely.

Can anybody help please? Thanks in advance.

---

### Post by PythonPower on 2009-02-16
You're not calling the file.close() function. Replace:

[PHP]f.close[/PHP]

With:

[PHP]f.close()[/PHP]

It's similar with the flush function I imagine. See [this]("http://docs.python.org/library/stdtypes.html#file.close").

---

### Post by wmcbrine on 2009-02-16
> **PythonPower said:**
> It's similar with the flush function I imagine.Or indeed with any function, yes. :D

I'd add that you don't need to flush a file just before closing it. (I realize that line was probably added in frustration when "f.close" didn't work.)

---

### Post by PythonPower on 2009-02-16
Indeed. :p

flush() is probably not necessary as said by wmcbrine. The Python docs are a little lacking for that function but they do say:

[QUOTE=Python 2.6.1 Docs for flush()]This may be a no-op on some file-like objects.[/QUOTE]

For which objects and whether close() calls flush() anyway, it is not stated.

---

### Post by tpg on 2009-02-16
Thanks very much everybody!

---

