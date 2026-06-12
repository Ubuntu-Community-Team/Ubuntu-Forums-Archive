---
title: "w3schools.com try it yourself editor"
date: 2011-10-08
forum: Programming Talk
---

### Post by AskTell on 2011-10-08
I was wondering how I could create something similar to w3schools try it yourself editor found here  [http://w3schools.com/xml/tryit.asp?filename=tryxml_display_table](http://w3schools.com/xml/tryit.asp?filename=tryxml_display_table)

I've never seen another website with a feature like this or a tutorial/howto on how it was made or how it could be made in theory.

---

### Post by Reiger on 2011-10-08
JavaScript has an **eval** function. So I imagine the W3CSchools editor simply listens for an event on the &#8220;Try it&#8221; button, then grabs the **innerHTML** (text) from the text area and feeds that to **eval**.

If you are going to make such a site yourself you should be aware of the security implications of using **eval** in such a straightforward manner, though. (Plenty of articles out there. Suggest to read up on XSS, CSRF.)

---

### Post by AskTell on 2011-11-01
It'll be awhile till i try to make something like this so I'll go ahead and mark this one solved :) thx for info!

---

