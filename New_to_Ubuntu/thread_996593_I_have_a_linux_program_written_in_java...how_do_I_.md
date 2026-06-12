---
title: "I have a linux program written in java...how do I run it?"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by B34ST1Y on 2008-11-29
As the title suggests, I have a program I downloaded, that was written in Java, and I dont see any scripts or anything in the zipped file.

```

http://sourceforge.net/project/showfiles.php?group_id=56429



```

how do I run a java program?


p.s. - it's a Java implementation of a DC++ (peer 2 peer) hub (server)

---

### Post by Sorivenul on 2008-11-29
From the included README:

> Installation

------------



To use Shasta,



1) Edit the 'properties' file to change any settings.  The defaults

should be fine, except you should set your own hub.name.



2) Run it.  You'll need to have Java J2SDK v1.4 installed

([http://java.sun.com/j2se/1.4/download.html](http://java.sun.com/j2se/1.4/download.html)).  Windows users must

use J2SDK 1.4.1beta as it fixes some critical bugs in v1.4.

	java -jar Shasta.jar



3) Enjoy!  The easiest way to monitor the hub is to log in with a

client (eg. DC++, [www.sourceforge.net/projects/dcplusplus](www.sourceforge.net/projects/dcplusplus)).  Type

"+help" into the chat to see a list of commands.



The hublist only displays a small portion of registered hubs so yours

may take some time to show up.

There is more in that document you may find of interest.  Good luck.

---

### Post by bukwirm on 2008-11-29
Too slow, never mind.

---

### Post by VirtualEdgar on 2008-11-29
Its already there... :)

```
java -jar Shasta.jar
```

---

### Post by B34ST1Y on 2008-11-29
wow I feel really stupid -_-



thanks. sorry to clog the tubez of the internet with stupid questions...hahah

---

### Post by Sorivenul on 2008-11-29
> **B34ST1Y said:**
> thanks. sorry to clog the tubez of the internet with stupid questions...hahah
Don't feel stupid, we all have questions like this sometimes.  You're not clogging the net, just adding to your own knowledge.  There is plenty of other useful information on these forums, just have to search for it.

That said, if your issue is resolved, please take time to mark this thread "SOLVED" by using the link provided in the "Thread Tools" section near the top of the page.  

Good luck!

---

