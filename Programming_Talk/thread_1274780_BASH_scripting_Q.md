---
title: "BASH scripting Q:"
date: 2009-09-24
forum: Programming Talk
---

### Post by Krupski on 2009-09-24
Hi all,

I don't know if a BASH script question belongs here... sorry mods.. move it if necessary.

Anyway, I have two little scripts in 4NT (a powerful command shell for Windows NT/XP) that takes any or all FILENAMES in a directory and converts them to lowercase or uppercase names.

For example, I can have this:

```

 Volume in drive C is 0-primary      Serial number is 0704:2009
 Directory of  C:\INCOMING\*

09/24/2009  11:06p        <DIR>    .
09/24/2009  11:06p        <DIR>    ..
09/24/2009  10:20p        <DIR>    TMP
09/22/2009   8:39p            512  LINUX.BIN
09/24/2009   8:42p          6,891  MAKE-VIDEO-LINKS-SCRIPT
09/23/2009   5:19p  4,009,549,824  UBUNTU-SERVER-SNAPSHOT-23-SEP-2009-1719.VHD
09/22/2009   8:23p            512  XP-BOOT.BIN
  4,009,557,739 bytes in 4 files and 3 dirs    4,009,566,208 bytes allocated
474,984,181,760 bytes free

```

Now, if I type "lower" (all by itself) I get this:

```

 Volume in drive C is 0-primary      Serial number is 0704:2009
 Directory of  C:\INCOMING\*

09/24/2009  11:07p        <DIR>    .
09/24/2009  11:07p        <DIR>    ..
09/24/2009  10:20p        <DIR>    TMP
09/22/2009   8:39p            512  linux.bin
09/24/2009   8:42p          6,891  make-video-links-script
09/23/2009   5:19p  4,009,549,824  ubuntu-server-snapshot-23-sep-2009-1719.vhd
09/22/2009   8:23p            512  xp-boot.bin
  4,009,557,739 bytes in 4 files and 3 dirs    4,009,566,208 bytes allocated
474,984,177,664 bytes free

```

Or I can do individual files:

```

C:\INCOMING>[COLOR="Blue"]**lower UBUNTU-SERVER-SNAPSHOT-23-SEP-2009-1719.VHD**[/COLOR]
C:\INCOMING\UBUNTU-SERVER-SNAPSHOT-23-SEP-2009-1719.VHD -> C:\INCOMING\ubuntu-se
rver-snapshot-23-sep-2009-1719.vhd
     1 file renamed

C:\INCOMING>dir

 Volume in drive C is 0-primary      Serial number is 0704:2009
 Directory of  C:\INCOMING\*

09/24/2009  11:08p        <DIR>    .
09/24/2009  11:08p        <DIR>    ..
09/24/2009  10:20p        <DIR>    TMP
09/22/2009   8:39p            512  LINUX.BIN
09/24/2009   8:42p          6,891  MAKE-VIDEO-LINKS-SCRIPT
09/23/2009   5:19p  4,009,549,824  [COLOR="Blue"]**ubuntu-server-snapshot-23-sep-2009-1719.vhd**[/COLOR]
09/22/2009   8:23p            512  XP-BOOT.BIN
  4,009,557,739 bytes in 4 files and 3 dirs    4,009,566,208 bytes allocated
474,984,177,664 bytes free

```


...and these are the 4NT scripts that do it:

```

@echo off
REM does "lower"
for %i in (%@if[%# eq 0,*,%$]) *ren "%i" %@lower["%i"]

@echo off
REM does "upper"
for %i in (%@if[%# eq 0,*,%$]) *ren "%i" %@upper["%i"]

```


Now, since 4NT is in many ways inspired by UNIX / Linux and console mode, I figure it's pretty simple to replicate this action with a BASH script.

I tried to do it myself with the "tr" command inside a BASH script, using "for f in $FILES".... blah blah... and couldn't get it to work right.

So, before I tear ALL my hair out... anyone know if I can do this and, if so, how?

Thank you in advance!!

