---
title: "Bash question"
date: 2008-04-18
forum: Programming Talk
---

### Post by docetes on 2008-04-18
Hi,

I've been out of the linux scripting loop for almost a  year and now I'm using stupid windows in work. My problem is, I have about 1.4GB of text files which I found through a search. Some of  these files have the same names so I can't just copy and paste from the search result. Any one got any ideas??

I was thinking of copying each file to a recreated folder structure.

Any help would be greatly apreciated cos I'm stuck on this one

---

### Post by ajgreeny on 2008-04-18
If you are using ubuntu to copy the files you could use rsync and add the -R option which adds the full path to the file name and shopuld allow the transfer of files with same names but different source folders.  Have a look at **man rsync**

If using windows, I haven't got a clue if it's possible.  Good luck!

---

### Post by docetes on 2008-04-18
the files are on a server which i can mount on an ubuntu laptop.   I have to search for the files with a certain word it and then copy them across to a new folder but some of the files are named the same(but are in different folders on the server).

would rsync work for this?

---

### Post by scorp123 on 2008-04-18
> **docetes said:**
> the files are on a server which i can mount on an ubuntu laptop.   I have to search for the files with a certain word it and then copy them across to a new folder but some of the files are named the same(but are in different folders on the server).

would rsync work for this? I once had to write something similar. There were several thousand of Word documents stored in a content management system and all those documents had the name **KB*xxxxxx*.doc** where "xxxxx" were numbers. Each document was sitting in its own subdirectory ... But when we wanted to migrate all those documents into the same directory and give them filenames that made more sense to a human I was facing this problem: How in the world am I supposed to rename several thousand Word documents? Open every single one of them and read what they are about and then change the filename based on that? Thank you but no thank you.

So I came up with this script. It uses the "wv" package (you have to install it -- "wv" can be used to manipulate Word documents from the command shell) and the wvSummary program from that package to find out what the internal document title is and then it renames the file "KB****.doc" based on that.

So as you are dealing with text files maybe you can exchange those parts with something that would make more sense, e.g. a "grep" of sorts that scans the content of the text file?

here is my script:
```
 batch_renamer.sh 

#! /bin/bash
for i in $( ls KB????.doc ); do
        OLDFILE=`echo $i | cut -d. -f1`
        # scan for the internal document title
        # and get rid of any special characters
        # so we get filenames that don't cause problems
        TITLE=`wvSummary $i | grep title | cut -c 13- | sed "s/[\.\:\/\'\+\{\}\;\"\\\=\?~\(\)\<\>\&\*\|\$]/ /g" | cut -c -100`

        NEWNAME=$OLDFILE"$TITLE"".doc"
        mv -v $i "$NEWNAME"
done 
```

---

### Post by ghostdog74 on 2008-04-18
```

find /full_path_here -type f -name "pattern.ext" -printf "%p\n" | awk 'BEGIN{ q="\047";dest="/destination" }
{
 old=$0
 sub(/^\//,"")
 gsub(/\//,"_",$0)
 cmd="mv "q old q" "q dest"/"$0 q
 system(cmd) 
 }'

```

---

### Post by pmasiar on 2008-04-18
midnight commander has nifty feature: compare directories, and it will show you which files are new or updated in each directory (and then you can pick which ones you want to copy/overwrite, even pick one-by-one if you want to). And mc has many more cool features, the best file manager since '83 or so.

---

### Post by scorp123 on 2008-04-19
> **pmasiar said:**
>  compare directories, and it will show you which files are new or updated in each directory (and then you can pick which ones you want to copy/overwrite, even pick one-by-one if you want to) Now that you mention it ... "unison" can do that too, also over a network  ... It's a GUI program. Just in case someone doesn't like midnight's text-based interface then they could give "unison" a try.

[http://en.wikipedia.org/wiki/Unison_%28file_synchronizer%29](http://en.wikipedia.org/wiki/Unison_%28file_synchronizer%29)

---

