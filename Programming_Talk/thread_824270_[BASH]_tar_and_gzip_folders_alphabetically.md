---
title: "[BASH] tar and gzip folders alphabetically"
date: 2008-06-09
forum: Programming Talk
---

### Post by altonbr on 2008-06-09
Right now I can tar (then gzip) all folders that start with 'a' or 'A'.

```
tar -cf a.tar a* A* &&
gzip -c a.tar > a.tar.gz &&
rm a.tar
```

How can I loop this so it checks all letters and numbers (and possibly some characters) while remaining case-insensitive?

The best I can think of is an array, but we need 'a' and 'A' to be on the same line, but '1' should be by itself and since a multi-dimensional array is impossible in BASH (or is it?), I'm at a loss...

---

### Post by dwhitney67 on 2008-06-09
Doesn't the "ls" command sort the listing?  If not, then rely on the "sort" command.

```
#!/bin/sh

for file in `ls`
do
        # check if the file is a directory (folder)
        if [ -d $file ]
        then
                tar czf $file.tar.gz $file
        fi
done
```

P.S.  If you need to use the "sort" command, then replace "ls" above with "ls | sort".

---

### Post by altonbr on 2008-06-10
Well, that's actually exactly what I had before, but I need to make an archive for each letter of the alphabet, hense 'a*' and 'A*'. How can I case-insensitively only return directories that start with 'a', then 'b', then 'c', all the way down to 'z', including numbers?

---

