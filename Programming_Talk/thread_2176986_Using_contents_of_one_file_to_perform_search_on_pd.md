---
title: "Using contents of one file to perform search on pdf contents"
date: 2013-09-26
forum: Programming Talk
---

### Post by sean20 on 2013-09-26
I've got about 600 single page PDF's and I've got to search them with about 50,000 possible strings inserted into one file and ideally get the string and filename where found inserted into a third document that's CSV.  I've come up with this so far and could use some help.

```
#!/bin/bash


while read p; do
        echo $p


found=1


for file in *.pdf ; do
   [ "$file" = '*.pdf' ] && echo "No PDF files found!" && exit 1
      match=$(pdftotext -q  "$file" - | grep -m 1 "$p")
      [ "$match" ] && echo "Page $i in $file" && found=0 && echo "$p,$file" &> results.csv
done


[ "$found" -ne 0 ] && echo "No search string matches found"


done < fullcatexp.csv
```


some help would be greatly appreciated!!!!!

---

### Post by steeldriver on 2013-09-26
Are the strings actually comma separated or one-per-line? If the latter, would it be more efficient to run pdftotext **once** for each .pdf file, and then use something like grep -HFf fullcatexp.csv (or fgrep -Hf fullcatexp.csv) to search for each fixed string in that file?

---

