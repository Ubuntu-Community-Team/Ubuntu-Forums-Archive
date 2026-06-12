---
title: "Killing child process kills parent"
date: 2011-05-17
forum: Programming Talk
---

### Post by johnelayn on 2011-05-17
[COLOR=black][FONT=Verdana]I have a Bourne shell script that was created in Fedora and it worked fine. At a few times during the script a child process is spawned, after I get the info I need from the child process, the I manually kill the child process via a ^c and the parent script keeps running.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Now I'm running the same script using ubuntu and when I kill the child process, the parent process dies also. How do I fix this? [/FONT][/COLOR]

---

### Post by cgroza on 2011-05-17
Why don't you use a killall or similar command to kill that process? Maybe the shell in Ubuntu handles the interrupt differently.

---

### Post by Blackbug on 2011-05-18
well, yes until for some own reasons you need to do this manually then its a different case. Otherwise best way will be to use killall, kill, pkill on to the specific process.

---

### Post by slavik on 2011-05-18
^C doesn't kill the child ...

When you send that interrupt to the terminal, it is sent to the main parent process. The main parent process in that terminal is usually the shell. The parent then sends the process to it's child (and so on recursively). So in essence, you are killing the parent and the signal cascades down to the child.

In order to change this, you need to handle the signal (default action for SIGINT is to die). Make it do something else and your process will die in a way you want (or not die at all).

Fun things can be had when you make a process not die on SIGINT.

---

### Post by Arndt on 2011-05-18
> **slavik said:**
> ^C doesn't kill the child ...

When you send that interrupt to the terminal, it is sent to the main parent process. The main parent process in that terminal is usually the shell. The parent then sends the process to it's child (and so on recursively). So in essence, you are killing the parent and the signal cascades down to the child.

In order to change this, you need to handle the signal (default action for SIGINT is to die). Make it do something else and your process will die in a way you want (or not die at all).

Fun things can be had when you make a process not die on SIGINT.

The manual page for 'setpgrp' says this:

"      A  session can have a controlling terminal.  At any time, one (and only
       one) of the process groups in the session can be the foreground process
       group  for  the terminal; the remaining process groups are in the back&#8208;
       ground.  If a signal is generated from the terminal (e.g.,  typing  the
       interrupt  key  to  generate  SIGINT), that signal is sent to the fore&#8208;
       ground process group."

This seems to indicate that the group of processes, not only its leader, receives the signal. Am I wrong?

---

### Post by psusi on 2011-05-18
Indeed, the SIGTERM goes to the entire foreground process group, so if you tell bash:

tail -f /var/log/messages

And then hit ctrl-C, then tail gets the signal, not bash.  If you do:

tail -f /var/log/messages | grep foo

Then both tail and grep get the signal.

---

### Post by slavik on 2011-05-19
> **psusi said:**
> Indeed, the SIGTERM goes to the entire foreground process group, so if you tell bash:

tail -f /var/log/messages

And then hit ctrl-C, then tail gets the signal, not bash.  If you do:

tail -f /var/log/messages | grep foo

Then both tail and grep get the signal.
bash gets the signal, too. except it will ignore it and pass it down.

all signals except SIGKILL can be ignored by processes.

---

### Post by johnl on 2011-05-19
> **slavik said:**
> bash gets the signal, too. except it will ignore it and pass it down.


I don't think that's true.  Only the process group that controls the terminal (via tcsetpgrp) will get the interrupt.

Normally in a shell you will initialize like so:

```

/* ignore C-c, C-z, etc */
signal(SIGINT, SIG_IGN);
signal(SIGQUIT, SIG_IGN);
signal(SIGTSTP, SIG_IGN);
signal(SIGTTIN, SIG_IGN);
signal(SIGTTOU, SIG_IGN);
   
/* make this processes group the controlling process group */
pid_t self = getpid();
setpgid(self, self);
tcsetpgrp(STDIN_FILENO, self);

```

So that we ignore SIGINT, SIGSTOP, etc.  Then when we execute a new job, for example 'ls | tail', we would:

* fork.
* reset signal handlers to SIG_DFL
* put process in a new process group as the group leader.
* exec ls

and then similarly for tail:

* fork
* reset signal handlers
* put process into the pgroup headed by 'ls'
* exec tail

and then finally, put the newly created process group into the foreground:

```

tcsetpgrp(STDIN_FILENO, pgid_of_ls);

```

So the new process group controls the terminal and will receive the signals.  The parent just reacts to the result of a waitpid() to see if a process is stopped or finished.

---

### Post by psusi on 2011-05-19
> **slavik said:**
> bash gets the signal, too. except it will ignore it and pass it down.

The quoted man page says otherwise.

> **slavik said:**
> all signals except SIGKILL can be ignored by processes.

And SIGSTOP.

---

