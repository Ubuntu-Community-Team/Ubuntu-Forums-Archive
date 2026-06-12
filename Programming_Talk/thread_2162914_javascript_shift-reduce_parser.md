---
title: "javascript shift-reduce parser"
date: 2013-07-16
forum: Programming Talk
---

### Post by ivanvodisek on 2013-07-16
Here is an universal parser in javascript: [http://synth.wink.ws/moonyparser/](http://synth.wink.ws/moonyparser/)


I've been to hell and back to make it faster, but that's it, shift-reduce can't be much faster. Unfortunately, finding errors in text makes it three times slower. At least it has linear parsing time.

---

### Post by ivanvodisek on 2013-07-17
i've just fixed some ugly bug about unspecified tokens. sorry for inconvenience.

oh, did i mention that the code is free for any use? just don't sue me, that's all :)

---

### Post by MG&amp;TL on 2013-07-17
That's pretty cool! Having dabbled with parsers and peered uneasily at the shift-reduce variety, I applaud the effort, especially in JavaScript*. :)


*[SIZE=1]&#8203;Nothing against JS. I just can't see it being easy to write a parser in.[/SIZE]

---

### Post by Ivan_Vodiek on 2013-11-18
[COLOR=#000000][FONT=trebuchet ms]Hi all.[/FONT][/COLOR]
[COLOR=#000000][FONT=trebuchet ms]A new version of Moony Parser is out. This time it implements "Earley" parser. Also handles all CFGs. It is up to 100 times faster than previous version in some cases. There should be less bugs because the code is simpler.[/FONT][/COLOR]
[COLOR=#000000][FONT=trebuchet ms][synth.wink.ws/moonyparser/]("http://synth.wink.ws/moonyparser/")[/FONT][/COLOR]

---

