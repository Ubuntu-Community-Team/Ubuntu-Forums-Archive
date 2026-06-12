---
title: "Process Running in Terminal"
date: 2012-11-22
forum: New to Ubuntu
---

### Post by Polydorus on 2012-11-22
I'm using dialup with Ubuntu 12.04 (64 bit) and occasionally will get the following message when trying to close my internet connection with Ctrl-C:  "There is a process running in this terminal.  Closing the terminal will kill it."  Is there a way to get the terminal to tell me what process is running?

TIA

---

### Post by Lars Noodén on 2012-11-22
You could try running [jobs](http://manpages.ubuntu.com/manpages/precise/en/man1/jobs.1posix.html) which will list the jobs running.

---

### Post by coldcritter64 on 2012-11-22
With the terminal still open, open system-monitor (from Dash). 
In the system monitor's view menu, click "dependencies" on. In my case I also show the system processes as well. 

In the attached screenshot you can see that I've used the terminal to launch gnome-system-monitor. You could use the same process to see what is holding the terminal open.

I also seem to have another terminal open somewhere :), ignore the second bash entry under the terminal.

---

### Post by Polydorus on 2012-11-23
> **Lars Noodén said:**
> You could try running [jobs]("http://manpages.ubuntu.com/manpages/precise/en/man1/jobs.1posix.html") which will list the jobs running.

Thanks for the reply.  I'm not sure if I did it right but typing " jobs " at the terminal prompt just results in a new prompt.  Changing to " jobs -l " gets the same non-result.

---

### Post by Polydorus on 2012-11-23
> **coldcritter64 said:**
> In the system monitor's view menu, click "dependencies" on. In my case I also show the system processes as well. 

That is what I'm seeing also.  So far the problem hasn't repeated so I don't have an answer to my question but it looks this will provide part of the answer.  Thank you very much.

---

