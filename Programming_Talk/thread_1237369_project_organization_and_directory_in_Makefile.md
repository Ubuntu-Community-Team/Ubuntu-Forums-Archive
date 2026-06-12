---
title: "project organization and directory in Makefile"
date: 2009-08-11
forum: Programming Talk
---

### Post by flylehe on 2009-08-11
Hi,
Here are my two questions:

1. I am now learning to manage my code with CVS, and I just want to make a repository for my C++ files, Makefile and bash and python scripts only, not the object files and executables. So I made several subdirectories under my project directory: src, bin, scripts, results and data. I put C++ files and Makefile under ~/myproject/src, bash and python scripts under ~/myproject/scripts and object and executables under ~/myproject/bin. I am hoping only the files under src and scripts will be updated via CVS.  I wonder how you guys organize your projects? Just hope to follow some good habits

2. Since I put my C++ files and Makefile into ~/myproject/src and object and executable files into ~/myproject/bin, I have to specify the directories in Makefile. Here is what I am doing
```

...
BIN_DIR=/home/myproject/bin/

all: $(BIN_DIR)myexecutable TAGS

TAGS: *.cc *.h
	etags --members --declarations -l c++ *.cc *.h

$(BIN_DIR)myexecutable: $(BIN_DIR)myobject.o
	$(CXX) $(CXXFLAGS) -o $@ $^ $(LDFLAGS)

Makefile.depend: *.h *.cc Makefile
	$(CXX) -M $(CXXFLAGS) *.cc > Makefile.depend

clean:
	\rm -f $(BIN_DIR)myexecutable $(BIN_DIR)*.o Makefile.depend TAGS

```
However this will give error
> 
make: *** No rule to make target `/home/myproject/bin/myobject.o', needed by `/home/myproject/bin/myexecutable'.

How to specify a different directory for object and executable files from C++ files in Makefile?

Thanks and regards!

---

### Post by uljanow on 2009-08-11
You can omit the directory in lines like 

$(BIN_DIR)myexecutable: $(BIN_DIR)myobject.o

if you tell make where to look for source files. This can be done by using the vpath feature of make.

VPATH = $(SRCDIR) 
vpath %.cc $(SRCDIR) 

> I am now learning to manage my code with CVS
Why not svn or git ?

---

### Post by flylehe on 2009-08-11
Thanks! I just googled a little bit about svn and git. Looks like git is more powerful. Probably I will use git instead of cvs.

As to my original question, I intended to put my Makefile together with my C++ files under src all files under which will be put into the repository, so I would like to know how to specify the directory for object and executable files in Makefile. 

From what you said, do you put your Makefile with Object and executable files under bin? Do you still put your Makefile into repository? How do you orgainze your project and what files do you put to the repository?

---

