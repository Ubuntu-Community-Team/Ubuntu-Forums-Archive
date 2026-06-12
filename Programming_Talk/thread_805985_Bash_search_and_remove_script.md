---
title: "Bash search and remove script"
date: 2008-05-24
forum: Programming Talk
---

### Post by Redscare on 2008-05-24
I have just started bash programming, moving from a C++ background, and find it very interesting. I actually have a job that I need to get done though, and was wondering if it could be done using bash, and I don't really have the time to search and experiment for the answer. I am editing a "customer's" webpage (just a side job so i can buy a decent computer) and what I need to do is remove references to certain pages from tables in mulitple other pages. What I need to do is remove the bolded text from every html file in a directory given remove.html(STUFF TO KEEP and STUFF TO REMOVE indicate that the text at those locations varies):
```

<table STUFF TO KEEP
   <tr STUFF TO KEEP
     <td STUFF TO KEEP 
     STUFF TO KEEP /td>

[B]  <td STUFF TO REMOVE 
         STUFF TO REMOVE remove.html STUFF TO REMOVE
     STUFF TO REMOVE /td>[/B]

     STUFF TO KEEP/tr>
STUFF TO KEEP /table>
```
Thank you very much in advance. As an added bonus would it be possible to check all the files without inputting remove.html and to check whether each reference to an html file exists, and if it does not remove it's corresponding line?

---

### Post by randallecook on 2008-05-24
Redscare,

How many total changes do you expect to make (files times edits within each file)? If it is only a dozen or so, I recommend just doing it manually. Yes, I know that learning to write a script to do this is a goal in and of itself, but if you are new to scripting, automated editing of code files is very risky.

I also come from a C++ background and would not trust my scripts to a task like this. There is only one way for it to be done right, and any number of ways for it to be done wrong. Obviously there are some script ninjas out there who can do this in their sleep (and probably do) :) Of course, if I had to modify hundreds of files, the effort to develop, debug, and test an automated tool is justified.

If you want to go the manual route, here is a script I use to identify all files that contain a certain string:

```

#!/bin/sh
# find in files

if [ $# -lt 2 ]
then
        echo "Usage: $0 dir string"
        echo "       Search recursively through dir for files containing string"
        exit 1
fi

find "$1" -type f | xargs grep -n "$2"

```

I usually call it 'fif' and use it like this:

fif /usr/include snprintf

Lastly, bash might not be the best tool for this. Perl or sed/awk might be more appropriate.

I hope this helps.

Randall

---

### Post by Redscare on 2008-05-24
Thanks for the reply, but the case is that there's a ton of files that need modifying, and i don't mind experimenting and testing i've got backups galore:). 

Using sed/awk was what i had in mind, i was wondering what parameters to pass. Is my impression that sed and awk are a part of bash wrong? Thanks again.

---

### Post by unutbu on 2008-05-24
redscare, I think this works.
Save this script as 'fix-html.pl':

```
#!/usr/bin/perl
# Usage: fix-html.pl remove.html ~/tmp/test/

use strict;
use warnings;
use File::Find;
use File::Spec;
use File::Path;
use File::Basename;
$/="";


my $pat=shift @ARGV;
my $dir=shift @ARGV;
$dir=File::Spec->rel2abs($dir);

#warn "dir=$dir";
die unless (-d $dir);

my ($dirname,$dirpath,$suffix) = fileparse($dir,qw());
#warn "($dirname,$dirpath,$suffix)";

my $newdir=File::Spec->catdir($dirpath,$dirname."-fixed");
#warn "newdir=$newdir";

my %options=(wanted=>\&process,no_chdir=>1);
find(\&process,$dir);

sub process {
    my $file=$File::Find::name;
    return unless (-f $file);
    # warn "file=$file";

    my $newfile=$file;
    $newfile=~s/^$dir/$newdir/;
    # warn "newfile=$newfile";
    my ($name,$path,$suffix) = fileparse($newfile,qw());
    mkpath([$path], 1, 0755);

    open(FILE,"<","$file") || die;
    open(NEW,">","$newfile") || die;
    while (my $line=<FILE>) {
	if ($line=~m|$pat|s) {
	    $line=~s/\s*<td(?!.*\/td>.*$pat).*$pat.*\/td>\s*//gs;
	    print NEW $line;
	}  else {
	    print NEW $line;
	}
    }
    close(NEW);
    close(FILE);

}


```

Make executable
```
chmod 755 fix-html.pl
```

If all the html files are in a directory called www, then run it like this:

```
fix-html.pl remove.html www
```

It will create a directory called www-fixed (in the same directory as www).

www should remained untouched. 

The script will go through every file it finds in all subdirectories of www. It will remove all <td...remove.html.../td> clauses that it finds and write the 'fixed' version of the file to a new file of the same name but in the www-fixed directory.

