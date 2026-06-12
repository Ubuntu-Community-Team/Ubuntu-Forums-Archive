---
title: "Is that being called?"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by pzs on 2008-11-27
I have a Perl script somebody sent me that implements a pipeline - it calls a number of shell tools in succession with some processing on the output. I want to know whether it runs a particular command, but I can't find the call in the script itself. It's possible it calls it from some library I'm not aware of.

Is there some command I can run that will trace the run of a particular command and tell me what other commands it invokes?

---

### Post by porchrat on 2008-11-27
If it is a script then when running the script use the -d switch to run the debugger.

If you're looking for something a little more complex then perhaps you should try the "perl-debug" package.

Hope this helps.

---

### Post by pzs on 2008-11-27
Actually, I'd prefer a non Perl specific solution for future reference. Is there some way of finding out what processes a process forks as it goes along? This would also give me a quicker method than stepping through the code (which takes half an hour to run at full speed) using a debugger.

---

