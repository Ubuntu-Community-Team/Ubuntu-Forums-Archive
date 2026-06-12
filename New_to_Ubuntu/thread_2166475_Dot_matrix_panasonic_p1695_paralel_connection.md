---
title: "Dot matrix panasonic p1695 paralel connection"
date: 2013-08-09
forum: New to Ubuntu
---

### Post by Vagelism_Meintasis on 2013-08-09
Hello to all.
I got a script that takes the temperature of a sensor and send it to a server but also need to print it out on a periodic basis on a dot matrix printer.
I got everything set up but... When the script sends a line "temperature something..."  I got on my printer only one or 2 characters.
I tried also in terminal to send a single line of text like
```
echo "test" > /dev/lp0
```
and still the same problem.
The command seems to go to the printer, since it move the head but always prints one or 2 characters.
Any solution?
Thank you!

---

