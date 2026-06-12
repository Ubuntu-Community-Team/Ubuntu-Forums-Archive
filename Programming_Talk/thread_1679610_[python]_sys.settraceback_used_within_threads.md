---
title: "[python] sys.settraceback used within threads"
date: 2011-02-01
forum: Programming Talk
---

### Post by Pyro.699 on 2011-02-01
Hello, here is some sample code for which i am going to use for the basis of my question :)

x.py
[php]
import sys, linecache

global FileName
FileName = globals()['__file__']

def _trace(frame, event, arg):
    if event == "line":
        lineno = frame.f_lineno
        filename = frame.f_code.co_filename
        if filename == FileName: return _trace
        line = linecache.getline(filename, lineno)
        sys.__stdout__.write( "[%s]%s %s\n" % (lineno, filename, line.rstrip()) )
    return _trace
     
class _stderr:
    def __init__(self):
        self.buff = ""
         
    def write(self, out):
        self.buff += out
        if out.find("\n") != -1:
            sys.__stdout__.write("[Error] %s"%self.buff)
            self.buff = "" 
    
class _stdout:
    def write(self, out):
        sys.__stdout__.write("[Out] %s"%out)
         
sys.stderr = _stderr()
sys.stdout = _stdout()
sys.settrace(_trace)


f = open("w.py")
exec(compile(f.read(), f.name, "exec"))
f.close()
[/php]

w.py
[php]
import threading, time

class Tester(threading.Thread):
    def __init__(self):
        threading.Thread.__init__(self)
        self.start()
        
    def run(self):
        for x in range(5):
            sys.stdout.write("%i, %i\n"%(x, x*3))
        int("t")

for y in range(5):
    sys.stdout.write("%i, %i\n"%(y, y*3))
    
t = Tester()
time.sleep(1)
int("s")
[/php]

The  output is located at [this link](http://pastebin.com/SqMnDSUv)  (Ive taken out the un-necessary information). When i refer to "lines"  they will relate to lines within this output file.

You will  notice that in lines 7 to 24 the output behaves properly and is  redirected to _stdout and the trace has been implemented properly (from  _trace), displaying which lines were called and all of that jazz. Lines  32 to 38 properly used _stdout but there was no trace of the actions  that were being taken. The error (caused by *int("t")*) was only  formated with the special **[Error]** tag on the first line, not on  every one; lines 53 to 60 however, did.

Any help in this area would be greatly appreciated :)

Thanks
~Cody

---

### Post by Pyro.699 on 2011-02-01
found my problems...

[list]
[*]threading.settrace
[*]if out.count("\n") > 3 or out == "\n":
[/list]

---

