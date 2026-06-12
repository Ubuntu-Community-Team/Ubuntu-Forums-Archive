---
title: "Producing error logs"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by Tapas Pain on 2008-10-12
Hello.  I recall reading somewhere (but have forgotten where) that for pretty much any program in Ubuntu, when you run it, and if there is an error or problem, you can run that program command with a certain switch to produce an error log.  Can anyone tell me if a) I am remembering this correctly; b) what the command is to produce an error log for any given program; and c) where I can find that log once it is produced?  Also (and forgive my newbiness here) what terminal command can I use to type out / view what is in the error log?  Sorry if this has already been posted somewhere - I tried searching the forums but didn't have any luck finding this specific question.  Thanks.

---

### Post by EdThaSlayer on 2008-10-12
I'm not sure about the producing an error log thing(KDE program crashes of apps with K in front of them do that automatically though) but you can check what crashed that program by running it in the terminal. After the application crashes you can just check what happened on the terminal(it could have been a segmentation fault or one of the myriad crash reasons), paste the output on the forums, and maybe someone will be able to help you.

---

### Post by iponeverything on 2008-10-12
A lot of programs have a "debug" or "verbose" flag and can be started from  the command line find out what it is with "man <program>".With "debug" the information usually ends up in a log and with "verbose" it is usually printed out in the window where your started the command (STDOUT or Standard out).  Log files for ubuntu are under /var/log --  Where the debug information is printed depends on the program, but there are not that many logs, so the information is not hard to find. "ls -ltr" will print the listing of the directory is the order, where the most recently modified will be at the bottom. Also "tail <logfile>" will show you the last few lines of the log file.

You can use "less" to look at the log files ">" will take you to end of the file and "<" and the space bar will page through it.  The arrow keys will also work for line by line.

---

