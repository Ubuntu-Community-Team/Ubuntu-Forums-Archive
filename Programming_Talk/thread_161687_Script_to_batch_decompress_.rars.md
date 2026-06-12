---
title: "Script to batch decompress .rars?"
date: 2006-04-17
forum: Programming Talk
---

### Post by Marquis_de_Carabas on 2006-04-17
I have a ton of .rar files that I wish to decompress, but doing them one by one takes far too long. unrar "*.rar* works fine, but the problem is that although some of the archives contain only one file, many contain several and I would like these to be expanded to their own directory.

I'm thinking that a shell script using the output of unrar v to work out how many files are in the archive and then proceeding accordingly would work well, but I'm not entirely sure how to achieve that. I'm a bit of a newbie at this scripting thang so any advice would be appreciated.

---

### Post by lotheac on 2006-04-17
I'm not the best scripter available but I wrote something real quickly and it seems to work.
```
#!/bin/bash

for file in $(ls *rar)
   do if (( `unrar l $file | tail -n 2 | grep -v ^$ | awk '{print $1}'` != 1 ))
        then mkdir $file-files
        cd $file-files
        unrar e ../$file
        cd ..
   else 
        unrar e $file
   fi
done
```
This will take the two last lines from the output of unrar l (last line is blank, so discard it), pass it through awk to output only the first column. If it's not 1, it'll create a directory (whose name is the filename and a '-files' appendix), cd into it and unrar the files there. If there's only one file in the archive, it'll just extract it in the current directory.

Hope it works. :)

---

### Post by Marquis_de_Carabas on 2006-04-18
Thank you! It works pretty well. It can't handle spaces in filenames though. I tried putting quotes around every instance of $file, but that hasn't helped.

I have a script which turns all the spaces into underscores, so it's not really a problem, but I'm curious as to how that could be recitified.

The other thing is that some of the .rar files have a weird empty file in them. Here's an example output of unrar l

```
UNRAR 3.40 freeware      Copyright (c) 1993-2004 Alexander Roshal

Archive Aleister_Crowley_-_The_Heart_of_the_Master_(TXT).rar

 Name             Size   Packed Ratio  Date   Time     Attr      CRC   Meth Ver
-------------------------------------------------------------------------------
 Crowley, Aleister - The Heart of the Master.txt    42484    14015  32% 10-05-03  12:08  .....A.   7CA5606D m5b 2.9
 Aleister Crowley - The Heart of the Master (TXT)        0        0   0% 06-04-0 6 01:10  .D.....   00000000 m0  2.0
-------------------------------------------------------------------------------
    2            42484    14015  32%

```

The script ends up creating a folder and putting the single text file in there. Which isn't a fault of the script of course; I'm not sure there's any way to work around these bizarre rars.

Thanks again, you've saved me a lot of time :)

---

### Post by lotheac on 2006-04-18
I suppose for a workaround to the space thing you'd have to use sed or something on the variable to escape whitespaces with a backslash, ie. replace them with a '\ '. That, or there might be an easier solution I'm not seeing.

I'm not sure (should probably read the manpage), but it could be that the 0-byte 'file' is in fact a directory, in which case you could just use unrar x instead of mkdir and cd (unrar x extracts with path).

---

### Post by Marquis_de_Carabas on 2006-04-18
> it could be that the 0-byte 'file' is in fact a directory

Yep, you're right. I really should have checked that possibility myself. It just didn't occur to me that anybody would want to create a .rar consisting of a directory containing one individual text file. Why would anyone do that?

Unfortunately most of the rars with multiple files in aren't in directories. The creator obviously got confused and thought that individual files needed to be in a directory while multiple files were fine just compressed together...

> That, or there might be an easier solution I'm not seeing.

When using unrar in the shell you can either escape the spaces or surround the filename with quotes.

```
 unrar e "Name of the file.rar"
```

works just as well as

```
unrar e Name\ of\ the\ file.rar
```

which is why I thought changing $file to "$file" would work, but for some reason it wasn't to be. I'm sure it's a simple matter of syntax or something. I'll figure it out eventually :)

---

### Post by lotheac on 2006-04-19
Well actually it just occurred to me it's not about escaping whitespaces or quoting the filename, it's because 'for file in $(ls *rar)' runs the loop for every whitespace-delimited word one by one -- ie. "Name of the file.rar" triggers the loop four times, for "Name", "of", "the" and "file.rar". There's a somewhat simple workaround, and that's using 'ls -b *rar'. This would make ls output "Name\ of\ the\ file.rar" instead of "Name of the file.rar" and the script should work correctly.

---

