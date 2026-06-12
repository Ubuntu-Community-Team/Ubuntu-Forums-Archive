---
title: "Evolution message preview does not work"
date: 2012-07-09
forum: New to Ubuntu
---

### Post by cwmoser on 2012-07-09
Ubuntu 12.04 64 bit
Evolution email app message preview often just stops
displaying email contents.  Seems like it gets hung
up on a prior email and won't change with the next
selected email.  Any fixes/udates???

Carl

---

### Post by cwmoser on 2012-07-10
Am I the only one with this problem, or has everyone
else converted to Thunderbird mail?

Carl

---

### Post by sg3524 on 2012-11-04
This is happening for me as well.  On three different devices (all 12.04).  Only happens on long messages.

These messages typically have been group discussions with multiple replies.  The norm here is showing previous emails in the thread with "<" on each line of the previous thread.  I got to thinking about this and the response I found from an Evolution developer saying this is related to gtkHTML.  

I configured evolution (edit->preferences->mail preferences->html messages) to use Plain text mode by selecting the option to "Show suppressed HTML parts as attachments"  and HTML Mode as "Only ever show plain text".  Now I can't replicate the problem.  HTML portions of inbound email are now attachments, which I can choose to view inline (handy because  get a fair amount of email that is only html).

I think gtkHTML is getting blown away by what it thinks is an enormous amount of html open tags and no closing ones.  But that is just a hunch, I did not try to verify it.

---

