---
title: "Reaping zombie children in Perl"
date: 2008-08-02
forum: Programming Talk
---

### Post by ConMan318 on 2008-08-02
I have a Perl script, and the end of it requires a dialog box, as well as doing some other things.  Since dialog boxes (using backticked terminal dialog boxes) essentially stall a program at that point, and I need to continue with the program whether the user has closed the dialog box or not, I decided to fork the processes and have the child process display the dialog box while the parent continues on with the program.  Now, I have the program running perfectly, the program continues with or without the dialog box being closed.

BUT as of now, if the dialog box is closed, a zombie process is created.

I have been searching for information on the 'waitpid' command but can't get it to work correctly.

Part of my code:
```

defined(my $pid = fork()) or die "Cannot fork(): $!";

unless($pid){
    `$message`; #contains code to display the dialog box
    exit(0);
}

#waitpid($pid, 0);

#rest of program here

```

The commented out 'waitpid' kills the zombie and continues the program but not until the dialog box is closed.  This makes the whole fork pointless.  I don't even know the syntax of this function, some sites have the args like I have them in my above code, others have it being 'fork(WNOHANG, -1)'.  I also don't know if this is even the function that is necessary to do what I need to do.

This seems like it should be extremely simple, I just can't find anything other than pretty obfuscated pages about this.

Thanks in advance.

---

### Post by slavik on 2008-08-02
read more on forking processes. you want to make a process that disjoins from the parent, or you can use the thread library (since Perl uses kernel threads) to create a disjoined thread (which doesn't have to be waited on).

---

### Post by ConMan318 on 2008-08-03
Could you maybe give a short example of a successful fork with zombie-reaping?  Even just a program that prints something while calculating 2 + 2 in a child process?  Because I have been reading up on it for over an hour and haven't figured out how to get this to do what I want.

---

### Post by slavik on 2008-08-03
```

#!/usr/bin/perl

use strict;
use warnings;
use Switch;

$SIG{CHLD} = "IGNORE";

my $fork_ret; #fork() return value

switch ($fork_ret = fork()) {
	case undef {print "couldn't fork\n";}
	case 0 { print "I am the child process, sleeping...\n"; `zenity --info`; }
	else { print $fork_ret . " is the pid of the child\n"; sleep; exit; }
}

```

I wouldn't use unless ... fork() returns 3 possible values, 2 of which are not undef. undef is returned if fork() failed. 0 is returned to the child, and the pid of the child is returned to the parent.

EDIT: nvm, I misunderstood your question (I assumed that the parent died before the child. I updated the code ...
btw, here's a link: [http://perldoc.perl.org/functions/fork.html](http://perldoc.perl.org/functions/fork.html)

---

### Post by ConMan318 on 2008-08-03
It seems like the $SIG{CHLD} = "IGNORE" is the key part, since the child process in your example code becomes a zombie when that's removed.  When I put this in my code, though, it causes it to exit prematurely, even before the forking occurs.

Thank you though, I'll try to delve into it a bit more and see if I can figure it out.

EDIT: I've got it working perfectly now, I just had to put the SIG{CHLD} part right before the fork instead of at the beginning to stop it from messing up the rest of the program.

---

