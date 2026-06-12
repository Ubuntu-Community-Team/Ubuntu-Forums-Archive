---
title: "C++ Function to get a list of running processes with pid's"
date: 2007-07-27
forum: Programming Talk
---

### Post by Sh4wn on 2007-07-27
Hi, :)

Is there any function to get a list of running processes with their pid's in C++? I've searched a lot, but the only thing I found was the ps command.

So does anyone if there exists such function? Thanks in advance. :)

---

### Post by noof on 2007-07-27
An ugly way to do it is to read the files under /proc/<pid>/ :) Not very portable I guess, but if you abstract it a class you can hide the ugliness :P

---

### Post by Sh4wn on 2007-07-27
Hmm yes, but I want to check if a process is runinng bij iets executable name, and then get the pid. I couldn't find the executable in one of the files.. 

Thanks for the reply though. :)

---

### Post by the_unforgiven on 2007-07-27
> **Sh4wn said:**
> Hmm yes, but I want to check if a process is runinng bij iets executable name, and then get the pid. I couldn't find the executable in one of the files.. 

Thanks for the reply though. :)
/proc/<pid>/cmdline gives the command line - how the process with PID <pid> was started.
Also /proc/<pid>/exe is a symlink to the binary running as <pid>.
Does that help?

---

### Post by Sh4wn on 2007-07-27
Ah thanks a lot, that helps indeed! :)

---

