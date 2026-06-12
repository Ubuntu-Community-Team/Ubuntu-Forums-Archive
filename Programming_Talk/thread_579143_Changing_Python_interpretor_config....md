---
title: "Changing Python interpretor config..."
date: 2007-10-18
forum: Programming Talk
---

### Post by spinetingler on 2007-10-18
I am learning wxPython 2.8.6.0. When I try to run the demo files I get the error "ImportError: No module named aui" The interpretor is using version 2.6.3.2. Is there a way to modify the interpretor to use version 2.8.6.0?

Thank you for any help.

---

### Post by pmasiar on 2007-10-18
seems to me you use wxPython version 2.8.6.0, running on Python version 2.6.3.2?

Usually only first two numbers are meaningful, rest are bugfixes and builds. So for simplicity, you have wxPython 2.8 (bugfix 3.2) running with Python 2.6 (bugfix 3.2)

You need to make sure that you installed wxPython (libraries) for Python 2.6, and not for some other versions. There isn't any 2.8 version of Python yet :-)

In python shell, can you 'import aui'?

If you are just starting with python, maybe don't dive to GUI just yet. Start with plain old and boring text/commandline code. Check PythonChallenge for puzzles to solve, GUI can be tricky.

---

### Post by spinetingler on 2007-10-18
No I cannot import aui... So how do I correct this?

---

### Post by pmasiar on 2007-10-18
it is not installed, or installed in a place where Python cannot find it.

Your options:
1) learn enough about administering now to fix it.
2) learn python with standard modules, and learn administering as you go.

---

### Post by spinetingler on 2007-10-18
I do appreciate your Perl's of wisdom but my situation begs for a more immediate and direct solution. As I stated in my original post I am learning wxPython and I am trying to use the demo programs as a base. I have completed several online tutorials but they only provide a minimal or the necessary information for skills development. Being able to solve my current dilemma would help two fold: 1) I would be able to have access to the demo files thus providing a richer environment to learning wxPython and 2) a solution would provide a deeper understanding of what a potential user of any application I might develop, could be faced with, and thus provide me with the heads-up and knowledge to resolve that issue. So again I ask, if you, or someone, could provide me. or point me in a productive direction, a solution it would be greatly appreciated.

---

### Post by pmasiar on 2007-10-18
As I said, looks like wxPython is not installed properly. Go and install it right. 

I don't use wxPython myself so I cannot help you more, sorry. Maybe someone else has advice based on more immediate experience.

But wxPython is not required to learn basic Python.

---

