---
title: "Executing a shell script on closing OOCalc"
date: 2006-12-03
forum: Programming Talk
---

### Post by jfl on 2006-12-03
I want to run a shell script when I am closing OpenOffice Calc. The scrip saves documents to different HD...

Of course, I could run a macro from inside OO to invoke the script, but I'd rather have something more general that could be used with other apps.

I vaguely remember reading about it on a forum many months ago ...

I am still running Dapper; it is an office box and cannot take chances !!!

Thanks for any suggestions.

JF

---

### Post by sitedesign on 2006-12-03
You could write a shell script to start OO Calc then have the rest of the script to do what you want. Then once OO Calc exits the rest of the script should run.

---

### Post by jfl on 2006-12-04
Thanks for the suggestion; however, it is used by people who are not "computer literate"; if I change the way they access OO, it is going to confuse them.

jf

---

### Post by Ramses de Norre on 2006-12-04
Calc is started by a perl script (/usr/bin/oocalc), so I guess you can append a second exec line in that script to run after oocalc is finished.

---

### Post by thomasaaron on 2006-12-04
run oocalc in the background.

start oocalc like this:

oocalc &

That runs it in the background and you won't have to wait for it to stop to do other things from the shell.

Hope that helps.

---

