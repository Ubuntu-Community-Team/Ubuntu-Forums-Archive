---
title: "Parallel Processing"
date: 2018-01-25
forum: Programming Talk
---

### Post by jacob-edward on 2018-01-25
Already found this thread:

[https://ubuntuforums.org/showthread.php?t=542442](https://ubuntuforums.org/showthread.php?t=542442)

and the first response has this:
[SIZE=1]
[COLOR=#ff0000]"dividing the work to parallelize cannot be done automatically, even in functional languages (you have to tell the compiler/interpreter what can be parallel)."[/COLOR][/SIZE][COLOR=#000000]

is exactly what I want to do, tell the compiler/interpreter what specifically is to be parallel processed...  I have no idea how to do that lol, here's my post on stack overflow:

[/COLOR][https://superuser.com/questions/1288743/assign-specific-cpus-specific-parallel-processes-on-larger-google-compute-engin](https://superuser.com/questions/1288743/assign-specific-cpus-specific-parallel-processes-on-larger-google-compute-engin)

but nobody has responded...  anybody know how to do this???  I don't want the parallel processing to be sandboxed from each other, the different processes will need to interact with each other regularly... Kubernetes, if I understand the concept correctly, is about sandboxing (containerizing) different processes so that they cannot interfere with each other for security concerns, it's suppose to be the more efficient version of sandboxing VM's (aka I don't have to worry about other people and their VM's infecting my VM)...  The only alternative I can think of is initializing several smaller VM's with only a single CPU that then interact with each other via a REST API but that would be inefficient for my particular project given the amount of RAM needed for the neural network is just a little less than the most RAM available from the largest High-memory machine type... I know the Intel chips are suppose to have optimization features but there are very specific sections that I could explicitly assign for parallel processing... anybody have a link?

I'm assuming there's a shell command???

---

### Post by QIII on 2018-01-25
Moved to Programming Talk

---

### Post by jacob-edward on 2018-01-26
> **QIII said:**
> Moved to Programming Talk

Thank you.  Just started learning the forums.

---

### Post by jacob-edward on 2018-01-26
[https://www.cyberciti.biz/faq/how-to-run-command-or-code-in-parallel-in-bash-shell-under-linux-or-unix/The](https://www.cyberciti.biz/faq/how-to-run-command-or-code-in-parallel-in-bash-shell-under-linux-or-unix/The) syntax is:command &command arg1 arg2 &custom_function &ORprog1 &prog2 &waitprog3In above code sample, prog1, and prog2 would be started in the background, and the shell would wait until those are completed before starting the next program named progr3. To displays status of jobs in the current shell session run jobs command as follows:$ jobs

---

### Post by jacob-edward on 2018-01-26
[https://www.cyberciti.biz/faq/how-to-run-command-or-code-in-parallel-in-bash-shell-under-linux-or-unix/](https://www.cyberciti.biz/faq/how-to-run-command-or-code-in-parallel-in-bash-shell-under-linux-or-unix/)
[FONT=arial]
[/FONT]
[FONT=arial][COLOR=#212529][FONT=Montserrat]The syntax is:[/FONT][/COLOR]
command &
command arg1 arg2 &
custom_function &
[COLOR=#212529][FONT=Montserrat]OR[/FONT][/COLOR]
prog1 &
prog2 &
wait
prog3
[COLOR=#212529][FONT=Montserrat]In above code sample, prog1, and prog2 would be started in the background, and the shell would wait until those are completed before starting the next program named progr3.[/FONT][/COLOR] 
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][COLOR=#212529][FONT=Montserrat]To displays status of jobs in the current shell session run [/FONT][/COLOR][jobs command]("https://www.cyberciti.biz/faq/unix-linux-jobs-command-examples-usage-syntax/")[COLOR=#212529][FONT=Montserrat] as follows:[/FONT][/COLOR]
$ jobs[/FONT]

---

### Post by jacob-edward on 2018-01-26
[http://www.acuriousanimal.com/2017/08/12/understanding-the-nodejs-cluster-module.html](http://www.acuriousanimal.com/2017/08/12/understanding-the-nodejs-cluster-module.html)

---

