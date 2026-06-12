---
title: "Help needed with file sorting"
date: 2012-11-21
forum: Programming Talk
---

### Post by Merrattic on 2012-11-21
I have some code snippets that can do what I want, but would like to be able to combine them together. I have a large number of files backed up (@ 250gb) that need sorting by file type. I would like to be able to search the whole fileset, which is many many sub directories deep, for a particular filetype, and then move them to a new location.

1st snippet
```
EXTS="jpg"; for ext in $EXTS; do mkdir $ext; mv  *.${ext} $ext; done
```This will find all files with extension jpg and create a directory before moving them all over. (It is possible to add more extensions to the variable to further automate, but I will probably be happy to run one at a time). I need to avoid overwriting duplicates and I understand I can add a switch to mv for this:

2nd snippet
```
mv --backup=numbered
```My problem is that this 1st snippet only covers the first directory down. I know about using find to move all files to a different location:

3rd snippet
```
find ~/[target folder] -type f -exec mv {} ~/[destination folder] \;
```
How do I go about combining, or using the intent from the 3 snippets to achieve what I am after. Also, for testing purposes, how would the same thing be done using cp?

Thanks in anticipation :)

---

### Post by drmrgd on 2012-11-21
A couple clarifications:  do you want to move (let's say) all .jpgs to 1 directory called (let's say) JPGs, or do you need more segmentation than that (e.g JPGS/FromJuly, JPGS/MyWedding/, etc.)?  Also, do you want to combine all of the .jpgs first, and then selectively pull a few out from time to time, or am I misunderstanding your second statement goal:

>  I would like to be able to search the whole fileset, which is many many  sub directories deep, for a particular filetype, and then move them to a  new location.

I think the find command will be what you want here as it seems your directory structure is too complex for a sane bash loop like in the first example.  If it's the most simple of the cases, I think something along the lines of :

```
mkdir <dest_folder> && find <target_root_folder> -type f -iname *.jpg -exec echo mv {} /path/to/<dest_folder> \;
```

If you add 'echo' before the move command (or copy if you prefer), you can see what would happen with that find and move command.  If you're happy with the results, simply remove 'echo' and it'll process the files.

Give us just a little more detail on your goals, and I'm sure this can be very easily simplified for you.

---

### Post by papibe on 2012-11-21
Hi Merrattic.

You almost got it. Try this.
```

find /path/to/source/ -type f -iname '*.jpg' \
    -exec **echo** mv -f --backup=numbered '{}' /path/to/destination/ \;
```
Same as drmrgd's suggestion, it is not actually moving files but echoing the mv command. Test it debug it, and when you feel confident remove the 'echo'.

'cp' supports the same options, so in case you prefer copy the files, just replace 'mv' with 'cp'.

Also make sure that '/path/to/destination/' in **[COLOR="Red"]not[/COLOR]** under '/path/to/source' or you'll get in trouble.

It could aslso be valuable to include *.jpeg files too:
```
find ... \( -iname '*.jpg' -or -iname '*.jpeg' \) ...
```

Tell us how it goes.
Regards.

---

### Post by Merrattic on 2012-11-22
Thanks to drmrgd and papibe for responses. I'll give it all a go and see how I get on.

The backup requirement is key, not so much for the .jpg extension but when I get to .html I want to avoid overwriting all those index.html files!

I do like my 1st snippet as the variable EXTS can take as many extensions as I can throw at it to improve automation, hence why I was hoping to augment the mv part of the code to cover all sub directories. I know it might be a matter of putting more *'s and /'s in front of the .{$ext} part ?

---

### Post by Vaphell on 2012-11-22
1. it's easy to automate find

```
ext=( "*mp3" "*avi" )
find_opt=()
for e in "${ext[@]}"
do
  (( ${#find_opt[@]} )) && find_opt+=( "-o" )
  find_opt+=( "-iname" "$e" )
done
echo "${find_opt[@]}"
*# -iname *mp3 -o -iname *avi*
find $path \( "${find_opt[@]}" \) ....
```
also arrays are better than flat strings (they have fewer problems with whitespace), so even if you stay with your *for* loop
use
```
ext=("ext1" "ext2")
for e in "${ext[@]}"; do mv ...; done 
```

