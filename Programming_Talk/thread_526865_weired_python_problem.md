---
title: "weired python problem"
date: 2007-08-16
forum: Programming Talk
---

### Post by RawMustard on 2007-08-16
My python code works great until I compile it to byte code and try to run the pyc files. 

On my workstation running Feisty they work fine, but on a another machine running feisty server, the pyc files won't run, the py files will however. Oh and I tried compiling them on the server, but that made no difference.  Anyone might have any clues for me to solve this dilemma?

---

### Post by PaulFr on 2007-08-16
Any error messages ? Any version difference ? Any difference in ```
env|grep PYTHON
```on the two machines ? Any difference in output from ```
python -v <script>.py
``` and ```
python -v <script>.pyc
```

---

### Post by RawMustard on 2007-08-16
Ok thanks for the reply.

I had a missing module on the server, python-apport.

So now when I type ./<script.pyc> it errors with just gobbaldy goop
but if I type python <script.pyc> it works fine.

It doesn't matter on my other machine?

---

### Post by RawMustard on 2007-08-16
So on my own workstation, I can type "./myScript.pyc" and my script runs.
But on my server version of feisty if I type the same the script errors and does nothing. However if I type "python myScript.pyc" it works fine.

Would this be some path issue perhaps?

---

### Post by pmasiar on 2007-08-16
first line of the Python script, #! says where Python lives. Is it different on your machines?

---

### Post by RawMustard on 2007-08-16
I checked my PYTHONPATH variable on all my machines here, all running feisty and they're all the same.  Apart from the gtk and gst modules which shouldn't be needed on a server?

Here's the error I get when I try to run the script.

I do $ python
>>> import py_compile
>>> py_compile.compile('libhmi_sys.py')

Then I chmod +x libhmi_sys.pyc

then I try and run it with ./libhmi_sys.pyc

and get:

```

root@tilsan1-hmi:/opt/tilsan/hmi# ./libhmi_sys.pyc sys:clrjs
: command not foundine 1: 
./libhmi_sys.pyc: line 2: {+Fc: command not found
./libhmi_sys.pyc: line 3: dZ
                            Z
                             d: command not found
./libhmi_sys.pyc: line 4: syntax error near unexpected token `('
./libhmi_sys.pyc: line 4: `Zd
                              jo;eiie   Zedjoeie       nend
djo1eideendjp eideiie       Zedjoeie       neiie        joeid
                                                      Zeidedjo4djo
ndjo                                                               e
     eqqedjoreideide
                        dZeiie
                               ZedjoAedjo4djo
ndjo                                         e
     eqqedjowedjojeide
                         eide  eideiie       Zedjoeie       neqedjoYeideideiie Zedjoeie       neqqnedS(iNt:iis/opt/tilsan/hmi/tmp/extInput.jss/opt/tilsan/hmi/hmi_db/s /media/TILSAN-USB/4roller-backups     /dev/sdb1cCs
                                                                            tidttidtidttidtittidtdtidtidttd      tidtid'
^[[?1;2c^[[?1;2croot@tilsan1-hmi:/opt/tilsan/hmi# 1;2c1;2c
bash: 1: command not found
bash: 2c1: command not found
bash: 2c: command not found

```

The exact same routine works fine on 4 other machines, but they're normal desktop installs.  This is a server install of Feisty.

---

### Post by pmasiar on 2007-08-16
From your discussion in other thread I guess you want to use .pyc instead of .py to gain some kind of source code protection? I doubt it is any good: bad security by little obscurity. You may want to look into psyco which compiles binaries, which might be  little better.

Python bytecode disassembler is standard module: [http://docs.python.org/lib/module-dis.html](http://docs.python.org/lib/module-dis.html) (remember: batteries are included) so it should be trivial to restore sources (minus comments).

Google gives couple Python obfuscators. Some encode strings, other replace identifiers with random names. [http://www.bitboost.com/](http://www.bitboost.com/) is a comercial one, claims to impede even bytecode disassembler.

---

### Post by RawMustard on 2007-08-16
Ok thanks for the tips :)

I'd still like to know why it doesn't work though :(

---

### Post by pmasiar on 2007-08-16
my guess would be some libraries have different versions. Or compare build number of Pythons - do all workstation use same build?

---

### Post by RawMustard on 2007-08-16
Yep they're all the same. :(

---

