---
title: "Bash script for joining multipart files - feedback/pointers needed"
date: 2006-12-18
forum: Programming Talk
---

### Post by f76 on 2006-12-18
Playing around with gentoo file manager [http://en.wikipedia.org/wiki/Gentoo_file_manager]("http://en.wikipedia.org/wiki/Gentoo_file_manager") 
i felt the need for a script to join multipart files. But u could use it just as well from Nautilus i guess.

Now that i have got mine working i thought i would post it here to see if you guys can help me w some pointers.. 

How would you make the script safer/faster?
And how would you solve the problem...
It might sound stupid to ask about a problem i have solved but i thought i could learn from some feedback. 
```
#!/bin/bash
echo "infile:"
echo "$1"
echo ""
# first sed makes sure the filename ends in .001 and replaces it w .0??
# second sed replaces spaces w backslashes
inname=$(echo "$1"|sed -e 's/\.001$/\.0\?\?/'|sed -e 's/\ /\\\ /g')
#echo $inname

# first sed makes sure the filename ends in .001 and replaces it w ""
# second sed replaces spaces w backslashes
outname=$(echo "$1"|sed -e s/\.001$//|sed -e 's/\ /\\\ /g')
#echo $outname
wholecommand=$(echo "cat $inname > $outname")
echo "command:"
echo $wholecommand
#it took some time to figure out this one:
eval $wholecommand

#to keep "gnome-terminal -w" open 
echo "******* Press <Enter> to continue ********"
read NAME
echo "$NAME!" 
```

---

### Post by duff on 2006-12-18
I'm not sure exactly what you're looking for.  But I've got a few comments.

1) Use "basename" instead of sed'ing away the extension
```
inname="$(basename "$1" 001)0??"
outname=$(basename "$1" .001)

```Should be the same thing you're trying to achieve

2) Why are you escaping the spaces in the file name?  Just use "$1" instead of $1 everywhere are you'll be find

3) What's with the $wholecommand variable?  Just put "cat $inname > $outname".  If it's only for debugging (so you can see what's actually being executed), start you're script with "set -x"

---

### Post by po0f on 2006-12-18
f76,

Why not just:
```
[FONT="Courier New"]$ cat filepart.001 filepart.002 filepart.003 > file[/FONT]
```

Or am I somehow missing what this script does?

---

### Post by f76 on 2006-12-18
You are ot really missing anything. I thought i would make it easier for myself in case i have 10+ splitfiles... so i just can send the first files name from a file manager and get cat to join i all together.

---

### Post by giruzz on 2006-12-18
Hi,

I'm just wondering..Have you created the script? If yes..can I have a look?

thanks

(I'm n00b with linux)

bye

g.

---

### Post by f76 on 2006-12-21
Yes its basically what i posted in the first posting.

---

### Post by francisco_athens on 2009-02-14
```
ls -1 -Q *.001 | awk -F'.' '{print $1"."$2"\"""\ "$1"."$2".\?\?\?\""}' | xargs -l1 par2repair
```

This is a one-liner to take care of a folder of files that looks like this:
```

file1 space [123456a].ogg.001
file1 space [123456a].ogg.002
file1 space [123456a].ogg.003
file1 space [123456a].ogg.004
file1 space [123456a].ogg.005
...
file1 space [123456a].ogg.par2
file1 space [5321fff].ogg.vol00+01.PAR2
file1 space [5321fff].ogg.vol00+02.PAR2
...
file2 space [5321fff].ogg.001
file2 space [5321fff].ogg.002
file2 space [5321fff].ogg.003
file2 space [5321fff].ogg.004
file2 space [5321fff].ogg.005
file2 space [5321fff].ogg.006
....
file2 space [5321fff].ogg.par2
file2 space [5321fffa].ogg.vol00+01.PAR2
file2 space [5321fff].ogg.vol00+02.PAR2...
file3...
and so on...
```

it will use AWK to process filenames, pass those on to par2repair (which can join the split files and verify/repair them if there are PAR2 files).
Full explanation on [Free Like GNU]("http://www.freelikegnu.org/?p=79")

---

