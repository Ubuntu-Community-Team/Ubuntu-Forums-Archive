---
title: "Perl - Files in a Folder"
date: 2008-07-09
forum: Programming Talk
---

### Post by vicpascow on 2008-07-09
I have ~100 files in a folder.

Each file has one line of data.
  For example, File42342340.csv:
     1,2,342,245,456,45,476
  Another example, File3420.csv:
     34,342,34,234,234

I want to iterate through every file in this directory, making a new file that has all of the data in it, seperated by line.

So, the file will look like this:
    1,2,342,245,456,45,476
    34,342,34,234,234

Just wondering if there is a quick way to do this?

---

### Post by AOZ on 2008-07-09
Now i have never programmed in perl, only java and C++, so this could be comletely wrong. but if all the filenames are named "File*.csv" could you not have some kind of loop that looks for every filename File*.csv with the CLI * wildcard? Read each fiel write to a new one and keep reading and writing till u have one file? Im sorry if this has been completely useless btw

---

### Post by apmcd47 on 2008-07-09
```

#!/bin/perl 

print  while(<>);

```
untested.

If it is called pcat: 
```

pcat *.csv > new.csv

```

---

### Post by ghostdog74 on 2008-07-09
> **vicpascow said:**
> I have ~100 files in a folder.

Each file has one line of data.
  For example, File42342340.csv:
     1,2,342,245,456,45,476
  Another example, File3420.csv:
     34,342,34,234,234

I want to iterate through every file in this directory, making a new file that has all of the data in it, seperated by line.

So, the file will look like this:
    1,2,342,245,456,45,476
    34,342,34,234,234

Just wondering if there is a quick way to do this?
unless you really want it in perl
```

# cat File* >> newfile.csv

```

---

### Post by apmcd47 on 2008-07-10
> **apmcd47 said:**
> ```

#!/bin/perl 

print  while(<>);

```
untested.


Oops! You don't even need the while:
```

print (<>);

```
should do it.
Also look at *glob* in the *perlfunc* man page.

I also agree with ghostdog74 that you really only need cat, but presumably you want to do this from within a larger perl application?

Andrew

---

### Post by henchman on 2008-07-10
what is the  difference between > and >> btw?

```


$ cat HTTP* > all.c
$ cat HTTP* >> all2.c
$ md5 all.c all2.c
b5901c2be8e17509612aa2d701ab8a95	all.c
b5901c2be8e17509612aa2d701ab8a95	all2.c



```

thanks :)

---

### Post by apmcd47 on 2008-07-10
> **henchman said:**
> what is the  difference between > and >> btw?



thanks :)

> replaces and >> appends:
```

$ echo "Hello sailor" > a1
$ echo "Hello sailor"> a2
$ echo "Hello world" > a1
$ echo "Hello world" >> a2
$ cat a1
Hello world
$ cat a2
Hello sailor
Hello world

```
...but now we're going off topic.

Andrew

---

### Post by vicpascow on 2008-07-10
Here is what I have so far:

```
#!/usr/bin/perl -w
use strict;
use warnings;
	
opendir (DIRECTORY, $ARGV[0]); 
open (OUTPUT, ">results.csv"); 

my $file;

while (defined($file = readdir(DIRECTORY))) {
	print OUTPUT $file;
}
		
print "Completed.\n";

close(OUTPUT);
closedir(DIRECTORY);
```


Unfortunately, this just prints out the names of the file, and not the data within each file.  Would you recommend making a subroutine to open each file?

What is the best way to do this?  I tried using the print (<>); but to no avail...

---

### Post by ghostdog74 on 2008-07-10
what do you mean no avail. ? At least show what errors you have got. 
```

#!/usr/bin/perl
while (<>) { print; }

```

---

### Post by vicpascow on 2008-07-10
Running just that script creates an infinite loop for me.

Running this:

```
#!/usr/bin/perl -w
use strict;
use warnings;
	
opendir (DIRECTORY, $ARGV[0]); 
open (OUTPUT, ">results.csv"); 

my $file;

while (defined($file = readdir(DIRECTORY))) {
	while (<>) { print; }
}
		
print "Completed.\n";

close(OUTPUT);
closedir(DIRECTORY);
```

Gives me the message: Can't do inplace edit: C:\DirectoryName\ is not a regular file at script.pl line 11.

---

### Post by ghostdog74 on 2008-07-10
> **vicpascow said:**
> Running just that script creates an infinite loop for me.

how are you running it? 
```

# ./myperlscript.pl file1 file2 file3 > newfile

```

---

### Post by vicpascow on 2008-07-10
perl C:\Scripts\script.pl C:\Directory

---

### Post by vicpascow on 2008-07-10
Because I have ~100 files, I just want to iterate through them.

---

### Post by ghostdog74 on 2008-07-10
then pass in wildcards
```

# ./myperlscript.pl *.csv

```
please try to experiment with your script before posting.

---

### Post by vicpascow on 2008-07-10
So, I did get this to work with your script, however, I still have the issue about iteration, however.

---

### Post by apmcd47 on 2008-07-10
> **vicpascow said:**
> Running just that script creates an infinite loop for me.

Running this:

```
#!/usr/bin/perl -w
use strict;
use warnings;
	
opendir (DIRECTORY, $ARGV[0]); 
open (OUTPUT, ">results.csv"); 

my $file;

while (defined($file = readdir(DIRECTORY))) {
	while (<>) { print; }
}
		
print "Completed.\n";

close(OUTPUT);
closedir(DIRECTORY);
```

Gives me the message: Can't do inplace edit: C:\DirectoryName\ is not a regular file at script.pl line 11.

The *while (<>)* opens the arguments to the script as files and the only file you have given is the directory name. Try replacing the *while (<>)* with ```
print OUTPUT do { local( @ARGV, $/ ) = $file ; <> }
```
and see what that does.

Oh, and make sure the new file you open isn't in the directory you are reading. If it is put in a check that the present $file is not your output file, else the infinite loop.

Andrew

---

### Post by apmcd47 on 2008-07-10
> **ghostdog74 said:**
> then pass in wildcards
```

# ./myperlscript.pl *.csv

```

He seems to be doing this on a Windows box. The wildcard probably won't get expanded, so perl will find ARGV[0] contains "*.csv".

He could try ```
@ARGV=glob @ARGV;
``` to expand the wildcard from within the perl script. I've never tried that.

... You're not *really* using the root prompt?

---

### Post by ghostdog74 on 2008-07-10
> **apmcd47 said:**
> He seems to be doing this on a Windows box. The wildcard probably won't get expanded, so perl will find ARGV[0] contains "*.csv".

have you tried on a windows box?

---

### Post by apmcd47 on 2008-07-10
> **ghostdog74 said:**
> have you tried on a windows box?

Not recently - I don't have perl on my Windows box. 

Andrew

---

### Post by badperson on 2008-07-10
okay, what the hell, I would do it like this, might be better ideas, but here goes:

```

my @csvFiles = glob(pathToFiles/*.csv) or die "can't open directory $!\n";
my @compileddData;

foreach my $c(@csvFiles){
open (CSV, "$c");
   while(<CSV>){
   push (@compiledData, $c);
   } #end while


} # end foreach

open (NEW, ">yourNewFile.csv");
foreach my $line(@compileddData){
print NEW $line, "\n";

}

```

people probably have other (very possibly better) ways, but I write that kind of script a lot. 
bp

---

