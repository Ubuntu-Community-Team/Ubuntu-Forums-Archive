---
title: "Eclipse Project Macro usage in C++ code"
date: 2009-02-02
forum: Programming Talk
---

### Post by iharrold on 2009-02-02
Any one know if it is possible to use the Managed Build Macros from eclipse inside my code?

I.e. I have a file location that is relative to my project location.
```
std::string fileloc = "/home/iharrold/workspace/test/file1.xml"
```

**/home/iharrold/workspace/test** is my project path and it is stored in "ProjDirPath" macro in my eclipse C/C++ managed make project.  Accessible by Project->Properties->C/C++ Build [Macros tab]

How do I get access to it in my C++ code such that if I install my project to a different location i.e. /test/file1.xml I don't have to go and modify all my code. 

I want something like ```
std::string fileloc = ${ProjDirPath:/file1.xml}
```

Is this possible?  Any ideas?

---

### Post by iharrold on 2009-02-03
FYI incase anyone cares, I found the answer to my problem.

Define a Preprocessor like this: (Project->Properties->C/C++ Build->GCC C++ Compiler->Preprocessor)
```
'PROJDIRPATH="${ProjDirPath}"'
```

Then just use it in your code:
```
std::stringstream fileloc;
fileloc<<PROJDIRPATH<<"/test/file1.xml"
std::cout<<"Filelocation is: "<<fileloc.str();
```

So PROJDIRPATH is the Preprocessor symbol and ${ProjDirPath} is the eclipse macro from a managed make file which tracks where my project is located.  Other items you could get is version info.

---

