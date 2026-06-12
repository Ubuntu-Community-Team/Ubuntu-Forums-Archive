---
title: "popen - Read _and_ write?"
date: 2008-07-30
forum: Programming Talk
---

### Post by HyperHacker on 2008-07-30
I've been using [popen()](http://www.opengroup.org/onlinepubs/007908799/xsh/popen.html) to control mplayer in slave mode from my program (in C++). However I need to get a reply back (from the get_property command), and popen() only lets you specify read *or* write. The reply just gets printed to stdout. How do I open another pipe to get the reply back?

---

### Post by dribeas on 2008-07-31
> **HyperHacker said:**
> I've been using [popen()](http://www.opengroup.org/onlinepubs/007908799/xsh/popen.html) to control mplayer in slave mode from my program (in C++). However I need to get a reply back (from the get_property command), and popen() only lets you specify read *or* write. The reply just gets printed to stdout. How do I open another pipe to get the reply back?

Create two unamed pipe, then fork. On the child process use dup2 to map stdin and stdout from and to the pipes and then exec mplayer.

The parent process can use the other ends of the pipes to talk to/receive from mplayer.

David

---

