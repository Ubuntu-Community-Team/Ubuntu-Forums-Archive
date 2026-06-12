---
title: "close a process (graciously) at specific time - shutdown computer [via command line]"
date: 2010-11-04
forum: Programming Talk
---

### Post by Claus7 on 2010-11-04
Hello,

the title says it all:

I want to close an application from command line at a specific time. Then also be able to close the computer safely.

For example I have opera browser open.
> wmctrl -l   ---> check all open windows of processes running
wmctrl -c *string_name_of_the_process*  ---> closes the window of the process graciously (not abruptly)

> at now +1 minute ---> executes a command after one minute (the command is given as input in the command prompt shown and after that pressing ctrl+d)

> at -l ---> lists all the processes that are scheduled using this command 
atrm *number_of_process* --> deletes a scheduled process 

> shutdown +50  ---> shuts down the computer after 50 minutes

What I want to do is:
> (open a terminal)
1) type there a command to close opera after e.g. 20 minutes and
2) in that terminal to type to shutdown the computer after 50 minutes.

the at command piped with the wmctrl command does not do the trick. Any thoughts are most welcome.

Regards!

---

