---
title: "errors from synaptic"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by islandstone on 2008-11-16
I keep getting this error when  insalling packages using synaptic, regardless of what i'm installing.

"This package is not an installer package , it does not actually contain the JDk documentation. You will need to go download one of the archives.

jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non update version if this is the first installation)
please visit

[http://java.sun.com/javase/downloads](http://java.sun.com/javase/downloads)

now and download,the file should be owned by root.root and copied to /tmp

press return to try again  no+return to abort.

return just repeats the error so I enter no , so far the error does not sem to have affected the install(s).

[IMG]http://lh4.ggpht.com/_j3_FbfYEV9U/SSBlC5ZwCDI/AAAAAAAAAOY/tkabwMMhza0/s128/Screenshot-Applying%20Changes.png[/IMG]

---

### Post by Sorivenul on 2008-11-16
The easy solution is to uncheck the two files mentioned in Synaptic and apply the changes.  
Uncheck:
jdk-6-doc 
jdk-6-doc-ja
Or their Ubuntu matches, which I believe are sun-java6-doc and sun-java6-doc-ja (but don't quote me as I'm not on my Ubuntu install right now).

If you want to install these, follow the [link]("http://java.sun.com/javase/downloads/index.jsp") and download the files.  

Good luck.

---

