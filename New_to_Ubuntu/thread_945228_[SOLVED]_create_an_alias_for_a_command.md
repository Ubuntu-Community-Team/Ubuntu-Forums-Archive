---
title: "[SOLVED] create an alias for a command"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by rkakkar on 2008-10-12
i have a long command with lots of options. i run this command on a regular basis. can i create a one word alias instead to shorten the typing?

---

### Post by DirtDawg on 2008-10-12
Hi. You first must allow aliases in bash. To do this, open your .bashrc file:
```
gedit ~/.bashrc
```
Look for the following lines and uncomment the conditional statement so it looks like this:
```
# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

```
You can then create aliases with the alias command. There are commented examples near the end of your .bashrc file like this:
```
alias ll='ls -l'
```
As mentioned in .bashrc, you can also create a new file in your home folder called .bash_aliases to store your aliases. They will still be recognized and they are more portable that way.

---

### Post by jamesrl on 2008-10-12
Yes, just edit the file .bash_aliases

Here are some aliases I use:

```
alias la='ls -al'
alias l.='ls -dF .[a-zA-Z0-9]*' 
alias ll='ls -ltr'
alias snano='sudo nano -BIA -C /tmp/nano/root'
alias du='du -h'
alias df='df -h'
alias konq='konqueror'
alias gotosleep='sudo /etc/acpi/sleep.sh force'
alias xpdf='acroread'
alias vnc8='vnc4server -cc 3 -depth 8 -geometry 1500x1000'
alias vnc='vnc4server -geometry 1500x1000'
alias cdlasttrash='cd ~/tmp/trash_myrm/`cat ~/tmp/trash_myrm/pointer`'
alias lslasttrash='ls ~/tmp/trash_myrm/`cat ~/tmp/trash_myrm/pointer`'
alias sshworkip='ssh -XC 128.84.47.113'

alias root='root -l'
## alias del='/bin/mv -t ~/.trash/ "$*" '
alias del='/bin/rm'
alias rm='~/local/bin/myrm'
alias oldrm='/bin/rm'
alias rrm='/bin/rm'
alias shred='/usr/bin/shred -u -z -n50'
alias oldshred='/usr/bin/shred'
= () { echo "scale=4; ${*}" | bc ; }

alias e='/usr/bin/emacs -nw'
alias enw='/usr/bin/emacs -nw'
em () { /usr/bin/emacs -g 150x65 ${*} & }
emacs () { /usr/bin/emacs -g 150x65 ${*} & }
semacs () { gksudo "/usr/bin/emacs -g 150x65 ${*}" & }

gpgclose () { gpg -r $USER -e $1 && shred $1 ;}

```

