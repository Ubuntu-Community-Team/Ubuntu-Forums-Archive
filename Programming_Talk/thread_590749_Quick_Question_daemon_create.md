---
title: "Quick Question daemon create?"
date: 2007-10-25
forum: Programming Talk
---

### Post by notaloafer on 2007-10-25
I'm a total newbie when it comes to the core aspects of Ubuntu (starting up scripts, etc) but here is what I have:

I have a server called a "JBLS Server"
[http://www.jbls.org/](http://www.jbls.org/)

The program runs in Java Sun 6 runtime environment and I currently have to start the service manually every time I restart the computer by issuing the following commands in Gnome in Terminal: 
```

su - jbls
-enter password-
cd /Desktop/JBLS
java -jar JBLS.jar

```

After issuing those commands the JBLS server starts up and starts accepting connections. The only problem lies when I stop the gnome service when I'm not using it (99% of the time). When I stop gnome it stops JBLS and kills the process. Also when I close the terminal window that the process is running in, it also kills the process.

**the question: ** how can I make the following commands into a background-running process or a daemon (if I'm using the term "daemon" correctly) so it automatically starts up and starts accepting connections when my server is rebooted?

If you need any more information please let me know!

Thanks!!!
-Eric

---

