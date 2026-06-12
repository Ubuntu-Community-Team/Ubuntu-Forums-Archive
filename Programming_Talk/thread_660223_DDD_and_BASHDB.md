---
title: "DDD and BASHDB"
date: 2008-01-06
forum: Programming Talk
---

### Post by mkisow on 2008-01-06
When I launch ddd from the command line (ddd --bash) I get an error that bash is not found.  When I launch ddd --interpreter=/bin/bash <script name> I get the same thing.  When I launch ddd --bash -debugger ddd launches without error I receive the hourglass and a message in the lower left that says opening session... in the lower payne I get a bash shell and I can launch bashdb <script name> from there but bashd dosen't behave correctly. 

I need to know what I am missing, I would use EMACS, but for someone used to the vi editor EMACS is a little backwards, and I like ddd's interface.  Can anyone point me in the right direction?

---

### Post by dwanders on 2008-10-08
Dont suppose you ever located a fix or a reason for this? I seem to be experiencing it as well.

---

### Post by meonkeys on 2009-01-10
I am also unable to use bashdb via DDD in Ubuntu 8.10.

Just found this: [http://archivum.info/ddd@gnu.org/2008-10/msg00010.html](http://archivum.info/ddd@gnu.org/2008-10/msg00010.html)

---

### Post by dwanders on 2009-01-10
Wow thats my post at DDD =) and you'll notice they never did answer anything. In fact they changed the topic entirely!

I still have not found an answer for this. I would really like to get it working too!

---

### Post by slavik on 2009-01-10
ddd works for scripts?

---

### Post by dwanders on 2009-01-10
Definitely - I am not of the old school (I would not even so much as consider myself a programmer!) but I would be lost without the step debugging provided by most gui IDEs. I really take my hat off to those guys that can keep track of stuff in their heads. Most stuff I do are system scripts with perl and bash. I love DDD with the perl and would get a ton more use out of it if the bash side of it worked! too. It uses a bunch of backend command line debuggers, for all kinds of things besides C or C++ - check it out

---

### Post by aj_org_nz on 2009-01-28
when I use:

ddd --debugger /usr/bin/bashdb <sript-name> 

DDD seems to work

---

### Post by dwanders on 2009-01-28
Hey - just tried it again in Ubuntu 8.10 (recently upgraded from LTS) and it seems to be working now just as aj_org_nz said. This is sweet now I can set up JEdit to call DDD directly for debugging bash scripts as well as my perl scripts! thanks to whomever fixed what ever issue it was.

---

### Post by meonkeys on 2009-01-28
> **aj_org_nz said:**
> when I use:

ddd --debugger /usr/bin/bashdb <sript-name> 

DDD seems to work

Works for me too on Ubuntu 8.10. Yay!

---

### Post by codell on 2012-08-08
Anyone got it working on Ubuntu 12.04?

---

### Post by Stabledog on 2012-08-21
> **codell said:**
> Anyone got it working on Ubuntu 12.04?

I'm seeing the same problem on 12.04.   Ugh.  Will post if I can track it down.

---

### Post by Quackers on 2012-08-21
This thread is over 3 years old. 
Thread closed.

---

