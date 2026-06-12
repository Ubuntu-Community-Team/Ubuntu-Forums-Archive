---
title: "logging commands not executed from the shell"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by dupa on 2008-09-02
hello!
i have a java application that uses getRuntime.exec and in this way it executes some shell commands.
I'm experiencing problems about this.
Is there a way to log every commands executed by a specific user?
I mean.. if i open a terminal and if I execute something, i find it using "history" command. how can I find logs of things executed in this "non standard way" ?
thanks

---

### Post by freak42 on 2008-09-02
Runtime.exec returns a "Process" Object
([http://java.sun.com/j2se/1.5.0/docs/api/java/lang/Runtime.html](http://java.sun.com/j2se/1.5.0/docs/api/java/lang/Runtime.html))

from the process object you can get input/output or error stream objects:
[http://java.sun.com/j2se/1.5.0/docs/api/java/lang/Process.html](http://java.sun.com/j2se/1.5.0/docs/api/java/lang/Process.html)

hth

---

### Post by dupa on 2008-09-02
> **freak42 said:**
> Runtime.exec returns a "Process" Object
([http://java.sun.com/j2se/1.5.0/docs/api/java/lang/Runtime.html](http://java.sun.com/j2se/1.5.0/docs/api/java/lang/Runtime.html))

from the process object you can get input/output or error stream objects:
[http://java.sun.com/j2se/1.5.0/docs/api/java/lang/Process.html](http://java.sun.com/j2se/1.5.0/docs/api/java/lang/Process.html)

hth

Thanks.. anyway, it's not a java question :)
My case is complicated.. i need to run a graphical app from a Tomcat web application, and so i set the DISPLAY environment variable to a Xvfb server.
If i set in a wrong way the DISPLAY var, i found in the err stream object the problem that display cannot be opened.. if I set correctly the DISPLAY var, I don't get any output in error/output but seems that application doesn't run at all.

Is there any way to see some linux log where that execution attempt will be logged?
thank you.

---

