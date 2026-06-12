---
title: "Suggestions with writing an NNTP server"
date: 2010-10-15
forum: Programming Talk
---

### Post by samalex on 2010-10-15
Hey Guys,

I'm thinking of hacking out a new project to create an NNTP server that can either bridge forums like phpBB to NNTP or house custom content in MySQL to serve via NNTP.  My problem though is I'm not sure which language offers the best support for NNTP natively or otherwise.

I know Qt has some simple NNTP support out of the box, but I wasn't sure if it'd be better to write something on my own in C++ or Python.  I've only done basic coding in either, and nothing using socket connections.  Likewise any suggestions on a good library in C++ or otherwise that would help?  I even thought about checking some of the open source NNTP servers, but I didn't know if digging through someone else's code would be a good first step.

Thanks for any suggestions... As for my skill set, I've been coding in one form or another since the mid 80s, but anymore my focus is more on the database side of things (I'm a DBA by profession).

Thanks again and take care --

Sam

---

### Post by samalex on 2010-10-15
I found [Newsd]("http://newsd.easysw.com/") which is a fairly simple NNTP Server, so I might start going through its source code and see if I can use portions of it to get me going. 

Take care --

Sam

---