and in case you were wondering what 'myrm' its an executable that keeps a buffer
in ~/tmp/trash_myrm of the last 100 things I deleted (as a regular user), in case
I ever want to restore something.  The script was based off of scripts from here:
[http://www.linuxforums.org/forum/linux-programming-scripting/13413-bash-script-call-bin-mv-spaces-handling-parameters.html](http://www.linuxforums.org/forum/linux-programming-scripting/13413-bash-script-call-bin-mv-spaces-handling-parameters.html)
```

fake_user_name:~$ cat ~/local/bin/myrm 

#!/bin/bash

DEFAULT_TRASHCAN_PATH=~/tmp/trash_myrm
BUFFER_START=100
BUFFER_END=199
SYSTEM_RM=/bin/rm

##-- end settings

if [ -z $TRASHCAN ]; then
	TRASHCAN=$DEFAULT_TRASHCAN_PATH
fi

if [ -f $TRASHCAN ]; then
	echo "Error: There is a file named with $TRASHCAN"
fi

if [ ! -d $TRASHCAN ]; then
	mkdir $TRASHCAN
fi

if [ "$1" == "--diskusage" -o "$1" == "-d" ]; then
	du -h -s $TRASHCAN
	exit
fi

if [ "$1" = "--purge" ]; then
	$SYSTEM_RM -rf $TRASHCAN/*
	exit
fi

POINTER=BUFFER_START
if [ -f $TRASHCAN/pointer ]; then
	POINTER=`cat $TRASHCAN/pointer`
fi

if [ "$1" == "--undo" -o "$1" == "-u" ]; then
	mv $TRASHCAN/$POINTER/*
	POINTER=$[$POINTER-1]
	if [ $POINTER -le $BUFFER_START]; then
		POINTER=$[$BUFFER_END-1]
	fi
	echo $POINTER > $TRASHCAN/pointer
	exit
fi

if [ "$1" == "--showpointer" -o "$1" == "-s" ]; then
	echo $POINTER
	exit
fi

POINTER=$[$POINTER+1];

if [ $POINTER -ge $BUFFER_END ]; then
	POINTER=$BUFFER_START
fi

echo $POINTER > $TRASHCAN/pointer

TARGETDIR=$TRASHCAN/$POINTER

if [ -d $TARGETDIR ]; then
	$SYSTEM_RM -rf $TARGETDIR/*
else
	mkdir $TARGETDIR
fi

if [ -z "$1" ]; then
	du -h -s $TRASHCAN
	exit
fi

file_to_remove="";

while [ -n "$1" ]
do
	if [ "${1:0:1}" != "-" ]; then
		mv -f "$1" $TARGETDIR
	fi
	shift
done

exit

```

---

### Post by Spitphire on 2008-10-19
Curious about your oldshred command, can you explain this to me please, i'm curious what it does??

```

alias oldshred='/usr/bin/shred'
= () { echo "scale=4; ${*}" | bc ; }

```

---

### Post by jamesrl on 2008-10-21
Explaining section:
```

alias shred='/usr/bin/shred -u -z -n50'
alias oldshred='/usr/bin/shred'
= () { echo "scale=4; ${*}" | bc ; }
```
I use the /usr/bin/shred command to delete `sensitive` data (e.g., a text file that  had passwords in it, or an unencrypted file that had grades for people I TA in it).  /usr/bin/shred overwrites the file to hide its contents, and my alias to shred uses default settings which (a) -u truncate and remove the file, (b) -z have a final overwrite of all 0s (hides that somethings been shredded), and (c) does it 50 times.
oldshred is just an alias to the original /usr/bin/shred command.

The next alias, is actually not an alias but a bash function, with the name of the function '=' which is a [cheap] command line calculator that displays decimals to 4 digits.  The syntax is send the string "scale=4; math_expression" to bc which is an arbitrary precision calculator that evaluates math_expression.  (sudo apt-get install bc if it can't find it).  I find i use this all the time for quick calculations where I don't want to bother opening up a real program (like octave / Mathematica / gnome-calculator / maxima).  Kind similar to the Alt-F2 calculator in KDE, but that gnome doesn't have anywhere. 

Examples of usage:
```

fake_user_name:~$ = 100*5 + 3/5
500.6000
fake_user_name:~$ = 381/13.2
28.8636
fake_user_name:~$ = 'sqrt(2)'
1.4142

```

examples of usage failing due to bash features (that is parentheses and * having special bash meanings) that i never figured how to turn off for just one command ...
```

fake_user_name:~$ = 100 * 5
(standard_in) 1: syntax error
## fails because it replaces * with all the names of the files in the 
## current directory before attempting to evaluate
fake_user_name:~$ = 100 *5
500
## works in current directory but could fail if there are any files 
## in the current directory with a name ending with a 5 (e.g. *5)
fake_user_name:~$ = sqrt 2
(standard_in) 1: syntax error
## need to enclose argument of sqrt (the 2) in parenthesis
fake_user_name:~$ = sqrt(2)
bash: syntax error near unexpected token `('
## fails because bash evaluates the parenthesis as a command to 
## bash rather than a symbol; must either escape paranthesis use \(  \)
## or enclose expression in quotes ' ' like:
fake_user_name:~$ = sqrt\(2\)
1.4142
fake_user_name:~$ = 'sqrt(2)'
1.4142

```

---

