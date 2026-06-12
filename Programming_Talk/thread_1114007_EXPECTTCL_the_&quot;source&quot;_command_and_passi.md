---
title: "EXPECT/TCL: the &quot;source&quot; command and passing arguments"
date: 2009-04-02
forum: Programming Talk
---

### Post by qmqmqm on 2009-04-02
Does anyone know how to pass parameters to Expect script if it is "source"ed from another Expect script?

For example, in an Expect script I have:

source "myOtherScript myArgument"

However I get error:

couldn't read file "myOtherScript myArgument": no such file or directory


Google did not give me anything useful...


Thanks a lot!

Tom

---

### Post by stevescripts on 2009-04-02
Tom,

Take a look at this page from the tcler's wiki:

[http://wiki.tcl.tk/10025](http://wiki.tcl.tk/10025)

If this doesn't solve your problem, feel free to ping me.

Steve

---

### Post by qmqmqm on 2009-04-02
> **stevescripts said:**
> Tom,

Take a look at this page from the tcler's wiki:

[http://wiki.tcl.tk/10025](http://wiki.tcl.tk/10025)

If this doesn't solve your problem, feel free to ping me.

Steve

Thanks again Steve! It works like a charm :)

---

