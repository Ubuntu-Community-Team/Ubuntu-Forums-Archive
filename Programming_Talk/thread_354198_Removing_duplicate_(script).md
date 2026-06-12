---
title: "Removing duplicate (script)"
date: 2007-02-05
forum: Programming Talk
---

### Post by runder on 2007-02-05
Not sure if this goes in this forum.. but it's in someway, bash/shell programming.

On my ubuntu box, I have many files named differently, but some of them are identical files.  I know that they are identical files if I do a md5sum check:

00bd06279cdceebd00a5c2affd1a61de  442833.jpg
00bd06279cdceebd00a5c2affd1a61de  459126.jpg
020bd9104e4885dadf2d68ebf05ded90  441197.mpg
020bd9104e4885dadf2d68ebf05ded90  459154.mpg
0222fb53039255c90ca91d6bd8d6cd1f  335629.jpg
0222fb53039255c90ca91d6bd8d6cd1f  339704.JPG
0222fb53039255c90ca91d6bd8d6cd1f  484299.JPG

All the md5sum of my files are stored in a single text file.  So I was thinking of making a script that would go through this list and remove from my hard drive every duplicates and leave only one left (in this case, delete for example, 339704.JPG and 4842999.JPG but keep 335629.jpg - I need just one copy of each).

What is the best way to remove all these duplicate files and keep only a single one?

Is there a tool downloadable from apt-get that I can do this?
Am I reinventing the wheel by attempting to create a script that will compare this md5sum text file and then delete the duplicate content of my hard drive?

---

### Post by Tomosaur on 2007-02-05
Never mind, wont have time, **deadlines** :O

---

### Post by clouserw on 2007-02-06
Here is a short perl script that should do what you want.  It assumes the text file is called "file.out" and everything is in the same directory.  As always, be wary of code other people give you, make a backup, your mileage may vary, etc.

```

#! /usr/bin/perl

my $file="file.out";

my %pile_o_md5sums = ();

if (!open(FH,"<$file")) { 
    print "Cannot open input file: $file\n";
    exit;
}

while (<FH>) { 

    if ($_ =~ /(.+) (.+)/) { 
        if ( exists $pile_o_md5sums{$1} ) { 
            print "Removing $2 due to conflict with $pile_o_md5sums{$1}\n";
            unlink($2) or print "Failed to remove $2!\n";
        } else { 
            $pile_o_md5sums{$1} = $2;
        } 
    } 

}

print "done.\n";

```

---

### Post by glotz on 2007-02-06
Here's one semi-automatic script [http://elonen.iki.fi/code/misc-notes/remove-duplicate-files/](http://elonen.iki.fi/code/misc-notes/remove-duplicate-files/)
There's also a tool in the repos I've used, findimagedupes

---

### Post by runder on 2007-02-06
Thanks.  I'll try what you guys suggested.

---

