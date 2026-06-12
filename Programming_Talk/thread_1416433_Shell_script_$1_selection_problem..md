---
title: "Shell script $1 selection problem."
date: 2010-02-26
forum: Programming Talk
---

### Post by Dennis Beekman on 2010-02-26
I know that shell scripts are not actually programming, but this seemed the most logical section to put this post... ;)

I have tons of shell scripts to install surtain program or setup surtain systems... and i wish to combine them.

it a very simple shell script.

```

if [ $1 = 'fprint' ]
then
#bunch of commands
elif [ $1 = 'boinc' ]
#bunch of commands
else
#bunch of commands 
fi

```

Now the first 2 things work if i type "sh install.sh fprint" or "sh install.sh bionc" 

but when i just type "sh install.sh" without any added command, in wich case it should go to the 'else' part of the script... it fails to run those commands.
It tells me that there is a unexpected operator.

i think the if statement cannot handle a empty variable like when i do not specify anything for $1

is there a way around that ?

---

### Post by geirha on 2010-02-26
Shell scripting is programming, so you posted this in the right place.

It's not the if that is complaining, it's the [ command (Yes, [ is a COMMAND, it's not part of the if-syntax. If takes a command and checks its return value, 0 = true, non-zero = false).

When you run the script with «sh install.sh fprint», «[ $1 = 'fprint' ]» will become «[ 'fprint' = 'fprint' ]» after all expansions have taken place, and then it runs, returning 0 (true).

When you run the script without arguments, «[ $1 = 'fprint' ]» will become «[ = 'fprint' ]» after variable expansion have taken place, which yields an error since [ expects an argument to the left of the = argument.

If you instead use «[ "$1" = 'fprint' ]», it will expand to «[ '' = 'fprintf' ]» which is legal, and will return 1 (false).

Rule of thumb, ALWAYS quote expansions (with double quote); "$1" "$foo" "${filepath##*/}" "$(some command)" etc...

See [http://bash-hackers.org/wiki/doku.php/syntax/words](http://bash-hackers.org/wiki/doku.php/syntax/words) and [http://www.grymoire.com/Unix/Quote.html](http://www.grymoire.com/Unix/Quote.html)

---

### Post by Reiger on 2010-02-26
Reason: you get a completely empty expression at the LHS of the = (equality) operator. sh really doesn't like that; empty strings in ifs that is.

The simple way out is something like prefixing it with a simple string so no empty strings can occur: "x$1" = "xfprint".

However your code has a more general problem: repetitive if statements that check against the same value over and over again.
There is the case construct which will do what you need and do it more elegantly (and also circumvent any issues with empty $1 strings):
```

case "$1" in
  fprint)
    # do fprint stuff here
  ;;
  boinc)
    # do boinc stuff here
  ;;
  *)
    # default: when nothing above this entry matches, proceed with the code here
  ;;
esac;

```

This can be used to good effect for long/short options:
```

help() {
  echo "
    This program <does some stuff>.
    
    Usage: $0 [-h|--help|program] where <program> is a program name. -h and --help bring up this \"help screen\".
    ";
}

case "$1" in
  fprint)
    # do frpint stuff
  ;;
  boinc)
    # do boinc stuff
  ;;
  -h|--help)
    help; # help screen requested
  ;;
  *) # error argument not recognized:
    echo "Error: option/program not recognized: \"$1\"";
    help; # show the help screen as added bonus
  ;;
esac;

```

---

### Post by Rany Albeg on 2010-02-26
Hello , 
Please check your mistakes :

```
#!/bin/sh
if [ "$1" = 'fprint' ]; then
	echo "Installing fprint...";
elif [ "$1" = 'boinc' ]; then
	echo "Installing boinc...";
else
	echo "Default.";
fi
exit 0
```

Execution:
```
rany@rany-laptop:~/Desktop$ ./install.sh 
Default.
rany@rany-laptop:~/Desktop$ ./install.sh fprint
Installing fprint...
rany@rany-laptop:~/Desktop$ ./install.sh boinc
Installing boinc...
```

Have a nice day.

EDIT: You guys are fast :) Well done. ( a smile is like an end of sentence? )

---

### Post by Dennis Beekman on 2010-02-26
Thank you very much... it seems both methods will do the job perfectly.

It completely eluded me why it was doing this... but now that you told me it makes actual sense.

Again thank you very much

---