### Post by sean20 on 2013-09-27
strings from [COLOR=#000000][FONT=Ubuntu Mono]fullcatexp.csv are like so
H2-34565
H1-56763
AB-1234

they need to be resulted after a search of 600+ PDFs in this format.

string, filename.pdf
string, filename.pdf

#1, my script isn't returning any results - sucky I know.
#2, how would I wrangle grep -HEf or fgrep -Hf into my method?

Thanx![/FONT][/COLOR]

---

### Post by steeldriver on 2013-09-27
I was thinking something like this?

```

#!/bin/bash

shopt -s nullglob

for file in *.pdf; do
  pdftotext "$file" - | fgrep -f "$1" --color --label="$file" -Hm1
done

```

which would output (the first match from each matching file) as

```

$ ./pdfgrep.sh fullcatexp.csv
filename.pdf:matching line
filename.pdf:matching line
filename.pdf:matching line
.
.
.

```

If you want just the matching portion rather than the whole line, add a -o to the grep options; if you must have the *string, file* output order then you can pipe (either within the script, or the output of the script) through an awk

```
| awk -F: 'BEGIN {OFS=", "}; {print $2, $1;}'
```

---

### Post by Vaphell on 2013-09-27
how about something like this
```

for file in *.pdf
do
  pdftotext "$file" - | fgrep -f "$1" -o | sort -u | awk -vf="$file" '{ print $1 ", " f; }'
done
```

---

### Post by sean20 on 2013-09-27
I tried to use this:

```
#!/bin/bash


shopt -s nullglob


for file in *.pdf
do
  pdftotext "$file" - | fgrep -f "$1" -o | sort -u | awk -vf="$file" '{ print $1 ", " f; }'
done

```
like so [root@opsview pdf]# ./findpdf.sh fullcatexp.csv

but it didn't provide any result at all and it finished really fast

afterward I tried the below with the same execute method and also provided no result

```
#!/bin/bash


shopt -s nullglob


for file in *.pdf; do
  pdftotext "$file" - | fgrep -f "$1" --color --label="$file" -Hm1 | awk -F: 'BEGIN {OFS=", "}; {print $2, $1;}'
done

```

for file in *.pdf
do
  pdftotext "$file" - | fgrep -f "$1" -o | sort -u | awk -vf="$file" '{ print $1 ", " f; }'
done
am I doing something wrong here?


Below with this query ./findres.sh N46-050AL returns "Page 1 in 216.pdf" but I don't care about page, only filename and search term, along with speed of query.

```

#!/bin/bash


[ "$*" ] || { echo "You forgot a search string!" ; exit 1 ; }


found=1


for file in *.pdf ; do
   [ "$file" = '*.pdf' ] && echo "No PDF files found!" && exit 1
   pages=$(pdfinfo "$file" | awk '/Pages:/ { print $NF }')
   for ((i=1 ; i<=$pages ; i++)) ; do
      match=$(pdftotext -q  "$file" - | grep -m 1 "$*")
      [ "$match" ] && echo "Page $i in $file" && found=0 && echo "$*,$file" &> results.csv
   done
done


[ "$found" -ne 0 ] && echo "No search string matches found"

```
and same code run like :  ./findres.sh fullcatexp.csv   returns no search string matches found.

HELP!!!

---

### Post by steeldriver on 2013-09-27
Are you sure the pdf files are in the current directory? Are there any special characters or formatting in the csv file that might be screwing up the matches?

It for sure works for me, e.g.

```

$ ls *.pdf
openstack-deployment.pdf  serverguide.pdf  Ubuntu1104EssentialsPreview.pdf
$ 
$ cat fullcatexp.csv 
Debian
Ubuntu Server
Canonical
man pages

```

Then
```

$ ./pdfgrep.sh fullcatexp.csv 
openstack-deployment.pdf:Canonical
serverguide.pdf:Ubuntu Server
Ubuntu1104EssentialsPreview.pdf:Canonical

```

or

```

$ ./pdfgrep.sh fullcatexp.csv | awk -F: 'BEGIN {OFS=", "}; {print $2, $1}'
Canonical, openstack-deployment.pdf
Ubuntu Server, serverguide.pdf
Canonical, Ubuntu1104EssentialsPreview.pdf

```

---

### Post by drmrgd on 2013-09-27
I think steeldriver and Vaphell are on it, but just for fun and my own practice, and probably just out of boredom, I hacked together this quickie perl script that may be close to what you're looking for.  Without real data to test it on, I'm not sure I've got all of your considerations in mind (I'm certain I haven't considered some edge cases!), and I'm not 100% sure if more effort needs to be considered in building any of the data structures and / or regexs given your input data.  
Given that the shell commands the above gurus are giving you is probably plenty enough, this might be overkill.  But, maybe you'll find this helpful?  Here's the script:

```

#!/usr/bin/perl
# Read in a file with search terms and a list of .pdf files, and output the search term and the .pdf file the term 
# was found in as a .csv output.  Can be expanded to potentially also list 


use warnings;
use strict;
use Data::Dumper;


my $lookup_file = shift;
my @pdf_files = @ARGV;
my %results;


# Read in the lookup file and store query terms in hash (just in case can be useful later)
open( my $lookup_fh, "<", $lookup_file ) || die "Can't open the lookup file '$lookup_file': $!";
my %lookup = map{ chomp; $_ => 1 } <$lookup_fh>;
close( $lookup_fh );


# Iterate over search terms to look up files and spit results out to a new hash
for my $pdf ( @pdf_files ) {
    open( my $pdf_fh, "-|", "pdftotext $pdf -" ) || die "Error converting file: $pdf";
    my @data = <$pdf_fh>;
    for my $search_term ( keys %lookup ) {
        push( @{$results{$search_term}}, $pdf ) if ( grep { $_ =~ /$search_term/ } @data );
    }
}


# Print out the results
for my $search_term ( sort keys %results ) {
    print join( ",", $search_term, $_ ), "\n" for ( sort { $a cmp $b } @{$results{$search_term}} );
}

```

If you provide it a lookup file with one search term on each line, and then a list of .pdf files to search (you can glob it if you like), the script will search each file for the term and if it finds one, it will print out the found term and the match.  If the term matches the same file multiple times, you'll only get one result, which I think is what you want.  I also stuck with using 'pdftotext' instead of a perl module for this excersise.  Not sure if I can get a speed increase with a perl module.  I tested it on about 40 .pdf files comprising about 245,000 lines and it ran in about 3.4 seconds.  So, hopefully it'll be fast enough for your needs.

---

