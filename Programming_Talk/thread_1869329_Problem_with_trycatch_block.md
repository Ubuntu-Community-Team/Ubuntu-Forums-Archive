---
title: "Problem with try/catch block"
date: 2011-10-25
forum: Programming Talk
---

### Post by robotz421 on 2011-10-25
I have a problem with a try/catch block.  I am using Gcc.  When my try block executes I get an error message:[INDENT]terminate called after throwing an instance of 'std::runtime_error' 
  what(): Segmentation fault 
Aborted

[/INDENT]My code looks like this:[INDENT]try
{[INDENT]...
[/INDENT]}
catch( std::exception& e )
{[INDENT]...
[/INDENT]}
catch( std::runtime_error& e )
{[INDENT]// I know this is redundant just threw it in to be sure
...
[/INDENT]}
catch( int x )
{[INDENT]...
[/INDENT]}
catch( ... )
{[INDENT]...
[/INDENT]}

[/INDENT]Why are my catch blocks not catching this error?  Any help would be greatly appreciated.

---

### Post by karlson on 2011-10-25
> **robotz421 said:**
> I have a problem with a try/catch block.  I am using Gcc.  When my try block executes I get an error message:[INDENT]terminate called after throwing an instance of 'std::runtime_error' 
  what(): Segmentation fault 
Aborted

[/INDENT]My code looks like this:[INDENT]try
{[INDENT]...
[/INDENT]}
catch( std::exception& e )
{[INDENT]...
[/INDENT]}
catch( std::runtime_error& e )
{[INDENT]// I know this is redundant just threw it in to be sure
...
[/INDENT]}
catch( int x )
{[INDENT]...
[/INDENT]}
catch( ... )
{[INDENT]...
[/INDENT]}

[/INDENT]Why are my catch blocks not catching this error?  Any help would be greatly appreciated.

What exactly are you doing inside the catch blocks?  Do you rethrow the exception?

It seems to me that your are trying to do signal processing in addition to exception handling that's all good but you should not be trying to catch and continue if you have a Segmentation Fault even though you can since it usually means that you have significant problem (usually with memory management) that you need to address..

---

### Post by Npl on 2011-10-25
im not sure how segmentation faults are handled with Linux, but I guess it just sends a signal to the process.
unless gcc does some complicated magic, you wont catch this kind of lowlevel error with C/C++ exceptions.

you`d need to overwrite the default signal handler to catch this error, the prototypes are in signal.h.

---

### Post by karlson on 2011-10-25
> **Npl said:**
> im not sure how segmentation faults are handled with Linux, but I guess it just sends a signal to the process.
unless gcc does some complicated magic, you wont catch this kind of lowlevel error with C/C++ exceptions.

you`d need to overwrite the default signal handler to catch this error, the prototypes are in signal.h.

Segmentation Faults on Linux don't throw exceptions.  It's a signal sent to the process, which seems to be processed through a custom handler.

---

### Post by robotz421 on 2011-10-25
Okay, I guess that is my answer, thank you.  Off to read about signal handling.

---

### Post by cgroza on 2011-10-25
Could you show us the exception you are trowing inside the try block?
Also, you should catch runtime_error before std::exception because any class derived from std::exception will be caught by the first catch block, so your second catch block will never get a chance to execute.

---

