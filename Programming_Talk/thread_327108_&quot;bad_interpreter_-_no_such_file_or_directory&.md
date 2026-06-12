---
title: "&quot;bad interpreter - no such file or directory&quot;"
date: 2006-12-28
forum: Programming Talk
---

### Post by Jayzilla on 2006-12-28
I'm trying to run a shell script, and it's not working.  

```
jayzilla@server1:~/roborumble/robocode$ ./roborumble.sh
bash: ./roborumble.sh: /bin/sh^M: bad interpreter: No such file or directory

```

Any ideas?

---

### Post by duff on 2006-12-28
install **sysutils** and then run **dos2unix** on your script.

---

### Post by Jayzilla on 2006-12-28
That did the trick.  

Thanks!

---

### Post by sobhanmaddineni on 2007-10-18
How to install the sysutils and run dos2unix

---

### Post by LaRoza on 2007-10-18
> **sobhanmaddineni said:**
> How to install the sysutils and run dos2unix

Looking in Synaptic would make things easy...

---

### Post by josef.sabl on 2008-02-01
In synaptic search for sysutils, check the checkbox and click apply. Then go to directory where you have the script and run dos2unix yourscript.sh.

Then your script should work, so try running it again.

---

### Post by TronBoRG on 2008-07-15
Thanks!!

---

