---
title: "installation error"
date: 2011-11-19
forum: New to Ubuntu
---

### Post by bob58523 on 2011-11-19
Greetings,

I am trying to install several different av programs but continue to get this error:

[I]Installing BitDefender Antivirus Scanner v7.6.4
dpkg: unrecoverable fatal error, aborting:
 syntax error: unknown user 'clamav' in statoverride file
Could not complete the installation of the package, aborting.[/I]

I get this when I try to re-install clamav with synaptic as well. I did have clamav installed on my system, but removed it using synaptic. I am running ubuntu 10.10 x64 with all the latest updates installed, and 4 gb of memory. Thanks in advance for any help that can be given.

Bob

---

### Post by roger_1960 on 2011-11-19
Hi

Go to terminal and try 
> sudo apt-get purge clamav
before reinstalling it (or other antivirus)

---

### Post by bob58523 on 2011-11-19
Hi....

I tried and got the reply that there was no clamav installed so nothing to remove.

BOb

---

### Post by roger_1960 on 2011-11-19
Hi again

Don't know the answer but the following link gives a start.  I suspect clamav has left itself in your statoverride file....

[http://www.wlug.org.nz/dpkg-statoverride%288%29](http://www.wlug.org.nz/dpkg-statoverride%288%29)

---