-- Roger

---

### Post by falconindy on 2009-09-24
Someone might have a better way to do this, but....

upper.sh
```
#! /bin/bash
if [[ -z $1 ]]; then
    for FILE in `find -maxdepth 1 -type f`; do
        mv $FILE `echo $FILE | tr "[:lower:]" "[:upper:]"`
    done
else
    mv $1 `echo $1 | tr "[:lower:]" "[:upper:]"`
fi
```lower.sh
```
#! /bin/bash
if [[ -z $1 ]]; then
    for FILE in `find -maxdepth 1 -type f`; do
        mv $FILE `echo $FILE | tr "[:upper:]" "[:lower:]"`
    done
else
    mv $1 `echo $1 | tr "[:upper:]" "[:lower:]"`
fi
```Accomplishes what you're looking for. Actually, I'm **sure** there's a better way than this to do it if it's only a single line in Windows. However, I'm going to bed.

---

### Post by Krupski on 2009-09-24
> **falconindy said:**
> Someone might have a better way to do this, but....

upper.sh
```
#! /bin/bash
if [[ -z $1 ]]; then
    for FILE in `find -maxdepth 1 -type f`; do
        mv $FILE `echo $FILE | tr "[:lower:]" "[:upper:]"`
    done
else
    mv $1 `echo $1 | tr "[:lower:]" "[:upper:]"`
fi
```lower.sh
```
#! /bin/bash
if [[ -z $1 ]]; then
    for FILE in `find -maxdepth 1 -type f`; do
        mv $FILE `echo $FILE | tr "[:upper:]" "[:lower:]"`
    done
else
    mv $1 `echo $1 | tr "[:upper:]" "[:lower:]"`
fi
```Accomplishes what you're looking for. Actually, I'm **sure** there's a better way than this to do it if it's only a single line in Windows. However, I'm going to bed.

Awesome. Thank you! This gives me a good head start.

I might end up needing to use a temp file and some way to preserve permissions as the "case changed" file is created as 0644 no matter what it originally was, and I get a "'name' and 'name' are the same file" error... but at least now I've got something to work with.


Thank you!

-- Roger

---

### Post by bigboy_pdb on 2009-09-24
To shorten it you can use the "rename" command instead (ie. 'rename "y/a-z/A-Z/" *' to rename all files using upper case characters).

For example, the code for upper would be:

*upper.sh*
```

#! /bin/bash

# I changed the line below so errors are displayed when the file doesn't exist
if [[ "$1" != '' ]]; then
    rename 'y/a-z/A-Z/' "$1"
else
    rename 'y/a-z/A-Z/' *
fi

```

I'm not certain if there's a way to shorten that any more.

---

### Post by geirha on 2009-09-25
First off, scripting is a type of programming, so this is definitely the right place to ask.

Code like this:
```
for file in `find -maxdepth 1 -type f`;
```
...is bad, as it will break for filenames containing spaces and certain other special characters. Use the shell's glob patterns (*, *.mp3, foo?.bar) instead. Secondly, parameter expansions (like $foo, $1, $@) should in most cases be quoted in soft-quotes ("") for the same reason. 

bigboy_pdb's solution does it right, and is safe to use. Big plus to bigboy_pdb :)

I recommend this guide for learning bash: [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide). It's the only guide I've seen that also teaches good practice in shell scripting.

---

### Post by falconindy on 2009-09-25
> **geirha said:**
> bigboy_pdb's solution does it right, and is safe to use. Big plus to bigboy_pdb :)
Rename won't discriminate between files and directories. Not sure if that was a requirement of the OP.

---

### Post by Krupski on 2009-09-25
> **falconindy said:**
> Rename won't discriminate between files and directories. Not sure if that was a requirement of the OP.

A big THANK YOU to all (especially **bigboy_pdb**) [IMG]http://www.gunsnet.net/forums/images/smilies/xyxthumbs.gif[/IMG]

Believe it or not, I wasn't aware of the "rename" command! I always used "mv"!

