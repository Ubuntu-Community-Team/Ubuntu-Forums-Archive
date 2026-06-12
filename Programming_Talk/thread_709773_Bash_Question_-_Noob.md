---
title: "Bash Question - Noob"
date: 2008-02-27
forum: Programming Talk
---

### Post by victorbrca on 2008-02-27
Would anyone be able to enlighten me why the first one works and the second without "for" loop does not?

```
#!/bin/bash

function teste() {
	for i in "$@" ; do
	  if [ -d "$i" ] ; then echo "Error: \"$1\" already exists" ; fi
	done
}

teste $1
```


```
#!/bin/bash

function teste() {
	  if [ -d "$i" ] ; then echo "Error: \"$1\" already exists" ; fi
}

teste $1
```

Thanks!!


Vic.

---

### Post by Mr. C. on 2008-02-27
> **victorbrca said:**
> function teste() {
	  if [ -d "$i" ] ; then echo "Error: \"$1\" already exists" ; fi
}

Think: What is "$i" here ?

MrC

---

### Post by k2t0f12d on 2008-02-27
In
```
#!/bin/bash

function teste() {
	  if [ -d "$i" ] ; then echo "Error: \"$1\" already exists" ; fi
}

teste $1
```

$i is unassigned.  Passing
```
teste $1
```
does not implicitly cause $i to become the value of $1

The [FONT="System"]for[/FONT] loop in the first example cycles through the arguments to [FONT="System"]teste[/FONT], assigning them incrementally to $i for one iteration each.

---

### Post by victorbrca on 2008-02-27
> **Mr. C. said:**
> Think: What is "$i" here ?

MrC

Wow... such a noob....  :mrgreen:  Thanks once again for the help Mr. C.


Victor.

---

### Post by victorbrca on 2008-02-27
> **k2t0f12d said:**
> In
```
#!/bin/bash

function teste() {
	  if [ -d "$i" ] ; then echo "Error: \"$1\" already exists" ; fi
}

teste $1
```

$i is unassigned.  Passing
```
teste $1
```
does not implicitly cause $i to become the value of $1

The [FONT="System"]for[/FONT] loop in the first example cycles through the arguments to [FONT="System"]teste[/FONT], assigning them incrementally to $i for one iteration each.

Thanks for the reply!!!  :)

---

### Post by victorbrca on 2008-02-28
Got another question for the same script. I'm not able to cd into the new folder.

Please keep in mind that these are exercises from a Bash book that I'm reading. I'm sure it will look very disorganized for most of you.


```
#!/bin/bash

# pasta="$1"

function teste() {
	  if [ -d "$1" ] ; then 
	   echo "Error: \"$1\" already exists" 
	   exit 1
	  fi

	  echo "$1" | grep -e '^[A-Za-z0-9]*$' > /dev/null

	  d="$?"

	  if [ "$d" = "0" ] ; then
	    mkdir -p "$1" 
	    [COLOR="Red"]cd `pwd`/"$1[/COLOR]"
	    pwd
	  elif [ "$d" != "0" ] ; then
	    echo "Please use letters or numbers only"
	    exit 1
	  else 
	    echo "Error"
	    exit 1
	  fi
}


teste $1
```

---

### Post by Martin Witte on 2008-02-28
I pasted this code into a file called script.bash, and then ran it without problems, the directory I gave as argument was created. an you post what error you get?
```
martin@toshibap200:~$ ./script.bash x
/home/martin/x
martin@toshibap200:~$ 

```

---

### Post by victorbrca on 2008-02-28
> **Martin Witte said:**
> I pasted this code into a file called script.bash, and then ran it without problems, the directory I gave as argument was created. an you post what error you get?
```
martin@toshibap200:~$ ./script.bash x
/home/martin/x
martin@toshibap200:~$ 

```

I get the same thing, however it should CD into the new created folder, which is not...   :-s

---

### Post by Mr. C. on 2008-02-28
What evidence do you have that it is not changing directories?  I hope you don't think that script running in a subshell will change your current shell's current working directory!

By the way, this is superfluous code:

```
cd `pwd`/"$1"
```

This is sufficient and cheaper:

```
cd "$1"
```

The cd command always appends the current directory when its argument is a relative path.

MrC

---

### Post by victorbrca on 2008-02-28
> **Mr. C. said:**
> What evidence do you have that it is not changing directories? 

Would the script itself also be executed in a subshell or only the loop? So trying something like this would also have no result?

```
#!/bin/bash

function teste() {
	  if [ -d "$1" ] ; then 
	   echo "Error: \"$1\" already exists" 
	   exit 1
	  fi

	  echo "$1" | grep -e '^[A-Za-z0-9]*$' > /dev/null

	  d="$?"

	  if [ "$d" = "0" ] ; then
	    mkdir -p "$1" 
	  elif [ "$d" != "0" ] ; then
	    echo "Please use letters or numbers only"
	    exit 1
	  else 
	    echo "Error"
	    exit 1
	  fi
}

teste $1
cd "$1"
pwd
```


I only used an absolute path as a failsafe. I thought somehow that it might be the problem.

Thanks!!!


Vic.

---

### Post by Mr. C. on 2008-02-28
> **victorbrca said:**
> Would the script itself also be executed in a subshell or only the loop? So trying something like this would also have no result?


No result whatsoever on your current shell.  For that, you can use shell functions.
A script executed is ALWAYS executed in a subshell.  Two concepts here to know: *execution* of a script (aka: exec) or *sourcing* a script (runs in *current* shell).  The different looks like:
```

/path/to/myscript
**.** /path/to/myscript

```

See Lecture 9, Sub-Shells chapter: [http://cis68b1.mikecappella.com/](http://cis68b1.mikecappella.com/) for more clarification.

MrC

---

### Post by victorbrca on 2008-02-28
> **Mr. C. said:**
> ...See Lecture 9, Sub-Shells chapter: [http://cis68b1.mikecappella.com/](http://cis68b1.mikecappella.com/) for more clarification.

MrC

Thanks a lot. I gave it a read and the language used on those documents seemed easy enough for a noob like me to understand. I'll use as part of my studies. 

The script now works as well...  :)

Thanks again...

Vic.

---

### Post by victorbrca on 2008-03-19
Got another one... :???:

This script works:

```
#!/bin/bash

echo "Enter app name"
read app

ps x | grep "$app" | grep -v 'grep'
echo
echo "Do you want to kill all items? [y|n] "

read resposta
	if [ "$resposta" = "y" ] ; then	
 	   termina=`ps x | grep "$app" | grep -v 'grep' | awk '{print $1 ; }'`
 		for i in `echo $termina` ; do
			kill -9 "$i"
		done
	fi
```


Now this does not:

```
read resposta
	if [ "$resposta" = "y" ] ; then	
 	   termina=`ps x | grep "$app" | grep -v 'grep' | awk '{print $1 ; }'`
 		for i in "$termina" ; do
			kill -9 "$i"
		done
	fi
```

I get an error that "kill" cannot read the numbers.

> ./finish.sh: line 16: kill: 6628
6640
6645: arguments must be process or job IDs


Shouldn't "for i in" be able to read "$var"?

Thanks,

Vic.

---

### Post by Mr. C. on 2008-03-19
Consider the difference between these two:

```
$ var='1 2 3 4'
$ for i in $var; do echo $i ; done
1
2
3
4
$ for i in "$var"; do echo $i ; done
1 2 3 4
```

---

### Post by victorbrca on 2008-03-20
> **Mr. C. said:**
> "...Consider the difference between these two..."

Wow... you are on all of them!!!  Thanks again Mr. C...


Vic.

---

