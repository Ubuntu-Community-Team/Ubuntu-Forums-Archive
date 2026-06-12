---
title: "Mythtv 0.18.1 + mysql5 issue fixed"
date: 2006-06-28
forum: Packaging and Compiling Programs
---

### Post by chipmonk010 on 2006-06-28
So there is a known bug that mythtv-0.18.1 doesnt work with mysql5. When you run mythfilldatabase to update your schedule listings it fails because "repeat" is used in the database queries. This is fixed by editing the datadirect.cpp file in the source code so that "isrepeat" is used in the queries which works with mysql5. I apt-get(ed) the source and patched the source code to fix the problem as per the packaging guide in the wiki. 

Now i want to know where to send it to get the fix in the repos?

I tried uploading to revu but my upload froze and now i cant re-upload it.....nor can i delete what i uploaded.....

should i contact the maintainer?

should i post a debdiff file somewhere?

what should i do?

Thanks
Chris

---

### Post by chipmonk010 on 2006-06-29
Ok. I have got the package uploaded to revu [http://revu.tauware.de/details.py?upid=2541](http://revu.tauware.de/details.py?upid=2541)
Feel free to try it

Chris

---

