---
title: "How to Add Opera Web Browser to Aptana Studio 3 (Run As external Program)"
date: 2011-07-07
forum: Programming Talk
---

### Post by samMD on 2011-07-07
Hi Im starting to write a Web Page and use Opera Im wondering how to add the browser to launch and test my code when ever i go to "run configurations" and add the opera program from the folder the console in aptana gives me this message:

> opera: please specify shared directory with -sharedir or in $OPERA_DIR

---

### Post by samMD on 2011-07-07
bump

---

### Post by samMD on 2011-07-08
bump

---

### Post by cariboo on 2011-07-08
Please don't bump more than once every 24 hours. The person that can answer your question may have not seen it yet.

---

### Post by samMD on 2011-07-12
@cariboo907 sorry about that got a little impatient xD

P.S solved I had to learn a bit more on linux(linuxcomman.org will help for linux beginners) if you want to use Opera as the browser to test your pages click the arrow next to the "Run" button(looks like the green play button) and when you go to change the the browser executable from firefox go into /usr/bin directory and select "opera"(program bin). You must go to exact directory otherwise aptana will complain about no "Shared libraries" spent an hour figuring it out xD 

and in "preferences" under "aptana" go to "Editors" and check "opera" click ok..and then click run voila! Opera will now be used to test the web pages

---

