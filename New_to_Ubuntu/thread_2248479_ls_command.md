---
title: "ls command"
date: 2014-10-15
forum: New to Ubuntu
---

### Post by ahmed16 on 2014-10-15
So in the ubuntu terminal i typed in "ls > list" but nothing shows up. Help me please.

---

### Post by kc1di on 2014-10-15
Hi ahmed16 and Welcome to Ubuntu, 

The command is ```
ls
``` not "ls>list"

[Here]("http://cli.learncodethehardway.org/bash_cheat_sheet.pdf") is a simple command cheat sheet for the most used commands.

---

### Post by Impavidus on 2014-10-15
**ls > list** will run the command **ls** and redirect all output that ls sends to the terminal to the file **list**. This means that no output appears in the terminal (except for error messages, if any) and that a file with the name "list" is created. Output redirects are explained in page 6 of the cheetsheet kc1di mentioned.

---

### Post by yancek on 2014-10-15
I'm not sure what you are trying to accomplish with the command but, in addition to what is posted above, the command as you have it will output a file named list in the directory from which it was run and include sub-directories/files in that directory.  You can also give a full path to include other directories.

---

