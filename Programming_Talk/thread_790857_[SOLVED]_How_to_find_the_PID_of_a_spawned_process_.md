---
title: "[SOLVED] How to find the PID of a spawned process in perl?"
date: 2008-05-11
forum: Programming Talk
---

### Post by unutbu on 2008-05-11
I want to spawn a child process in perl, and be able to use the child's PID in the parent process while the child is running.

For the sake of programming integrity I do not want to process `ps auxw` output and find the PID that way. (What happens if there is more than one process with a similar name?) It just feels ugly.

I can do it in bash, so I am shocked I can not do it better in perl:

play-xevil.sh
```
#!/bin/bash

xevil -cb &
PID=$!
TOGGLE='Pause';
REPLY='';
while  [ "$REPLY" != "q" ]; do
    read -p "$TOGGLE or Quit (<RET>/q) ";
    if [ "$REPLY" = "q" ]; then
	kill -9 $PID;
	break;
    else
	if [ "$TOGGLE" = "Pause" ]; then
	    TOGGLE='Resume';
	    kill -s STOP $PID;
	else
	    TOGGLE='Pause';
	    kill -s CONT $PID;
	fi
    fi

done
exit
```

This is my attempt to do the same thing in perl. It does not work because $pid refers to the child perl process "play-xevil.pl" -- it does not refer to the "xevil -cb" process that the child spawns. I understand the problem, but I don't know how to solve it.

play-xevil.pl:
```
#!/usr/bin/perl
use strict;
use warnings;

my $pid = fork();
if (not defined $pid) {
    warn "resources not avilable.\n";
} elsif ($pid == 0) {
    print "I'M THE CHILD\n";
    open(XEVIL, "xevil -cb |");
    
    close(XEVIL);
#    system("xevil -cb");
    exit(0);
} else {
    print "I'M THE PARENT, PID=$pid\n";
    my $toggle='Pause';
    while (1) {
	my $cmd="$toggle or Quit (<RET>/q)";
	print "$cmd ";
	my $resp=<STDIN>; chomp($resp);
	$resp='q' if ($resp=~m/^\s*$/);
	if ($resp=~m/^q/i) {
	    system("kill -9 $pid");
	    last;
	} elsif ($toggle eq 'Pause') {
	    $toggle='Resume';
	    system("kill -s STOP $pid");	
	} else {
	    $toggle='Pause';
	    system("kill -s CONT $pid");	
	}
    }
    waitpid($pid,0);
}

```

---

### Post by unutbu on 2008-05-11
This perl script seems to work but I don't understand why I have to add 1 to $pid to get the right process. I'm not even sure if this method is reliable if the machine had more processes being created at the same time.

```
#!/usr/bin/perl
use strict;
use warnings;

my $pid=open(XEVIL,"xevil -cb 2>/dev/null & |");
$pid++;
my $toggle='Pause';
my $resp='y';
while (!($resp=~m/^q/i)) {
    my $cmd="$toggle or Quit (<RET>/q)";
    print "$cmd ";
    my $resp=<STDIN>; chomp($resp);
    $resp='y' if ($resp=~m/^\s*$/);
    if ($resp=~m/^q/i) {
	system("kill -9 $pid");
	last;
    } elsif ($toggle eq 'Pause') {
	$toggle='Resume';
	warn "kill -s STOP $pid";
	system("kill -s STOP $pid");	
    } else {
	$toggle='Pause';
	system("kill -s CONT $pid");	
    }
}
close(XEVIL);

```

---

### Post by ghostdog74 on 2008-05-11
you don't have to execute a system call to kill. Perl has its own kill.
See perldoc -f kill. Also of interest would be perlipc.

---

### Post by unutbu on 2008-05-11
Thanks ghostdog74 for the heads-up on perl's kill function, and perlipc. 

Now that I have a working script, I'm particularly puzzled why adding 1 to $pid was necessary to get it to work. Any ideas why that that might be?

---

### Post by slavik on 2008-05-12
if using system(), you will not be able to get the pid of the process you are calling inside it, what you are wanting to do is the basic shell process (use exec isntead of system())

the reason why adding 1 to the pid of the process that calls system() is simply you 'being lucky' that the kernel assigns a pid of parent+1 to the child process.

pseudo code for the basic shell process
```
switch (fork_ret = fork()) {
 case -1: //can't fork;
 case 0: //child, do an exec call
 case default: //parent, fork_ret is the child's pid
}
```

---

### Post by unutbu on 2008-05-12
Thanks ghostdog74 and slavik, with your help I've found a solution:

```
#!/usr/bin/perl
use strict;
use warnings;

my $pid = fork();
if (not defined $pid) {
    warn "resources not avilable.\n";
} elsif ($pid == 0) {
    warn "I'M THE CHILD\n";
    exec("xevil -cb");
    exit(0);
} else {
    warn "I'M THE PARENT, PID=$pid\n";
    my $toggle='Pause';
    while (1) {
	my $cmd="$toggle or Quit (<RET>/q)";
	print "$cmd ";
	my $resp=<STDIN>; chomp($resp);
	$resp='y' if ($resp=~m/^\s*$/);
	if ($resp=~m/^q/i) {
	    kill 9, $pid;
	    last;
	} elsif ($toggle eq 'Pause') {
	    $toggle='Resume';
	    warn "kill -s STOP $pid";
	    kill 'STOP', $pid;
	} else {
	    $toggle='Pause';
	    kill 'CONT', $pid;
	}
    }
    waitpid($pid,0);
}
```

---