### Post by Phenax on 2008-06-10
here is how to do case-insensitive globbing:
> 
$ ls
a  aa  Aa  AaaaaaAAAaaAAAaa
$ shopt -s nocaseglob
$ ls a*
a  aa  Aa  AaaaaaAAAaaAAAaa
$ shopt -u nocaseglob
$ ls a*
a  aa
I can't help you more as I've got to wake up in six hours so I'm hitting the sack, here are some resources:
[http://wooledge.org:8000/BashFAQ](http://wooledge.org:8000/BashFAQ) (best faq has a ton of good stuff)
#bash irc.freenode.net (very good support channel)

---

### Post by dwhitney67 on 2008-06-10
I reread your initial requirements, and now I understand what you are trying to accomplish.  My Bash skills are not up to par to solve this problem.

Perhaps the following can help you get onto the right path:
```
#!/bin/bash

for char in [aA-zZ,0-9]
do
        echo $char
done
```
Unfortunately I do not have any idea on how to group the 'a' directories with the 'A' ones, test for their existence, and then build a list to use with the tar command.

---

### Post by dwhitney67 on 2008-06-10
Ok, this is probably lame, but I believe it will work:
```

#!/bin/bash

for char in [a-z,0-9]
do
        DIRS="$char*"

        case $char in
            [0-9]) ;;
            [a])   DIRS="$DIRS A*";;
            [b])   DIRS="$DIRS B*";;
            [c])   DIRS="$DIRS C*";;
            [d])   DIRS="$DIRS D*";;
            [e])   DIRS="$DIRS E*";;
            # Add additional letters here
            [y])   DIRS="$DIRS Y*";;
            [z])   DIRS="$DIRS Z*";;
            *)     DIRS="IGNORE";;
        esac


        if [ "$DIRS" != "IGNORE" ]
        then
                TARBALL=`echo $DIRS | cut -d ' ' -f1`.tar.gz

                echo "Creating $TARBALL..."
                tar czf $TARBALL --ignore-failed-read $DIRS 2> /dev/null
        fi
done

```

---

### Post by ghostdog74 on 2008-06-10
```

for c in {a..z}
do
 cmd="tar cvf ${c}.tar ${c}*"
 echo $cmd
done 
for files in {A..Z}*
do
 lower=$(echo $files | tr '[A-Z]' '[a-z]')
 first=${lower:0:1}
 cmd="tar cv -A ${first}.tar $files*"
 echo $cmd
done

```

---

### Post by altonbr on 2008-06-10
As always, ghostdog74 shows up with an excellent answer :P

Here's what I get returned
> ./test2.sh 
tar cvf a.tar aab ab ahdt
tar cvf b.tar baaa bAabsdf bse
tar cvf c.tar c*
tar cvf d.tar d*
tar cvf e.tar e*
tar cvf f.tar f*
tar cvf g.tar g*
tar cvf h.tar h*
tar cvf i.tar i*
tar cvf j.tar j*
tar cvf k.tar keep.sh
tar cvf l.tar l*
tar cvf m.tar m*
tar cvf n.tar n*
tar cvf o.tar o*
tar cvf p.tar p*
tar cvf q.tar q*
tar cvf r.tar rOGER that! man!90r
tar cvf s.tar s*
tar cvf t.tar test2.sh test.php test.sh
tar cvf u.tar u*
tar cvf v.tar v*
tar cvf w.tar w*
tar cvf x.tar x*
tar cvf y.tar y*
tar cvf z.tar z*
tar cv -A a.tar Aaa
tar cv -A a.tar AAAafsd
tar cv -A b.tar B**
tar cv -A c.tar C**
tar cv -A d.tar D**
tar cv -A e.tar E**
tar cv -A f.tar F**
tar cv -A g.tar G**
tar cv -A h.tar H**
tar cv -A i.tar I**
tar cv -A j.tar J**
tar cv -A k.tar K**
tar cv -A l.tar L**
tar cv -A m.tar M**
tar cv -A n.tar N**
tar cv -A o.tar O**
tar cv -A p.tar P**
tar cv -A q.tar Q**
tar cv -A r.tar R**
tar cv -A s.tar S**
tar cv -A t.tar T**
tar cv -A u.tar U**
tar cv -A v.tar V**
tar cv -A w.tar W**
tar cv -A x.tar X**
tar cv -A y.tar Y**
tar cv -A z.tar Z**


Here's what I ended up writing in PHP as a wrapper to 'find' and 'tar':
[PHP]<?php

/**
 * tar and gzip an entire directory by first letter or number
 * tar_by_letter.php
 * Copyright (C) 2008  Brett Alton <brett.jr.alton@gmail.com>
 *
 * This program is free software: you can redistribute it and/or modify
 * it under the terms of the GNU General Public License as published by
 * the Free Software Foundation, either version 3 of the License, or
 * (at your option) any later version.
 *
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU General Public License for more details.
 *
 * You should have received a copy of the GNU General Public License
 * along with this program.  If not, see <http://www.gnu.org/licenses/>.
 */

// a pre-defined array of characters to use
$needles = array (
					'a','b','c','d','e','f','g','h','i','j','k','l','m',
					'n','o','p','q','r','s','t','u','v','w','x','y','z',
					1,2,3,4,5,6,7,8,9,0
				);

// define the path to search
$path_to_zip = realpath(getcwd()); // current directory

// define the path to save the zip files to
$save_to_path = realpath(getcwd()); // currently the current directory

// go to the folder specified
chdir($path_to_zip);

foreach ($needles as $needle)
{
	// find all files in the currenct directory that match '$needle*'
	$collection = str_replace('./', '', shell_exec('find . -maxdepth 1 -iname \''.$needle.'*\'')); // replace './' with ''
	
	// explode results of 'find; into a PHP array
	$collection_array = explode("\n", $collection);
	
	foreach ($collection_array as $entity)
	{
		// prune non-directories
		if (is_dir($entity) && $entity != $path_to_zip)
		{
			// if the file being analyzed is a directory, add it to the dirs[] array
			$dir_array[] = addcslashes(escapeshellcmd($entity),'! '); // make sure it is command line safe (escape spaces, etc.)
		}
	}

	// if $dir_array exists
	if ($dir_array)
	{
		// implode the PHP array back to a string, just as tar expects
		$dir_list = implode(' ',$dir_array);
	}
	
	// if directories have been found, tar/gzip them
	if ($dir_list)
	{
		shell_exec('tar -czf '.$save_to_path.'/'.$needle.'.tar.gz '.$dir_list);
	}
	
	// destroy known dirs
	unset($dir_array,$dir_list); // just to be sure
}[/PHP]

The only difference really, is that PHP uses find to be case insensitive and doesn't create a tarball if the directory don't exist, but look how much more code I have :S

---

### Post by ghostdog74 on 2008-06-10
you might want to check PEAR for ARchive Tar class (Tar.php?), instead of calling tar from the shell. This makes your code portable to other platforms.

---

### Post by altonbr on 2008-06-10
> **ghostdog74 said:**
> ```

for c in {a..z}
do
 cmd="tar cvf ${c}.tar ${c}*"
 echo $cmd
done 
for files in {A..Z}*
do
 lower=$(echo $files | tr '[A-Z]' '[a-z]')
 first=${lower:0:1}
 cmd="tar cv -A ${first}.tar $files*"
 echo $cmd
done

```

Is there anyway that I can check that teach file/folder ${c}* finds is a directory? Seems a bit more convoluted once I throw that in.
```
if [ -d $c ]; then
fi
```

but what replaces $c? Because above it used ${c}* to check for ALL filenames, whereas this is on an individual basis.

> **ghostdog74 said:**
> you might want to check PEAR for ARchive Tar class (Tar.php?), instead of calling tar from the shell. This makes your code portable to other platforms.

Yeah, that's a great idea, but this script only has to run once, so until I need to run this on a Windows machine, I'll just use shell_exec. But actually, I'm looking to switch to your BASH script over my PHP script, for efficiency sake.

---

### Post by dwhitney67 on 2008-06-10
Why don't you try giving the script I wrote a chance?  (see post #6).  I believe it is efficient enough.

---

### Post by altonbr on 2008-06-10
> **dwhitney67 said:**
> Why don't you try giving the script I wrote a chance?  (see post #6).  I believe it is efficient enough.

I'm trying to figure out how to have more needles (including numbers and other characters) without having to type repeated lines like in yours. ghostdog has the right idea, I'm just not the proficient in BASH yet to modify it.

EDIT:: Yup, this shared environment doesn't support PHP on the command line. Looks like I'm porting to BASH.

---

### Post by altonbr on 2008-06-10
What's the equivalent to PHP's explode() and implode() in BASH?

---

### Post by dwhitney67 on 2008-06-10
> **altonbr said:**
> I'm trying to figure out how to have more needles (including numbers and other characters) without having to type repeated lines like in yours. ghostdog has the right idea, I'm just not the proficient in BASH yet to modify it.

EDIT:: Yup, this shared environment doesn't support PHP on the command line. Looks like I'm porting to BASH.

Ghostdog's version is more compact/readable, however I wasn't impressed that it attempts to create tar-balls (actually, it just sets up the cmd string) for each character from a to z, then A to Z.  What if there isn't a directory commencing with the letter 'c' or 'C'?  It looks to me that the tar command will be executed anyhow.

---

### Post by altonbr on 2008-06-10
> **dwhitney67 said:**
> Ghostdog's version is more compact/readable, however I wasn't impressed that it attempts to create tar-balls (actually, it just sets up the cmd string) for each character from a to z, then A to Z.  What if there isn't a directory commencing with the letter 'c' or 'C'?  It looks to me that the tar command will be executed anyhow.

He just echos what the command would look like, it doesn't actually run.

Here is the script I have so far:
```
md5_file='md5sum'

# if the md5sum file exists
if [ -f $md5_file ]; then
	# delete it
	rm -f $md5_file # don't want duplicates
fi

# loop from a to z
for char in {a..z}; do

	# create tarball name
	tarball=${char}.tar.gz

	# list by letter
	listing=`find . -maxdepth 1 -iname "${char}*" | cut -d '/' -f 2` # cut './' out
	
	# make sure listing has found something!
	if [ "$listing" != "" ]; then
		# create the tarball
		tar -czf ${tarball} ${listing}
	
		#run an md5sum
		md5sum ${tarball} >> ${md5_file} # create md5 checksum and append to file
	fi
done 
```
The problem is that it doesn't escape directory names like "rsf!! fdas sd " (pretend that is one dir) and it can't skip custom files such as 'md5sum' or 'do_not_tar_me.txt'.

Thanks for all your self so far dwhitney and ghosthand :)

