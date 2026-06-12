---
title: "Using apache error log"
date: 2010-11-27
forum: Programming Talk
---

### Post by japhyr on 2010-11-27
Hello,

I am coding a browser-based front end to a database using python.  When there is an error in the programming, the message goes to the apache error log and all I see is a 500 Internal Server error.  I tried making a custom error page that would write the error to the browser for immediate feedback, but for understandable security reasons that is difficult.

What is a good workflow for accessing that error log efficiently?  The best I can come up with is keeping a terminal window open running 'tail -f error.log', but even that involves consistent window switching and pagedowns.  Any suggestions?

---

