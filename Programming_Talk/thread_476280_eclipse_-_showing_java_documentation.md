---
title: "eclipse - showing java documentation?"
date: 2007-06-17
forum: Programming Talk
---

### Post by drorl on 2007-06-17
hi.
when eclipse suggests methods automatically (auto completion) it shows the relevant documentation near them, just for my classes and not for java API methods and classes.
does any one know how can i make it visible also for java's code?
thanks
dror

---

### Post by Woei on 2007-06-17
> **drorl said:**
> hi.
when eclipse suggests methods automatically (auto completion) it shows the relevant documentation near them, just for my classes and not for java API methods and classes.
does any one know how can i make it visible also for java's code?


Try Window -> Preferences -> Java -> Installed JREs -> Edit -> clicking on rt.jar -> Javadoc location. You can put in an URL like on the screenshot below, but you'd better be on a fast, low-latency connection for that. Preferably, you should install the sun-java6-doc package, and point the dialog to its install location, e.g. /usr/lib/jvm/java-6-sun/docs/api.

[[IMG]http://woei.be/images/eclipse_doc.png[/IMG]]("http://woei.be/images/eclipse_doc_full.png")

---

### Post by drorl on 2007-06-17
now i see only the official java's documentation without my code's documentation that was visible before when no source for the docs was defined.
how can i make them "live" together?
thanks
dror

---

