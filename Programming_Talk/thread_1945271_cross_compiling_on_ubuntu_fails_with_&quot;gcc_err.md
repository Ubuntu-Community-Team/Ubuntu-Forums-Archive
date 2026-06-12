---
title: "cross compiling on ubuntu fails with &quot;gcc: error trying to exec 'cc1':&quot;"
date: 2012-03-22
forum: Programming Talk
---

### Post by jpoc on 2012-03-22
I am trying to cross compile for an embedded linux platform.

I am running on ubuntu and I am using a gcc based toolchain that was supplied by the folks who manufacture the platform.

They have given me a total of five toolchains and four work just fine. I have been able to build code and ship libraries back and I have been told that these are working OK.

For the last toolchain, I get the following error when I try to run make:

gcc: error trying to exec 'cc1': execvp: No such file or directory

There is a cc1 in the toolchain of similar size to the cc1 in the other toolchains and all of the permissions and access modes look OK.

The folks who supplied the toolchain say that it works for them so I expect that it may be some install or config issue.

Any ideas?

---

### Post by jpoc on 2012-03-22
I found out a little bit more. If I add '-v' to the compiler flags I get gcc to give verbose info about exactly what commands it is executing.

On one of the toolchains that works, I see that the command run by gcc is something like:

/opt/<path to gcc>/../<relative path to cc1>cc1

On the toolchain that fails, all that is specified is:

cc1

No where does that path come from. When it is running, gcc of course knows that path to itself but where does that relative part come from. It is certainly not specified in any of my makefiles. Is it hard coded inside the gcc executable?

I guess that I could work around this by adding the location of cc1 to the path. That might be acceptable if I was only trying to build one target but on a build server that is supposed to be building a hundred targets, that is just not on.

---