---

### Post by ghostdog74 on 2008-06-10
> **altonbr said:**
> ```

...
	listing=`find . -maxdepth 1 -iname "${char}*" | cut -d '/' -f 2` # cut './' out
	 
```


you can try using full path name, instead of ".". eg find /path -name....
anyway, here's another way,since you want to skip directories(not tested for efficiency though)
```

find /fullpath -maxdepth 1 -type f -printf "%f\n" | while  read files
do
    lower=$(echo $files | tr '[A-Z]' '[a-z]')
    first=${lower:0:1}
    if [ -f ${first}.tar ] ;then
        tar cv -A ${first}.tar $files
    else
        tar cv ${first}.tar $files
    fi 
done 

```

---

### Post by geirha on 2008-06-10
Or you could use find|xargs like so:
```

find . -maxdepth 1 -iname "${char}*" -print0 | xargs -0 -r tar zcf ${char}.tar.gz

# If the tarball exist, do the md5sum of it.
[ -f ${char}.tar.gz ] && md5sum ${char}.tar.gz >> ${md5_file}

```
with the -r to xargs, it will only run the tar command if there are any output from the find-command.

---

### Post by ghostdog74 on 2008-06-10
> **altonbr said:**
> What's the equivalent to PHP's explode() and implode() in BASH?

