---
title: "Script to remove spaces from names of files"
date: 2010-05-24
forum: Programming Talk
---

### Post by wannabegeek on 2010-05-24
Hi all,

I have been learning some shell script basics on and off this year.

I think it would be great to have a script which deletes the spaces (multiple)in a file name.

Would anyone care to share such a script with me so that I may copy it and try to 
understand the  commands ?

I know that I'll need a loop, with sed and a variable to store the name as a string.
I don't know how to save a string as a variable from stdin.

I know that I could look all this up over the course of a few days, but it would be nice to 
have a little tutoring if someone is interested.

thanks,
wbg

---

### Post by MadCow108 on 2010-05-24
```

for file in *; do #loop on all in folder
  if [ ! -d "$file" ]; then #skip directories
    newfilename=`echo "$file" | sed -e "s/ //g"`; #remove spaces
    mv "$file" "$newfilename" 2>/dev/null; #rename, and ignore error messages on same file by redirecting stderr to garbage drive
  fi
done

```

---

### Post by BoneKracker on 2010-05-24
Here is your script:
```
find -name '* *' -execdir rename " " "" {} +
```

This has the advantage of not performing un-needed operations on files not having spaces in their names.  Also, this works recursively (not merely on files in the present directory, but files within its subdirectories as well).

---

### Post by wannabegeek on 2010-05-25
hi guys
 
thanks a lot for the scripts....

I tried bonekracker's first because it is so short...

didn't get it to work however....is   -execdir   the same as exec but for the entire dir ?

will play around with both today....didn't know find was so powerful...unix  

wbg

---

### Post by geirha on 2010-05-25
```
#!/bin/bash
for file in ./*" "*; do
  echo mv -v "$file" "${file// }"
done

```

The reason the rename didn't work is because Ubuntu has the perl rename command (there are several rename commands, with different syntaxes). The perl rename uses perl-regex:
```
rename -n 's/ //g' ./*" "*
```

