---
title: "Zenity Bash Cript Issue"
date: 2008-02-27
forum: Programming Talk
---

### Post by regomodo on 2008-02-27
`

---

### Post by Mr. C. on 2008-02-27
Change your interpreter line to:

```
#!/bin/bash -e
```

MrC

---

### Post by Mr. C. on 2008-02-27
Sorry, I hit return too quickly...

This command doesn't make sense:

```
cat /dev/ttyUSB0 | tee > (zenity --progress --pulsate) >log.txt
```

You are redirecting BOTH into a subshell and into a file.  You can only setup one STDOUT redirection for a pipeline.  And tee already provides you with the redirection into both the FILE and STDOUT.  So, you want something like:

```
cat /dev/ttyUSB0 | tee log.txt | zenity --progress --pulsate
```

That is, dump the contents of the device to the pipeline, where tee reads it, dups the output to both STDOUT and to the file named log.txt, and its STDOUT is piped to zenity.

MrC

---

