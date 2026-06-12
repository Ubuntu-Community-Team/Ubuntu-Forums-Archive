---
title: "Calling and returning data from terminal to perl"
date: 2006-10-27
forum: Programming Talk
---

### Post by luken8r on 2006-10-27
I am a n00b to perl programming and I think this is a simple question. 
How do you call and run some terminal program through a perl script that will return a data string and use that string?

What I have is a function that currently calls some command that will test an address in ROM and return that value, check it in an if/else and return some value. This value returned is a number string, so I can manipulate that with no  problem:

sub function {
    return 0 unless -x '/usr/local/bin/srom';
    my $model_data = `/usr/local/bin/srom -a 10 -r 2`;
    if (($model_data ge "0510") && ($model_data le "0513")) {
        return (1);
    } else {
        return (0);
    }

This is checking a serial number in flash, if the number is between 0510 - 0513, return true

Now my question is, how do I call some other command that returns a text string and not a number and use that string to pass a true/false statement?

The command would call something like this 

my $poe_active = 'poe ds';

That command will return 

name@terminal:~$ poe ds
POE device missing or unpowered

If not detected

After this command is called will the variable $poe_active contain the text string 'POE device missing or unpowered'?

---

### Post by Tom_servo on 2006-10-27
Off the top my head before I head for bed look at the system call.

There are two main ways in Perl to interact with command line backticks ` or use system. To get the results back from command and not just a number use system e.g.

$test = system ("ls -l ");
print "$test\n";

Cheers

---

