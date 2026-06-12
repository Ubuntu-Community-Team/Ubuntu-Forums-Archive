---
title: "(Request) Learning the shell, scripting and general administration"
date: 2013-08-07
forum: New to Ubuntu
---

### Post by Tlawrence on 2013-08-07
A million googles/bings/yahoos/ducks leads me to various forum posts asking the same question and almost always with the same response -to read (some book/pdf/tutorial).

I'm reading through O'Reillys learning the bash shell, advanced bash scripting guide, and a few other scripting and bash books. 

The problem I'm running into is that reading and tinkering and figuring out vim and rudimentary scripts is all good and great but it isn't meaningful hands on experience.

Can anyone recommend some resources or projects with real life practice with bash scripting or linux administration. With plenty of explanations, examples and exercises? 

Thanks.

---

### Post by Lars Noodén on 2013-08-07
You could look around your system for examples.  Reading through them, but not changing them, will give you some ideas.

Here is one way to find some of the shell scripts:

```

find /etc/ /usr/ -exec grep -El '#!/bin/sh|#!/bin/bash' {} \; 2>/dev/null 

```

There are two programs being used there, [find](http://manpages.ubuntu.com/manpages/raring/en/man1/find.1.html) and [grep](http://manpages.ubuntu.com/manpages/raring/en/man1/grep.1.html).  find is searching two hierarchies.  grep is looking for a regular expression with two patterns, logical OR.  Errors and warnings from either are sent to the bit bucket so you get just a list of shell scripts.  

Once you have the list you can then scan it for interesting implementations.  The list will be long so you can skip the ones that are complex or hard to understand until later.

By the way, I hope your search for resources turned up these:
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)
[http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ)
[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

### Post by Tlawrence on 2013-08-08
Thanks, 
I do try looking for relevant scripts but it's not easy to decipher and retain what I'm reading without actually using them in a practical or meaningful way. I'd like to learn more on nagios, netapp, kickstart, but I've no idea where to begin or any small scale projects I can take on to learn these without breaking stable or live systems.

---

### Post by Vaphell on 2013-08-08
set up a virtual machine, install test system in it, snapshot it so you have the option to rollback, tweak things to your heart's content.

---

### Post by Tlawrence on 2013-08-12
Building off this idea; I want to configure two vms, a server (Probably centos) and a client (probably fedora or ubuntu)
I'd like to set up apache, a simple file server, and a basic/static website (local to my own network). Then once I have that all set up digging into nagios.


Starting with apache, any good starting points?

---

