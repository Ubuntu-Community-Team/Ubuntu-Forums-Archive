---
title: "[SOLVED] Need some help with the shell!"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by Slime mold on 2008-11-26
OK, I need to make it so that when given a folder, will go to all subfolders and execute a program. Is possible?

Thank you for help!

---

### Post by cmnorton on 2008-11-26
Can you provide more detail as to what you want to do?

---

### Post by binbash on 2008-11-26
what is the extension of the program?For python example : 

python /home/username/asdasd/asdasd/bsd.py

---

### Post by jenkinbr on 2008-11-26
Do you mean to have the shell go through the folder recursively, executing everything
(by the way, that sounds dangerous, unless you know exactly what's in there and what it does)

or do you mean to have a program, when given a directory, to go through and process each file under that folder.

A bit more discription as to what you are trying to do is neccessary in order to help you.

---

### Post by amauk on 2008-11-26
If you mean what I think you mean, then this will do the trick

(although this is in Absolute Beginners, and what you're asking is fairly complex so I may have misunderstood completely.....:confused:)

This is a script I use to manage data archived in directories according to month and year

example structure:
/data/
/data/2008/
/data/2008/11/
/data/2008/11/file.tar.gz

Basically, given a command (and optional arguments) it runs the command on all sub-directories inside the top-level directory

Eg. running
```
subdir_run du -hs /data/2008
```
will output the size of each month directory in 2008

```
1.1G	/data/2008/01/
1.8G	/data/2008/02/
703M	/data/2008/03/
1.6G	/data/2008/04/
```

I have a similar script for files inside directories, and combining the two you can script out actions to perform on large directory structures

Anyway, my **subdir_run** script

```
#!/bin/bash

function print_usage {
	echo "Usage: `basename $0` <command> [-args] /top/level/dir/"
	exit 1
}

# Parse args
eval LAST_ARG=\$$#
RUN_CMD=""
STR_ARGS=""
for ARG in "$@"
do
	if [ -z "$RUN_CMD" ]; then
		RUN_CMD="$ARG"
	else
		if [ "$ARG" != "$LAST_ARG" ]; then
			if [ -z "$STR_ARGS" ]; then
				STR_ARGS="${ARG}"
			else
				STR_ARGS="${STR_ARGS} ${ARG}"
			fi
		fi
	fi
done

# Check args
if [ -z "$RUN_CMD" ]; then
	echo "Error: No command specified"
	print_usage
else
	RUN_CMD="`which $RUN_CMD`"
	if [ -z "$RUN_CMD" ]; then
		echo "Error: Command not found"
		print_usage
	fi
fi

if [ -d "$LAST_ARG" ]; then
	TOP_DIR="${LAST_ARG%/}" # remove trailing slash if present
else
	echo "Error: Directory not found"
	print_usage
fi

for SUB_DIR in "${TOP_DIR}"/*
do
	if [ -d "$SUB_DIR" ]; then
		${RUN_CMD} ${STR_ARGS} "${SUB_DIR}"
	fi
done

```

---

### Post by Slime mold on 2008-11-27
> **jenkinbr said:**
> Do you mean to have the shell go through the folder recursively, executing everything
(by the way, that sounds dangerous, unless you know exactly what's in there and what it does)

or do you mean to have a program, when given a directory, to go through and process each file under that folder.

A bit more discription as to what you are trying to do is neccessary in order to help you.

I know my limit. :) I just want to run same program on all my family photo, but I have over 10000 organised all in separate folder. 2531 folders, re-entering a command would be crazy, no?


> **amauk said:**
> If you mean what I think you mean, then this will do the trick

(although this is in Absolute Beginners, and what you're asking is fairly complex so I may have misunderstood completely.....:confused:)

This is a script I use to manage data archived in directories according to month and year

example structure:
/data/
/data/2008/
/data/2008/11/
/data/2008/11/file.tar.gz

Basically, given a command (and optional arguments) it runs the command on all sub-directories inside the top-level directory

Eg. running
```
subdir_run du -hs /data/2008
```
will output the size of each month directory in 2008

```
1.1G	/data/2008/01/
1.8G	/data/2008/02/
703M	/data/2008/03/
1.6G	/data/2008/04/
```

I have a similar script for files inside directories, and combining the two you can script out actions to perform on large directory structures

Anyway, my **subdir_run** script

```
#!/bin/bash

function print_usage {
	echo "Usage: `basename $0` <command> [-args] /top/level/dir/"
	exit 1
}

# Parse args
eval LAST_ARG=\$$#
RUN_CMD=""
STR_ARGS=""
for ARG in "$@"
do
	if [ -z "$RUN_CMD" ]; then
		RUN_CMD="$ARG"
	else
		if [ "$ARG" != "$LAST_ARG" ]; then
			if [ -z "$STR_ARGS" ]; then
				STR_ARGS="${ARG}"
			else
				STR_ARGS="${STR_ARGS} ${ARG}"
			fi
		fi
	fi
done

# Check args
if [ -z "$RUN_CMD" ]; then
	echo "Error: No command specified"
	print_usage
else
	RUN_CMD="`which $RUN_CMD`"
	if [ -z "$RUN_CMD" ]; then
		echo "Error: Command not found"
		print_usage
	fi
fi

if [ -d "$LAST_ARG" ]; then
	TOP_DIR="${LAST_ARG%/}" # remove trailing slash if present
else
	echo "Error: Directory not found"
	print_usage
fi

for SUB_DIR in "${TOP_DIR}"/*
do
	if [ -d "$SUB_DIR" ]; then
		${RUN_CMD} ${STR_ARGS} "${SUB_DIR}"
	fi
done

```

I have not had time to test this yet, you must understand, but You just said my exact, issue, so it should, THANKS ALOT!

---

### Post by nixscripter on 2008-11-27
If I might make a silly suggestion.

Run this in the terminal: ```
 find /root/dir/path -type f -exec **your-command-here** {} \;
```

Include that backslash on the semicolon.

This will run the command once for each file, specifying the path as its last argument (where the {} is).

---

### Post by amauk on 2008-11-27
actually, not silly at all
you can reproduce my entire script with one line

```
find /top/dir/ -mindepth 1 -maxdepth 1 -type d -exec du -hs {} \;
```

but I find a script is more useful for chaining together different actions

---

