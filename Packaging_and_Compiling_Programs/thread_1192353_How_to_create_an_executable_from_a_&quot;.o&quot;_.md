---
title: "How to create an executable from a &quot;.o&quot; file?"
date: 2009-06-20
forum: Packaging and Compiling Programs
---

### Post by trilobite on 2009-06-20
Hi all - 

 I'm getting involved in helping to do some docs for a project. The project uses the "Boost QuickBook" tool to help in creating the docs. 

 Anyway, to cut a long story short, I followed the instructions which should have (IIUC) created an executable called "quickbook". Instead, all that I have found (in a particular subdirectory) is about ten or so ".o" files, including "quickbook.o".  

 I believe they're "object files", not executables, so mny question is - can I create an executable from "quickbook.o", and if so, how?  

 Very many thanks in advance - bye for now - 
- trilobite

---

### Post by curvedinfinity on 2009-06-20
Object files are compiled source code. You make the object files with a command like this:

```

gcc -c yoursource.c -o objects/yourobject.o

```

(run a separate command for each source file)

Next you have to "link" each object file and all of the libraries you are using into a binary:

```

gcc -o yourexecutable objects/yourobject1.o objects/yourobject2.o -lLibrary

```

Alternatively, you can perform both steps at the same time:

```
gcc source1.c source2.c -lLibrary -o yourexecutable
```

Make a text file in your project called compile.sh and put your gcc commands into it like this:

```

#!/bin/sh
gcc source1.c source2.c -lLibrary -o yourexecutable

```

Then right click the file, select properties, and make it executable. Now when you want to compile your project, just double click that file and run it.

[http://www.google.com/search?q=gcc+object+file+link](http://www.google.com/search?q=gcc+object+file+link)
[http://www.google.com/search?q=gcc+compile+example](http://www.google.com/search?q=gcc+compile+example)

---

