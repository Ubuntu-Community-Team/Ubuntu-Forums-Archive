---
title: "need scripting help"
date: 2007-03-24
forum: Programming Talk
---

### Post by stealth75711 on 2007-03-24
```
$!/bin/sh

echo '$dirinfo = "$Stealth 4/24/2007"

        if '$dirinfo = "dirinfo dirs"


        ls -l | grep '^d' | wc -l

        if '$dirinfo = "dirinfo files"



        ls -l | grep '^-d' | wc -l

else

echo '$dirinfo "Invalid command"

fi

```

Hello,

In the above scriptfile i am trying to

1. at the command dirinfo list my name and date
2. at the command dirinfo dirs display number of directories in my current directory
3.at the command dirinfo files to display the number of files in the current directory.
4. then finally an error message if non-conditions met

I am sure its syntax errors can anyone help me get this
Script file working?

---

### Post by lloyd_b on 2007-03-24
The proper way to handle this situation is with a "case" structure.  Here's a simple script that I think you can modify to accomplish what you want:
```
#!/bin/bash
case "$1" in
"")     echo "No Parameter"
        ;;
dirs)   echo "dirs"
        ;;
files)  echo "files"
        ;;
*)      echo "Invalid option"
        ;;
esac
```

Now for the explanation:  Assume that the script is named "dirinfo", as in your example.  The $1 argument refers to the "first command line parameter" (after the command name).  

"") refers to a "null string", which triggers if you had typed just "dirinfo"

dirs) is what triggers if you type "dirinfo dirs"

files) is what triggers if you type "dirinfo files"

*) triggers if none of the preceding cases are true. 

The ;; lines terminate each case, and the esac terminates the case structure.

Hope this will put you on the right track.

Lloyd B.

---

### Post by stealth75711 on 2007-03-24
```
#!/bin/bash
case "$1" in
"")	echo "Stealth March 24, 2007"
	;;
dirs)	echo ls -l | grep '^d' | wc -l
	;;
files)	echo ls -l | grep '^-d' | wc -l
	;;
*)	echo "Invalid option"
	;;
esac
```

ok and my output is this

#sh dirinfo
Stealth March 24, 2007

#sh dirinfo dirs
0

#sh dirinfo files
0

#sh dirinfo dfg
Invalid option

My question is if i am in my home directory
shouldnt it output more than 0 directories
and 0 files?  I would think it would since i have
files and directories. How do i tweak the 
commands?

---

### Post by lloyd_b on 2007-03-24
First off - could you post the output from "ls -l" in your home directory?  I run that script in my home directory, and get the following:
```
lloyd@laptop:~$ dirinfo dirs
6
```

With this from "ls -l":
```
drwxr-xr-x 2 lloyd lloyd  4096 2007-03-24 15:57 bin
drwx------ 2 lloyd lloyd  4096 2007-03-24 01:30 Desktop
drwxr-xr-x 2 lloyd lloyd  4096 2007-03-24 08:58 download
-rw-r--r-- 1 lloyd lloyd 67393 2007-03-14 06:10 Excalibur.jpg
drwxr-xr-x 6 lloyd lloyd  4096 2007-03-09 14:12 gnutella
-rw-r--r-- 1 lloyd lloyd  1730 2007-03-13 21:25 key.gpg.asc
drwxr-xr-x 2 lloyd lloyd 24576 2007-03-09 12:11 music
drwxr-xr-x 3 lloyd lloyd  4096 2007-03-24 15:54 stuff
-rw-r--r-- 1 lloyd lloyd  1730 2007-03-13 21:25 test

```

So that part appears to be working fine.

The "files" option has a problem:  "grep '^-d'" is looking for a line that starts with a "-", and is followed by a "d", not a line that doesn't start with 'd'.  

What you're probably looking for is "grep '^-'", which will trigger on any line whose first character is a '-'.

Changing that grep and running in my home directory produces the following:
```
lloyd@laptop:~$ dirinfo files
3
```
Which is correct.

