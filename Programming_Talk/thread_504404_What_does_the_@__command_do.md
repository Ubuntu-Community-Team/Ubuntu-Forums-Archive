---
title: "What does the @_ command do?"
date: 2007-07-19
forum: Programming Talk
---

### Post by stigala on 2007-07-19
While running a perl-script on Ubuntu 7.04 I got a "No such file or directory" error. When I checked out the error-trace (mert-moses.pl line 919), I found the command "system(@_);". 

According to this definition of the perl system-command, it is used to execute commands in the underlying OS ("Perl allows access to commands in the underlying operating system in several ways via the system command: execute a command in a subshell and return to the calling program.") But I haven't figured out what kind of command @_ is in a Linux OS yet or whether the real problem is connected to it.)

If anyone knows what the @_ /system(@_) command does or have other ideas about why I get the error, please let me know!

Stig

Output from script
```
Executing: bin/moses-scripts/scripts-20070717-1342/training/filter-model-given-input.pl ./filtered /home/stig/wsDirMoses/model/moses.ini /home/stig/wsDirMoses/tuning/input
Can't exec "bin/moses-scripts/scripts-20070717-1342/training/filter-model-given-input.pl": No such file or directory at bin/moses-scripts/scripts-20070717-1342/training/mert-moses.pl line 919.
Failed to execute: bin/moses-scripts/scripts-20070717-1342/training/filter-model-given-input.pl ./filtered /home/stig/wsDirMoses/model/moses.ini /home/stig/wsDirMoses/tuning/input
  No such file or directory
```

mert-moses.pl (line 919 in bold)
```

sub safesystem {

print STDERR "Executing: @_\n";

**system(@_);**

if ($? == -1) {

print STDERR "Failed to execute: @_\n $!\n";

exit(1);

}

elsif ($? & 127) {

printf STDERR "Execution of: @_\n died with signal %d, %s coredump\n",

($? & 127), ($? & 128) ? 'with' : 'without';

exit(1);

}

else {

my $exitcode = $? >> 8;

print STDERR "Exit code: $exitcode\n" if $exitcode;

return ! $exitcode;

}

}
```

---

### Post by Ramses de Norre on 2007-07-19
@_ is the list of incoming  parameters to your stub, so you should look at where the stub is called.

---

