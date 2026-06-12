---
title: "regex search and create new files"
date: 2011-08-07
forum: Programming Talk
---

### Post by thaitang on 2011-08-07
I have a huge html document I have created from an online book that I want to format in small-size chunks for my "old" mobile phone. There is about 500-ish chapter size chunks i want to split the doc into. I created the following links in the doc to allow hyperlinking to the chapter headings, which would be a nice place to chop each section.
```
<a href="#canItoc" name="canItxt" style="text-decoration:none">Canto I</a>: Nárad</font><br>
```I am pretty sure sed is out of its depth doing something like this but, I would like to run a oneliner that searches for regex ```
/^<a href="#can([IVXCL]{1,7})/
``` and copies all of the following lines until it finds the next occurrence of ```
/^<a href="#can([IVXCL]{1,7})/
``` and starts a new file. The file would ideally be named using the regex found. I think awk might be a solution but unfortunately I am pretty awk-ignorant. if anyone can rip off a oneliner for this that would be great.

PS I am often re-formatting e-books to better display on my old mobile phone. So actually this oneliner would allow me to edit entire books and then split them up after, which would save me a lot of time editting individual chapters.

thanx
tt

---

### Post by thaitang on 2011-08-07
Ok so a really ugly solution using sed is:
```
sed -ri '/<a href="#can.*<br>$/N;s/<br>\n(<font|<b>|\&#)/<br>\1/g'
```It works, but the command needs to be iterated, well in some cases probably 500 times. Afterwards each chapter is contained on a single line which might make it easier to dump single lines to their own files? But really there is surely a cleaner solution than this?
cheers,
tt

---

### Post by dethorpe on 2011-08-09
Not a one liner, but a quick and dirty perl script that may do what you are after, can can easily be modified if not.
 
```
 
#! /usr/bin/perl
use strict;
use warnings;
 
my $chapter_fh;
 
# loop through all lines of file name passed on stdin
while (<>) {
    # check for chapter start
    if (/^<a href="#can([IVXCL]{1,7})/) {
        print "Found chapter $1\n";
        # close the current chapters file if opened
        close $chapter_fh if $chapter_fh;
        # open the new file for the next chapter
        open ($chapter_fh,'>',"$1.html") || die "Can't open file $1. $!";
    }
    # print the line to the current chapter file
    print $chapter_fh $_;
}
close $chapter_fh;
 

```
 
 
Save it as a file called split.perl (ot any other name of your choice) and run as:
 
```
./split.perl <filename of book to split>
```

---

