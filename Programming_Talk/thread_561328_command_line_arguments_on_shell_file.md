---
title: "command line arguments on shell file"
date: 2007-09-27
forum: Programming Talk
---

### Post by Fixman on 2007-09-27
Is there a way that, on a shell file, to accept command line arguments? I remember that, in DOS, you cound use %1% to access command arg nº1, but how do you do it on UNIX?

---

### Post by overkillm on 2007-09-27
$0 through $9 can be used to reference command line arguments, if I'm not mistaken.  $0 is the shell script itself. So, if your script is called *myscript*, then for the command line: 

myscript foo bar

$0 = myscript
$1 = foo
$2 = bar

This is off the top of my head so I may be a bit off, but I think it's right.

---

### Post by LaRoza on 2007-09-27
[http://www.ibm.com/developerworks/library/l-bash2.html](http://www.ibm.com/developerworks/library/l-bash2.html)

---

