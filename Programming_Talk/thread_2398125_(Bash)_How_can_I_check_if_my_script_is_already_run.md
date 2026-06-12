---
title: "(Bash) How can I check if my script is already running in another instance?"
date: 2018-08-07
forum: Programming Talk
---

### Post by Paddy Landau on 2018-08-07
I have a Bash script that must never run two instances at the same time. Therefore, I need to check at the start whether or not it's already running, and if so, terminate.

I was experimenting with using pgrep as follows.
```
if (( $( pgrep --count --full "${0}" ) > 1 )); then exit; fi
```
Unfortunately, this doesn't work. After plenty of bafflement and investigation, I found that when only one instance of the script is running, bizarrely the [FONT=lucida console]pgrep[/FONT] command sometimes returns 1 and sometimes 2. I don't know why, but suspect that it's because sometimes it catches its own request and sometimes not.

I have also tried to use [FONT=lucida console]pidof[/FONT], but regardless of what I do, [FONT=lucida console]pidof[/FONT] always returns status code 1. It's like it just doesn't work on my system.

I am at a loss as to how to proceed. How can I reliably check if the script is already running?

---

### Post by TheFu on 2018-08-08
Lock files and semaphores are the normal solution to this. You'll want to catch any signals that could break the running script so you can have a cleanup routine remove a lock file or any semaphores.  [http://www.csc.villanova.edu/~mdamian/threads/posixsem.html](http://www.csc.villanova.edu/~mdamian/threads/posixsem.html)
Lock files are easier.

---

### Post by edadasiewicz on 2018-08-08
I would consider using a lock file.  Check out the flock command which manages locks from shell scripts.

---

### Post by Paddy Landau on 2018-08-08
Thank you. The semaphores look interesting, but I'm not a C programmer (I use only Bash). I'll take a good look at the flock command.

---

### Post by Paddy Landau on 2018-08-08
The end of the flock manual shows how to do this, but it's unclear, and it doesn't explain how to block (instead of queue) a duplicate run.

I managed to figure it out, and it works, so that's done now.

Thanks for the heads-up.

---

