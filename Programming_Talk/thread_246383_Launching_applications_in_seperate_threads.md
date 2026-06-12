---
title: "Launching applications in seperate threads"
date: 2006-08-29
forum: Programming Talk
---

### Post by rupy on 2006-08-29
Hi Guys,

It is possible to launch applications seperately, and indpendantly from the shell that you run them in.

EG: when I run something from shell it attaches that to the shell - if I close the shell the application closes as well, I want it to be entirely seperate.

---

### Post by Anonii on 2006-08-29
> **rupy said:**
> Hi Guys,

It is possible to launch applications seperately, and indpendantly from the shell that you run them in.

EG: when I run something from shell it attaches that to the shell - if I close the shell the application closes as well, I want it to be entirely seperate.

Ctrl + z, will bring the application to the background.
Then by using the command "bg" you can check which tasks are on the background, and by "fg" and the task number you will bring them back to the foreground and you will be able to use them.

But from what I remember you cant use the application while its on the background, but I think it will continue to run its task. For example a torrent client ,will continue downloading while in the bg, but you wont be able to change settings etc, till you bring it to the foreground. I dont know a method, unfortunately, to control the bg applications.

---

### Post by kwalo on 2006-08-29
> **rupy said:**
> EG: when I run something from shell it attaches that to the shell - if I close the shell the application closes as well, I want it to be entirely seperate.Have you tested nohup(1) ?

---

### Post by peabody on 2006-08-29
> **rupy said:**
> Hi Guys,

It is possible to launch applications seperately, and indpendantly from the shell that you run them in.

EG: when I run something from shell it attaches that to the shell - if I close the shell the application closes as well, I want it to be entirely seperate.

Yes, it's called daemonizing a process.  It involves forking once, closing stdin, stderr, and stdout, and forking again.  I think there's just a little bit more to it than that, but I'm sure google will get you a good example quickly if you type in "unix daemonizing examples".

---

### Post by rupy on 2006-08-29
The ctrl+z method doesnt really work, cos as soon as you do that it just moves "focus" off the process and freezes it - not to mention its still attached to the console.

nohup doesnt seem to do much - still attached to the console.

daemonizing a process sounds very complicated - there must be a simpler way to do it? How does the "run command" work under the kde menu?

---

### Post by csy on 2006-08-29
man screen

---

### Post by peabody on 2006-08-29
> **rupy said:**
> 
nohup doesnt seem to do much - still attached to the console.


did you try actually closing the console and checking?  nohup does catch the hangup signal effectively daemonizing a process.  I've used it countless times.

> 
daemonizing a process sounds very complicated - there must be a simpler way to do it? How does the "run command" work under the kde menu?

Since this is the programming forum I assumed you were interested in how to program it, but it sounds like you're simply intrested in how to do it from a user interface standpoint, in which case nohup is your friend.  It's always worked for me.  As for kde I really don't know, although anything you launch in KDE is essentially attached to the session I believe (it will die when you log out) so it may not do anything differently than how you're doing it from a terminal.

---

### Post by christhemonkey on 2006-08-29
You do know that if you run a command from a terminal,

and then suffix it with an &
it will run independant of the terminal?

e.g.:
```
nautilus & 
```

---

### Post by peabody on 2006-08-29
> **christhemonkey said:**
> You do know that if you run a command from a terminal,

and then suffix it with an &
it will run independant of the terminal?

e.g.:
```
nautilus & 
```

This doesn't run it independant of the terminal, it runs the process in the *background*.  Whether it stays up after closing the terminal depends on how the process handles hangups.

---

### Post by tomchuk on 2006-08-29
nohup nuatilus &

---

