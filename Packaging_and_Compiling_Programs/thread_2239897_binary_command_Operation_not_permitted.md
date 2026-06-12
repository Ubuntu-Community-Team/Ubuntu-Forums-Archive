---
title: "binary command: Operation not permitted"
date: 2014-08-16
forum: Packaging and Compiling Programs
---

### Post by jgilfn on 2014-08-16
Greetings,
When I compile a bash script with the SHC command, then I copy it to the /usr/bin folder and then when I try to execute it in terminal it displays me this error:
(command): Operation not permitted

Is it a permission problem?
What should I do?

Thank you in advance...

---

### Post by sisco311 on 2014-08-16
When you create the binary with shc, you have to use the -T option to allow it to be traceable. 

See: [https://wiki.ubuntu.com/SecurityTeam/Roadmap/KernelHardening#ptrace_Protection](https://wiki.ubuntu.com/SecurityTeam/Roadmap/KernelHardening#ptrace_Protection)

---