More examples here: [http://mywiki.wooledge.org/BashFAQ/030](http://mywiki.wooledge.org/BashFAQ/030)

---

### Post by BoneKracker on 2010-05-25
It worked for me.  Maybe I typo'd something or used an invalid test case.

Anyway, yes, the -execdir option will execute the command in braces, on any file it finds, but it will first 'cd' to the directory in order to execute the command.  (To be honest, now that I think of it, I'm not sure that's necessary in this case, but I don't suppose it can be harmful.)

See the man page for 'find'.  'Find' is a very powerful tool, like sed and awk, which many people go years without taking the trouble to learn, because it is a PITA to remember all the various options.  There are cases where it is exactly what you want, though (when you are selecting files based on attributes other than their textual content).

Start with a test directory with a handful of bogus files in it (some with spaces in their names), and then create one or two other test directories within it (with files in them, named similarly).  (I.e., recreate a simple example of the scenario you are trying to make work.)  Make a recursive copy of the whole tree so you can perform multiple tests without renaming files.  Then, referring to the man page, fiddle around with the 'find' command I provided until you get it to do what you want.  As I say, it worked for me (given that simple test case).

Likewise, you can rename files in any number of ways, but batch-renaming files based on a simple pattern change is specifically what 'rename' is for.

---

### Post by geirha on 2010-05-25
BoneKracker, you probably have this rename command on your system: [http://linux.die.net/man/1/rename](http://linux.die.net/man/1/rename)

On Ubuntu, the rename command installed by default is
[http://manpages.ubuntu.com/manpages/lucid/en/man1/prename.1.html](http://manpages.ubuntu.com/manpages/lucid/en/man1/prename.1.html)

---

### Post by BoneKracker on 2010-05-25
> **geirha said:**
> ```
The reason the rename didn't work is because Ubuntu has the perl rename command (there are several rename commands, with different syntaxes). The perl rename uses perl-regex

Ah, that makes sense. So, if we use the more simple "-exec" instead of "-execdir", which really isn't needed, and if we use rename with perl regular expression, then I suppose it would be:[CODE]find -name '* *' -exec rename -n 's/ //g' {} +
```

---

### Post by BoneKracker on 2010-05-25
> **geirha said:**
> BoneKracker, you probably have this rename command on your system: [http://linux.die.net/man/1/rename](http://linux.die.net/man/1/rename)

On Ubuntu, the rename command installed by default is
[http://manpages.ubuntu.com/manpages/lucid/en/man1/prename.1.html](http://manpages.ubuntu.com/manpages/lucid/en/man1/prename.1.html)
Yes, that's right.  Thank you for pointing that out. :)

Does the revised command look okay to you?
```
find -name '* *' -exec rename -n 's/ //g' {} +
```

---

### Post by geirha on 2010-05-25
Actually the -execdir is needed. Otherwise you risk renaming a directory before all the files inside it are renamed. -depth should also be used for the same reason.

```
find . -depth -name '* *' -execdir rename -n 's/ //g' {} +
```

Also, check what rename's -n option does.

---

### Post by BoneKracker on 2010-05-25
> **geirha said:**
> Actually the -execdir is needed. Otherwise you risk renaming a directory before all the files inside it are renamed. -depth should also be used for the same reason.

```
find . -depth -name '* *' -execdir rename -n 's/ //g' {} +
```

Also, check what rename's -n option does.

Okay, I've looked at the man page you guys have.  So, when you're actually ready to run it for real, you'd remove the -n.

Good point about "-depth", but you do you really need both "-depth" and "-execdir"?  Won't "-depth" alone avoid the path resolution conflict (renaming a directory before its files)? 

I assume the dot is the rootpath for the command.  That would be presumed to be "." by default, wouldn't it?

---

### Post by geirha on 2010-05-25
> **BoneKracker said:**
> Okay, I've looked at the man page you guys have.  So, when you're actually ready to run it for real, you'd remove the -n.

Good point about "-depth", but you do you really need both "-depth" and "-execdir"?  Won't "-depth" alone avoid the path resolution conflict (renaming a directory before its files)? 


-execdir without -depth:
Say you find «./a b/» and «./a b/c d». Rename will rename «./a b» to «./ab», then it will try to rename «./a b/c d/» to «./ab/cd», but at that point, «./a b» no longer exists.

-depth and -exec + instead of -execdir +
Say you find the same as above. Since -depth is on, «./a b/c d» comes before «./a b/». So now you risk it trying to rename «./a b/c d» to «./ab/cd» before it renames «./a b» to «./ab».

> **BoneKracker said:**
> 
I assume the dot is the rootpath for the command.  That would be presumed to be "." by default, wouldn't it?

It would, at least with GNU find. Other implementations of find may require a path there, so it's a good practice to always provide it.

[http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind)

---

### Post by BoneKracker on 2010-05-25
My question was, "wouldn't 'depth' alone be enough...?"  (not execdir alone).

My point: because the find returns the full path, the rename command does not need to be executed in the actual subdirectory.  Regardless of whether 'execdir' is used (instead of 'exec'), 'depth' has already taken care of the path issue (the subdirectories will be worked before the directories are renamed).

---

### Post by kaibob on 2010-05-25
The OP stated that that he wanted to remove spaces from file names. That being the case, the '-type f" option should be considered, as it prevents unwanted changes to directory names.

---

### Post by BoneKracker on 2010-05-25
> **kaibob said:**
> The OP stated that that he wanted to remove spaces from file names. That being the case, the '-type f" option should be considered, as it prevents unwanted changes to directory names.

Valid point.  And -writable might be advisable too, if there is a chance the directory contains files for which the user does not have write permissions.

---

### Post by geirha on 2010-05-26
```
$ rename -v 's/ //g' "a b/c d" "a b"
Can't rename a b/c d ab/cd: No such file or directory
a b renamed as ab

```

directories are files too btw.

---

### Post by BoneKracker on 2010-05-26
Everything in linux is a "file".  But not everything is a "regular file" (which is what -type f means).  The -type f argument means the file is not a device, socket symlink, _directory_, etc..```
~/test $ ls -R
.:
a b

./a b:
c d
~/test $ find -type f -name '* *' -execdir rename ' ' '' {} +
~/test $ ls -R
.:
a b

./a b:
cd

```

---

### Post by geirha on 2010-05-26
```

$ find
.
./a b
./a b/c d
$ find . -depth -type f -name '* *' -exec rename -v 's/ //g' {} +
Can't rename ./a b/c d ./ab/cd: No such file or directory

```

Right, so the rename you have only tries to rename the basename apparently, while prename tries to rename the whole path.

---

### Post by BoneKracker on 2010-05-26
> **geirha said:**
> ```

$ find
.
./a b
./a b/c d
$ find . -depth -type f -name '* *' -exec rename -v 's/ //g' {} +
Can't rename ./a b/c d ./ab/cd: No such file or directory

```

Right, so the rename you have only tries to rename the basename apparently, while prename tries to rename the whole path.

No.

Here that is without '-type f':
```
~/test $ find -depth -name '* *' -exec rename ' ' '' {} +
~/test $ ls -R
.:
ab

./ab:
cd
```


Here it is _with_ -type -f, but without -depth:
```
brendlerjg@typhoon ~/test $ find -type f -name '* *' -exec rename ' ' '' {} +
rename: renaming ./a b/c d to ./ab/c d failed: No such file or directory
```

Here it is with '-type f', without '-depth', but with '-execdir' (as I said earlier, either '-depth' or '-execdir' will resolve the path conflict, both are not necessary in this case):
```
~/test $ ls -R
.:
a b

./a b:
c d
~/test $ find -type f -name '* *' -execdir rename ' ' '' {} +
~/test $ ls -R
.:
a b

./a b:
cd

```

---

### Post by geirha on 2010-05-26
> **BoneKracker said:**
> 
Here it is with '-type f', without '-depth', but with '-execdir' (as I said earlier, either '-depth' or '-execdir' will resolve the path conflict, both are not necessary in this case):


Indeed, but with the perl rename, they are necessary because it renames the whole path, not just the basename as the rename on your system does.

---

### Post by wannabegeek on 2010-05-26
this is kickass....I need more time to shift through this...

I just got a huge jumble of music  and misc crap from a friend with a good music collection all in one 'Back Up"  file.....

I need to remove spaces, then sort into directories with grep and xargs  I think...

---

### Post by geirha on 2010-05-26
I don't understand why you need to remove the spaces for that..?

---

### Post by BoneKracker on 2010-05-26
> **geirha said:**
> Indeed, but with the perl rename, they are necessary because it renames the whole path, not just the basename as the rename on your system does.

Oh, I think I see what you mean.  It processes the entire path as a "file".  Okay, that's just different behavior.

I thought you meant the 'rename' from util-linux-ng was not renaming the directory.

Sorry, I'm getting tired.

---

### Post by BoneKracker on 2010-05-26
> **geirha said:**
> I don't understand why you need to remove the spaces for that..?

Because "Otis\ Redding\ -\ Ain't\ No\ Sunshine\ When\ She's\ Gone.mp3" is aesthetically unappealing to him?

---

### Post by geirha on 2010-05-26
Just put quotes around it and the backslashes are not needed.

---

### Post by wannabegeek on 2010-05-26
hi folks..
> Because "Otis\ Redding\ -\ Ain't\ No\ Sunshine\ When\ She's\ Gone.mp3" is aesthetically unappealing to him?this is true...even if quotes fix it

I spent time tonight working with find tonight and the options -depth -exec
...really cool program

thanks to [geirha]("http://ubuntuforums.org/member.php?u=243323") and Bonekracker I will be reading these posts for a while...

---

### Post by geirha on 2010-05-26
Do not forget -depth, and the reason nothing gets renamed is because of the -n argument to rename, which means dry-run; just write what would've been done, but don't actually do it.

```
man find
man rename
```

```
find . -depth -name '* *' -execdir rename -v 's/ //g' {} +
```

The substitution command s/regex/replacement/g replaces all matches of regex with replacement. In this case, the regex is just a space, and the replacement is the empty string. The g at the end makes it do it for all matches on the line; without it, only the first space will be replaced.

It's more common to replace spaces with underscores btw. If you want to do that, change the substitution to 's/ /_/g'.

---

### Post by BoneKracker on 2010-05-26
geirha, you explain things well, in a clear, concise manner.  You ought to write documentation.

---

### Post by kaibob on 2010-05-26
> **kaibob said:**
> The OP stated that that he wanted to remove spaces from file names. That being the case, the '-type f" option should be considered, as it prevents unwanted changes to directory names.

> **geirha said:**
> Indeed, but with the perl rename, they are necessary because it renames the whole path, not just the basename as the rename on your system does.

Thanks geirha. I had forgotten that prename removes spaces from directories in the path. Perhaps something similar to the following would be better:

```
#!/bin/bash

find /target/directory -type f | while read -r file ; do
   dir="${file%/*}"
   base="${file##*/}"
   mv "$file" "${dir}/${base// /}"
done
```

---

### Post by wannabegeek on 2010-05-26
I understand now...

I have used option -n for rsync, and appreciate it fully...

Thanks so much for a very clear and complete treatment of a simple question, which turned out to be a
real learning experience.

having a teacher is a gift, it really cuts the learning curve down...Although I have stayed up all night getting weird custom stuff to work too...that's par for the course I suppose

thanks again
wbg

---

### Post by kaibob on 2010-05-26
> **BoneKracker said:**
> geirha, you explain things well, in a clear, concise manner.  You ought to write documentation.
Geirha has assisted me with a number of somewhat convoluted bash issues, and I agree that his help is always excellent. In one case, I had been struggling with a shell script for longer than I care to admit and decided to ask in this forum for help. Within 15 minutes or so, geirha posted a solution that worked great.

---

### Post by wannabegeek on 2010-05-28
Hi everyone,

So I used this nice script to convert some files. I found a cool blog for audio scripting.
[http://ocaoimh.ie/how-to-convert-from-wma-to-mp3/](http://ocaoimh.ie/how-to-convert-from-wma-to-mp3/) 

check out how he removes the spaces...
Plus I'm curious about the use of the  **for  **loop. I have seen this usage but only 
familiar with the C and C++ style loop syntax.

Anyone feel like explaining ?
cheers and tia,
wbg
[PHP]
#!/bin/bash 
 
current_directory=$( pwd ) 
 
#remove spaces 
for i in *.wma; do mv "$i" `echo $i | tr ' ' '_'`; done 
 
#remove uppercase 
for i in *.[Ww][Mm][Aa]; do mv "$i" `echo $i | tr '[A-Z]' '[a-z]'`; done 
 
#Rip with Mplayer / encode with LAME 
for i in *.wma ; do mplayer -vo null -vc dummy -af resample=44100 -ao pcm -waveheader $i && lame -m s audiodump.wav -o $i; done 
 
#convert file names 
for i in *.wma; do mv "$i" "`basename "$i" .wma`.mp3"; done 
 
rm audiodump.wav
[/PHP]

---

### Post by kaibob on 2010-05-28
> **wannabegeek said:**
> Hi everyone,

So I used this nice script to convert some files. I found a cool blog for audio scripting.
[http://ocaoimh.ie/how-to-convert-from-wma-to-mp3/](http://ocaoimh.ie/how-to-convert-from-wma-to-mp3/) 

check out how he removes the spaces...
There seems to be some agreement that it's best to avoid the use of external commands--such as tr and sed--when the same task can be done with bash. For example, bash can be used to remove spaces and to convert case:

> $ file="file with spaces.txt" ; echo "${file// /}"
filewithspaces.txt

$ file="FILE with UPPERCASE.txt" ; echo "${file,,}"
file with uppercase.txt

I don't understand the issue with the for loop and can't help there. 

Anyways, I'm glad you got things working as you want.

---

