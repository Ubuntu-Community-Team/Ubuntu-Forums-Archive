---
title: "New to bash scripting - Problem using FOR"
date: 2009-06-26
forum: Programming Talk
---

### Post by oduartix on 2009-06-26
I need a **for** cicle to handle all files with a certain extension which in this case is **bib**.
When I run the following command on the bash **shell**:

>*find . -name "*.bib"*

I get these results:
./Arquitectura/Lisboa/Bairro Alto/raw/P7226658.ORF.bib
./Arquitectura/Lisboa/Bairro Alto/raw/P7226659.ORF.bib
(...)

My issue, and I haven't been able to overcome it, is when I try to port that to a shell script using **for**:

**for** [COLOR="DarkRed"]sidecar_file[/COLOR] **[B]in**[/B] `find . -name [COLOR="Red"]"*.bib"`[/COLOR]

As a lot of my folder names contain spaces, this time I will get a lot more rows, as the **for** control structure seems to run a cicle for each token in the **in** evaluation:

./Arquitectura/Lisboa/Bairro
Alto/raw/P7226658.ORF.bib
./Arquitectura/Lisboa/Bairro
Alto/raw/P7226659.ORF.bib

Is there a clean way out of this? Something that doesn't involve renaming  the files from [ ] to [_]?

BTW, my goal is to check for each **bib** file ex: (IMG123.RAW.bib) if there is a file (IMG123.RAW). If not the **bib** file gets deleted. I've got all other parts of the script sorted out, parameter validation, initializations, tests, cicles, several optional deleting commands, etc. It's kind of frustrating to be against this wall with only a very unclean window with a view to success.

---

### Post by ghostdog74 on 2009-06-26
use a while read loop instead
```

find ..... | while read FILE
do
 #do something with $FILE
done 

```

---

### Post by oduartix on 2009-06-26
> **ghostdog74 said:**
> use a while read loop instead
```

find ..... | while read FILE
do
 #do something with $FILE
done 

```
You mean redirecting the output of the **find** command to a file and then reading it line by line? Won't that read instruction you posted also read **just a token?**
(edit) Now that I look further to your suggestion, I'm wondering: it doesn't write any file does it? It's just a pipe redirection from one command to another, right?

I had also thought about using a file, but that will require extra permissions to the user which could (just in theory) limit the script. The rest of the script will assume the user has file deletion permissions all over the directory tree that the script processes, but I just wondered whether a cleaner solution existed.

---

### Post by ghostdog74 on 2009-06-26
> **oduartix said:**
> You mean redirecting the output of the **find** command to a file and then reading it line by line? 

no, that doesn't pipe to a file. It just reads off whatever is output from the find command to stdout.

please read the bash link in my signature.

---

### Post by stroyan on 2009-06-26
Another option is to temporarily change the value of the IFS input field separator variable so that only newlines separate fields.
That will work as long as you don't have filenames with newlines in them.
```

#save original IFS value
OIFS=$IFS
#change IFS to only newlines
IFS=$'\n'
for f in $(find . -name "*.bib")
do
 echo handle "$f"
done
#restore IFS value
IFS=$OIFS

```

Both the pipe to read and the

---

### Post by kaibob on 2009-06-27
If all of the files are in one directory, you do not need to use the find command. A simple for loop will do what you want.

```
for FILE in *.bib ; do
echo "$FILE"
done
```

If you need the script to work recursively in the target directories and all subdirectories, then the find command is the way to go and ghostdog74's suggested solution is what I would use.

```
find . -name "*.bib" -type f | while read FILE
do
echo "$FILE"
done
```

As an aside, in the above "FILE" is a variable that holds the file name piped to it by the find command. You can use FILENAME or whatever your like. The important point is that it's a variable not an actual file.

---

### Post by oduartix on 2009-06-27
Thanks everyone.
I like the IFS solution as it's very clean and allows better readability of the code, but I will also try redirecting from stdout as it incorporates better the shell philosophy.

---

### Post by geirha on 2009-06-27
The following will find all files (-type f) ending with .bib (-name "*.bib"), and for each of those files, it will pass it on to a tiny shell script (-exec sh... \;) that tests if a file with the same name, minus the ending .bib, exists, and if that returns true, it prints it (-print)
```
find -type f -name "*.bib" -exec sh -c 'test -f "${1%.bib}"' -- {} \; -print
```

If you're confident it only prints the files it should delete, then replace "-print" with "-delete" to have the find command delete them.

---