PHP's explode and implode is like split and join of Perl/Python.
you can use  tools like cut/awk or even using bash's IFS that works with fields
```

# split
awk 'BEGIN { string="a,b,c" 
 #split , explode
 m = split(string,s,",")
 print s[1] 
 # join, implode
 for ( i=1;i<=m ;i++){ 
  if ( i==m ){
    printf s[i]
  }else {
    printf "%s,",s[i]
  }
 }
}'

```

---

### Post by altonbr on 2008-06-10
> **geirha said:**
> Or you could use find|xargs like so:
```

find . -maxdepth 1 -iname "${char}*" -print0 | xargs -0 -r tar zcf ${char}.tar.gz

# If the tarball exist, do the md5sum of it.
[ -f ${char}.tar.gz ] && md5sum ${char}.tar.gz >> ${md5_file}

```
with the -r to xargs, it will only run the tar command if there are any output from the find-command.

What about running 'sed' on the 'find' results before piping to 'xargs'?

There are three or four folders I must skip, but I'm having problems with sed:
```
$ echo 'NOoOo!' | sed s/o/0/i
```
> N0oOo!

Why doesn't it replace all of the 'o' with '0' like a normal regular expression?

Also, it seems to be over kill to pipe to sed four times. I'm stuck! Arg.

@ghostdog:
Thank you very much again. AWK is something I'll have to look into another day, but it appears to be very useful.

EDIT: Or wait, I guess I could use that AWK statement just as I did in my PHP version. Is there anyway to get that on one line so I can still pipe it to xargs?

---

### Post by geirha on 2008-06-10
> **altonbr said:**
> What about running 'sed' on the 'find' results before piping to 'xargs'?

There are three or four folders I must skip,

All folders or some? If all folders, then just add «-type f» to the find-command to only match files. You can also add something like «-not -name "*foo"» To not match files and dirs ending with foo.

> 
 but I'm having problems with sed:
```
$ echo 'NOoOo!' | sed s/o/0/i
```

Why doesn't it replace all of the 'o' with '0' like a normal regular expression?

It will only replace the first match on each line, but you can make it replace all by adding a 'g'
```
echo 'NOoOo!' | sed s/o/0/ig
```

---

### Post by altonbr on 2008-06-10
> **geirha said:**
> All folders or some? If all folders, then just add «-type f» to the find-command to only match files. You can also add something like «-not -name "*foo"» To not match files and dirs ending with foo.


It will only replace the first match on each line, but you can make it replace all by adding a 'g'
```
echo 'NOoOo!' | sed s/o/0/ig
```

Both of those are my fault (RTFM), thank you for clarifying.

I think I'm close here, but I keep getting an error:

```
md5_file='md5sum'

# if the md5sum file exists
if [ -f $md5_file ]; then
	# delete it
	rm -f $md5_file # don't want duplicates
fi

# loop from a to z
for char in {a..z}; do
	find . -maxdepth 1 \( -iname "${char}*" -not -iname "agentphotos" -not -iname "listingphotos" -not -iname "${md5_file}" \) -print0 | cut -d '/' -f 2 | xargs --null --no-run-if-empty tar czf ${char}.tar.gz

	# If the tarball exist, do the md5sum of it.
	[ -f ${char}.tar.gz ] && md5sum ${char}.tar.gz >> ${md5_file}
done 
```

> tar: .\n: Cannot stat: No such file or directory
tar: Error exit delayed from previous errors

I have a feeling it doesn't like my slew of -iname's.

---

### Post by altonbr on 2008-06-10
Maybe porting my code from PHP to Python is in order...

EDIT: Nevermind, this shared environment doesn't have PHP, Python or rsync available :S

---

### Post by ghostdog74 on 2008-06-10
> **altonbr said:**
> ```

for char in {a..z}; do
	find . -maxdepth 1 \( -iname "${char}*" -not -iname "agentphotos" -not -iname "listingphotos" -not -iname "${md5_file}" \) -print0 | cut -d '/' -f 2 | xargs --null --no-run-if-empty tar czf ${char}.tar.gz

	# If the tarball exist, do the md5sum of it.
	[ -f ${char}.tar.gz ] && md5sum ${char}.tar.gz >> ${md5_file}
done 
```

In your code, you are calling the find,cut and xargs command 26 times because of the for loop.
you can do away with the for loop. Use the find command to find only files, then get their first character and do the necessary, like the eg in post #16

---

