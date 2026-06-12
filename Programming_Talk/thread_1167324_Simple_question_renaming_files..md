---
title: "Simple question: renaming files."
date: 2009-05-22
forum: Programming Talk
---

### Post by Jefferythewind on 2009-05-22
Hello all, I have began studying the bash shell and linux programming, and i have come across a problem i need some help with.  It has to do with the rename command.  

Basically i have a directory with files in it, and I want to change all the names in the directory with one command, instead of changing the names one by one in the GUI.  The new names could all be in a series like, file1, file2, file3, etc.  I have written a little program in gedit like this:

[COLOR="Red"]#!/bin/bash

if [ ! -d $1 ]; then
    echo "$1 is not a directory!" 1>&2
    exit 1
fi

for filename in $1/*; do
fn=$(basename "$filename")

 echo "$filename"

done
[/COLOR]

This gives me the printout of all the filenames.  So that is good.  So now i am trying to implement the rename command to do the conversion to each file.  this is what i did:

[COLOR="Red"]#!/bin/bash

if [ ! -d $1 ]; then
    echo "$1 is not a directory!" 1>&2
    exit 1
fi

for filename in $1/*; do
fn=$(basename "$filename")

 echo "$filename"
 rename $filename zhou0 zhou?

done [/COLOR]

I put in this line according to what i found at the man pages, but i am not getting anywhere, and i don't understand the error message:

Bareword found where operator expected at (eval 1) line 1, near "/media/ipod"
	(Missing operator before d?)

As you can see i am trying to change files that are on my ipod.

Thanks for any help.  I am trying to learn the ins and outs of Linux and Ubuntu because i like it so much, but as you can see i am not an expert.

---

### Post by unutbu on 2009-05-22
rename expects a perlexpr followed by filenames. (For example, 
"rename 's/ /_/g' *" removes all spaces from filenames and directory names.)
Since you are essentially renaming files one at a time, perhaps the mv command is more in line with what you need:

[PHP]#!/bin/sh
N=1
ls -tr -1 | while read file
do
    if [ ! -d "$file" ]; then
	echo "mv $file file$N"
	N=$((N+1))
    fi
done
[/PHP]

---

### Post by SadaraX on 2009-05-23
Not related to your shell program, but for a GUI app to rename your files in mass, have you considered GPRename? [http://gprename.sourceforge.net/](http://gprename.sourceforge.net/)

---

### Post by Jefferythewind on 2009-05-23
Hi unutbu, thanks a lot for the help.  I will mention that i am doing this because the script i am using to play mp3s on my ipod shuffle does not recognize chinese characters, so i want to change all the names of these songs from chinese to anything with letters, really, then i will be able to listen to them.  i added your script to mine and i have run it and i got an output like this:

user@user-laptop:/media/ipod/g$ renamesongs /media/ipod/g
mv 03 - &#38738;&#33457;&#29943;.mp3 file1
mv 01 - &#29275;&#20180;&#24456;&#24537;.mp3 file2
mv 10 - &#26368;&#38263;&#30340;&#38651;&#24433;.mp3 file3
mv 04 - &#38525;&#20809;&#23429;&#30007;.mp3 file4
mv 09 - &#29980;&#29980;&#30340;.mp3 file5
mv 05 - &#33970;&#20844;&#33521;&#30340;&#32004;&#23450;.mp3 file6
mv 02 - &#24425;&#34425;.mp3 file7
mv 07 - &#25105;&#19981;&#37197;.mp3 file8
mv 06 - &#28961;&#38617;.mp3 file9
mv 08 - &#22336;.mp3 file10

It looks like this is just the output from the echo part of the script you gave me, but it is still not changing the names of the files in the folder.  I have tried changing a few things but nothing has worked, as i still don't know exactly what i am doing.  Like i tried taking out the echo and the quotation mark, so that line would look like this:

mv $file file$N

but i just get this:

user@user-laptop:/media/ipod/g$ renamesongs /media/ipod/g
mv: target `file1' is not a directory
mv: target `file2' is not a directory
mv: target `file3' is not a directory
mv: target `file4' is not a directory
mv: target `file5' is not a directory
mv: target `file6' is not a directory
mv: target `file7' is not a directory
mv: target `file8' is not a directory
mv: target `file9' is not a directory
mv: target `file10' is not a directory


Well thanks if you could help me out, i am going to continue to look for an answer and will post if i get it!

---

### Post by unutbu on 2009-05-23
Hi Jefferythewind, I forgot that the script I posted only echo'd commands rather than
performing them. Here is a version which should perform the moves:

[PHP]#!/bin/sh
N=1
ls -tr -1 | while read file
do
    if [ ! -d "$file" ]; then
    mv "$file" "file$N"
    N=$((N+1))
    fi
done  [/PHP]

By putting double-quotes around "$file", you protect the variable "file" from being
interpreted as more than one argument in the mv command.

When you get the error 
```

mv: target `file1' is not a directory
```

it means mv thought it was being called with 3 or more arguments, as in
```

mv a.mp3 b.mp3 file1
```

and so it expects file1 to be a directory.

Something weird must be happening due to the Chinese characters in the filename which causes bash to interpret $file as more than one argument (as though there was a space in between some of the characters?) I don't really know. However, I think putting double-quotes around the "$file" variable may solve the problem.

---

### Post by Jefferythewind on 2009-05-23
Hi, thanks, thats the ticket!  I got, i thought you may have been doing that echo command for that reason, i just didn't know exactly how to fix it.  I used the mv command on a single file also for the same purpose, great.  thanks for the help, unutbu!

---

### Post by unutbu on 2009-05-23
Wonderful! Glad I could help.

---

### Post by mcai8sh4 on 2009-05-23
Don't know if this is any help, but a while ago I was renaming a load of mp3's using the ID3 tag data to create the file name for all mp3s in a directory.
Below is my test code - ***Be Careful If You Use - If bad things happen not my fault*** (although I have used it and it seemed to work ok)

You'll need id3 (apt-get install id3)

And it should work - If you're unsure make a copy of a directory and test it - then you don't loose anything and then have to hunt me down!

```
#!/bin/bash
  #
  #
  # rename mp3 files using data from the ip3 tags
  # just a test - do not use unless you can afford loss
  #
  # mcai8sh4
  #
  # updated: changed "cp... rm..." to "mv" so I don't loose more music!
 #
 # set shopt to there is no problem with the case with filename globbing (unset at end of prog - just in case)
shopt -s nocaseglob
for FILE in *.{mp3,MP3}; do
    if  [ "$(id3 -l "$FILE" |  sed -e s/[^:]*:\ //)" = "No ID3 tag." ]; then
        echo "$FILE has no data available"
    else
        new_name=$(id3 -l "$FILE" | sed -ne2p | sed -es/[^:]*:\ // -es/\ *$// -es/\ *[[:alpha:]]*:\ /##/ -es/'\(.*\)##\(.*\)/\2 - \1.mp3'/)
        #new_name=$(id3 -l "$FILE" | grep Title | sed -es/[^:]*:\ // -es/\ *$// -es/\ *[[:alpha:]]*:\ /##/ -es/'\(.*\)##\(.*\)/\2 - \1'/ -es/$/'.mp3'/)
        echo -n "$FILE   --- will become --->  $new_name [y/n] : "
        read ANS
        case $ANS in
            y | yes )   mv  "$FILE" "$new_name"
            #   THIS WAS A BAD IDEA : rm "$FILE"
            ;;
            *)  echo "File not altered!"
        esac
    fi
done
shopt -u nocaseglob
```

It's a bit of a hack - but I'm still learning, and it worked in the end.

---

### Post by Jefferythewind on 2009-05-23
Thats pretty cool, I am way more of a beginner than you.  That would be helpful for a lot of file names to get them to a standard format.  For what i am trying to do, the short script that unutbu made is great and easy, but after you have done it it doesn't distinguish between file names anymore.  It is just like file1, file2, file3.  But that is all i needed, ipod shuffle doesn't have a screen or anything to display filenames.

I guess i am still wondering what is the use of the rename command?  mv seems to rename the file.  And, what is a perlexpr?  But anyway i have a lot to learn and there is a lot of documentation out there so i'll take a look.

thanks everybody.

---

### Post by unutbu on 2009-05-24
Hi Jefferythewind, rename is a powerful and useful command to know. Its syntax comes from the Perl programming language.

Here is an example using the rename command:
```

rename 's/ /_/g' *
```

It changes spaces to underscores in all items in a directory.

's/ /_/g' is a so-called "perlexp". 
The s tells rename to substitute. 
The /'s are just dividers. s/A/B/ means replace all A's with B's.
The g at the end of the perlexp tells rename to replace "globally". 

Without the "g", a file called 
```

"a file with spaces"
``` would be renamed ```
"a_file with spaces"
```

For each file, only the first match is replaced. 

With the "g", 
```

"a file with spaces" 
```

becomes
```

"a_file_with_spaces"
```

For more info, type 

```
man rename
```

to read the man page.

---

### Post by kaibob on 2009-05-24
> **unutbu said:**
> Hi Jefferythewind, rename is a powerful and useful command to know. Its syntax comes from the Perl programming language....

I agree with unutbu that rename is immensely useful. Post 2 in the following thread contains many practical examples of rename usage and is helpful after learning the basics of rename:

[http://ubuntuforums.org/showthread.php?p=5210531](http://ubuntuforums.org/showthread.php?p=5210531)

---

### Post by Jefferythewind on 2009-05-25
Cool, thanks unutbu and kaibob, i think i should be all set for all my file renaming needs.  the rename command does seem very powerful and i'm glad i have a little handle on how to use it.

---

### Post by ghostdog74 on 2009-05-25
> **Jefferythewind said:**
> Cool, thanks unutbu and kaibob, i think i should be all set for all my file renaming needs.  the rename command does seem very powerful and i'm glad i have a little handle on how to use it.

you can try the script i wrote (see my sig last link). save it as filerename.py as on command line: 
```

# ls -1
01 - &#29275;&#20180;&#24456;&#24537;.mp3
03 - &#38738;&#33457;&#29943;.mp3
04 - &#38525;&#20809;&#23429;&#30007;.mp3
10 - &#26368;&#38263;&#30340;&#38651;&#24433;.mp3

# filerenamer.py -s ".*(\.mp3)" -e "file_01:100\1" -l "*.mp3"
==>>>>  [ /home/03 - &#38738;&#33457;&#29943;.mp3 ]==>[ /home/file_01.mp3 ]
==>>>>  [ /home/10 - &#26368;&#38263;&#30340;&#38651;&#24433;.mp3 ]==>[ /home/file_02.mp3 ]
==>>>>  [ /home/01 - &#29275;&#20180;&#24456;&#24537;.mp3 ]==>[ /home/file_03.mp3 ]
==>>>>  [ /home/04 - &#38525;&#20809;&#23429;&#30007;.mp3 ]==>[ /home/file_04.mp3 ]


```

remove the "-l" option to commit changes.

---

### Post by Jefferythewind on 2009-05-25
Thats pretty cool, although it seems like it does the same thing as the rename and mv commands in linux.  I guess having the python compatibility makes it more universal than bash shell commands.

---

### Post by ghostdog74 on 2009-05-25
> **Jefferythewind said:**
> Thats pretty cool, although it seems like it does the same thing as the rename and mv commands 
execute the script with -h option. you can see there are many other options that rename doesn't have. for example you can undo your renaming if you see something wrong. Or like in your case, replacing with a running sequence, which rename also doesn't provide. (AFAIK).

---

### Post by Jefferythewind on 2009-05-26
Great point, i will read more about your script.  There is a lot to be said for the undo capability.

---

