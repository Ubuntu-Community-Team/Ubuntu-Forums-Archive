---
title: "Simple Bash script: please explain"
date: 2011-12-10
forum: Programming Talk
---

### Post by Stovey on 2011-12-10
Hi everyone!  Would someone please take a moment and walk me through the following Bash script.  These three items surprised me:

1.  I haven't seen $# before.  I'm guessing it's the number of arguments passed from the command line.
2.  1>&2.  No idea on this one.
3.  fn=$(basename "$filename").  I haven't seen basename before.

I'm working through the [linuxcommand.org](http://www.linuxcommand.org/wss0140.php) bash tutorial, and this script is Lesson 14.  The author usually provides an explanation for new concepts, but apparently not this time.

code:
> #!/bin/bash

# cmp_dir - program to compare two directories

# Check for required arguments
if [ $# -ne 2 ]; then
	echo "usage: $0 directory_1 directory_2" 1>&2
	exit 1
fi

# Make sure both arguments are directories
if [ ! -d $1 ]; then
	echo "$1 is not a directory!" 1>&2
	exit 1
fi


if [ ! -d $2 ]; then
	echo "$2 is not a directory!" 1>&2
	exit 1
fi

# Process each file in directory_1, comparing it to directory_2
missing=0
for filename in $1/*; do
	fn=$(basename "$filename")
	if [ -f "$filename" ]; then
		if [ ! -f "$2/$fn" ]; then
			echo "$fn is missing from $2"
			missing=((missing+1))
		fi
	fi
done
echo "$missing files missing"

---

### Post by Lars Noodén on 2011-12-10
> **Stovey said:**
> 
1.  I haven't seen $# before.  I'm guessing it's the number of arguments passed from the command line.
2.  1>&2.  No idea on this one.
3.  fn=$(basename "$filename").  I haven't seen basename before.


1.  Dunno yet.

2.  Redirects stdout (1) to stderr (2)  So the output of echo in the example then goes to stderr instead of stdout.

3.  The contents of the variable 'fn' is set with value produced by running [basename](http://manpages.ubuntu.com/manpages/oneiric/en/man1/basename.1posix.html) with the parameter found in the variable "filename"

---

### Post by hakermania on 2011-12-10
*1.  I haven't seen $# before.  I'm guessing it's the number of arguments passed from the command line.*
Yes, it's the number of arguments.
* 2.  1>&2.  No idea on this one.*
There are 2 output streams, a stream that all normall output should be passed to and a stream were all the error output should be passed to. The former is called stdout and the latter stderr. If you do
```

echo "Hello"

```
this will be sent to stdout
If you do
```

echo "Hello" 1>&2

```
then it will be sent to stderr.
Stdout and stderr exist in case you want to filter the output of a command.
Stdout is called using '1' and stderr using '2'
For example:
```

bash ./myscript > /dev/null

```
will throw all the stdout output to /dev/null and
```

bash ./myscript 2> /dev/null

```
will throw all the stderr to /dev/null
[I] 3.  fn=$(basename "$filename").  I haven't seen basename before
[/I]'basename' is a normal command.You can try it yourself, it returns the basename of a given path, for example
```
basename /home/alex/image.jpg
```
will return
```
image.jpg
```

Hope I helped

---

### Post by Paddy Landau on 2011-12-10
Read the Bash manual: enter the command```
man bash
```It is good practice to use curly brackets when using $. So, instead of:```
$#
$@
$USER
```rather use:```
${#}
${@}
${USER}
```The reason why becomes apparent when you start using more advanced constructs, such as:```
${#STR}
${LIST[@]}
${ELEM['b']}
${PARAM:5:2}
${ANSWER%%y}
```

---

### Post by Stovey on 2011-12-10
Great!  Thanks for your help everybody, it's clear now.

---

### Post by Paddy Landau on 2011-12-11
> **Stovey said:**
> Great!  Thanks for your help everybody, it's clear now.
Thank you. Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") to help others with similar problems.

---

