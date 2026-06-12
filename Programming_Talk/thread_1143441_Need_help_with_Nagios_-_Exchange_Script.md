---
title: "Need help with Nagios - Exchange Script"
date: 2009-04-29
forum: Programming Talk
---

### Post by creolbuay on 2009-04-29
Ok.. Here we go.. I am new to scripting in general and need lots of assistance. I have a small project to complete that will allow us to monitor a exchange web site (OWA) from Nagios3. I have a check already in place to check if the site is up and running via http checks. What I need to do now is find a way to ensure that one can actually login and get emails. 
I have searched for two days now and can't seem to find anything whatsoever on the topic. Any assistance will be greatly appreciated.

---

### Post by creolbuay on 2009-05-06
Figured it out never mind:P. This Thread can be closed.

---

### Post by uvdevnull on 2009-06-12
> **creolbuay said:**
> Figured it out never mind:P. This Thread can be closed.

Can you post your resolution for future searchers?  Including myself. I can log in using check_http but I can't check content due to this error seen in verbose output from the check:

```
This page uses frames, but your browser doesn't support them.
```

If I disable frame support in Firefox, it also gives the same error.

---

