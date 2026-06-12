---
title: "Simple, solid open source mail server?"
date: 2010-07-08
forum: Programming Talk
---

### Post by Cuddles McKitten on 2010-07-08
I'm starting work on a (slightly) customized mail server and I'd like to see if anyone has any suggestions as to which one I look into.  It needs to have STMP and POP3 support and I'd prefer that it be as simple as possible; looking through fifty .C files just to find the right function is no fun.  Obviously, security is another important factor.  Lastly, I'll also be using an open source webmail client which currently is Open WebMail.

The only modification I'm going to be making (for now) is checking a MySQL DB before sending the message on to the user and having a custom bounce message if it fails the check.

At the moment, I think qmail is going to be my choice, but I thought I might as well try to tap the abundant experience here to check my work.

---

