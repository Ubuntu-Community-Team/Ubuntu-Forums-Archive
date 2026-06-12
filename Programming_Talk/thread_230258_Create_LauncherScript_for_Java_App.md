---
title: "Create Launcher/Script for Java App??"
date: 2006-08-05
forum: Programming Talk
---

### Post by featherking on 2006-08-05
I need to run this command

```
java -cp jts.jar:jcommon-1.0.0.jar:jfreechart-1.0.0.jar:jhall.jar:other.jar:rss.jar -Xmx256M jclient.LoginFrame .
```

But from this directory /home/chris/IBJts or ~/IBJts. If i try to create a launcher with ```
~/IBJts/java -cp jts.jar:jcommon-1.0.0.jar:jfreechart-1.0.0.jar:jhall.jar:other.jar:rss.jar -Xmx256M jclient.LoginFrame .
``` It gives me an error.

Is there a certain way i can create a launcher to run this command? I had also thought of a script that could go to the directory and then run the command from there but i wouldnt know where to begin to write that

Any ideas?

---

### Post by ToniWiki on 2007-04-03
Try this:

(I suppose that jar files are in  /home/chris/IBJts)

1.- Create a script like this:

```

#!/bin/sh
cd /home/chris/IBJts
java -cp jts.jar:jcommon-1.0.0.jar:jfreechart-1.0.0.jar:jhall.jar:other.jar:rss.jar -Xmx256M jclient.LoginFrame .

```

2.- Create a launcher to the previous script in Desktop or where you want.

It worked for me. :)

---

### Post by hogsmate on 2010-04-26
Thanks ToniWiki that helped me a lot :) :popcorn:

---