2. you can enable *globstar* in bash
it allows for ** which matches dir chains of any length
```
shopt -s globstar
for f in **/*.txt; do echo $f; done
```

---

### Post by Merrattic on 2012-11-22
Aha, thanks for your input vaphell. So if I

ext=("ext1" "ext2")
for e in "${ext[@]}"; do mv ...; done

> shopt -s globstar
EXTS=("jpg"); for ext in "${EXTS[@]}"; do mkdir $ext; mv --backup=numbered **/*.${ext} $ext; done

I'll get a directory called jpg full of every jpg in the sub directories ? (I understand I could replace "mv  --backup=numbered" with "echo" just to test?)

I was missing the glob part when I tried it before....

---

### Post by Vaphell on 2012-11-22
in theory exactly that should happen.
yes, echoing first is a smart thing to do, never run mv/rm if you are not absolutely sure what will happen as there is no undo.

---

### Post by Merrattic on 2012-11-22
OK, had a chance to test. All methods work fine in terms of going down the chain of all the sub directories and moving files. The "--backup=numbered" is not working in any of the methods though so any files with the same name are getting overwritten. I tried changing the timestamp on one of the files with the same name but this didn't help. Using the -i switch works. ??

---

### Post by steeldriver on 2012-11-22
are you testing with the 'echo' still in place by any chance? the --backup=numbered won't come into effect until you do it for real and there are some actual conflicts

```
$ ls -R
.:
dir1  dir2  dir3

./dir1:
file.avi  file.jpg  file.mp3  file.mp4  subdir

./dir1/subdir:
file.avi  file.jpg  file.mp3  file.mp4

./dir2:
file.avi  file.jpg  file.mp3  file.mp4  subdir

./dir2/subdir:
file.avi  file.jpg  file.mp3  file.mp4

./dir3:
$
$ mkdir {avi,jpg,mp3,mp4}
$ shopt -s globstar; exts=(avi jpg mp3 mp4); for ext in "${exts[@]}"; do mv --backup=numbered -t "$ext/" **/*."$ext" ; done
$
$ ls -R
.:
avi  dir1  dir2  dir3  jpg  mp3  mp4

./avi:
file.avi  file.avi.~1~  file.avi.~2~  file.avi.~3~

./dir1:
subdir

./dir1/subdir:

./dir2:
subdir

./dir2/subdir:

./dir3:

./jpg:
file.jpg  file.jpg.~1~  file.jpg.~2~  file.jpg.~3~

./mp3:
file.mp3  file.mp3.~1~  file.mp3.~2~  file.mp3.~3~

./mp4:
file.mp4  file.mp4.~1~  file.mp4.~2~  file.mp4.~3~

```

---

### Post by Merrattic on 2012-11-22
Yep, testing for real :)

Ah, just spotted you have a "-t" after --backup=numbered. Let me try :~

---

### Post by Merrattic on 2012-11-22
Hmmmm, adding the -t seems to break things, sees the target file but wants it to be a target directory for moving ?
```
mv: target `dir1/dir2/my.pdf' is not a directory
```when "pdf" should be the target directory (above dir1)

---

### Post by steeldriver on 2012-11-22
sorry I should have mentioned: the -t specifies the *target*, it's just an alternative syntax for the command i.e.

```
mv -t dir/ file
```instead of

```
mv file dir/
```If you just throw a -t in to the second form it will try to write *dir* to *file *- no what you want at all

---

### Post by Merrattic on 2012-11-22
This is agonisingly close ;)

Here is my current line:
```
EXTS=("pdf"); for ext in "${EXTS[@]}"; do mkdir $ext; mv --backup=numbered **/*."$ext" "$ext"; done
```To test, I have two files called my.pdf down in different sub directories, they both get moved but one gets overwritten.

