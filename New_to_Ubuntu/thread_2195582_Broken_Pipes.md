---
title: "Broken Pipes?"
date: 2013-12-25
forum: New to Ubuntu
---

### Post by jtmcgraw2-44-8 on 2013-12-25
Upon shutdown or reboot I get a message that says "could not write bytes: Broken pipes." I've not the faintest clue as to what this means, and whether or not I should be concerned. Is this a problem? If so, what does it mean and how may I resolve it?

---

### Post by Impavidus on 2013-12-25
A [pipe](http://en.wikipedia.org/wiki/Pipe_%28Unix%29) is a way to send data from one process to another. When the reading process terminates or simply closes the pipe, the pipe is broken and the writing process has to handle this, usually (and by default) by terminating. Often processes are designed to terminate with a broken pipe, the tool **yes** is rarely terminated in any other way than with a broken pipe. If everything works fine, there's no reason to be concerned.

---

