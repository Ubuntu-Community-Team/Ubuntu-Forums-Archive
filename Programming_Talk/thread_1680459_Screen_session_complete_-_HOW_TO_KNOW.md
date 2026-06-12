---
title: "Screen session complete - HOW TO KNOW"
date: 2011-02-02
forum: Programming Talk
---

### Post by rcktsingh on 2011-02-02
Hi All,

I am not sure if this is the correct forum to post this query. Apologies if it isn't.

My query: Lets say I have put a job under a screen session, and then detached the session. Now, is there any way I can know that my job is complete (complete job means the bash shell command line comes back) ? 

Some of the ways to notify the user about it could be- send a message on the shell saying "Hello there, your job is complete".

Any help is appreciated. 
TIA

---

### Post by gmargo on 2011-02-02
You could run **ps(1)** and check for the process id that you carefully noted before detaching your **screen(1)** session.

Or run your stuff through a shell script wrapper that writes a file somewhere (or invokes a notifier program) when it's finished.

---

