---
title: "Unix IPC: Signals"
date: 2007-09-18
forum: Programming Talk
---

### Post by Rij on 2007-09-18
I am a little stuck with IPC using signals. The idea is to make serialize the startup execution of a process "network" followed by N processes named "node". 

So, in my "network", I have the following:
kill(0, SIGUSR1); 

In the "nodes", I am waiting for the SIGUSR1 signal. So the code is like this:
void sig_handler(int signo) {
if (signo == SIGUSR1) usr_interrupt = 1;
return;
}

volatile sig_atomic_t usr_interrupt;
int main(....) {
...

if (signal(SIGUSR1, sig_handler) == SIG_ERR) // print err msg
sigset_t mask, oldmask;
sigemptyset(&mask);
sigaddset(&mask, SIGUSR1);
sigprocmask(SIG_BLOCK, &mask, &oldmask);
while (!usr_interrupt) sigsuspend(&oldmask);
usr_interrupt = 0;
sigprocmask(SIG_UNBLOCK, &mask, NULL);

cout << ID << " will proceed\n";

---------------------------------------
I have 5 "node" and 1 "network" processes running.
Whats happening is that only one process (one corresponding to node 0) handles the signal. All the other processes are forever waiting for the signal and is not receiving it. I thought since I sent kill with 0 as the 1st argument, all processes in the same group should get notified. What's wrong?

Also, I am ignoring SIGUSR1 in all other processes.

---

### Post by Arndt on 2007-09-19
> **Rij said:**
> I am a little stuck with IPC using signals. The idea is to make serialize the startup execution of a process "network" followed by N processes named "node". 

So, in my "network", I have the following:
kill(0, SIGUSR1); 

In the "nodes", I am waiting for the SIGUSR1 signal. So the code is like this:
void sig_handler(int signo) {
if (signo == SIGUSR1) usr_interrupt = 1;
return;
}

volatile sig_atomic_t usr_interrupt;
int main(....) {
...

if (signal(SIGUSR1, sig_handler) == SIG_ERR) // print err msg
sigset_t mask, oldmask;
sigemptyset(&mask);
sigaddset(&mask, SIGUSR1);
sigprocmask(SIG_BLOCK, &mask, &oldmask);
while (!usr_interrupt) sigsuspend(&oldmask);
usr_interrupt = 0;
sigprocmask(SIG_UNBLOCK, &mask, NULL);

cout << ID << " will proceed\n";

---------------------------------------
I have 5 "node" and 1 "network" processes running.
Whats happening is that only one process (one corresponding to node 0) handles the signal. All the other processes are forever waiting for the signal and is not receiving it. I thought since I sent kill with 0 as the 1st argument, all processes in the same group should get notified. What's wrong?

Also, I am ignoring SIGUSR1 in all other processes.

I tried to reproduce your scenario, with somewhat different code (and in C, but that should hardly matter). It works for me. My "network" process does a setpgrp() before spawning the "node" processes, and it also does a signal(SIGUSR1, SIG_IGN) itself. Before I did the latter, it showed behaviour similar to yours, because it killed itself before more than one "node" had time to react.
I don't know if this helps.

---