This format does the same thing:
```
EXTS=("pdf"); for ext in "${EXTS[@]}"; do mkdir $ext; mv --backup=numbered **/*.${ext} $ext; done
```

---

### Post by Vaphell on 2012-11-22
add **-v** switch to make *mv* verbose and check what happens
you should get something like this:

```
`1/2/test.txt' -> `txt/test.txt'
`1/test.txt' -> `txt/test.txt' (backup: `txt/test.txt.~1~')
`test.txt' -> `txt/test.txt' (backup: `txt/test.txt.~2~')
```

i think that files ending with ~ may be hidden.

---

### Post by Merrattic on 2012-11-22
Thanks Vaphell, they were hidden, a quick CTRL-h revealed all. Everything worked as planned.

So how do I stop files with a ~ at the end being a hidden file? Is there something like chmod or do I need to do a rename on them?

---

### Post by Vaphell on 2012-11-22
renaming will be fine
```
$ rename -nv 's/(.+)[.]([^.]+)[.]~(.+)~/$1--$3.$2/' *~*~
test.txt.~1~ renamed as test--1.txt
test.txt.~2~ renamed as test--2.txt
test.txt.~3~ renamed as test--3.txt
test.txt.~4~ renamed as test--4.txt
test.txt.~5~ renamed as test--5.txt
```
*-n* is dry run, remove *n* to actually rename

---

### Post by Merrattic on 2012-11-22
Yes, seems no way of simply unhiding. Found a simple sed command to remove the last "~"
```
rename  's/~$//' *
``` just need to build that in :)

---

### Post by Vaphell on 2012-11-22
rename works with the same expressions (eg s/from/to/). In my example i cut main part of the name ($1), original extension ($2) and the number between ~ ~ ($3) and construct the new name off these parts.
Sed would require piping names one by one which makes the approach suck.

---

### Post by Merrattic on 2012-11-22
OK, ready to mark as solved :) Many thanks to everyone, especially Vaphell for guidance and support.

Here is my one liner, which needs to be placed in the top directory. One can add as many different file extensions as needed into the variable array EXTS. I have used txt and jpg as example extensions.
> shopt -s globstar; EXTS=(txt jpg); for ext in "${EXTS[@]}"; do mkdir $ext; mv --backup=numbered **/*.${ext} $ext; rename 's/~$//' "./$ext/"*; done If I break it down a bit with comments:
```
# allows sub directory matching

shopt -s globstar;


#sets the variable with extensions, from 1 to many

EXTS=(txt jpg);


#runs the code for each extension in the variable array EXTS

for ext in "${EXTS[@]}";


#do something

do


#make a directory with the same name as the extension

mkdir $ext;


#move files with the extension in all sub directories to the created top
#level directory of the same name.
# The **/* code which is enabled by the shopt -s globstar command
# allows matching with all sub directories
# The backup=numbered ensures any duplicates are renamed, so no files
#are overwritten 

mv --backup=numbered **/*.${ext} $ext;


# renames the duplicate files by removing the last character if it
# is a "~" in order to unhide the files. There are better ways of
# doing this ;)

rename 's/~$//' "./$ext/"*;


# all done after iterating through each extension type

done
```

---

### Post by steeldriver on 2012-11-22
Glad to hear you got it working

Just one nitpick - it's generally considered good shell programming practice to use lower case for your own variables - upper case  (like EXTS) is reserved for system environment variables (if you use upper case there's a chance of overwriting a system variable - which can cause all kinds of hard-to-diagnose wierdness)

---

### Post by Merrattic on 2012-11-23
Yes, made me feel uncomfortable using it :) Just helps when reading the code to differentiate between exts and ext :)

---

### Post by Merrattic on 2012-11-24
Slight amendment to the shopt command to allow moving of hidden files and files from hidden directories
```
shopt -s globstar dotglob
```

---

