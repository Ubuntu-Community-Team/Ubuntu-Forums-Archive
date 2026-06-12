---
title: "SIGKILL vs SIGINT"
date: 2012-09-30
forum: Programming Talk
---

### Post by IAMTubby on 2012-09-30
Hello,
I googled up a bit and I'm aware that SIGKILL is ungraceful termination(signal #9) whereas SIGINT is on pressing the Ctrl+c and is not killing, but only interruption.

But, what I find hard to understand is, even after doing a Ctrl+c, when I do a $ps, I don't see that process. Since it is only interrupted and not killed, shouldn't it still show up is the ps output.

I'm not able to figure out what SIGINT does.

Thanks.

---

### Post by Vaphell on 2012-09-30
depends on what the process does with that SIGINT, usually it means exit.

---

### Post by Majorix on 2012-09-30
It is the same as sending CTRL-C. Try it in the terminal.

---

### Post by trent.josephsen on 2012-09-30
SIGINT can be caught and handled. It's like telling the process "Please stop what you're doing." The process is free to ignore the signal, or implement a handler that does anything it wants. The default behavior is to terminate, and this is what most processes will do. It's typical, but not required, for a process to handle SIGINT by gracefully terminating -- closing any open files, network connections, or database handles and stopping the current operation in such a way that prevents data loss or corruption.

SIGKILL can't be handled by the receiving process. If a process gets sent SIGKILL, it's toast, period. If a process receives SIGKILL in the middle of a database transaction or file write (for instance), it has no chance to exit gracefully and data loss or corruption may occur.

When you do Ctrl-C in the terminal, the terminal sends SIGINT to the running process. Like I said before, most processes will gracefully terminate on receiving SIGINT. Once it's terminated, it's just as surely ended as if it had been SIGKILL'ed or exited normally -- you shouldn't expect to see it in ps because it's still gone.

But there are some programs that don't respond to SIGINT in that way. bash is one example; if you hit Ctrl-C at a shell prompt, it'll just cancel whatever you've typed on that line -- not terminate the whole shell. Again, this is because the behavior when a process receives SIGINT is determined by the process itself. vi is another program that doesn't handle SIGINT by terminating.

---

### Post by Lars Noodén on 2012-09-30
[SIGINT and others](http://manpages.ubuntu.com/manpages/precise/en/man7/signal.7.html) can be caught and handled.  You can try running the perl script below in one terminal and in another sending various signals to it using kill or pkill.  Or in the same terminal you could press ctrl-C to send SIGINT.

```

#!/usr/bin/perl

use sigtrap qw(die QUIT);

sub trap_int {
 print qq(Ouch\n);
 exit ( 0 );
}

sub trap_hup {
 print qq(Hang up\n);
}

$SIG{INT} = \&trap_int;
$SIG{HUP} = \&trap_hup;

while (1) {
  print qq(Doing something for 500 seconds\n);
  sleep( 500 );
  print qq(Continuing\n);
}

```

Some programs will, for example, reload the configuration file when receiving a SIGHUP.  But what the program actually does upon receiving a signal is up to the designer.

---