### Post by oduartix on 2009-06-27
> **stroyan said:**
> Another option is to temporarily change the value of the IFS input field separator variable so that only newlines separate fields.

(...)
IFS=$'\n'
(...)


I know this must be pretty basic, but I can't get this line to work inside the script. It works and sets the variable if I'm directly on the bash, but inside the script, I always get:
**delete_orphans: 47: =\n: not found**

Still with the IFS separator variable set to '\n' in the shell it doesn't cut it. To say the truth perhaps I should say it cuts too much (same behavior as before).

So I need to put my LISP programmer shoes again (after 14 years in the closet) and try the **while** suggestion or try **geirha**'s suggestion which seems much more simple than the string operations I was working on the file names.

Thanks again. 
I'll be back.

---

### Post by geirha on 2009-06-27
> **oduartix said:**
> I know this must be pretty basic, but I can't get this line to work inside the script. It works and sets the variable if I'm directly on the bash, but inside the script, I always get:
**delete_orphans: 47: =\n: not found**


Sure you haven't made a typo in there? Like ```
$IFS='\n'
``` instead of ```
IFS=$'\n'
```
There must be no spaces around the = either.

---

### Post by oduartix on 2009-06-27
> **geirha said:**
> Sure you haven't made a typo in there? Like ```
$IFS='\n'
``` instead of ```
IFS=$'\n'
```
There must be no spaces around the = either.
Thanks geirha!
Right on the money!!! I should probably get more sleep...

Still, it's almost there (it's not breaking lines on tokens) but a little short... Oddly, now besides cutting on new lines, it's cutting on character "n" like this:

**./Cursos/Challenges/How fast can you go/raw/P5048379.ORF.bib**

is broken into:

[B]./Cursos/Challe
ges/How fast ca
 you go/raw/P5048379.ORF.bib
[/B]

What I've got so far is this (I'm not executing any command on the file yet, I'm still debugging):

```
#!/bin/bash

# Exit function with usage feedback
usage(){
	echo "Recursively deletes all .BIB and .XMP sidecar files for which it doesn't find a parent image file. "
	echo "Usage: delete_orphans -action [path]"
	echo " action = -d 		deletes files"
	echo " action = -m 		moves files to trash bin folder"
	echo " action = -t 		just test (does not delete) "
	echo " action = -a		asks before deleting "
	echo " action = -c		counts files "
	echo " [path]			path to search defaults to . "
}

