---
title: "Shell Scripting Help"
date: 2008-04-08
forum: Programming Talk
---

### Post by The Afterdark on 2008-04-08
Hey guys,

I'm just starting to learn Shell Scripting and I'm doing it in Ubuntu.

I've gotten a few scripts to work, but there is one that isn't working and the fact that it's so simple but doesn't work is annoying me.

```

#!/bin/sh
alias ll='ls -l'
alias ldir='ls -aF'
alias copy='cp'

```

I can enter those commands individually into the shell prompt, and they work just fine.  For example, if I type in 

```
alias ll='ls-l'
```

then everytime I use the 'll' command, it will perform the function of 'ls -l'.  

But running the shell script itself doesn't do that.  

```

$ chmod +x aliasthis
$ ./aliasthis

```

Once I do that, and enter 'll', it says that the command is not recognized by bash or something.  

Any help on this?  I really am lost as to what to do, I've been banging my head on it for a while (even though there's not many lines to bang my head over).

Thanks in advance!

---

### Post by pseudo-random on 2008-04-08
At a guess I'd say its because you want to set an environment variable for your current environment bu the shell script is setting it for a different environment.
If you just want to change aliases then edit .bashrc in your home folder.

---

### Post by PabloCardoso on 2008-04-08
You shouldn't be setting alias through an independent shell script. You simply add those lines (without the #!/bin/sh) to your ~/.bashrc. The next time you open a console/terminal, your aliases will be ready to go.

I don't know if this helps you, but that was my two cents :P
HTH!


Ops, looks like pseudo-random got here first! Just in case I'll leave some aliases of my own:
```

alias rm='rm -i'
alias ls='ls -lah --color'
alias du='du -h --max-depth=1'
alias df='df -hl'

```

---

### Post by unbuntu on 2008-04-08
> **PabloCardoso said:**
> You shouldn't be setting alias through an independent shell script. You simply add those lines (without the #!/bin/sh) to your ~/.bashrc. The next time you open a console/terminal, your aliases will be ready to go.

I don't know if this helps you, but that was my two cents :P
HTH!


Ops, looks like pseudo-random got here first! Just in case I'll leave some aliases of my own:
```

alias rm='rm -i'
alias ls='ls -lah --color'
alias du='du -h --max-depth=1'
alias df='df -hl'

```

While this is true, in Ubuntu they do use an individual script for all the aliases - probably this makes .bashrc a bit tidier.


This is the section in the default Ubuntu's .bashrc
```

if [ -f ~/.bash_aliases ]; then

    . ~/.bash_aliases

fi

```

All you need to do is to put all your alias statements in bash_aliases

---

### Post by stroyan on 2008-04-08
Unbuntu's quote from .bashrc using ~/.bash_aliases shows the key to solving your problem.
When you do
```

$ chmod +x aliasthis
$ ./aliasthis

```
The ./aliasthis script is actually run by a different shell process.
Your aliases are set in that process.  But they don't affect the original shell.
To set aliases in your original shell you can use the 'source' or '.' command.
```

$ . ./aliasthis
or
$ source ./aliasthis

```
Those commands tell the original shell to read the file and execute the commands inside it.

---

### Post by The Afterdark on 2008-04-14
Thanks a bunch guys!  That helped, putting it in bashrc worked.

I still don't understand why the original script wouldn't work though.  I added the directory of the script to the $PATH variable.  Basically I'm able to call the script without even the ./ thingy from anywhere in the system.

> **stroyan said:**
> Unbuntu's quote from .bashrc using ~/.bash_aliases shows the key to solving your problem.
When you do
```

$ chmod +x aliasthis
$ ./aliasthis

```
The ./aliasthis script is actually run by a different shell process.
Your aliases are set in that process.  But they don't affect the original shell.
To set aliases in your original shell you can use the 'source' or '.' command.
```

$ . ./aliasthis
or
$ source ./aliasthis

```
Those commands tell the original shell to read the file and execute the commands inside it.

Hmmm... I'll give this a shot tonight.

---

### Post by The Afterdark on 2008-04-15
> **unbuntu said:**
> While this is true, in Ubuntu they do use an individual script for all the aliases - probably this makes .bashrc a bit tidier.


