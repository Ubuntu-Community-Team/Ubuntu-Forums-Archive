---
title: "bash functions are not recognized in scripts"
date: 2008-07-19
forum: Programming Talk
---

### Post by bogdanbiv on 2008-07-19
I've set up a special user account for KDE development (his home being /home/kde-devel).

I have copied the following script
[http://techbase.kde.org/Getting_Started/Increased_Productivity_in_KDE4_with_Scripts/.bashrc](http://techbase.kde.org/Getting_Started/Increased_Productivity_in_KDE4_with_Scripts/.bashrc) into 
/home/kde-devel/.bashrc

It mainly contains variables and bash functions needed to build & run KDE.

Trouble is that in scripts although variables expand correctly, the functions are not seen (command ./test: line 1: cs: command not found). Example:

Exerpt from ~/.bashrc:

```
# Change to the source directory.  Same as cb, except this
# switches to $KDE_SRC instead of $KDE_BUILD.
# Usage: cs KDE/kdebase
#   will change to $KDE_SRC/KDE/kdebase
# Usage: cs
#   will simply go to the source folder if you are currently in a build folder
#   Example:
#     $ pwd
#     /home/user/build/KDE/kdebase
#     $ cs && pwd
#     /home/user/src/KDE/kdebase
function cs {
	local dest current
 
	# Make sure source directory exists.
	mkdir -p "$KDE_SRC"
 
	# command line argument
	if test -n "$1"; then
		cd "$KDE_SRC/$1"
	else
		# substitute build dir with src dir
		dest=`pwd | sed -e s,$KDE_BUILD,$KDE_SRC,`
		current=`pwd`
		if [ "$dest" = "$current" ]; then
			cd "$KDE_SRC"
		else
			cd "$dest"
		fi
	fi
}
```

Bad behaviour in scripts:
home/kde-devel/bin$ ./test
./test: line 1: cs: command not found
/home/kde-devel/bin
./test: line 3: cb: command not found
/home/kde-devel/bin
kde-devel@bog-desktop:~/bin$ ./test
./test: line 1: cs: command not found
/home/kde-devel/bin
./test: line 3: cb: command not found
/home/kde-devel/bin
kde-devel@bog-desktop:~/bin$ cat test
cs
pwd
cb
pwd



When I call the same functions from the command prompt (interactive session), there arent any problems.

I have Kubuntu 8.04

---

### Post by dtmilano on 2008-07-19
The ~/.bashrc file determines the behavior of interactive shells. Use ~/.bash_profile instead.

---

### Post by bogdanbiv on 2008-07-20
It works with ~/.bash_profile! Thanks a lot!

One more question though:
I need to put the line `source ~/.bash_profile` at the beginning of every script, otherwise the functions defined still do not work.
Ain't bash_profile supposed to be executed automatically? Do I have to do it manually in every script I need? what's the idea then - it behaves just like a normal script?

---

### Post by mike2357 on 2008-07-20
Scripts default to /bin/sh, also known as the Bourne shell.  To specify another shell, must be specified (preceded by #!) on the very first line of the script, even before any comment lines, and with no indentation.

So to make your script run in /bin/bash, make this the first line:

#!/bin/bash

---