### Post by altonbr on 2008-06-10
> **ghostdog74 said:**
> In your code, you are calling the find,cut and xargs command 26 times because of the for loop.
you can do away with the for loop. Use the find command to find only files, then get their first character and do the necessary, like the eg in post #16

You're right. I've taken a little something from each post and sometimes I'm getting advancements lost in translation.

My problem currently is escaping paths like "Hello, my name is Joe!". 'tar' will see that as 5 separate directories.

I posted it in a separate thread here: [http://ubuntuforums.org/showthread.php?t=825383](http://ubuntuforums.org/showthread.php?t=825383)

---

### Post by ghostdog74 on 2008-06-10
> **altonbr said:**
> 

My problem currently is escaping paths like "Hello, my name is Joe!". 'tar' will see that as 5 separate directories.


```

# echo "help" >> "this is a test file with spaces"
# ls -1 this\ is\ a\ test\ file\ with\ spaces
this is a test file with spaces
# find . -name "this *" -print0 | xargs -0 tar rf test.tar
# tar tvf test.tar
-rw-r--r-- root/root        25 2008-06-10 13:50:06 ./this is a test file with spaces


```

---

### Post by Phenax on 2008-06-10
> **ghostdog74 said:**
> ```

# echo "help" >> "this is a test file with spaces"
# ls -1 this\ is\ a\ test\ file\ with\ spaces
this is a test file with spaces
# find . -name "this *" -print0 | xargs -0 tar rf test.tar
# tar tvf test.tar
-rw-r--r-- root/root        25 2008-06-10 13:50:06 ./this is a test file with spaces


```

Practically the same thing I posted in the other thread at the same time.. :)

---

### Post by altonbr on 2008-06-10
> **ghostdog74 said:**
> ```

# echo "help" >> "this is a test file with spaces"
# ls -1 this\ is\ a\ test\ file\ with\ spaces
this is a test file with spaces
# find . -name "this *" -print0 | xargs -0 tar rf test.tar
# tar tvf test.tar
-rw-r--r-- root/root        25 2008-06-10 13:50:06 ./this is a test file with spaces


```

But you just showed me code above that doesn't use xargs because, as you said, it'll run 26 times. How would you do that in terms of your code in #16?

---

### Post by ghostdog74 on 2008-06-11
> **altonbr said:**
> But you just showed me code above that doesn't use xargs because, as you said, it'll run 26 times. How would you do that in terms of your code in #16?
well, if you want to try the method at post #16, use the rf option ( or the -null option as suggested from the other thread ) 
eg
```

find ...... | while read file
do
 ...
 tar rf ... 
 ...
done 

```

---

### Post by altonbr on 2008-06-11
> **ghostdog74 said:**
> well, if you want to try the method at post #16, use the rf option ( or the -null option as suggested from the other thread ) 
eg
```

find ...... | while read file
do
 ...
 tar rf ... 
 ...
done 

```

How does that escape spaces in file/folder names?

Like, if you had file that look like this:
> Aaa
AAAafsd
ahdt
baaa
bAabsdf
bse
rOGER that! man!90r ?&%$
this is a test file with spaces
How would you pass that to 'tar' without it breaking? Or am I misunderstanding what -r does?

This is what the one looks like with tabbed auto-escaping:
> cd rOGER\ that\!\ man\!90r\ \?\&%\$

---

### Post by ghostdog74 on 2008-06-11
just supply them to tar?
```

# echo "help" > 'rOGER that! man!90r ?&%$'
# ls -1 rOGER\ that\!\ man\!90r\ \?\&%\$
rOGER that! man!90r ?&%$
# files='rOGER that! man!90r ?&%$'
# tar rf test.tar "$files"
# tar tvf test.tar
-rw-r--r-- root/root         5 2008-06-11 12:32:27 rOGER that! man!90r ?&%$

```
i leave to you to put that into the script.

---

### Post by altonbr on 2008-06-11
So pretty much the only thing I was missing was that
> find ... -print0 | xargs -0 ...
had to match?

This is my final code and I'm sticking to it. It still creates a directory of '.' but whatever, I'm going to bed.

```
md5_file='md5sum'

# if the md5sum file exists
if [ -f $md5_file ]; then
	# delete it
	rm -f $md5_file # don't want duplicates
fi

# loop from a to z
for char in {a..z}; do
	find . -maxdepth 1 -iname "${char}*" -print0 | xargs -0 --null --no-run-if-empty tar czf ${char}.tar.gz

	# If the tarball exist, do the md5sum of it.
	[ -f ${char}.tar.gz ] && md5sum ${char}.tar.gz >> ${md5_file}
done 
```

---

