---
title: "Can't execute any .sh!"
date: 2012-09-15
forum: New to Ubuntu
---

### Post by spa21788 on 2012-09-15
My laptop updated the other day, ubuntu 12.04, since then I can't execute any of my .sh even when in properties the execute box is ticked, can someone help me please, it's urgent! :(

---

### Post by steeldriver on 2012-09-15
what is the exact error message? are you trying to execute them from the current dir

```
./myscript.sh
```or are they somewhere else? if the latter, have you checked that your PATH environment variable is set correctly?

---

### Post by josephmills on 2012-09-15
1st) if these are bash scripts we do not need any .sh at the end this is confusing and not needed 
but if there sh then cool. sounds like a permission trouble can you go to your dir that you hold your scrits (maybe ~/bin) and do a 
```
ls -al 
```
then paste the output here please and thanks

---

### Post by spa21788 on 2012-09-15
warning: The VAD has been replaced by a hack pending a complete rewrite
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  138 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  23
  Current serial number in output stream:  23


Tried to run it from terminal and got that...

---

### Post by Wim Sturkenboom on 2012-09-15
Playing games ? ;) Enter that first line in google and you get plenty of hits.

---

