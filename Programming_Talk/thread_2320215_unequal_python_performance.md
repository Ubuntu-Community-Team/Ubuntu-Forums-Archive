---
title: "unequal python performance"
date: 2016-04-11
forum: Programming Talk
---

### Post by evan7 on 2016-04-11
I have two identical dell optiflex computers running identical installations of ubuntu with identical bios set ups.  However when I run the same python code on the different machines I have different performance as measured using the command line "time python myprog.py".  I have included a simple code snippet to show just iterating matrix * vector code and uses the time module time() function to measure time.  As no other programs are running this matches the output from the unix time command.  One computer takes about twice as long to run the code but everything I can check is the same (bios settings, kernel, version of python, module version, ...) I do not know what I am missing.  I have run numerous system profilers and benchmark programs and they come out identical  (e.g  [http://browser.primatelabs.com/geekbench3/6040783](http://browser.primatelabs.com/geekbench3/6040783)  vs [http://browser.primatelabs.com/geekbench3/6040735](http://browser.primatelabs.com/geekbench3/6040735))

any thoughts? tyia

---

### Post by evan7 on 2016-04-12
I am very perplexed by this.  I wrote a very similar code in c, compiled on each machine separately and ran to find that the compiled c code has identical run times.  So I can now say this is something to do with the python installation.  Normally I would uninstall and reinstall python.  However, as I recall there is much in the OS that is tied to python.  Any advice on trying to reinstall a python distribution?

---

