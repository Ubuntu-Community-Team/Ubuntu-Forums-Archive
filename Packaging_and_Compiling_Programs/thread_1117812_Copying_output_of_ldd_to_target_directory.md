---
title: "Copying output of ldd to target directory"
date: 2009-04-06
forum: Packaging and Compiling Programs
---

### Post by FrankL on 2009-04-06
Dear all,

I am not sure whether this is the right subforum, excuse me if I am incorrect.

The problem I have is the following. I try to run a program, which I copied from another computer, in a chroot environment. The chroot-environment however needs quite some libraries to be able to run the program. Because of that, I would like to fill /usr/lib, /lib, etc. with the appropriate libraries, without having to copy all libraries in these directories from the computer the program was originally installed on. You might wonder why I don't just recompile the program and all its dependencies: I don't have the rights to do so, I scarcely got the rights to setup my own chroot environment.

Now, I know how to find the libraries the program needs by using ldd. So, the next step is to copy all of these to the appropriate place in my chroot environment. But how can I do this in a simple way, without moving each one by hand? Can I pipe the output of ldd to something useful or is there any other way?

Hopefully the question is clear and someone can help. Thanks a lot in advance,

       kind regards,

                 Frank

---

