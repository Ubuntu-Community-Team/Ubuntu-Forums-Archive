---
title: "Writing a Script"
date: 2014-10-06
forum: New to Ubuntu
---

### Post by Quarkrad on 2014-10-06
I use gadminrsync to run a back process.  I would like to write a simple script that runs the gadmin for me.  I have written simple scripts and actioned them via an icon on the desktop - my question is:   Assuming the name of the gadmin back up script is called **test**, how do I get the script I want to write not only to fire up gadmin but also action **test**?

---

### Post by nerdtron on 2014-10-06
Even with you explanation, I'm a bit confused but here goes...
Want a script call another script to run? Just input the path to the script you want to call.
```
/bin/bash /path/to/call/test 
```
Want to run a script and make sure another script is also run after the first once is completed? Add && between the two commands.
```
/bin/bash /path/to/first/script && /bin/bash /path/to/second/script
```

---

### Post by Habitual on 2014-10-06
> **Quarkrad said:**
> I use gadminrsync to run a back process.  I would like to write a simple script that runs the gadmin for me.  I have written simple scripts and actioned them via an icon on the desktop - my question is:   Assuming the name of the gadmin back up script is called **test**, how do I get the script I want to write not only to fire up gadmin but also action **test**?

I hope you meant test.sh , as naming a file the same as a bash internal, or a system utility both called 'test' is a bad idea.

---

### Post by Quarkrad on 2014-10-06
Thanks - just what I needed (yes - it is called test.sh)

---

