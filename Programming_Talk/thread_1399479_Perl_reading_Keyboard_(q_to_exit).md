---
title: "Perl reading Keyboard (q to exit)"
date: 2010-02-05
forum: Programming Talk
---

### Post by sprouty on 2010-02-05
Hi All,

I have a program that loops forever or until you press ctrl+c. I'm wondering if it possible to watch for the q character or ctrl+c being pressed and exit the program (I would want to delete some temp files first and change the colour of the prompt back.)

Many Thanks,

Sprouty

---

### Post by linebp on 2010-02-06
This is an example of how you can catch ctrl^C and "q" entered on the command line. The function cleanup is called when this happens. 

Are you absolutely sure you want to catch ctrl^C? If your code in cleanup goes wrong, you can no longer interrupt it with ctrl^c.

```

# set a new handler for ctrl^C
$SIG{INT} = \&cleanup;

sub cleanup {
    # Put code to delete files and change prompt color here
    exit()
}

while($input = <STDIN>){
    # strip user input of newline
    chomp($input); 
    # See if we got a quit command
    if ( $input eq "q") {
	cleanup()
    }
    # The rest of your Perl script goes here
}

```

---

