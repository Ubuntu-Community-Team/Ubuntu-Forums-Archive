---
title: "Installing PDT via Eclipse?"
date: 2007-04-20
forum: Programming Talk
---

### Post by barmazal on 2007-04-20
Is it possible, maybe i just misread on PDT webpage but there is method to install these tools from Eclipse updates manager? How i do it if it's possible

Thanks

---

### Post by Mirrorball on 2007-04-20
Add this as a new remote site:
[http://download.eclipse.org/tools/pdt/updates/](http://download.eclipse.org/tools/pdt/updates/)
Enable it, Callisto and Eclipse Updates too. Click next and select PDT. Then it's going to complain you didn't install a plugin X. Find this plugin and select it. Then it's going to complain you didn't install Y. Select Y and so on... It's annoying dependency hell but just keep going.

---

### Post by barmazal on 2007-04-20
```
Network connection problems encountered during search.
  Unable to access "http://www.software-mirror.com/eclipse/tools/pdt/updates/".
    Error parsing site stream. [whitespace required]
    Error parsing site stream. [whitespace required]
```


this is what  i get with that link, this is what i've got before as well sorry i haven't pointed that out in my first post

---

### Post by Mirrorball on 2007-04-20
Try [http://download.eclipse.org/tools/pdt/downloads/](http://download.eclipse.org/tools/pdt/downloads/) then.

---

### Post by barmazal on 2007-04-20
jokes, last slash was the problem with it it works fine and yeah you was totally right about half of Callisto downloaded along with PDT, don't know what Java stuff mostly has to do with it.


thanks for help

---

### Post by jrosell on 2008-11-04
Use [http://download.eclipse.org/tools/pdt/updates/]("http://download.eclipse.org/tools/pdt/updates/ instead") instead
Thanks from [http://sistemakiwi.com]("http://sistemakiwi.com")

---

