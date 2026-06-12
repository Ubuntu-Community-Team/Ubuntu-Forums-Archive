---
title: "Errors in Python Code"
date: 2009-01-13
forum: Programming Talk
---

### Post by vietwow on 2009-01-13
Dear all,

I often use online tool [http://utilitymill.com/utility/pyc_xray](http://utilitymill.com/utility/pyc_xray) to decompile binary python code, it works well. So I want to view its code, I click "Edit & View Source", it give me the code :

```
#Mostly from the code here http://nedbatchelder.com/blog/200804/the_structure_of_pyc_files.html

import dis, marshal, struct, sys, time, types

def show_file(f):
    magic = f.read(4)
    moddate = f.read(4)
    modtime = time.asctime(time.localtime(struct.unpack('L', moddate)[0]))
    print "magic %s" % (magic.encode('hex'))
    print "moddate %s (%s)" % (moddate.encode('hex'), modtime)
    code = marshal.loads(f.read())
    show_code(code)
    
def show_code(code, indent=''):
    print "%scode" % indent
    indent += '   '
    print "%sargcount %d" % (indent, code.co_argcount)
    print "%snlocals %d" % (indent, code.co_nlocals)
    print "%sstacksize %d" % (indent, code.co_stacksize)
    print "%sflags %04x" % (indent, code.co_flags)
    show_hex("code", code.co_code, indent=indent)
    dis.disassemble(code)
    print "%sconsts" % indent
    for const in code.co_consts:
        if type(const) == types.CodeType:
            show_code(const, indent+'   ')
        else:
            print "   %s%r" % (indent, const)
    print "%snames %r" % (indent, code.co_names)
    print "%svarnames %r" % (indent, code.co_varnames)
    print "%sfreevars %r" % (indent, code.co_freevars)
    print "%scellvars %r" % (indent, code.co_cellvars)
    print "%sfilename %r" % (indent, code.co_filename)
    print "%sname %r" % (indent, code.co_name)
    print "%sfirstlineno %d" % (indent, code.co_firstlineno)
    show_hex("lnotab", code.co_lnotab, indent=indent)
    
def show_hex(label, h, indent):
    h = h.encode('hex')
    if len(h) < 60:
        print "%s%s %s" % (indent, label, h)
    else:
        print "%s%s" % (indent, label)
        for i in range(0, len(h), 60):
            print "%s   %s" % (indent, h[i:i+60])

#Main utility code
from cStringIO import StringIO
f=StringIO(PYC)
show_file(f)
```

But when I run it on CentOS 5 :

```
[root@server ~]# ./dis.py
Traceback (most recent call last):
  File "./dis.py", line 3, in <module>
    import dis, marshal, struct, sys, time, types
  File "/root/dis.py", line 49, in <module>
    f=StringIO(PYC)
NameError: name 'PYC' is not defined

```

Can u help me to find out the reason ?

Thanx

---

### Post by $USER on 2009-01-13
I am currently trying to learn python, So I don't really understand much of the code. But I think it is trying to import itself.  Maybe thats normal, but seems wierd to me.  You are running dis.py and it is trying to import dis.py.  I dunno. good luck though.

---

### Post by vietwow on 2009-01-13
I have tried change script's name, still error :

```
[root@server ~]# mv dis.py asm.py

[root@server ~]# ./asm.py crackme.pyc
Traceback (most recent call last):
  File "./asm.py", line 3, in <module>
    import dis, marshal, struct, sys, time, types
  File "/usr/local/python/lib/python2.5/dis.py", line 49, in <module>

NameError: name 'PYC' is not defined
```

---

### Post by MrStill on 2009-01-13
I am rusty with python; but, I will venture a guess if you don't mind. 

You have 'PYC' is being passed as a variable to a function without any prior mention of that variable. If you are writing/reading a file called 'PYC' then you may try passing PYC as a string or a string containing the value 'PYC'. As I said, I am not up to speed with python; however, most programming languages, even loosely typed similarly to Python, would want some initialization of a variable before passing to a function. 

A good tip is to check docs provided by the people who maintain the language. Python seems to have good documentation on their website. Check the two links below to see if they provide better understanding.  

[http://docs.python.org/library/stringio.html](http://docs.python.org/library/stringio.html)
[http://effbot.org/librarybook/cstringio.html](http://effbot.org/librarybook/cstringio.html)

I hope this helps. I'm sorry if I am telling you stuff you already know

---

### Post by unutbu on 2009-01-14
Change
[PHP]
from cStringIO import StringIO
f=StringIO(PYC)[/PHP]

to
[PHP]
import sys
f=open(sys.argv[1],'r')[/PHP]

Then run the script like this:
```

./asm.py file.pyc
```

---

