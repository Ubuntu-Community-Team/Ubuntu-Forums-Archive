---
title: "batch editing problem."
date: 2007-02-15
forum: Programming Talk
---

### Post by ac7ss on 2007-02-15
I have a scripting problem that I hope someone can help me with.

I have a problem that can be summarized with the following file:

```
...
tagA
... 
labelG
...
tagB
...
labelG
...
tagA
...
labelG
...
```

The ... represent several (unknown #) of lines that do not contain either [tag.|label.] lines. The script I am looking for should read the tag lines, and change the next occuring label line based on the tag line. (a seperate pass would be acceptable for each tag type. they are fixed fields with known possible values.) The format is fixed, ie. there will never be two labels before another tag is found.

I am sure that there is an easy way to do this in sed or awk. but I havn't found it yet.

Thanks.

---

### Post by LotsOfPhil on 2007-02-15
Here it is in perl. I hope perl is acceptable.
```

#!/usr/bin/perl
$file = 'file';
open(infile, "<$file") or die "Cannot open $!";
@contents = (<infile>);
close(infile);
open(outfile, ">$file") or die "Cannot open $!";
                                                                                
foreach $line (@contents) {
        chomp($line);
        if($line =~ /tag/){
                print "Tag found!\n";
                $tag = substr($line,3);
        }
        if($line =~ /label/) {
                print "Do whatever you need since the tag is $tag.\n";
                $line = $line;
        }
        print outfile "$line\n";
}
                                                                                
close(outfile);

```

You'll need to change the "$line = $line" file to whatever you want.

---

### Post by WW on 2007-02-15
Here is a Python version.  It acts as a filter: it reads from stdin and writes to stdout.
```

#!/usr/bin/env python

import sys
import string

linenumber = 0
label_linenumber = -1
tag = None

for line in sys.stdin:
    linenumber = linenumber + 1
    if line[0:5] == "label":
       # Found a label
       if tag == None:
           # Error...
           s = str(linenumber)
           sys.stderr.write("Error:  Misplaced label at line "+s+".")
           if (label_linenumber > 0):
               sprev = str(label_linenumber)
               sys.stderr.write(" Previous label occurred at line "+sprev+"\n")
               sys.stderr.write("Error:  Missing tag between lines "+sprev+" and "+s+"?\n")
           else:
               sys.stderr.write("  Missing first tag?\n")
           break
       label = line[5:].strip()
       label_linenumber = linenumber
       # What should we do with the label?
       # This code will print the label followed by the tag in brackets.
       print "label", label+'['+tag+']'
       tag = None
    elif line[0:3] == "tag":
        # Found a tag
        tag = line[3:].strip()
        # Handle the tag line here.  I just print it.
        print line,
    else:
        # Not a tag or label, so just print it.
        print line,

```
If you don't want to check for misplaced labels, you can remove the 'if tag == None' line and its associated block of code.

---

### Post by ac7ss on 2007-02-15
> **LotsOfPhil said:**
> Here it is in perl. I hope perl is acceptable.
```

#!/usr/bin/perl
$file = 'file';
open(infile, "<$file") or die "Cannot open $!";
@contents = (<infile>);
close(infile);
open(outfile, ">$file") or die "Cannot open $!";
                                                                                
foreach $line (@contents) {
        chomp($line);
        if($line =~ /tag/){
                print "Tag found!\n";
                $tag = substr($line,3);
        }
        if($line =~ /label/) {
                print "Do whatever you need since the tag is $tag.\n";
                $line = $line;
        }
        print outfile "$line\n";
}
                                                                                
close(outfile);

```

You'll need to change the "$line = $line" file to whatever you want.

How well will this work with a 2 meg text file? Other than that I think I can see how it works. I assume that there is an easy way to replace just a portion of the label line. I will see if I can find that myself.

I haven't tried pearl yet. and size is why I was using sed before. Can i use $1 or somesuch to enter the filename in a script?

thanks.

---

### Post by LotsOfPhil on 2007-02-15
I don't know about the size. 2 meg sounds like a lot, but in terms of the RAM on the machine it's not. I really have no idea.

As far as $1, the equivalent is $ARGV[0]

Just change
 $file = 'file';
     -to-
 $file = $ARGV[0];

If you need help with the changing label part, just ask.

---

### Post by ac7ss on 2007-02-15
turned out not to be a problem. Figured out the s/// for replacing the field as well.  Thank you everyone!

I gotta learn Perl now...

---

### Post by ac7ss on 2007-02-16
Well it looks like the perl was the solution I was looking for. I am able to expand it now to do all of the changes I wanted to do in a single pass. Works somewhat quickly as well. (around 675 changes total, minimal (<3 seconds) time.)

Not that anyone here cares, but I am using it to modify Geocaching.com's .gpx files so that the short cache names reflect the type and difficulty of the cache. I will post the script on the geocaching site when complete.

---

