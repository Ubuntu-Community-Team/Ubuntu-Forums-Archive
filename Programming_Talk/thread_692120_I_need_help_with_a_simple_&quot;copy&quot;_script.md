---
title: "I need help with a simple &quot;copy&quot; script"
date: 2008-02-09
forum: Programming Talk
---

### Post by Sciamano on 2008-02-09
Hi all,
I'm no programmer at all, and even though I tried using bash commands, I can't seem to find the right ones.

Basically I need to "scan" a folder and all its subfolders, and make copies (which must be called cover.jpg) of all the files called "Album Art.jpg"
I can't simply rename them (that would be easy with KRename), I have to make copies of them.

How do I do that? Any help appreciated!

Thanks,
Luca

---

### Post by ghostdog74 on 2008-02-09
```

find /path -name "cover.jpg" -exec cp "{}" "Album art.jpg" \;

```

---

### Post by Sciamano on 2008-02-09
Thanks ghostdog, just two questions: can I run this from the command line?

Also, shouldn't "cover.jpg" and "Album Art.jpg" be switched in their position?
I have to copy "Album Art.jpg" to a new file called "cover.jpg".

Thanks

---

### Post by ghostdog74 on 2008-02-09
> **Sciamano said:**
> Thanks ghostdog, just two questions: can I run this from the command line?

Instead of giving you the answer, i would like you to try it and enjoy the process

> 
Also, shouldn't "cover.jpg" and "Album Art.jpg" be switched in their position?
I have to copy "Album Art.jpg" to a new file called "cover.jpg".
Thanks
likewise.  you can rearrange the order and find out. Its more fun this way than telling you the answer :)

---

### Post by Sciamano on 2008-02-09
I just don't want to mess anything up, that's all...

---

### Post by Sciamano on 2008-02-10
Well, I tried both, and it did not work at all.
None produced any files...

---

### Post by Sciamano on 2008-02-11
up! :)
Please help me! :-P

---

### Post by ghostdog74 on 2008-02-11
ever wondered how people's going to help you without more info like how you execute the commands , error messages etc besides  just "not working at all" ?

---

### Post by NovaAesa on 2008-02-11
Methinks maybe you need to replace 'path' in the command with the actual path that you are wanting.

Just have a look at the output of find --help:
```

ps@inspiron:~$ find --help
Usage: find [path...] [expression]

default path is the current directory; default expression is -print
expression may consist of: operators, options, tests, and actions:

operators (decreasing precedence; -and is implicit where no others are given):
      ( EXPR )   ! EXPR   -not EXPR   EXPR1 -a EXPR2   EXPR1 -and EXPR2
      EXPR1 -o EXPR2   EXPR1 -or EXPR2   EXPR1 , EXPR2

positional options (always true): -daystart -follow -regextype

normal options (always true, specified before other expressions):
      -depth --help -maxdepth LEVELS -mindepth LEVELS -mount -noleaf
      --version -xdev -ignore_readdir_race -noignore_readdir_race

tests (N can be +N or -N or N): -amin N -anewer FILE -atime N -cmin N
      -cnewer FILE -ctime N -empty -false -fstype TYPE -gid N -group NAME
      -ilname PATTERN -iname PATTERN -inum N -iwholename PATTERN -iregex PATTERN
      -links N -lname PATTERN -mmin N -mtime N -name PATTERN -newer FILE
      -nouser -nogroup -path PATTERN -perm [+-]MODE -regex PATTERN
      -wholename PATTERN -size N[bcwkMG] -true -type [bcdpflsD] -uid N
      -used N -user NAME -xtype [bcdpfls]

actions: -delete -print0 -printf FORMAT -fprintf FILE FORMAT -print 
      -fprint0 FILE -fprint FILE -ls -fls FILE -prune -quit
      -exec COMMAND ; -exec COMMAND {} + -ok COMMAND ;
      -execdir COMMAND ; -execdir COMMAND {} + -okdir COMMAND ;

Report (and track progress on fixing) bugs via the findutils bug-reporting
page at http://savannah.gnu.org/ or, if you have no web access, by sending
email to <bug-findutils@gnu.org>.
ps@inspiron:~$ 

```

Maybe try something more like this:
```
find /home/uname/Music -name "cover.jpg" -exec cp "{}" "Album art.jpg" \;
```

EDIT: I don't exactly have much experience with CLI or bash, so maybe I'm on the wrong path here. Something to think about and try anyway. That's the best way of learning - trying new things.

---

### Post by NovaAesa on 2008-02-11
oops, i hit quote instead of edit on my previous post.

---

### Post by Sciamano on 2008-02-11
@NovaAesa: Thanks for the suggestion, but of course I've put the right path instead of "/path". I'm not a programmer but I can go that far :)
I've also read the help pages for the command 'find', but to no avail. :(

@ghostdog74: I wrote the commands in a terminal shell, and I can't report any error messages because there were none. It's simply like nothing happened.

