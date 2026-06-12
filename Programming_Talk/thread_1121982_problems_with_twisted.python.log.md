---
title: "problems with twisted.python.log"
date: 2009-04-10
forum: Programming Talk
---

### Post by NetSkay on 2009-04-10
hello,
im developing an application, and im trying to use the PythonLoggingObserver from twisted.python.log... 
this is a very strange occurance for me because the PythonLoggingObserver works on my development computer and on one of my ubuntu servers that i installed python-twisted on; however, on another 2 servers that i tested i get an error that 'module' does not have attribute PythonLoggingObserver...

i import the twisted class like so
from twisted.python import log
then i call like so
myvar=log.PythonLoggingObserver()
myvar.start()

im trying to avoid making my own observer, so i decided to simply dir(log) and my print output was as follows

['DefaultObserver', 'FileLogObserver', 'ILogContext', 'LogPublisher', 'Logger', 'NullFile', 'StdioOnnaStick', '__builtins__', '__doc__', '__file__', '__name__', '_clearIgnores', '_flushErrors', '_ignore', '_ignoreErrors', '_keepErrors', '_keptErrors', '_oldshowwarning', 'addObserver', 'callWithContext', 'callWithLogger', 'clearIgnores', 'context', 'datetime', 'defaultObserver', 'deferr', 'discardLogs', 'division', 'err', 'failure', 'flushErrors', 'ignoreErrors', 'logerr', 'logfile', 'msg', 'reflect', 'removeObserver', 'showwarning', 'startKeepingErrors', 'startLogging', 'startLoggingWithObserver', 'sys', 'theLogPublisher', 'threadable', 'time', 'util', 'warnings']

as you can see the PythonLoggingObserver is missing alltogether, has it been moved to another class, or is it some sort of a installation or packet error caused by ubuntu or the repositories...

if anyone could help, much appreciated...
thank you

---

### Post by pmasiar on 2009-04-11
Your question is very specialized, I am sure you will have more luck when asking at twisted dev mailing list.

---

### Post by NetSkay on 2009-04-12
actually, looking over things, and i consulted the sys admin whos on our dev team, we came to the conclusion that we were simply running outdated twisted version...
our server runs ubuntu hardy LTS, and the framework in the repositories is 2.1, the current is 8.2, waaayyyyy outdated, we had a choice of upgrading to intrepid ibex, but we decided not to, instead the admin found a fix, and we went ahaed and got the latst twisted from the intrepid ibex repositories

this leaves me wondering, why does hardy use a separate repository than intrepid does, and someone should seriously update twisted on hardy lts!

---