By the way, my original (Windows console) scripts did NOT operate on directory names... unless I specified the directory name explicitly.

I don't know why it works that way... since there's no test in the Windows script to distinguish between files and directories... they just "happen" to work that way.

It won't be a problem if directory names get renamed since 99% of the time I'll be using this code in a larger script that takes Windows/DOS files (with CR/LF endings and uppercase names) and "fix" them to lowercase, LF only UNIX style files and they will be in their own directory anyway.

I do this because I'm always working on C and 68HC11 assembler code in both Linux and Windows console mode and I need to "sync" my work between Windows and Linux.

If there IS a simple way to make the script ignore directories unless explicitly named though... I would be interested to see how to do it.

Thanks again to all!

-- Roger

---

### Post by Krupski on 2009-09-25
> **geirha said:**
> I recommend this guide for learning bash: [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide). It's the only guide I've seen that also teaches good practice in shell scripting.

I'll check that out. Thanks!

-- Roger

---

### Post by bigboy_pdb on 2009-09-25
Sorry, I was writing this post before you responded, Krupski, but I wasn't able to submit it until now.

> **falconindy said:**
> Rename won't discriminate between files and directories. Not sure if that was a requirement of the OP.

You're right. I checked the output and noticed that it doesn't.

There's also another problem. The script doesn't take in more than one file as a parameter. The following code fixes these problems and is shorter:

*upper.sh*
```

#! /bin/bash
find "$@" -mindepth 0 -maxdepth 1 -print0 -type f | xargs -0 rename 'y/a-z/A-Z/'

```

For 'lower.sh', just swap 'a-z' with 'A-Z'. Also, you can name the scripts 'upper' and 'lower'. You'd need to use the command 'chmod 755 upper lower' to make them executable and then you can place them in a bin directory, such as "/home/USER/bin", (or another directory that's within the PATH variable) so that they can be used from any directory.

I should also explain at least some of what's going on with the code.

"$@" (with the double quotes around it) is the same as having all the arguments that are passed to the script in double quotes. For example, for 'upper a b c', "$@" is the same as ' "a" "b" "c" '.

xargs processes all input as arguments for another command. For example, 'echo "a b c" | xargs rm' (or 'xargs rm <<< 'a b c') is the same as the command 'rm a b c'.

The option '-print0', for the find command, causes file names to be separated by null characters (which are not allowed in file names). The '-0' argument in xargs indicates that input is to be split at null characters. In other words, files are being sent from find to xargs using the null character as a file name separator.

For the find command, depth 0 refers to the arguments and depth 1 refers to the base directory from which the script was called. When no arguments are specified, all the file names in the base directory are printed. When arguments are specified, only the files that are found and listed as arguments are printed.

You can find more information about the "find" and "xargs" command using the "man" command (ie. 'man find' and 'man xargs').

Thanks falconindy for your responses. It was late when I read the post and I hadn't understood what was being asked properly. Without your posts, I would have wasted my time doing something that's incorrect.

---

### Post by bigboy_pdb on 2009-09-25
With respect to learning more about bash scripting, there's a couple of other guides that you can use as well. The "Advanced Bash-Scripting Guide" and the "Bash Guide for Beginners" can be found on the ["The Linux Documentation Project" website in the "guides" section]("http://tldp.org/guides.html").

You may also want to look at the "bash" manual (which can be accessed using 'man bash'). Also, when you're learning commands, you'll probably need to look at some of their manuals as well (which can be seen by using 'man COMMAND').

Furthermore, if you're looking for a command that is related to a concept, one way to search for it is to use the "apropos" command. For example, if you're looking for a command for viewing TCP packets that are coming through a networking interface, you can use 'apropos tcp' to see commands that are related to the TCP protocol.

---

### Post by Krupski on 2009-09-25
> **bigboy_pdb said:**
> The following code fixes these problems and is shorter:


Thank you again! That works perfectly. And thanks for the descriptions of how it works. The scripts now do *exactly* what I wanted!

Thanks again!

-- Roger

---

