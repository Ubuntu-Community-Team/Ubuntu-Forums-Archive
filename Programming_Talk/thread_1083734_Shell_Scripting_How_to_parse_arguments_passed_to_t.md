---
title: "Shell Scripting: How to parse arguments passed to the script"
date: 2009-03-01
forum: Programming Talk
---

### Post by jucas_lo on 2009-03-01
Hi!

I'm new to bash scripts, and I wanted to know how to parse arguments in a script, in the same way as the command line tools in linux do.

For example when you use find, and you wanna find files with a particular name, then you do "find -name *somename*".

I was wondering if there is a standard way to do that on a bash script, or if you just parse the arguments manually....

Also i would like to have long and short forms for my scripts options (such as -h or --help for a help option)

I'd appreciate any help or comment from you guys!

thank you very much!!!!

:guitar:

---

### Post by dwhitney67 on 2009-03-01
Use getopt.

Reference the man-page for more details.

---

### Post by jimi_hendrix on 2009-03-01
> **dwhitney67 said:**
> use getopt.

Reference the man-page for more details.

+1

---

### Post by jucas_lo on 2009-03-01
Thanks guys that was exactly what I was looking for.

---