This is the section in the default Ubuntu's .bashrc
```

if [ -f ~/.bash_aliases ]; then

    . ~/.bash_aliases

fi

```

All you need to do is to put all your alias statements in bash_aliases

That worked.  :)


But I did some more programming, and ran into more problems while writing other simple scripts.  
Okay, here we go:

I wrote this script creativelly called "testfile"

```

#!/bin/sh

if [ -d $dir1 ]; then
	echo "dir1 is a directory"
else
	echo "dir1 is not a director"
fi

if [ -f $dir1 ]; then
	echo "dir1 is  a regular file"
else
	echo "dir1 is not a regular file"
fi 

```

Here is what I got for an output when I ran the file:

```
ehsun@ehsun-ubuntu:~/bin$ testfile
dir1 is a directory
dir1 is  a regular file
ehsun@ehsun-ubuntu:~/bin$ ls
greplog  testfile
ehsun@ehsun-ubuntu:~/bin$ 

```

dir1 was neither a directory nor a file :S
Is there any reason why that file isn't working the way it should?  Basically it should determine whether the given parameter is a file or directory or neither.

-----

Next problem.

I basically am working out of a book, so I copied this script out of it.

```
#!/bin/sh
# inpath - Verifies that a specified program is either valid as is,
# 			or that it can be found in the PATH directory list.

in_path()
{
	# Given a command and the PATH, try to find the command.
	# Returns 0 if found and executable, 1 if not.  Note that
	# this temporarily modifies the IFS (input field seperator)
	# but restores it upon completion.

	cmpd=$1		
	path=$2		
	retval=1
	oldIFS=$IFS	
	IFS=":"

	for directory in $path
	do
		if [ -x $directory/$cmd ]; then
			retval=0				# if we're here, we found $cmd in $directory	
		fi
	done

	IFS=$oldIFS
	return $retval
}

checkForCmdInPath()
{
	var=$1
	# The variable slicing notation in the following conditional 
	# needs some explanation: ${var#expr} returns everything after
	# the match for 'expr' in the variable value (if any), and
	# ${var%expr} returns everything that doesn't match (in this
	# case, just the very first character).  You can also do this in
	# Bash with ${var:0:1}, and you could use cut too: cut -c1.

	if [ "$var" != "" ]; then
		if [ "${var%${var#?}}" = "/" ]; then
			if [ ! -x $var ] ; then
				return 1
			fi
		elif ! in_path $var $PATH ; then
			return 2
		fi
	fi
}

if [ $# -ne 1 ] ; then
	echo "Usage: $0 command" >&2 ; exit 1
fi

checkForCmdInPath "$1"
case $? in
	0 ) echo "$1 found in PATH"					;;
	1 ) echo "$1 not found or not executable"	;;
	2 ) echo "$1 not found in PATH"				;;
esac

exit 0
```


Here's an output:
```

ehsun@ehsun-ubuntu:~$ inpath /usr/bin/MrEcho
/usr/bin/MrEcho not found or not executable
ehsun@ehsun-ubuntu:~$ inpath MrEcho
MrEcho found in PATH
ehsun@ehsun-ubuntu:~$ inpath Echo
Echo found in PATH
ehsun@ehsun-ubuntu:~$ 
```

So apparently, MrEcho is a command found in the path?  That can't be right.
Why isn't this one working?

If you guys can help out, that would be great.  Thanks in advance!

---

### Post by The Afterdark on 2008-04-15
> **stroyan said:**
> Unbuntu's quote from .bashrc using ~/.bash_aliases shows the key to solving your problem.
When you do
```

$ chmod +x aliasthis
$ ./aliasthis

```
The ./aliasthis script is actually run by a different shell process.
Your aliases are set in that process.  But they don't affect the original shell.
To set aliases in your original shell you can use the 'source' or '.' command.
```

$ . ./aliasthis
or
$ source ./aliasthis

```
Those commands tell the original shell to read the file and execute the commands inside it.


Oh and yes, this worked too!  Thanks!
But I have a question.  If the aliasthis script was run by another shell, why arent commands like echo, more, less, or cat, run by another shell?  Or are they?

---