### Post by jazzmuzik on 2006-04-19
```
for file in $(ls *rar)
```

This works for me:

for file in *rar

---

### Post by lotheac on 2006-04-20
Or that. Let's try again... I'm still learning.
```
#!/bin/bash

for file in *rar
   do if (( `unrar l $file | tail -n 2 | grep -v ^$ | awk '{print $1}'` != 1 ))
        then unrar e $file ${file%\.rar}/
   else 
        unrar e $file
   fi
done
```

This will create directories with the filename minus the extension, which in my opinion is nicer than what I had previously... but it required some googling :)

Also I found out that unrar will accept another directory to extract to only if it has a forward slash, which shortens the script slightly.

---

### Post by Jose Catre-Vandis on 2006-05-24
Thanks the use of the double quotes to allow for spaces in the compressed file names is a useful tip. I had a batch of files to unrar, all password protected. Used the following:

```
unrar e -y "*.rar"
```
(e -> extracts to current directory, -y -> suppresses confirmations etc)

Typed the password once and the whole lot got done. I know this doesn't strictly fit in with the need above, but the thread helped me, and had to share success!

---

### Post by rascalli on 2007-10-07
how does this work if I have .r00 and so on files ?

Does it extract them also ?

I tried this script.
but it only works in the folder that has the rar's

my set-up is : 

/storage -->> /storage/movies -->> /storage/movies/movie1/ -->> /storage/movies/movie1/CD1
/storage -->> /storage/movies -->> /storage/movies/movie1/-- >>storage/movies/movie1/CD2
/storage -->> /storage/movies -->> /storage/movies/movie1/ -->>/storage/movies/movie2/

Would it be possible to make a script for this ?

or to avoid doing this in the future an script for glftpd that comes in after upload is completed

---

### Post by Mediapirate on 2008-08-21
Yea because the fact that you have to go into the actual directory makes it useless to me as I only have one thing i need to extract in each directory.

Is there a way of doing it so it extracts all the directorys AND subdirectories?

Thanks.

Edit:

Not sure if anyone really cares but:
> find . -name *.rar -execdir rar e '{}' ;

That's how to do subdirectories as well!

And for files with part01.rar.

Change it to:
> find . -name *part01.rar -execdir rar e '{}' ;

---

### Post by chagos on 2011-05-05
The next bash script doesn't work for archive that have spaces or special characters in their names
```
#!/bin/bash

for file in *.part1.rar
   do unrar x $file ${file%\.part1.rar}/
done
```

I 've enclosed file names like this: '*.part1.rar'
but not works.
Any ideas ?

---

### Post by erind on 2011-05-05
Simply double quote the variable *file*:

```
#!/bin/bash

for file in *.part1.rar
  do 
    unrar x "$file" "${file%.part1.rar}"/
  done
```

---

### Post by chagos on 2011-05-05
Thanks, it works!

Is possible to check if a rar archive name contain these characters: part1, or part01, or part001 and if don't, run the extraction command somehow like in the post above ?
Or simply, if it's monovolume or not.

---

### Post by erind on 2011-05-05
> **chagos said:**
> Thanks, it works!

Is possible to check if a rar archive name contain these characters: part1, or part01, or part001 and if don't, run the extraction command somehow like in the post above ?

If I understand correctly, you can try something along the lines of: 

```
#!/bin/bash

ls *.rar | egrep -v '(*.part[0-1]{1,3}.rar)' | 
 while read file
  do 
       unrar x "$file" "${file%.rar}"/
  done
```But I believe you're looking for something more general, which runs for every rar file:

```
#!/bin/bash
for file in *.rar
 do 
   unrar x "$file" "${file%.rar}"/
 done
```> Or simply, if it's monovolume or not.Sorry, I'm not following you.

---

### Post by chagos on 2011-05-06
Sorry, your code extract both single volume and multi volume rars from the current folder and create folders for every volume:

```
#!/bin/bash

ls *.rar | egrep -v '(*.part[0-1]{1,3}.rar)' | 
while read file
do 
   unrar x "$file" "${file%.rar}"/
done
```

---

### Post by erind on 2011-05-06
The codes I provided were something that you needed to work more on, given your different current requirements.
Anyway to avoid creating more directories, you need to modify this part of the script - *"${file%.rar}"*. 
You can read more on 'file globbing' and 'Parameter substitution' in:
[http://tldp.org/LDP/abs/html/regexp.html](http://tldp.org/LDP/abs/html/regexp.html)
[http://tldp.org/LDP/abs/html/parameter-substitution.html](http://tldp.org/LDP/abs/html/parameter-substitution.html)

---

