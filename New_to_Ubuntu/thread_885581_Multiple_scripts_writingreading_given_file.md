---
title: "Multiple scripts writing/reading given file"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by ingrid_ozikem on 2008-08-10
This is a general Linux question I guess but I have a script that writes to a given file every 5 minutes (it opens and closes the file for each write operation).

 I want to have another script that generates graphs from this file when I want them.  Would it be a problem if it so happens that my second script is reading and processing the data file when the first script wakes up at the end of a 5 minute wait and tries to open the same data file to write?

Sorry.. a rather basic question..

---

### Post by mike2357 on 2008-08-10
Theoretically it could be a problem, especially if the write operation includes a lot data, or takes awhile to write.

If the writing operation is very fast, you're unlikely to notice anything.

One option is to just try it and monitor the situation over several days.  Another option is to have your graphing program check to see if the writing program is running at the moment, and if so, abort.

---

### Post by algorithm786 on 2008-09-04
Hi Guys, I am newbie in linux ... and I have recently joined the Ubuntu Forum... But I don't know how to post my own problem. Please help me.

---