#Check if the parameters were passed
if [ $# != 1 -a  $# != 2 ] ; then
	usage
	exit
fi 

action=$1
path=$2
# Set a default value of . to path if none was passed
if [ -z $path ] ; then
	path=.
fi

# Validate parameters
if [ $action != '-d' -a $action != '-t' -a $action != '-a'  -a $action != '-m' -a $action != '-c' ] ; then
	usage
	exit
fi 

# Check for valid path
if [ ! -d $path ] ; then
	usage
	echo "Invalid path!"
	exit
fi 

# Defaults Initializations
deleted=0
command="mv -f"
destination="/dev/null"

#save original IFS value and set it to a Newline
originalIFS=$IFS
IFS=$"\n"

# Set command to apply  and destination of deleted files according to the action
if [ $action = '-m' ]; then
	destination="~/.local/share/Trash/files/"
elif [ $action = '-a' ]; then
	command="mv -i"
elif [ $action = '-t' ]; then
	command="echo mv -f"
fi

# LOOP for every sidecar file (*.xmp | *.bib) below $path
for sidecar_file in `find $path \( -name "*.bib" -o -name  "*.BIB" -o -name "*.xmp" -o -name "*.XMP" \) -print`
do
	# Calculate the ORIGINAL filename by removing the extension .BIB or .XMP
	orphaned_file=`expr substr $sidecar_file 1 $(expr length $sidecar_file - 4)`
        # Is the SIDECAR file orphaned?
	if [ ! -f $orphaned_file ]; then
                # count action doesn't execute <command file destination>, all others do
		if [ $action != '-c' ]; then
			echo "$command $sidecar_file $destination"
		fi
		deleted=$((deleted+1))
	fi
done

#restore IFS value
IFS=$originalIFS

#Final output
if [ $action != '-c' ]; then
	echo "Command successful. $deleted files deleted. "
else
	echo $deleted
fi
```

---

### Post by ghostdog74 on 2009-06-27
why do you want to make it harder for yourself.? try not to meddle with IFS unnecessary, use the while read loop.

---

### Post by geirha on 2009-06-27
There's a difference between "" quotes and '' quotes, and in the case of IFS, you want to use single quotes, not double quotes.
```
IFS=$'\n'
```

Also, always quote variables containing paths. E.g.
```
[ -z $path ]
# should be
[ -z "$path" ]

```
or else the spaces will come to haunt you.

---

### Post by oduartix on 2009-06-28
> **ghostdog74 said:**
> no, that doesn't pipe to a file. It just reads off whatever is output from the find command to stdout.

Well, I've tried the WHILE construct and as you said it is much simpler and works out of the box. But now I have a problem removing the extension. 

```
find "$path" \( -name "*.bib" -o -name  "*.BIB" -o -name "*.xmp" -o -name "*.XMP" \) -print | while read sidecar_file
do
	# Calculate the ORIGINAL filename by removing the extension .BIB or .XMP
	orphaned_file=`expr substr $sidecar_file 1 $(expr length $sidecar_file - 4)`
done
```

the **orphaned_file** assignment produces error:
expr: syntax error

It was working before so I figure it has something to do with the way I'm evaluating and the new presence of spaces.
Any clues?
TIA.

> **ghostdog74 said:**
> please read the bash link in my signature.
Wow! A reference on bash scripting. I think it's not a coincidence that when I was on training I had already stumbled on your page long before this thread even started. 
BTW congratulations on winning the sack race. :D

---

### Post by oduartix on 2009-06-28
> **oduartix said:**
> 
```
orphaned_file=`expr substr $sidecar_file 1 $(expr length $sidecar_file - 4)`

```
the **orphaned_file** assignment produces error:
expr: syntax error

It was working before so I figure it has something to do with the way I'm evaluating and the new presence of spaces.
Any clues?
TIA.
:D
As **geirha** predicted, the spaces came back to hunt me.
Solved by replacing **$sidecar_file** with **"$sidecar_file"**

Thanks everyone. With your invaluable help, I'll probably finish it today.

---

### Post by geirha on 2009-06-28
> **oduartix said:**
> 
the **orphaned_file** assignment produces error:
expr: syntax error

Probably because of spaces in the path. Remember to put "" around to keep the spaces in check.

Though, try with the built-in variable substitution instead. This one cuts off everything from the last . till the end.
```
orphaned_file=${sidecar_file%.*}
```

---

### Post by ghostdog74 on 2009-06-28
> **oduartix said:**
>  But now I have a problem removing the extension. 

you don't have to use external expr command to remove extension. example
```

file="afile.xml"
echo ${file%.xml}
file=${file%.xml}

```

---

### Post by oduartix on 2009-06-28
> **geirha said:**
> 
Though, try with the built-in variable substitution instead. This one cuts off everything from the last . till the end.
```
orphaned_file=${sidecar_file%.*}
```
> **ghostdog74 said:**
> you don't have to use external expr command to remove extension. example```

file="afile.xml"
echo ${file%.xml}
file=${file%.xml}

```
I had solved it already with $ but both your examples are much cleaner than my **expr** use. Anyway you are making it very clear that I must invest some time in studying variable substitution as it's too powerful to miss, and it's probably one of the most useful mechanics in Bash. Unfortunately it's still a very gray area to me.

I went with **geirha's** solution because I'll be working 2 different  extensions with both upper and lowercase.

Now, if you bear with me just a little longer I need some extra help. :(
On order for my command to work (and it will either delete or move the sidecar file to another folder) I will need to replace " " with "\ " so that:
**mv 2008-12-21 Jantar de Natal\IMG001.ORF.bib /dev/null**
gets replaced with: 
**mv 2008-12-21\ Jantar\ de\ Natal\IMG001.ORF.bib /dev/null**

I've tried:
transformed=${sidecar_file//" "/"\ "} but I get an error:
Bad substitution

I don't know what's wrong because I can't even a simpler "1" to "2" substitution to work in the script even though it works in the **bash**.

---

### Post by lloyd_b on 2009-06-28
Instead of trying to get "\ " everywhere there's a space, it's simpler to just wrap the arguments in double quotes.  For example, instead of```
$command $sidecar_file $destination
```, use```
$command "$sidecar_file" "$destination"
```

Note - you can get a literal double-quote into a string by using \".

Lloyd B.

---

### Post by oduartix on 2009-06-29
> **lloyd_b said:**
> Instead of trying to get "\ " everywhere there's a space, it's simpler to just wrap the arguments in double quotes.  For example, instead of```
$command $sidecar_file $destination
```, use```
$command "$sidecar_file" "$destination"
```

Note - you can get a literal double-quote into a string by using \".

Oh boy, the more I work at this the further from the end line I seem to get... :(
But at least I'm not sure it's related to bash. Running this script with option -a (which means the command will be [COLOR="DarkGreen"]***mv -i ***[/COLOR])

```
# Defaults Initializations
declare -i deleted
deleted=0
command="mv -f "
destination=" /dev/null"

# Set command to apply  and destination of deleted files according to the action
if [ $action = '-m' ]; then
	destination=" ~/.local/share/Trash/files/"
elif [ $action = '-a' ]; then
	command="mv -i "
elif [ $action = '-t' ]; then
	command="echo mv -f "
fi

# LOOP for every sidecar file (*.xmp | *.bib) below $path
find "$path" \( -name "*.xmp" \) -print | while read sidecar_file; do
	# Calculate the ORIGINAL filename by removing the extension
	orphaned_file=${sidecar_file%.*}
        # Is the SIDECAR file orphaned?
	if [ ! -f "$orphaned_file" ]; then
                # count action doesn't execute <command file destination>, all others do
		if [ $action != '-c' ]; then
			$command "$sidecar_file" "$destination"
		fi
		deleted=$((deleted+1))
	fi
done

#Final output
if [ $action != '-c' ]; then
	echo "Command successful. $deleted files deleted. "
else
	echo $deleted
fi
```

the output is:
**[COLOR="DarkRed"]mv: cannot move `./work/023 Vera/102OLYMP/P3017133.ORF.xmp' to ` /dev/null': No such file or directory[/COLOR]**

If I try it directly in the bash:
**mv ./work/023\ Vera/102OLYMP/P3017133.ORF.xmp  /dev/null**
I get:
[COLOR="DarkRed"][B]mv: inter-device move failed: `./work/023 Vera/102OLYMP/P3017133.ORF.xmp' to `/dev/null'; unable to remove target: Permission denied
[/B][/COLOR]
even though I can delete the file with:
[B]rm -i ./work/023\ Vera/102OLYMP/P3017133.ORF.xmp
[/B]

And why oh why?:
> sh delete_orphans -c
outputs:
[COLOR="DarkRed"]delete_orphans: 42: declare: not found
0
[/COLOR]
while:
> ./delete_orphans -c
outputs:
[COLOR="DarkRed"]0
[/COLOR]

What is happening? Why is **deleted** = 0? Al these subtleties are burning a hole in my head... :(

---

### Post by ghostdog74 on 2009-06-29
why are you moving to /dev/null?? if you want to remove files, just use rm, if you want to truncate a file to 0 bytes, just use it like this
```

prompt# > file_to_truncate

```
otherwise, supply a proper destination!

---

### Post by geirha on 2009-06-29
> **oduartix said:**
> 
the output is:
**[COLOR="DarkRed"]mv: cannot move `./work/023 Vera/102OLYMP/P3017133.ORF.xmp' to ` /dev/null': No such file or directory[/COLOR]**

If I try it directly in the bash:
**mv ./work/023\ Vera/102OLYMP/P3017133.ORF.xmp  /dev/null**
I get:
[COLOR="DarkRed"][B]mv: inter-device move failed: `./work/023 Vera/102OLYMP/P3017133.ORF.xmp' to `/dev/null'; unable to remove target: Permission denied
[/B][/COLOR]
even though I can delete the file with:
[B]rm -i ./work/023\ Vera/102OLYMP/P3017133.ORF.xmp
[/B]


Not sure why you expect moving something to /dev/null would delete it, but it won't, it will try to replace the file /dev/null instead. You really do need to use rm.

Also, 
```

destination=" /dev/null"
# is different from
destination="/dev/null"

```

> **oduartix said:**
> 
And why oh why?:
> sh delete_orphans -c
outputs:
[COLOR="DarkRed"]delete_orphans: 42: declare: not found
0
[/COLOR]
while:
> ./delete_orphans -c
outputs:
[COLOR="DarkRed"]0
[/COLOR]

What is happening? Why is **deleted** = 0? Al these subtleties are burning a hole in my head... :(

That's because you have a command piped to while. It's a confusing annoyance with bash. When you do 
```
find "$path" \( -name "*.xmp" \) -print | while read sidecar_file; do
    # ...
done

```
The while loop will be run in a subshell. So, the deleted variable is only incremented in that subshell, while in the main, it will remain 0. One way to circumvent that is to use [process substitution](http://mywiki.wooledge.org/ProcessSubstitution).
```
while read sidecar_file; do
    # ...
done < <(find "$path" \( -name "*.xmp" \) -print)

```

---

