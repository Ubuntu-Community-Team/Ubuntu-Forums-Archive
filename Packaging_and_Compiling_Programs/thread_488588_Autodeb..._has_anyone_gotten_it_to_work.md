---
title: "Autodeb... has anyone gotten it to work??"
date: 2007-06-30
forum: Packaging and Compiling Programs
---

### Post by brennydoogles on 2007-06-30
I have been playing around with autodeb recently, and I have yet to get it to work has anyone else had this problem?? Here is the output of my most recent attempt:

```
brendon@brendon-linux:~/downloads$ autodeb pidgin-2.0.2.tar.bz2 
/home/brendon/bin/autodeb: 29: function: not found
Aborting...
/home/brendon/bin/autodeb: 31: RestoreState: not found
brendon@brendon-linux:~/downloads$ 

```

Is there some sort of configuration problem on my system, or is it a problem with autodeb??

---

### Post by brennydoogles on 2007-07-04
bump??

---

### Post by abhijeetmaharana on 2007-07-23
Came here by Google due to [http://ubuntuforums.org/showpost.php?p=3062600&postcount=101](http://ubuntuforums.org/showpost.php?p=3062600&postcount=101).

Change the first line from !/bin/sh to !/bin/bash. It is mentioned in the known problems and bugs section.

But you will most likely run into some syntax errors.
I am also trying to make it run. Let me know about any progress made at your end.

---

