---
title: "Bash script - Conv. text file into mp3 files (one per page) of speech using Festival"
date: 2007-09-12
forum: Programming Talk
---

### Post by kentl on 2007-09-12
Hi!

I have been trying to create a Bash script, but I'm having problems. I feel that it's not very hard, but I am a beginner at using Bash.

What I want to do is turn a PDF file into spoken text in mp3s. I have "Festival" installed.

First I copy paste each page into a text file with the header "Page X". This is the only way to know which page it was, as they have different amount of text and line numbers in them. I need the Page number so that I can reference the "real document". This step is all manual, and it's not a problem for me.

Now I want to turn these pages into spoken text in mp3 files. I have the "design" of the script. But I don't know how to implement it. :-( If someone could help me I would appreciate it a lot! I don't think a big script is necessary, but my Bash scripting skills are too weak.

**encodepages.sh**:
[LIST=1]
[*]Take INPUTFILE as in argument
[*]Split INPUTFILE into "one page per file" by matching the substring "Page X\n" where X is a number >=1. The files should preferably be named INPUTFILE+_page1, ... , INPUTFILE+_pageN. The set of new files produced by this step is referred to as NEWFILES.
[*] For each SPLITTEDFILE of these NEWFILES. Do a "cat SPLITTEDFILE|text2wave|lame - SPLITTEDFILE.mp3
[/LIST]
Example of how this script would look "in action":
```

$ ls
overview.txt
$ cat overview.txt
Page 1

This is some text on the first page. You will get an idea of what I mean so I will just type blah from now on.

Blah blah blah blah blah blah blah.

Page 2

Some more blah blah blah blah blah blah blah. Blah blah blah blah blah blah blah blah blah blah blah blah blah blah blah blah.

Page 3

And the last page of blah blah blah blah blah blah blah blah blah blah blah blah blah blah blah blah blah blah blah blah.

Blah blah blah blah blah blah blah blah blah blah blah blah blah blah blah.
$ encodepages overview.txt
((( I don't know the exact output to stdo, some encoding information from lame etc )))
$ ls
overview.txt
overview_page1
overview_page2
overview_page3
overview_page1.mp3
overview_page2.mp3
overview_page3.mp3

```

I guess the script will only be four or five lines? I hope someone can help me or give me some hint on how to do it.

---

### Post by McNils on 2007-09-12
I have a realy simple perl hack for you :)

```

my $file = $ARGV[0];

my $out = "${file}_page$start";

open(F,$file);
my @files;
while (<F>) {
    if (/^Page (\d+)$/) {
	$out = "${file}_page$1";
	push @files, $out;
	open(B, ">$out");
	next
    }
    print B $_;
}

for my $f (@files) {
    my $cmd = "cat $f|text2wave|lame - ${f}.mp3";
    system($cmd);
}

```

Use like this. You wrap this inside a bash skript... 
perl skript.pl file

---

### Post by kentl on 2007-09-12
Thank you! I think your solution was nice, very compact and did what it was supposed to do. I actually solved it myself as well, using a Python script.

Defenitely not as compact as yours, mine's a hack. My list of defences (hehe) include:
[LIST]
[*]I learned (parts of) Python while doing it
[*]I am very tired
[*]hm...
[*]I am tired? ;-)
[/LIST]
Anywho, here's my version:
```

#! /usr/bin/python

# *********************************************************
# * Initialize                                            *
# *********************************************************


import sys, re, os

if len(sys.argv) != 2:
    print "Which file do you want to split and encode?"
    sys.exit(1)

inputfilename = sys.argv[1]

print "The input file is: " + inputfilename

try:
    inputfileobject = open(inputfilename, 'r')
except IOError:
    print "Can't open file for reading."
    sys.exit(1)

regexpnewfilepoint = "Page [0-9]+"
newfilepoint = re.compile(regexpnewfilepoint)

# *********************************************************
# * See that first line starts with the regexp            *
# *********************************************************

if not newfilepoint.match(inputfileobject.readline() ):
    print "The input file must have splitpattern on first line"
    sys.exit(1)
inputfileobject.seek(0) # We want to start from the beginning

# *********************************************************
# * Start processing                                      *
# *********************************************************

outfilename = ""

for line in inputfileobject:
    print "   ::   " + line.strip()
    
    if newfilepoint.match(line):
        # If there is currently an outfile open
        if outfilename != "":
            outfile.close()
            os.system("text2wave < " + outfilename  + " |lame - " + inputfilename + "_" + outfilename + ".mp3")
            
        # Open new file to write this part in
        outfilename = inputfilename + "_" + line.replace(" ","").strip()
        try:
            outfile = open(outfilename, 'w')
        except IOError:
            print "Can't open " + outfilename + " for writing."
            sys.exit(1)
    # Write current line to the out file
    outfile.writelines(line.strip() + "\n")

# *********************************************************
# * Last line in file has been processed                  *
# *********************************************************

outfile.close()
os.system("text2wave < " + outfilename  + " |lame - " + inputfilename + "_" + outfilename + ".mp3")

sys.exit(0)

```

---

