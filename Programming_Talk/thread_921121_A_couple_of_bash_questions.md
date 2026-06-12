---
title: "A couple of bash questions"
date: 2008-09-15
forum: Programming Talk
---

### Post by nbakewell on 2008-09-15
Hey all,

I've just started to work with Bash and although Google offers up some tutorials on it searching for specific questions have so far been unproductive - so I have a couple of simple questions to ask, if I may.

First, is there a way to split apart certain output?  For example, I am performing a "ls -l" to give me all files + permissions, but I just want to extract the permissions part.  So, my file listing may look like:

```
-rwxrwx--- 0 nbakewell csmajor 0 Sep 15 21:22 mytext.txt
-rwxrwx--- 0 nbakewell csmajor sep 14 18:02 second.txt
```

But I just want:
```
-rwxrwx---
-rwxrwx---
```

On the same note, I also want to be able to extract the owner value, not just the first value.

Second, is there a way to immediately kill the script from executing?  A command like "quit" or "die"?

Third, if I want to print to standard error output, do I just use:
```
echo "error message" 2>
```

Thanks!

---

### Post by LaRoza on 2008-09-15
> **nbakewell said:**
> 
First, is there a way to split apart certain output?  For example, I am performing a "ls -l" to give me all files + permissions, but I just want to extract the permissions part.  So, my file listing may look like:

On the same note, I also want to be able to extract the owner value, not just the first value.

[http://www.softpanorama.org/Tools/cut.shtml](http://www.softpanorama.org/Tools/cut.shtml)


> 
Second, is there a way to immediately kill the script from executing?  A command like "quit" or "die"?


[http://en.wikipedia.org/wiki/Control-C](http://en.wikipedia.org/wiki/Control-C)

Hope that helps

---

### Post by ghostdog74 on 2008-09-15
> **nbakewell said:**
> 

On the same note, I also want to be able to extract the owner value, not just the first value.


you can use awk
```

ls -l |awk '{print $1,$3}'

```
you can also use cut, but not that flexible as awk.

> 
Third, if I want to print to standard error output, do I just use:
```
echo "error message" 2>
```

Thanks!

```

echo "error message" 2>1 

```

check my sig for learning bash

---

### Post by LaRoza on 2008-09-15
> **ghostdog74 said:**
> 
you can also use cut, but not that flexible as awk.


Sometimes, having something that does the job perfectly is better than something that does it and more.

C is more flexible than awk, but that doesn't make it more suitable.

---

### Post by ghostdog74 on 2008-09-15
> **LaRoza said:**
> Sometimes, having something that does the job perfectly is better than something that does it and more.

you mean awk doesn't do the job perfectly? what i mean by "flexible" is in case OP wants to do more processing such as finding a string or calculating, using awk is more suitable.

---

### Post by nbakewell on 2008-09-16
Thanks for the help - two more questions.  First, back to my original one, I meant a call to immediately quit the program from within the script itself, not from keyboard input.  And second, I am getting this syntax error in my script "dircmp":

```
Retrieving listing of dir: testdir
: command not found
: command not found
'ircmp: line 7: syntax error near unexpected token `
'ircmp: line 7: `ChkFile()
```

From this code, and I'm not sure why - I checked to make sure there were spaces where they are needed, but other than that I'm stuck.

```
echo "Retrieving listing of dir:" $1

#===========
# Version 1b
#===========

ChkFile() 
	{

	filename="$1"
	status=0
	if [ ! -e "$filename" ] ; then	
		#========================================
		# Check fails if the file does not exist.
		#========================================
		status=1;
	elif [ -d "$filename" ] ; then
		#==============================================
		# Check fails if a directory file does not have
		# both x (search) and r (read) permissions.
		#==============================================
		if [ ! -x "$filename" ] ; then
			status=2
		elif [ ! -r "$filename" ] ; then
			status=3
		fi
	elif [ -f "$filename" ] ; then
		#==============================================
		# Check fails if a regular file does not have
		# r (read) permission.
		#==============================================
		if [ ! -r "$filename" ] ; then
			status=4
		fi
	else
		#==============================================
		# Check fails if the file is of another type.
		#==============================================
		status=5
	fi
	return $status
	}

GetLst() 
	{


	if [ "$1" = -r ] ; then
		maxDepth=""
		shift 1
	else
		maxDepth="-maxdepth 1"
	fi

	#------------------------------------
	# Get the list of files using "find".
	#------------------------------------
	dirname="$1"
	cd "$dirname" 2>/dev/null
	list=`find . -mindepth 1 $maxDepth "(" -type d -o -type f ")" 2>/dev/null`
	#-----------------------------------
	# Find has "./" at the start of each 
	# filename. Remove.  Also sort.
	#-----------------------------------
	list=`echo "$list" | sed 's/..//' | sort`

	#--------------------------------------------
	# Check each file in the list passes ChkFile
	#--------------------------------------------
	status=0
	[ -n "$list" ] && while : ; do
		read filename
		[ $? != 0 ] && break
		ChkFile "$filename"
		if [ $? != 0 ] ; then
			list="$filename"
			status=1
			break;
		fi
	done <<<"$list"

	echo "$list"
	return $status
	}

GetLst $1
```

---

### Post by ghostdog74 on 2008-09-16
put a shebang at the first line of your script. Then put set -x and then run your script
```

#!/bin/bash
set -x
...
...
...
your code
...


```
you will see where you went wrong.

---

### Post by nbakewell on 2008-09-16
edit: apparently editing bash files in notepad/other text editors adds invisible characters that create syntax errors?  Do I have to write bash scripts in nano or some other built in editor?  I wrote the same simple dir test script through notepad and it gave me the same syntax error, and then straight through nano and it works.

---

### Post by ghostdog74 on 2008-09-16
it runs fine for me.

---

### Post by nbakewell on 2008-09-16
The whole script, with ChkFile and GetLst?

I keep getting "Unexpected end of file" errors when I try to run this script:

```
if [ -d "$1" ] ; then
    echo $1 "is a directory."
fi
```

I wrote it through nano so I know notepad or anything is adding unseen characters.

---

### Post by eentonig on 2008-09-16
If you edit your scripts in Windows (notepad), then yes you're likely to get annoying side-effects. 

Best thing to do is use a *nix compatible editor under windows if you have to. Or better yet, spent some time in learning basic vim.

Once you get beyond the basics, vim will prove to be an asset you couldn't imagine. And if you install the 'bash-support.vim', you'll get a lot of nifty helpfull features that will save you a lot of typo's and stuff.

---

### Post by nbakewell on 2008-09-16
That last script I wrote was entirely though nano on the putty terminal window connected to a linux machine - isn't nano a linux compatible editor?

---