If you can tell me that all files are prefixed by something like 'src=' then I can modify the code to check if remove.html exists and remove the <td.../td> clause only if remove.html does not exist.

Test carefully before you rely on my solution.
Tell me if there are any problems, I'll try to fix.

---

### Post by Redscare on 2008-05-24
This script is almost perfect, it only has one issue; it needs to stop at the first /td> it encounters, because if there is another /td> in the entire document the script deletes all the text between the remove.html <td and the last /td> in the document. In the example, almost all the text would be deleted, whereas only the bolded text should be removed:
```
<td../td>        --->not removed, correct
[b]<td...remove.html...   --->removed, correct
.../td>                --->removed, correct[/b]
RANDOM TEXT            --->removed, not correct
<td...notremove.html   --->removed, not correct
......../td>           --->removed, not correct

```
Thanks again,and the perl code is fine, i was just wondering if a bash/sed/awk solution is also possible.

---

### Post by unutbu on 2008-05-24
Thanks for catching that error. I think this version is simpler, and now hopefully correct.

```
#!/usr/bin/perl
# Usage: fix-html.pl remove.html ~/tmp/test/

use strict;
use warnings;
use File::Find;
use File::Spec;
use File::Path;
use File::Basename;
$/="";


my $pat=shift @ARGV;
my $dir=shift @ARGV;
$dir=File::Spec->rel2abs($dir);

#warn "dir=$dir";
die unless (-d $dir);

my ($dirname,$dirpath,$suffix) = fileparse($dir,qw());
#warn "($dirname,$dirpath,$suffix)";

my $newdir=File::Spec->catdir($dirpath,$dirname."-fixed");

my %options=(wanted=>\&process,no_chdir=>1);
find(\&process,$dir);

sub process {
    my $file=$File::Find::name;
    return unless (-f $file);
    warn "file=$file";

    my $newfile=$file;
    $newfile=~s/^$dir/$newdir/;
    warn "newfile=$newfile";
    my ($name,$path,$suffix) = fileparse($newfile,qw());
    mkpath([$path], 1, 0755);

    my $str;
    open(FILE,"<","$file") || die;
    while (<FILE>) {
	$str.=$_;
    }
    close(FILE);

    my @fragments=split(/(?=<td)/,$str);

    foreach my $frag (@fragments) {
	if ($frag=~m|$pat|) {
	    $frag=~s/\s*<td.*\b$pat\b.*\/td>\s*//gs;
	}
    }
    $str=join('',@fragments);

    open(NEW,">","$newfile") || die;
    print NEW $str;
    close(NEW);

}

```

I bet there is a way to do this with bash/sed/awk, I'm just not very good with those tools.

---

### Post by LaRoza on 2008-05-24
> **Redscare said:**
> 
Using sed/awk was what i had in mind, i was wondering what parameters to pass. Is my impression that sed and awk are a part of bash wrong? Thanks again.

sed and awk (and others) are not part of Bash. Bash is a [Unix shell]("http://en.wikipedia.org/wiki/Unix_shell"). In fact, the default shell for Ubuntu is Dash.

However, sed and awk are [Standard Unix Programs]("http://en.wikipedia.org/wiki/List_of_Unix_programs"). They will be found on all full Unix and Unix like systems. They are programs, but they are always there.

---

### Post by Redscare on 2008-05-24
The script is flawless, thanks very much. Once again i was just wondering, as a proof of concept, can this be done in bash/sed/awk? 

Again, thanks a lot. Thinking about learning perl now:)

---

### Post by Redscare on 2008-05-28
So no bash/sed/awk wizards willing to help?:)

---

### Post by mssever on 2008-05-28
> **LaRoza said:**
> In fact, the default shell for Ubuntu is Dash.
Bash is the default shell in Ubuntu. /bin/sh runs dash, but if you fire up a terminal, you'll get bash, not dash. (The program at /bin/sh has no relation whatsoever to the default shell. Some *nix variants use csh or similar as the default shell--MacOS uses tcsh--but POSIX requires every POSIX-compatible system to have a /bin/sh that supports a standardized syntax. I'm not sure what shell MacOS uses as /bin/sh. Most Linuxes use bash as /bin/sh, and Ubuntu uses dash.)
> **Redscare said:**
> The script is flawless, thanks very much. Once again i was just wondering, as a proof of concept, can this be done in bash/sed/awk?
Yes, it can, but it would require too much work. Ruby or Perl are better suited for such a task. That said, ghostdog74 is the forums' resident awk promoter. Maybe he can help with awk. Such a task would be *very* difficult in pure bash without using some combination of sed and/or awk.

---

### Post by ghostdog74 on 2008-05-28
Frankly, I don't understand what is required. What is remove.html doing inside that html file..etc. @OP , if you still want to use unix tools for this purpose, you should provide clear description of what you want, a sample input file (not those you made up), and your expected output. msserver or other unix experts will try to help you out.

---

