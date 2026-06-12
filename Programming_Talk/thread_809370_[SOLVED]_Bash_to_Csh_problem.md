---
title: "[SOLVED] Bash to Csh problem"
date: 2008-05-27
forum: Programming Talk
---

### Post by Gordiller on 2008-05-27
Hey guys, I'm having a problem in my internship...the MAN as asked me to translate this bash file into a sch file, this script should convert any specific man page into a pdf file..ok my problem is that this command "man 1 -t ls | ps2pdf -i -o ls.pdf", even in the shell, doesn't work...Can somebody help me..

---

### Post by WW on 2008-05-27
That is actually two commands, with the output of the first piped to the second.  If you run them individually, which one doesn't work?

Try:
```

$ man 1 -t ls > ls.ps

```
Does this create a Postscript version of the man page?  If so, try
```

ps2pdf ls.ps

```
If ls.ps was successfully created by the first command, this command should create ls.pdf. (After a quick look at the ps2pdf manpage and a little googling, I didn't find documentation of the -i and -o options; presumably -o is to specify the output file, but this seems unnecessary.)

EDIT: My Mac has the command **pstopdf**
```

$ pstopdf
Usage: pstopdf [inputfile] [-o outname] [-l] [-p] [-i]
Try: man pstopdf
$

```
It looks like your ps2pdf command is using the option style of the pstopdf command.  You should use something like this, instead:
```

man 1 -t ls | ps2pdf - ls.pdf

```

---

### Post by Gordiller on 2008-05-28
Thankx WW..that was a great help..indeed the -i and -o options were apart of the original code which use the pstopdf command.

---

