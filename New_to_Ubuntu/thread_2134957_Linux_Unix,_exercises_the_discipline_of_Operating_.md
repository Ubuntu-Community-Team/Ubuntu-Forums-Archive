---
title: "Linux Unix, exercises the discipline of Operating Systems. part 2"
date: 2013-04-12
forum: New to Ubuntu
---

### Post by Quesado on 2013-04-12
Greetings all.
I'm completely newbie when it comes to programming with Ubuntu, I study electrical engineering and computer and got a chair this semester called OS, where we were asked to hand over the following exercise until April 22.
The exercise is as follows:


2nd. Write a C program emulates That The Following shell command line:
"Ls -1 | sort-r> output.txt; less output.txt".
Should the program include the use of the ls, sort, and less commands, and the Implementation
of the pipeline and the output redirection. The ";" character separates commands (or pipelines) That
are executed in sequence. Thus, in this problem the "less output.txt" command is executed after
the "ls -1 | sort-r> output.txt" pipeline has terminated. To Implement the pipeline part, your
Should program use two processes, create a pipe between Them, redirecting the stdout of the first process
to the input of the pipe and the stdin of the second process from the output of the pipe (Investigate
the dup () and dup2 () system calls). Do not forget to close the file descriptors extra, such That the
processes of the pipeline start with exactly three open file descriptors, as expected. You Should Also
Appropriately Implement the output redirection of the sort command, and run all the commands ls,
sort, and less in combination, the above specified in the command line. You may also need the wait ()
or the waitpid () system calls (see man 2 wait). It is not permitted to employ the system () function
to Implement the program to solve this question.


I do not understand any of this, zero! Any help or tip that I can provide will be very grateful


respects

[COLOR=#000000]PS: I Portuguese so please forgive my bad English[/COLOR]

---

### Post by oldos2er on 2013-04-12
From the Code of Conduct: 

While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.

Closed.

---