Note:  Both the "files" and "dirs" options have a bit of a problem, in that neither  correctly handle symbolic links (whose first character will be "l").  This can be resolved by changing the ls command to "ls -lL", which will resolve those links to either files or directories.

Finally, the script does not look for "hidden" files and directories (i.e. files/directories whose name starts with a '.').  You can change this by modifying the ls command to "ls -laL", but I'm not certain as to whether or not that's what you want. 

Lloyd B.

---

### Post by stealth75711 on 2007-03-24
stealth@Zamis-laptop:~$ sh dirinfo dirs
0

#ls -l

#these are just some of my files and directories
drwxr-xr-x 3 stealth stealth     4096 2007-01-11 02:41 tt
-rw-r--r-- 1  stealth stealth   12511 2007-02-19 11:15 ubuntuedgy.odt
-rw-r--r-- 1  stealth stealth    3244 2007-01-12 19:47 uninstal.log
-rw-r--r-- 1  stealth stealth      15 2007-01-30 10:18 Unsaved Document 1
-rw-r--r-- 1  stealth stealth    3296 2007-01-11 20:05 Untitled.jpg
drwxr-xr-x 2 stealth stealth      4096 2007-02-02 16:47 video Files
-rw-r--r-- 1  stealth stealth    36057 2007-02-02 16:47 video.php
drwxr-xr-x 2 stealth stealth    4096 2007-01-20 14:57 vista1024
-rw-r--r-- 1 stealth stealth       310 2007-02-24 16:21 Wages1Panel.java
-rw-r--r-- 1  stealth stealth     1085 2007-02-24 15:51 Wages.class
-rw-r--r-- 1 stealth stealth       984 2007-02-24 16:27 Wages.java
-rw-r--r-- 1 stealth stealth       960 2007-02-24 16:13 Wages.java~
drwxr-xr-x  stealth stealth     4096 2007-01-23 17:02 work
drwxr-xr-x 4 stealth stealth     4096 2007-01-30 12:19 workspace
-rw-r--r-- 1 stealth stealth     80705 2007-02-17 19:02 wwNina.jpg
-rw-r--r-- 1 stealth stealth     351744 2007-02-22 18:59 Zarmonia(1).doc
-rw-r--r-- 1 stealth stealth    351744 2007-02-22 18:55 Zarmonia.doc

stealth@Zamis-laptop:~$ sh dirinfo files
0

#And heres what the script file currently looks like
```
#!/bin/bash
case "$1" in
"")     echo "Stealth March 24, 2007"
        ;;
dirs)   echo ls -lL | grep '^d' | wc -l
        ;;
files)  echo ls -laL | grep '^-' | wc -l
        ;;
*)      echo "Invalid option"
        ;;
esac

```

#still its not reading my files or directories :(
#i want script file to read all my current directories and files

---

### Post by lloyd_b on 2007-03-24
```
dirs)   echo ls -lL | grep '^d' | wc -l
        ;;
files)  echo ls -laL | grep '^-' | wc -l
        ;;
```

Lose the "echo" parts on these lines:
```
dirs)  ls -lL | grep '^d' | wc -l
        ;;
files)  ls -laL | grep '^-' | wc -l
        ;;
```

Sorry, I spotted this issue earlier, and I was removing the "echo" parts without even thinking about it.  "echo" is used to display a string without executing it.  In this case, you want to execute the commands.

Note: you've got "-laL" for files, but "-lL" for directories - there are a LOT of directories in the typical home directory that start with "." (besides the standard "." and "..", you'll generally find application specific directories, such as ".mozilla" or ".mplayer").  Whether or not you want to include these directories in the count is up to you.  If you want to avoid counting the "." and ".." implied entries, us "ls -lAL" - the 'a' includes these entries, the 'A' does not.

Lloyd B.

---

### Post by stealth75711 on 2007-03-24
keith@Zamis-laptop:~$ sh dirinfo
Stealth March 24, 2007
stealth@Zamis-laptop:~$ sh dirinfo dirs
21
stealth@Zamis-laptop:~$ sh dirinfo files
107


:) It works!

thanks for the help i got alot to
learn about scripting!!:guitar:

---