### Post by stroyan on 2008-04-16
> **The Afterdark said:**
> 
```

#!/bin/sh
if [ -f $dir1 ]; then
	echo "dir1 is  a regular file"
else
	echo "dir1 is not a regular file"
fi 

```

Here is what I got for an output when I ran the file:

```
ehsun@ehsun-ubuntu:~/bin$ testfile
dir1 is a directory
dir1 is  a regular file
ehsun@ehsun-ubuntu:~/bin$ ls
greplog  testfile
ehsun@ehsun-ubuntu:~/bin$ 

```

dir1 was neither a directory nor a file :S
Is there any reason why that file isn't working the way it should?  Basically it should determine whether the given parameter is a file or directory or neither.

You did not say or print what the dir1 variable was set to.
I suspect that it was not set at all.
Then your test "if [ -f $dir1 ];" would become "if [ -f ];".
The bash FAQ at [http://tiswww.case.edu/php/chet/bash/FAQ](http://tiswww.case.edu/php/chet/bash/FAQ)
notes in topic E1 that the test builting will return true if it has one non-NULL argument.
"-f" is not null, so the test returns true.

---

### Post by stroyan on 2008-04-16
> **The Afterdark said:**
> ...
Here's an output:
```

ehsun@ehsun-ubuntu:~$ inpath /usr/bin/MrEcho
/usr/bin/MrEcho not found or not executable
ehsun@ehsun-ubuntu:~$ inpath MrEcho
MrEcho found in PATH
ehsun@ehsun-ubuntu:~$ inpath Echo
Echo found in PATH
ehsun@ehsun-ubuntu:~$ 
```

So apparently, MrEcho is a command found in the path?  That can't be right.
Why isn't this one working?


  Your script has a typo.  You have ```
cmpd=$1
```  You need ```
cmd=$1
```
Because cmd is not set you end up testing for -x on directories in PATH.
And the directories are executable.

---

### Post by stroyan on 2008-04-16
> **The Afterdark said:**
> Oh and yes, this worked too!  Thanks!
But I have a question.  If the aliasthis script was run by another shell, why arent commands like echo, more, less, or cat, run by another shell?  Or are they?
Echo is actually a shell builtin.  It is done directly in the shell that reads that command.
More, less, and cat are executables.  They do run as another process, although not a shell process.
Your "aliasthis" file was a shell script starting with "#!/bin/sh".
So it was run in a shell process by exec.
(Ubuntu actually links /bin/sh to /bin/dash rather than /bin/bash.)

You can test for whether a command is a shell builtin, function, alias, or file using the "type" builtin.
```

$ type xxx
bash: type: xxx: not found
$ type type
type is a shell builtin
$ type echo
echo is a shell builtin
$ type ls
ls is aliased to `ls --color=auto'
$ type more
more is /bin/more
```

---

### Post by The Afterdark on 2009-01-20
Hey guys, I have another question about bash scripting.  

I'm writing a script to modify certain emails.  The details aren't necessary, but what I really want is to be able to turn this: 

```
cat $SRCDIR/$f | sed -e "s/Subject\:FW\: BENCH\([^ ]*\) \([a-zA-Z0-9]*\)\(.*\)/Subject\:FW\: BENCH\1-$TOKEN-$inc \2-$TOKEN-$inc \3/" -e "s/Subject\:FW\: EX\([a-zA-Z0-9]*\)\-\([a-zA-Z0-9]*\)\-\([a-zA-Z0-9]*\)/Subject\:FW\: EX\1-$TOKEN-$inc \2-$TOKEN-$inc \3/" -e "s/Subject\: BENCH\([^ ]*\) \([a-zA-Z0-9]*\)\(.*\)/Subject\: BENCH\1-$TOKEN-$inc \2-$TOKEN-$inc \3/" -e "s/Subject\: EX\([a-zA-Z0-9]*\)\-\([a-zA-Z0-9]*\)\-\([a-zA-Z0-9]*\)/Subject\: EX\1-$TOKEN-$inc \2-$TOKEN-$inc \3/" -e "s/Date\:\([^ ]*\) \([^ ]*\) \([^ ]*\) \([^ ]*\) \(.*\)/Date\:\1 $DATE $MONTH $YEAR \5/" -e "/BODY/,/\/BODY/ s/$BODYTOKEN/$BODYTOKEN-$TOKEN-$inc/" > "$DESTDIR/$f-$inc.msg";

```

Into something much neater, with each sed command seperated per line in the script, like this:

```
   sed -e "s/Subject\:FW\: BENCH\([^ ]*\) \([a-zA-Z0-9]*\)\(.*\)/Subject\:FW\: BENCH\1-$TOKEN-$inc \2-$TOKEN-$inc \3/"\ 
   -e "s/Subject\:FW\: EX\([a-zA-Z0-9]*\)\-\([a-zA-Z0-9]*\)\-\([a-zA-Z0-9]*\)/Subject\:FW\: EX\1-$TOKEN-$inc \2-$TOKEN-$inc \3/"\ 
   -e "s/Subject\: BENCH\([^ ]*\) \([a-zA-Z0-9]*\)\(.*\)/Subject\: BENCH\1-$TOKEN-$inc \2-$TOKEN-$inc \3/"\ 
   -e "s/Subject\: EX\([a-zA-Z0-9]*\)\-\([a-zA-Z0-9]*\)\-\([a-zA-Z0-9]*\)/Subject\: EX\1-$TOKEN-$inc \2-$TOKEN-$inc \3/"\ 
   -e "s/Date\:\([^ ]*\) \([^ ]*\) \([^ ]*\) \([^ ]*\) \(.*\)/Date\:\1 $DATE $MONTH $YEAR \5/"\ 
   -e "s/Date\: \([^ ]*\) \([^ ]*\) \([^ ]*\) \([^ ]*\) \(.*\)/Date\: \1 $DATE $MONTH $YEAR \5/"\ 
   -e "/BODY/,/\/BODY/ s/$BODYTOKEN/$BODYTOKEN-$TOKEN-$inc/" > "$DESTDIR/$f-$inc.msg";

```

Unfortunately, the script doesn't seem to treat the "\" character at the end of the line, the way the interactive terminal does.  
Does anyone know how I can get a continuation of the command on the next line?  

Thanks in advance.

---

### Post by ghostdog74 on 2009-01-20
put all your sed commands inside an sed script. and use the -f option of sed to execute it.

---

### Post by The Afterdark on 2009-01-20
Is there any other way to do it?  I don't want to implement two different scripts.  It would be best if I could just do it all in the bash script.  Is there a way to do that?

---

### Post by The Afterdark on 2009-01-20
I figured it out!  Apparently bash is just cool like this:

```
   cat $SRCDIR/$f | sed "
   s/Subject\:FW\: BENCH\([^ ]*\) \([a-zA-Z0-9]*\)\(.*\)/Subject\:FW\: BENCH\1-$TOKEN-$inc \2-$TOKEN-$inc \3/
   s/Subject\:FW\: EX\([a-zA-Z0-9]*\)\-\([a-zA-Z0-9]*\)\-\([a-zA-Z0-9]*\)/Subject\:FW\: EX\1-$TOKEN-$inc \2-$TOKEN-$inc \3/
   s/Subject\: BENCH\([^ ]*\) \([a-zA-Z0-9]*\)\(.*\)/Subject\: BENCH\1-$TOKEN-$inc \2-$TOKEN-$inc \3/
   s/Subject\: EX\([a-zA-Z0-9]*\)\-\([a-zA-Z0-9]*\)\-\([a-zA-Z0-9]*\)/Subject\: EX\1-$TOKEN-$inc \2-$TOKEN-$inc \3/
   s/Date\: \([^ ]*\) \([^ ]*\) \([^ ]*\) \([^ ]*\) \(.*\)/Date\:\1 $DATE $MONTH $YEAR \5/
   s/Date\:\([^ ]*\) \([^ ]*\) \([^ ]*\) \([^ ]*\) \(.*\)/Date\:\1 $DATE $MONTH $YEAR \5/
   /BODY/,/\/BODY/ s/$BODYTOKEN/$BODYTOKEN-$TOKEN-$inc/" > "$DESTDIR/$f-$inc.msg";
```

I never needed those "\" characters or the "-e" parameter in the first place, so long as I quote across multiple lines.  

Thanks anyways!

---

