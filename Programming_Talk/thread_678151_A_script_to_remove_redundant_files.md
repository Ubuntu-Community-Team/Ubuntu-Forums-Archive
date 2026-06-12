---
title: "A script to remove redundant files"
date: 2008-01-25
forum: Programming Talk
---

### Post by zazuge on 2008-01-25
One day i've ended with a 15GB of redundant pdf files
I didn't know how to manage this mess.
I started by searching files with same names to remove but there's still files who were corrupt so I've writen a script that search to files with same name
I show a comparison between them (modificatation time ,md5sum ,CRCsum ,a file size).

```
#!/bin/bash
echo "scaning files ..."
find "$1" -type f > list_fichier
echo "finding files with same names..."
cat  list_fichier |sed 's/\/.*\///g'|sort|uniq -c|sort -n|sed '/1/d'|sed 's/ //g'|sed 's/^[0-9]//g'>list_fichier_doublons
echo "building file list..."
#cat  list_fichier_doublons|xargs -n 1  find $1   -name|sed 's/\ /\\\ /g' |xargs -n 1 ls -s -ltgG| cut -d' ' -f1,3- >list_fichier
for x in `cat list_fichier_doublons` ;do find "$1" -name "$x" -exec ls -s -ltgG "{}" ';' ;done| cut -d' ' -f1,5,6,7->list_fichier
echo "calculating sum ..."
#cat  list_fichier_doublons|xargs -n 1  find $1   -name|xargs sum|cut -c 1-5> list_fichier_sum
for x in `cat list_fichier_doublons` ;do find "$1" -name "$x" -exec sum "{}" ';' ;done|cut -d' ' -f1>list_fichier_sum
echo "calculating MD5sum ..."
#cat  list_fichier_doublons|xargs -n 1  find "$1" -name|xargs md5sum|cut -c 1-32 > list_fichier_md5sum
for x in `cat list_fichier_doublons` ;do find "$1" -name "$x" -exec md5sum "{}" ';' ;done|cut -d' ' -f1>list_fichier_md5sum
echo "now printing ..."
paste list_fichier list_fichier_sum list_fichier_md5sum
#rm -f list_fichier_sum list_fichier_md5sum list_fichie
```

but I've found files with diffirent file names but same content (data).
so i've tried to search not files with redundant filenames but to look to similare content.

I was not satisfied with the scripts i've found on the net so i've dicided to write my own.

here is a script that delete the redundant files.
your are warned this script is no toy it's not less harmless than a shotgun.
and i don't have to warn you that there's no cure for stupidity.
I'm no expert ,i just begun using Linux 2 years ago.
come to thing about it, bash scripting is so powerful that any administrator can execute complex tasks without having to programme with any language.
And last but not least you can't do something like this with a stupid zindowz unless you some proprietary product, so long live Linux!

```
#!/bin/bash
mkdir temp
cd temp
echo generating md5 hashs
find $1 -type f \( -iname '*.doc' -o -iname '*.xls' -o -iname '*.pdf' \) -exec md5sum "{}" ';' > filelist.md5
echo sorting file hashs
#sort -k1 filelist.md5 > sortedfilelist.md5
echo extracting redundant hash keys
#cat sortedfilelist.md5 |cut -d' ' -f1 |uniq  > keys.md5
echo building file to remove list
for x in `cat keys.md5` ;do
        echo "$x"
        length=`grep "$x" sortedfilelist.md5|cut -d' ' -f3- |wc -l`
        if ((length-1>0)) ;then
                grep "$x" sortedfilelist.md5|cut -d' ' -f3-|tail -n $((length-1))
                echo "--------------------------"
        fi
done filetoremove
echo removing files
for ((i=0;i<  $((`cat temp/filetoremove|wc -l`))  ;i++ )) ;do x=`tail -n $i temp/filetoremove|head -n 1 ` ;rm -yv "$x" ;done
cd ..
rm -rf temp
```

the behavior is simple but dangerous the first instance of a file (in the order of finding) is skiped the later instances are deleted.
feel free to modify this script "It's a gift to the community", I thing every one can contribute to make it better.
don't lunch the script on the root beacause it will treat symbolic links like normal files and maybe erase the real file :lolflag:

---

### Post by Acglaphotis on 2008-01-25
I made a deb for something like this, you probably wanna look at the source, it uses md5 to look for duplicates.


[http://www.mediafire.com/?1xmvjy9thxd](http://www.mediafire.com/?1xmvjy9thxd)

---

### Post by a9bejo on 2008-01-25
Hi zazuge,

This is a useful script.  However, it is usually good UNIX style if you split separate tasks into separate little programs that read text from standard input and print to standard ouput. This makes your program a lot more powerful. And if you have code to find duplicate files, why just restrict yourself to deleting them?  

This little script simply reads a list of files and prints out a list of duplicate files  (files are compared by their md5 hashes):

[php]
#!/usr/bin/env python
#name: md5twins
#(c) Benjamin Ferrari
#license: http://www.gnu.org/licenses/gpl-3.0.txt
import sys, hashlib, os
seen = []
for line in sys.stdin:
  filename = line.strip()
  if os.path.isdir(filename): continue
  try:
    digest = hashlib.md5(open(filename,'rb').read()).digest()
    if digest in seen: print(filename)              
    else: seen.append(digest)
  except IOError: pass      
[/php]

You can use it like this

```

find /path/to/your/files | md5twins 

```

Now, if you want to delete the files, you just pipe the output to a program that deletes files. 
```

find /path/to/your/files | md5twins  | xargs rm

```

or, if you want to know how many duplicate files you have, you pipe the output to a program that counts:

```

find /path/to/your/files | md5twins  | wc - l

```

and so on

---

### Post by ghostdog74 on 2008-01-25
> **a9bejo said:**
> 
Now, if you want to delete the files, you just pipe the output to a program that deletes files. 
```

find /path/to/your/files | md5twins  | xargs rm

```

why do this, when you can code everything in Python ?
using simply os.walk() and os.remove()

---

### Post by clasificado on 2008-01-26
> **ghostdog74 said:**
> why do this, when you can code everything in Python ?

Oh yeah. Thats the bad thing about Linux: So many options :lolflag:

clasificado

---

### Post by a9bejo on 2008-01-26
> **ghostdog74 said:**
> why do this, when you can code everything in Python ?
using simply os.walk() and os.remove()

Because then I would end up with a program that only deletes files in a directory.  My program is much simpler yet can do so much more:

```

grep '\.mp3'  myplaylist.m3u | md5twins |  xargs mpg123

```

...plays only the unique songs in a m3u playlist. 


```

grep -H 'To: Benjamin Ferrari' ~/Maildirs/mail.misc/cur/* | awk '{FS=","}{print $1}'  | md5twins | wc -l

```

...counts all unique emails that  were send to me personally


And think of all the options that programs like find and rm have.  If you wanted to give the program the whole power of find, you would have to write a lot of code that has already been written and that people already know how to use.

---

### Post by zazuge on 2008-01-26
> **a9bejo said:**
> ...  However, it is usually good UNIX style if you split separate tasks into separate little programs that read text from standard input and print to standard ouput. This makes your program a lot more powerful.....
Thanks, you got a point,  i've read "The art of computer programing"
and I know about the Unix toolbox thingy ,but bad programing & bad conception still haunting me, the legacy of visualbasic past .......:lol:

Your code is so elgant ...... Bravo =D>

---

