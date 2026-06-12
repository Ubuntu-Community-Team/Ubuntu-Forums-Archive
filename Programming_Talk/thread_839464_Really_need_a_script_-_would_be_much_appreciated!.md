---
title: "Really need a script - would be much appreciated!"
date: 2008-06-24
forum: Programming Talk
---

### Post by onesikgypo on 2008-06-24
Hi,

i myself am not a linux coder (though i know of some other languages, however i really havent got time to read tuts atm) - and was wondering if someone more experienced who would find this easy could help me, id really appreciate it.

Script details - there are two main dirs/files that the script will use:

/path/to/random/folder1/filename.txt
/path/to/random/folder2/

What i need the script to do, is firstly, read the 1st file i specified, that is: /path/to/random/folder1/filename.txt

In that file, the contents are as follows:

/path/to/random/folder3/file1.dat
/path/to/random/folder3/file2.dat
/path/to/random/folder3/file3.dat
(note the actual files are not file1.dat, file2.dat etc., but they all have the extention of .dat)

for each line, it needs to check the second folder i mentioned, that is: /path/to/random/folder2 - for the same filename, but with the extention .stat

So taking the first one for example,
it would check for /path/to/random/folder2/file1.stat (this will always exist)

It then needs to read the third line of that .stat file and see if it matches "String AAA"

If it matches, then the corresponding .dat line in the .txt file should be deleted, and a file should be written with that filename - so say /home/true.txt should have file1 written to it

So then, at this point, the contents of /path/to/random/folder1/filename.txt would be as follows:

/path/to/random/folder3/file2.dat
/path/to/random/folder3/file3.dat

the script would then continue to check the remaining files, doing the same process.

(note, if when it checks if the third line of the .stat files matches "String AAA" - it does not, then the script should be halted there, and the next file in the .txt file should be checked).

Also, please note, ill be running this as a cron job, so if maybe another launguage, such as python or perl would be better suited, it does not make a difference to me.

I hope ive explained that clearly, if anyone could help me out, it would be appreciated alot!

Thankyou.

---

### Post by geirha on 2008-06-24
Unless I've misunderstood something, I believe this should do what you want.
[php]#!/bin/bash

truefile=$(mktemp)
falsefile=$(mktemp)
string="String AAA"
for file in $( < /path/to/random/folder1/filename.txt); do
    statfile="/path/to/random/folder2/$(basename "$file" .dat).stat"

    # Doesn't hurt to check if the statfile exists 
    if ! [ -f "$statfile" ]; then 
        echo "$statfile not found. Aborting." >&2
        exit 1
    fi

    # if line 3 matches $string
    if head -3 "$statfile" | tail -1 | grep -q "$string"; then
        echo "$file" >> "$truefile"
    else
        echo "$file" >> "$falsefile"
    fi
done

# Overwrite the file we read with the list of all "false" files
cat "$falsefile" > /path/to/random/folder1/filename.txt && rm "$falsefile"
# move the list of "true" files somewhere?
mv "$truefile" /home/true.txt
[/php]

---

### Post by ghostdog74 on 2008-06-24
```

#!/bin/bash

awk 'BEGIN{
 folder2check = "/path/to/random/folder2/"
 q="\047"
 FS="[/.]"
}
/dat$/{
    linesstore[++e]=$0
    file2check = folder2check $(NF-1)".stat"
    testcmd = "test -f "q file2check q
    r = system(testcmd)
    if ( r == 0) {            
        #if stat file exist
        c=0
        while ( ( getline line < file2check ) > 0 ) {
          ++c
          if (c == 3 && line ~ /String AAA/) {
            toremove[$0]
            break
          }else if ( c==3 && line !~ /String AAA/) {
            break           
          }        
        }
     }else { 
      print "Stat file " file2check " does not exist"
     }     
}
END {
  for ( i=1;i<=e;i++ ) {
   if (! ( linesstore[i] in toremove )) {
      print "line sotr " linesstore[i] > "newfile.txt"
   }
  }
  cmd = "mv "q "newfile.txt"q " /path/to/random/folder1/filename.txt"
  # system(cmd) #uncomment to use
}
' /path/to/random/folder1/filename.txt

```

---

### Post by onesikgypo on 2008-06-24
thanks for the quick reply geihra, with your one, i get the following error:

mv: missing destination file operand after `/tmp/tmp.gabhi23284'
Try `mv --help' for more information.

will try ghostdog74's one now :)

---

### Post by geirha on 2008-06-24
Oops, a > has sneaked in where it shouldn't be [php]mv "$truefile" > /home/true.txt
# should've been
mv "$truefile" /home/true.txt
[/php]

---

### Post by onesikgypo on 2008-06-24
alright thanks geihra, your one works perfect now :)

i did try the script ghostdog74 posted, however, it didnt seem to work at all, there were 3 files in the "filename.txt" 2 of which should have been removed by the end. But thankyou for the time you put in it.

The only last thing i might ask geirha is whether it is possible, that in the "true.txt" only the filename is there.

So instead of

/path/to/random/folder2/file.dat

it is just

file

:)

But either way, thankyou so much!

---

### Post by ghostdog74 on 2008-06-24
> **onesikgypo said:**
> 
i did try the script ghostdog74 posted, however, it didnt seem to work at all, there were 3 files in the "filename.txt" 2 of which should have been removed by the end. 

did you uncomment the system(cmd) near the end. ?? anyway, since geirha's one works, use his.

---

### Post by geirha on 2008-06-24
> **onesikgypo said:**
> 
The only last thing i might ask geirha is whether it is possible, that in the "true.txt" only the filename is there.

So instead of

/path/to/random/folder2/file.dat

it is just

file


Changing
[php]echo "$file" >> "$truefile"[/php]
to
[php]basename "$file" .dat >> "$truefile"[/php]
should do the trick

---

### Post by onesikgypo on 2008-06-24
thankyou geihra, that worked.

and yes ghostdog74, your right, i hadnt uncommented that line, i must have missed it.

---

### Post by onesikgypo on 2008-06-24
hi, sorry, ive seemed to have picked up a bug, it seems that each time the script is run, whatever used to be in the file that it is outputing to, in the script example it is /home/true.txt , is deleted and so becomes empty, not sure why it would do this, any suggestions would be great.


<< problem solved >>

i used:

cat "$truefile" >> /home/test.txt
rm -f "$truefile"

instead

---