I tried both of the following:
```
find /media/musica/Area\ Musica -name "cover.jpg" -exec cp "{}" "Album Art.jpg" \;
```

```
find /media/musica/Area\ Musica -name "Album Art.jpg" -exec cp "{}" "cover.jpg" \;
```

I also tried with quoting the directory, since it contains a space:
```
find "/media/musica/Area Musica" -name "Album Art.jpg" -exec cp "{}" "cover.jpg" \;
```
(and also the same as above, but with "Album Art.jpg" and "cover.jpg" switched)

Here is how the terminal looks after I give the command. I can hear the disk "running", but simply there is no output in the terminal (nor any "cover.jpg" created anywhere):
```
luca@desktop:~$ find /media/musica/Area\ Musica -name "cover.jpg" -exec cp "{}" "Album Art.jpg" \;
luca@desktop:~$
```

You probably think I'm lazy, but I'm not. I'm more than willing to learn, but in order to do that I'd need someone to teach me ;)

Thanks

---

### Post by amingv on 2008-02-11
[COLOR="Red"]**PYTHON APPRENTICE; WATCH OUT FOR WIDE TURNS!!!**[/COLOR]

That said, I came up with a little script that worked under my testing. It shouldn't be of any harm, but I suggest you backup your files just in case...
The script assumes you have write access to the directory; at the top of the script are 3 self explanatory variables that you must modify to match your situation.

Here it is:

[PHP]#!/usr/bin/python
#Filename: rsrch.py

import os
import shutil as sh

path = '/media/musica/Area Musica'
preName = 'cover.jpg'
postName = 'Album Art.jpg'

tree = os.walk(path)

for root, dirs, files in tree:
    os.chdir(root)
    for sfile in files:
	    if sfile == preName:
		    sh.copy(sfile, postName)
[/PHP]

[ATTACH]59394[/ATTACH]

<edit>
I just re-read the OP, I've got preName and postName backwards, just change the values from one to the other...
</edit>

---

### Post by Sciamano on 2008-02-11
Thanks amingv, it definitely works. :)

This solves my contingent problem (copying all "Album Art.jpg" files to "cover.jpg" files), but it does not solve my thirst for knowledge.

I really would love to learn bash scripting, so I'd like to make such a script using that method.
I've been reading the [Advanced Bash Scripting guide]("http://tldp.org/LDP/abs/html/"), but it looks too advanced to me :)
Anyone has any suggestions regarding a good starting guide? Something like "Bash Scripting for idiots" would be nice :-)

---

### Post by amingv on 2008-02-11
I am very glad it helped :)

> **Sciamano said:**
> I just don't want to mess anything up, that's all...

As for your thirst of knowledge, this will not help at all. When experimenting, sometimes... stuff happens...

I know close to nothing about shell scripting, but (from the posts I've read) ghostdog seems quite skilled with it, for this reason I suppose his version works, somehow...
I would definitely go for his advice on experimenting, it is the best way to learn (of course this doesn't mean going careless).

As for a "simpler" guide [http://www.linuxcommand.org/](http://www.linuxcommand.org/) has been recommended before. I'm sure some of the stickies will help you as well.

---

### Post by Sciamano on 2008-02-11
I'm sure ghostdog knows what he's talking about. I'm definitely not doubting about anyone's abilities here... it's only that when I tried his code, it did not produce anything.
It might need to be retouched, but I have no idea of where and how. :-P

Thanks for the link, I'll give it a try. It looks easier than the Advanced Guide.

---

### Post by ghostdog74 on 2008-02-11
@Sciamano
```

find /path -type f -name "cover.jpg" -printf "cp '%p' '%h/Album art.jpg'\n" | sh

```
check the man page of find (GNU) for the meaning of %p and %h  for the -printf option. To see what's going on, just run the find command without the |sh .
As for the previous solution i posted, all cover.jpg found in subdirectories will be copied to the current directory where you run the command, that's why you saw nothing.
As for learning resource, you can go to the  5th link in my sig.

---

### Post by Sciamano on 2008-02-13
Thanks ghostdog74, this is what I meant, and it now works.
Thanks also for the link suggestion. I'll do my best to learn from there, and from the site amingv suggested too.

---

### Post by shawnhcorey on 2008-02-13
You should play around with `find` so you know exactly what's in your directories.

This will list all files with extensions JPG or JPEG:
```
find /path -iname \*.jpg -o -iname \*.jpeg
```

I think the problem is the case of the file.  In find, -name is case-sensitive, -iname is not.  Try:
```
find /path -iname 'album*art.jp*g'
```
and see what comes out.

---

### Post by Sciamano on 2008-02-13
Thanks shawn, but the [new code]("http://ubuntuforums.org/showpost.php?p=4313647&postcount=16") posted by ghostdog works perfectly.
Anyway, thanks for pointing out the differences between -name and -iname, it might be useful to me in the future.

---

