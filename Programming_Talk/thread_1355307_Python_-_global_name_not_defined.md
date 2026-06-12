---
title: "Python - global name not defined"
date: 2009-12-14
forum: Programming Talk
---

### Post by hawkeye2777 on 2009-12-14
I'm working on writing some Python scripts for some WiiRd tools. This one specifically deals with the WiiRd assembly codes. With that aside, here is what I currently have for my source (not completely finished yet).

vdappc.py:
```
class DisAssemble():
    """Disassemble code into their respective opcodes"""
    
    def __init__(self):
        self.vda = None
        self.binfile = "./tmp/code.bin"
    
    def set_opcodes(self):
        """Get opcodes from assembled code (disassemble code)"""
        
        if (sys.platform == "win32"):
            self.vda = "./ext/win32/vdappc.exe"
        elif (sys.platform == "darwin"):
            pass #No OSX binary on hand
        else:
            self.vda = "./ext/linux/vdappc" #Linux
        
        if (self.vda != None):
            output = sub.Popen([self.vda, self.binfile, "0"], stdout=sub.PIPE, stderr=sub.PIPE).communicate()
        
        if (output[1] == ""):
            #Format the junk out
            a = []
            for i in range(len(output[0].split("\n"))):
                a.append((output[0].split("\n")[i]).split("\t", 1))
            for i in range(len(output[0].split("\n"))):
                a.pop()
            self.opcodes = " ".join("\n".join(a).split("\t"))
        else:
            self.opcodes = ("%s: No codes found" % (vda, )) #Error
            
    def get_opcodes(self):
        return self.opcodes
```

(Note that the above is not the entire source)

Before I started adding more methods or using this class in other files, I tested this in a Python console (by importing the file). This was the error I came across:

```
>>> import vdappc
>>> b = vdappc.DisAssemble()
>>> b.set_opcodes()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "vdappc.py", line 49, in set_opcodes
    if (self.vda != None):
NameError: global name 'binfile' is not defined
```

While my experience with Python isn't the best, I have not been able to find the cause of this error at all; I've searched and looked at tutorials for a few hours; nothing has worked so far. Could someone help point out the cause of the error?

---

### Post by nelfin on 2009-12-14
Have you edited and saved vdappc.py since opening the console (if you re-import a module then you get the module object from __modules__, rather than having it reloaded). Try

[PHP]>>> import imp
>>> imp.reload(vdappc)[/PHP]

Otherwise, try getting rid of the compiled bytecode version (vdappc.pyc) and importing again.

Finally, you can try checking out globals() and locals() before and after importing vdappc (from a fresh console session).

---

### Post by hawkeye2777 on 2009-12-14
> **nelfin said:**
> Have you edited and saved vdappc.py since opening the console (if you re-import a module then you get the module object from __modules__, rather than having it reloaded). Try

[PHP]>>> import imp
>>> imp.reload(vdappc)[/PHP]

Otherwise, try getting rid of the compiled bytecode version (vdappc.pyc) and importing again.

Finally, you can try checking out globals() and locals() before and after importing vdappc (from a fresh console session).
Deleting the bytecode file did the trick; thanks!

---

### Post by nelfin on 2009-12-14
No worries, whilst having modules be loaded from precompiled bytecode makes sense to improve load times for oft used ones from the standard library or wherever, it's quite annoying when you're working on a module yourself.

---

