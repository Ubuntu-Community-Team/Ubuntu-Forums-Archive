---
title: "changed value of variable not reflecting, python"
date: 2010-10-11
forum: Programming Talk
---

### Post by Blackbug on 2010-10-11
I have following code (its not complete)
 
I have a variable filename which i have declared outside function scope and changing value of that in one function and want to use the changed value in other function, but it doesnt changes.
 
I am new to python, and I was wondering how to make this variable global so that changed value is reflected everywhere something like static in c++
 
If any other work around, plz suggest
```

#! /usr/bin/env python
 
import sys
import os
noOfTabLine=0
counter=0
tabCounter=0
fileName="" #needs to declare this as global
 
def checkArgs():
 print "Priting arguments:%s"%len(sys.argv)
 if len(sys.argv) == 1:
  raise NameError('No arguments entered')
  print sys.argv[2] 
 
for arg in sys.argv:
 if '-file' in arg:
  if os.path.exists(sys.argv[2]):
  fileName=sys.argv[2]
  print "Filename is : %s"%fileName
 else: 
  print "invalid file"
  raise NameError('Invalid FileName')
 
 
def countFunction(): 
 for line in open(fileName):
 counter2=0
 counter += 1
 for z in line:
  if '\t' in z:
   tabCounter += 1
   counter2 += 1
   if counter2 != 0:
     noOfTabLine += 1
     print "-------------------------------------------------------------------"
     print "COUNT: %s"%noOfTabLine
     print "Number of TABSPACES: \033[31m%s\033[0m at line no. : \033[31m%s\033[0m"%(tabCounter,counter)
     print "Line : \033[34m%s\033[0m"%line
     print "-------------------------------------------------------------------\n"
   tabCounter=0 
 
  if noOfTabLine == 0:
    print "*********************************************************************"
    print "\033[32mNo TabSpaces Found\033[0m"
    print "*********************************************************************"
  else: 
    print "*********************************************************************"
    print "\033[31mTotal Lines Affected with TabSpaces : \033[0m%s"%noOfTabLine
    print "*********************************************************************"
 
checkArgs()
countFunction() 

```

---

### Post by jpkotta on 2010-10-11
Put your code in [[HTML][/HTML]code][/code[HTML][/HTML]] tags.  Otherwise it's very hard to read, and in the case of Python, impossible to read unambiguously (syntactic indentation).

In Python, variables are taken from the global* namespace if they are not assigned, and created in the local namespace if they are assigned.  If you want to assign a global, you have to use a [global statement]("http://docs.python.org/reference/simple_stmts.html#the-global-statement").  Python's scope rules are somewhat complex, but are usually the Right Thing in practice.

* There isn't anything equivalent to the global namespace of C/C++ in Python.  Global variables are always local to modules (usually, a single source file is the same as a module), and can be shared between modules with import statements.

---

### Post by mo.reina on 2010-10-11
> **Blackbug said:**
> I have following code (its not complete)
 
def countFunction(): 
 for line in open(fileName):
 counter2=0
 counter += 1
 for z in line:
  if '\t' in z:
   tabCounter += 1
...
...


indentation here isn't correct, you have to indent the lines after the for loop when you open the file...

i'm not quite clear what you mean, but if you're saying that the variable fileName isn't changing after you run checkArgs(), it's because you didn't return it.  it's valid only in the checkArgs() function, that's its scope.  

after you return it, you have to pass it to the other function, which i assume is countFunction().  it can be modified like so:

```
def checkArgs():
 print "Priting arguments:%s"%len(sys.argv)
 if len(sys.argv) == 1:
  raise NameError('No arguments entered')
  print sys.argv[2] 
 
for arg in sys.argv:
 if '-file' in arg:
  if os.path.exists(sys.argv[2]):
  fileName=sys.argv[2]
  print "Filename is : %s"%fileName
 else: 
  print "invalid file"
  raise NameError('Invalid FileName')
  return fileName #<----

def countFunction(fileName): #<----  
 for line in open(fileName):
 counter2=0
 counter += 1
 for z in line:
  if '\t' in z:
   tabCounter += 1
   counter2 += 1
...
...
...
fileName = checkArgs() #assign the variable fileName to the returned value of checkArgs()
countFunction(fileName) #pass variable fileName to the function

```

try not to use global variables, it's bad practice and should only be done when absolutely necessary (i can't even really think of one instance, but that's probably due to my inexeprience).

---

