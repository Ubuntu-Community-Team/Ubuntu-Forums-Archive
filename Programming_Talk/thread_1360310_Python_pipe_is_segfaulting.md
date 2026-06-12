---
title: "Python pipe is segfaulting"
date: 2009-12-20
forum: Programming Talk
---

### Post by AndThenWhat on 2009-12-20
I am trying to create a Python GUI for the "pianobar" cli application and it enters the username, password, and station perfectly and says the song that is about to play and then "Segmentation Fault"

```
      43)     Wolfgang Amadeus Mozart Radio
       44)     Wolfmother Radio
       45)     Zion I Radio
[?] Select station: 1
|>  Station "Alternative Pop/Rock" (147018560214960856)
(i) Receiving new playlist... Ok.
|>  "Let Me Go" by "3 Doors Down" on "Seventeen Days" <3
Segmentation fault
```

I think it is because I need to change the encoding of the pipe to something sound-related, but I don't know what is happening here.  Does anyone know how to play sound from a pipe?

---

### Post by AndThenWhat on 2009-12-21
I discovered after a LOT of trial and error, that oddly enough the program was segfaulting because it was trying to send continuous output and i wasn't receiving it because I needed to use the readlines() function.

This stand-alone Ubuntu Pandora Radio client is very near completion!

---

