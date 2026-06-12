---
title: "xhost works?"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by thull on 2008-11-01
I have a laptop running Ubuntu 7.10. When I'm home, I want to be able to edit files on the laptop using my desktop machines. I have two -- one running old Red Hat, the other recent Fedora -- where I just run:

  $ xhost +laptop
  $ telnet laptop
  $ emacs foo

And these work like they've always worked. I have another desktop (miles) running Ubuntu 7.10, and when I do those things, I get:

  Display miles:0.0 unavailable, simulating -nw

When I run xhost on miles, I get:

  access control disabled, clients can connect from any host
  INET:laptop

Which looks good to me. I never learned any of the other security methods with X because xhost always worked ok before.

The laptop also refuses to accept X connections. How is this configured under Ubuntu?

Note also that I haven't figured out how to get sshd to run under Ubuntu, although I did get telnetd running. Obvious tools like the System Services menu thingy don't cover these cases.

---

