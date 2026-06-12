---
title: "request scripts in Solaris"
date: 2009-01-30
forum: Programming Talk
---

### Post by zpzpzp on 2009-01-30
Hi

Are there any good resources online where I can learn about the "request script" that they are talking about on this page:
[http://www.unix.com/unix-advanced-expert-users/59181-using-request-script.html](http://www.unix.com/unix-advanced-expert-users/59181-using-request-script.html)

I am new to unix, and do not even know what language this script is written in...

I would very much appreciate any info/resources on request scripts and how to understand/write them.

Paul

---

### Post by escapee on 2009-01-30
What exactly do you want your script to request?  This one seems specific to something.

It's a shell script.

---

### Post by dwhitney67 on 2009-01-30
Here's one [resource]("http://www.ibiblio.org/pub/packages/solaris/sparc/html/creating.solaris.packages.html") I found by Googling.

It's been over 5 years since I worked on something similar, so I may or may not be able to help you further.  If you do not know how to write scripts, then I suggest you learn the basics.

A Solaris package typically contains scripts, though they are not required.  Here's a list of some scripts that one may consider adding to a package:
[LIST]
[*]preinstall
[*]preremove
[*]postinstall
[*]postremove
[*]checkinstall
[*]request
[/LIST]

Unless you like typing command line statements over and over again (until you get the package right), consider also developing a script that handles the steps necessary to create the package itself.

---

### Post by zpzpzp on 2009-01-31
Thank you Escapee and dwhitney67!

Both of your answers were very helpful and I have been learning shell scripts!

Paul

---

