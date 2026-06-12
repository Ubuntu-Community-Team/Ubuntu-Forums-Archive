---
title: "Include Bash in Gambas"
date: 2010-02-02
forum: Programming Talk
---

### Post by Chamillionaire2 on 2010-02-02
What's Up?

OK, So I'm trying to make a executable file using gambas, But I'm completely new to VB and gambas, Is it possible to include some bash script in the project?

Probably rather simple, I'm just too much of an idiot to figure it out myself. :-(

Thanks Bye.

** I found how to include a bash file into your script, But can't find out how to actully put the commands into your script.

---

### Post by saulgoode on 2010-02-02
You would use either the SHELL command or the EXEC command. SHELL will process a string as though it were typed on the command line (expanding all the wildcards and applying I/O redirection), while EXEC calls the program directly and does not provide any of the niceties of the shell (but is much faster).

examples:
```
SHELL "ls *.og? >oggfiles.txt"

EXEC ["/usr/bin/ls", "asinglefile.ext", "anotherfile.ext"]

```

---

### Post by Flimm on 2010-02-02
You can make an executable of your project by clicking Project, Make, Executable. It will compile to a .gambas file which requires gambas2-runtime to execute. You can also make a Debian package for your project which is what I would recommend for distribution.

I'm not sure what you mean by bash commands, but you can run commands in the code of your project the way saulgoode explained.

---

