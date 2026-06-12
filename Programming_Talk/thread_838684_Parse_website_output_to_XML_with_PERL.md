---
title: "Parse website output to XML with PERL?"
date: 2008-06-23
forum: Programming Talk
---

### Post by hansoffate on 2008-06-23
This is my first crack at trying to write some perl to get anything done.  I am trying to pick this up as I go.  I work in a plant biology lab at UCDavis.  The person incharge asked me if I could try to write a perl script to take a file with a list of ORF IDs, search NCBI to find out what Genes they correspond to, and get the GIs (Gene ID Number) to create a table with the ORF number with the corresponding GIs.

I have created a file with the 750 ORFs separated 1 on each line. I was thinking of taking each line then adding it to the end of the URL [http://www.ncbi.nlm.nih.gov/sites/entrez?db=protein&cmd=search&term=######](http://www.ncbi.nlm.nih.gov/sites/entrez?db=protein&cmd=search&term=######)
Each line would be added immediately after "term=", replacing the #####.

An example of an output that I would be working with is here: [http://www.ncbi.nlm.nih.gov/sites/entrez?db=protein&cmd=search&term=Q0085](http://www.ncbi.nlm.nih.gov/sites/entrez?db=protein&cmd=search&term=Q0085)
The first 5 means there are 5 GIs that the ORF correspond to.  I need to take the 5 GI numbers that are following the 5 5 0 and put that in the same field as the ORF number Q0085. 

When I tried to use LWP::Simple; to get the url to see if this was possible, I got the html page with all the code.  Do I have to write something to strip all the HTML code out and leaves the GI's?

---

### Post by HalPomeranz on 2008-06-24
> **hansoffate said:**
> Do I have to write something to strip all the HTML code out and leaves the GI's?

Yup, but it's not that bad.  In fact, here you go:

```

#!/usr/bin/perl

use LWP::Simple;

while (<>) {
    chomp;
    $html = get("http://www.ncbi.nlm.nih.gov/sites/entrez?db=protein&cmd=search&term=$_");
    unless (length($html)) {
	warn "Unable to load page for '$_'\n";
	next;
    }

    @found = ();
    foreach $line (split("\n", $html)) {
	next unless (($gi) = $line =~ m#/entrez/viewer.fcgi\?db=protein&amp;id=.*?">([^<]+)</a>#);
	push(@found, $gi);
    }
    print "$_: ", join(' ', @found), "\n";
}

```

The above code will read in your file of ORFs (one per line) and produce output like: "Q0085: P00854 NP_009313 NP_987083 AAS50173 CAA09832".

The above code is pretty "brittle".  For example, if the remote site ever changes the URLs in their web pages, the code will stop working.  Similarly, if the resulting GI numbers need to be displayed on multiple pages, my code will only grab the numbers off the first page.  But it's a starting point for you anyway.

---

### Post by hansoffate on 2008-06-24
I just realized I gave the wrong links to you.  Here is what the link actually looks like. [http://eutils.ncbi.nlm.nih.gov/entrez/eutils/esearch.fcgi?db=protein&term=Q0085](http://eutils.ncbi.nlm.nih.gov/entrez/eutils/esearch.fcgi?db=protein&term=Q0085)

As you can see in the code I have been working on, I am just trying to get it (for now) to get the .xml record for one search term and save it.  Then using XML::Simple  take out the GIs named Id in the xml output file.  However, this code doesn't actually work.  It takes the url and saves it as a .xml file.  I also have it individually get each ID.  Obviously, this code won't work for 750 searches that have more or less then 5 Ids.  Also, I still haven't figured out a way to get this to output to a file formatted like this.

Q0085: 21264385  6226527  45239026  44978832  4160374  (or something to this extent)

Any ideas or suggestions is greatly appreciated.
Thanks for the help,
Hans

```

#!/usr/bin/perl -w
# Determining frequency of nucleotides

#use module
use XML::Simple;
use Data::Dumper;
use LWP::Simple;

# Get the name of the file with the DNA sequence data
print "Please type the filename of the list of ORFs:";

$orf_list = <STDIN>;

# Remove the newline from the DNA filename
chomp $orf_list;

# open the file, or exit
unless ( open(ORFFILE, $orf_list) ) {

    print "Cannot open file \"$orf_list\"\nFile may not exist.\n\n";
    exit;
}


$content = 
get("http://eutils.ncbi.nlm.nih.gov/entrez/eutils/esearch.fcgi?db=protein&term=Q0085");

# Also write the results to a file called "countbase"
$outputfile = "GIs.xml";

unless ( open(GIs, ">$outputfile") ) {

    print "Cannot open file \"$outputfile\" to write to!!\n\n";
    exit;
}

print GIs "$content";
close(GIs);

## create object
#$xml = new XML::Simple (KeyAttr=>[]);

## read XML file
#$data = $xml->XMLin("GIs.xml");

my $xml = XMLin("GIs.xml");

print Dumper($xml);

# access XML data
print "$xml->{IdList}->{Id}->[0]\n";
print "$xml->{IdList}->{Id}->[1]\n";
print "$xml->{IdList}->{Id}->[2]\n";
print "$xml->{IdList}->{Id}->[3]\n";
print "$xml->{IdList}->{Id}->[4]\n";

## dereference hash ref
## access <employee> array
#foreach $Id (@{$xml->{IdList}})
#{
#	print $Id-{Id}, "\n"; 
#	print "\n";
#}

# exit the program
exit;


```

---

### Post by slavik on 2008-06-24
ok, two things ... use strict; and use warnings;

if you don't have that, don't give your code out.

---

### Post by HalPomeranz on 2008-06-25
@hansoffate:  You're making this way too difficult.  Here's all you need to get the job done:

```

#!/usr/bin/perl

use LWP::Simple;

while (<>) {
    chomp;
    $html = get("http://eutils.ncbi.nlm.nih.gov/entrez/eutils/esearch.fcgi?db=protein&term=$_");
    unless (length($html)) {
	warn "Unable to load page for '$_'\n";
	next;
    }

    @found = ();
    foreach $line (split("\n", $html)) {
	next unless (($gi) = $line =~ m#<id>([^<]+)</id>#i);
	push(@found, $gi);
    }
    print "$_: ", join(' ', @found), "\n";
}

```

@slavik:  "use strict; use warnings;"?  For a 15 line throw-away script?  Are you kidding me?

---

### Post by pmasiar on 2008-06-25
> **HalPomeranz said:**
> @slavik:  "use strict; use warnings;"?  For a 15 line throw-away script?  Are you kidding me?

Not kidding. Inserting those can be done by default by editor, using them can occasionally save you couple of minutes debugging when typo.

if you are not a code cowboy, it's just a habit - like looking both sides even if you cross one-way street.

---

### Post by hansoffate on 2008-06-25
@HalPomeranz Thanks for the script

I tried adding use strict, but it would error out and wouldn't run so I took it off.  I did add warnings though.  I made it output to a text file instead of print.  

I need to now make it read a text document "ids.txt" containing 750 different ORFs (separated per line) get the corresponding GIs, and append to a document for all 750 entries.  I tried getting the perlscript to do this by reading a few tutorials/syntax pages.  I can't figure out what I am doing wrong.  Can anyone lend a hand?

Thanks for the help,
Hans

```
#!/usr/bin/perl

use warnings;
use LWP::Simple;

open IDS, ">ids.txt" or die $!;
@orfs = <IDS>;
close(IDS);

foreach $orfs (@orfs) {
	chomp($orfs);
    $html = get("http://eutils.ncbi.nlm.nih.gov/entrez/eutils/esearch.fcgi?db=protein&term=$orfs");
    unless (length($html)) {
	warn "Unable to load page for '$orfs'\n";
	next;
    }

    @found = ();
    foreach $line (split("\n", $html)) {
	next unless (($gi) = $line =~ m#<id>([^<]+)</id>#i);
	push(@found, $gi);
    }
    open (MYFILE, '>>data.txt');
    print MYFILE "$orfs: ", join(' ', @found), "\n";
    close (MYFILE);
    ###print "$_: ", join(' ', @found), "\n";
}

```

---

### Post by ghostdog74 on 2008-06-25
```

open IDS, ">ids.txt" or die $!;  <----- you open file handle for output
@orfs = <IDS>;  <----- but here you use it as input... 
close(IDS);

```

---

### Post by hansoffate on 2008-06-25
> **ghostdog74 said:**
> ```

open IDS, ">ids.txt" or die $!;  <----- you open file handle for output
@orfs = <IDS>;  <----- but here you use it as input... 
close(IDS);

```

I thought the @orfs = <IDS>; line takes the txt file and turns it into an array.

Sorry, I am a complete beginner.
I tried following this.
[http://www.perlfect.com/articles/perlfile.shtml](http://www.perlfect.com/articles/perlfile.shtml)

---

### Post by HalPomeranz on 2008-06-25
You can just use my script.  Assuming you save the script in a file called "getinfo", you would just run:  "getinfo ids.txt >data.txt".

The "while (<>) ..." loop in my script means process the contents of any files specified on the command-line.  If there are no file names specified then the script just reads from the standard input (so you can pipe the output of another program into it).  This is the "Unix way" and why the "<>" operator in Perl works the way it does.

The ">data.txt" in the command-line above means to save the output of the script into the file named data.txt, truncating data.txt and removing any data that might have originally been in it.  If you want to append the output to data.txt you would say ">>data.txt" instead.

---

### Post by ghostdog74 on 2008-06-25
> **hansoffate said:**
> I thought the @orfs = <IDS>; line takes the txt file and turns it into an array.

Sorry, I am a complete beginner.
I tried following this.
[http://www.perlfect.com/articles/perlfile.shtml](http://www.perlfect.com/articles/perlfile.shtml)

change ">ids.txt" to "<ids.txt".

---

