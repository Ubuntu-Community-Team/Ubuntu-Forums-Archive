---
title: "Output from diff"
date: 2008-04-23
forum: Programming Talk
---

### Post by EvilMarshmallow on 2008-04-23
Hey all,

I'm working on a project where I periodically download a text file and see if there is anything new appended to it since the last download.  I think a bash script with **diff** will do what I need, but I need a little help formatting it.

Currently it does this:

2c1
> 2,4,6,8,10

What I'd like is to only get the new text piped into a temporary text file... so that when I run it, my temp file will have only the 2, 4, 6, 8, 10, without the superfluous info.  

How might I accomplish such a thing?

---

### Post by ghostdog74 on 2008-04-23
maybe you want to [check]("http://www.linuxselfhelp.com/gnu/diffutils/html_chapter/diff_3.html") this out first. Good read

---

### Post by Can+~ on 2008-04-23
Like doing 

```
diff file1 file2 > /tmp/diffoutput.txt
```

*edit: wrong forum, heh*

---

### Post by EvilMarshmallow on 2008-04-23
Can+~, you're almost to where I need to go!  I knew how to redirect the output, but the problem is that diff adds that junk in front of the file's contents.  My file comes out looking like this:

1a2,4
> 2,4,6,8
> 2,4,6,8
> 2,4,6,8

But I want the output file to look like this:

2,4,6,8
2,4,6,8
2,4,6,8

I read about line formats in the link ghostdog provided but I can't get them to work the way I want... when I do

diff --line-format='%L' test1 test2

I get a consolidated output of all the records, not just the ones that are different.  What did I do wrong?

---

### Post by unutbu on 2008-04-23
This script will only show those lines from the output of diff which begin with '>'.

```
#!/usr/bin/perl
use strict;
use warnings;

my ($file1,$file2);
$file1=shift @ARGV;
$file2=shift @ARGV;

open(DIFF,"diff $file1 $file2 |") || die;
while (<DIFF>) {
    next if (/^[^>]/);
    s/^>\s+//g;
    print;
}
close(DIFF);

```

Save it as 'sdiff' (short diff?).
Usage:

```
sdiff file1 file2 > sdiff.out
```

---

### Post by ghostdog74 on 2008-04-23
if that's the case, 
```

diff file1 file2 | awk '/^>/{gsub(/>/,"");print}'

```

---

### Post by kragen on 2008-04-23
Ideally you want to use some sort of diff api, rather than trying to mangle the output of another program.

---

### Post by stroyan on 2008-04-23
If you know that the file is just getting longer then you don't really need a diff of the files.  You can use dd and skip to the new part of the new file.
This example uses the stat command to get the old file length to skip.
```

dd bs=1 skip=$(stat -c %s file1) if=file2 2>/dev/null

```

---

### Post by EvilMarshmallow on 2008-04-24
Every now and then (probably once per day), the file that I download will be smaller than the previous version because the system I'm monitoring has reset the data file.

Ghostdog's use of awk does exactly what I need.  I figured it would be something like that, but I'm still quite the noob and my awk-fu is virtually nonexistent as of yet.

Stroyan's idea is interesting... I may use part of it to decide whether the file should be diff'd with the older one... in the case of a file reset, the results of a diff would be all the records, even the ones from the older file, right?  So perhaps checking the stat on the new one to see if it's longer or shorter is a really good idea (which should always be obvious, I'm running this in a cron job every 1-2 minutes, monitoring a process that happens probably every 45 seconds or so).

Thanks everyone for your help...

---

### Post by gug@fnal.gov on 2008-04-24
diff -u $file1 $file2 | grep "+" | grep -v "@@" | sed-e"s%+%%"

Not as elegant as some of the other suggestions.

---

