---
title: "Eclipse Galileo issues on Ubuntu 9.10 64bit"
date: 2009-12-20
forum: Programming Talk
---

### Post by tinny on 2009-12-20
Hello

I am running Eclipse Galileo (downloaded from eclipse.org) on Ubuntu 9.10 64 bit. I have installed the sun-java6-jdk package.

```

$ java -version
java version "1.6.0_15"
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
Java HotSpot(TM) 64-Bit Server VM (build 14.1-b02, mixed mode)

```

One issue I am having is that I cannot install any new plugins. 

```

Help > Install New Software

```

Ive noticed that in general the UI doesn't correctly show a list of the available components from a given update site. If I resize the UI the list appears, but after selecting the desired components and clicking "next" nothing happens.

Does anyone out there have Eclipse Galileo (3.5.1) running on Ubuntu 9.10 64 bit?

Thanks

---

### Post by AndThenWhat on 2009-12-20
Have you installed the 'eclipse-rcp' package? Mine wouldn't install any plugins until I installed that.

---

### Post by Can+~ on 2009-12-20
```
#!/bin/bash

export GDK_NATIVE_WINDOWS=true
<where eclipse is>/eclipse # the eclipse binary executable
```

(Or use a local path)

Use that to fix the issue.

---

### Post by tinny on 2009-12-20
Thanks for the replies

Ive "fixed" my issue by using Eclipse 3.5.1 from the repositories.

Then I install all eclipse related packages (brute force, I know)

```

sudo apt-get install eclipse*

```

I can now install my plugin. (JBoss SEAM tools)

Yah! Now I can enter JSF and EJB hell!

---

