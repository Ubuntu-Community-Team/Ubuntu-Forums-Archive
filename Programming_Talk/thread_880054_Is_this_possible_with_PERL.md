---
title: "Is this possible with PERL?"
date: 2008-08-04
forum: Programming Talk
---

### Post by hansoffate on 2008-08-04
I have been able to write 3 perlscripts with the help of others on this forum to perform a search and pull out information that I needed for some protein analysis through various sites.  I have a list of 240 different proteins that need query to the SGD database and pull some information.  So far, the URL has always included the proteinID so I could easily substitute each search term in the URL.  

Here is an example for one of the proteins: YFR011C
[http://db.yeastgenome.org/cgi-bin/locus.pl?locus=YFR011C](http://db.yeastgenome.org/cgi-bin/locus.pl?locus=YFR011C)

If you scroll down and look in the middle frame, you can see the dropdown box that says "ORF Genomic DNA".  For each of the proteins, I need to get the "ORF Genomic DNA" sequence.  The new URL when you get the sequence is:
[http://db.yeastgenome.org/cgi-bin/getSeq](http://db.yeastgenome.org/cgi-bin/getSeq)

This URL doesn't change per protein, so I don't know how to write this script.  I would like to pull out the sequence of each of the proteins in the list.
>YFR011C  Chr 6  
ATGGGTTCAAACACTTCCAAAGTGGGTGCTGGTGCAGAAAAACAACAAGTCTATACTCCG
CTAACACAGATCGATTTTTCACAGTCTTTGGTTTCTCAATTGGATTCATCGAAGGAATCA
GACTATGTCACCAAGCAAAATGCAGAAAAGTTCATTGAGAAGAAGGTTTCACAAAGGCTA
TCTAACCTAGAAGTTGAAACGTTAAAGAAGTTTGAAGATACTTTGAACAATTCACTATTA
TCAGACGACGACAAGGATGCCGTTGATGGAATATCATCAAGTTCATTGAATAATCAAATC
GAGTCGTTGAACAAGAAACTAACATTATTTGATCAATTAGAGTTACAAAAGTTGGAGAAA
TATGGGGGTGCCAAAGGTAAATCTGATAAAAAAACCGACAACGGCAGCATTTCTATAAAG
GCAAAATTGACTGAGTGTCTTTTGGCCAATAAGGGCAAGCCATTGAATTGTTACGAAGAG
ATGGAAGAATTCAAGAAGCTCGTTATGGGTTGA

Any ideas on how to write this would be greatly appreciated,
Hans

---

### Post by unutbu on 2008-08-04
[http://db.yeastgenome.org/cgi-bin/getSeq?seq=YFR011C](http://db.yeastgenome.org/cgi-bin/getSeq?seq=YFR011C)

---

### Post by hansoffate on 2008-08-04
Awesome.  Thanks unutbu.  Here is my perlscript so far, but my REGEX isn't working to take out the sequence.  Any Ideas?

```
#!/usr/bin/perl
use strict;
use warnings;
use LWP::Simple;


open IDS, "<ids.txt" or die $!;
my @orfs = <IDS>;
close(IDS);

open (MYFILE, '>data.csv');
print MYFILE "Protein_DNA_Sequence\n";


foreach my $orfs (@orfs) {
	{
	chomp($orfs);
    my $html = get("http://db.yeastgenome.org/cgi-bin/getSeq?seq=$orfs");
    unless (length($html)) {
	warn "Unable to load page for '$orfs'\n";
	next;
    }


    my @found = ();
    foreach my $line (split("\n", $html)) 
	{
	next unless (my ($gi) = $line =~ m#<pre>([^<]+)</pre>#i);
	push(@found, $gi);
	}


    foreach my $gi (@found)
		{
		print MYFILE "$gi\n";	
		}	
}

close (MYFILE);
exit;
}
```

---

### Post by unutbu on 2008-08-04
```
#!/usr/bin/perl
use strict;
use warnings;
use LWP::Simple;

open IDS, "<ids.txt" or die $!;
my @orfs = <IDS>;
close(IDS);

open (MYFILE, '>data.csv');
print MYFILE "Protein_DNA_Sequence\n";


foreach my $orfs (@orfs) {
    print "Getting $orfs\n";
    chomp($orfs);
    my $html = get("http://db.yeastgenome.org/cgi-bin/getSeq?seq=$orfs");
    unless (length($html)) {
	warn "Unable to load page for '$orfs'\n";
	next;
    }


    my @found = ();
    foreach my $line (split("<pre>", $html)) {
	next unless (my ($gi) = ($line =~ m#([^<]+)</pre>#i));
	push(@found, $gi);
    }


    foreach my $gi (@found) {
	print MYFILE "$gi\n";	
    }
}
close (MYFILE);

```

---

### Post by hansoffate on 2008-08-07
Thanks Unutbu.  Worked like a charm.  I really liked the way you split after <pre>.  It makes it much easier.  Also, I like your suggestion of "Getting $orf".  I incorporated that into my other older scripts.  

Now, with the sequences I pulled, I have to make a table which enzymes will not cut and will cut only once.  I am trying to use this website to pull the information: [http://tools.neb.com/NEBcutter2/index.php](http://tools.neb.com/NEBcutter2/index.php)

I pasted this into the textbox and press submit.  
>YFR011C  Chr 6  
ATGGGTTCAAACACTTCCAAAGTGGGTGCTGGTGCAGAAAAACAACAAGTCTATACTCCG
CTAACACAGATCGATTTTTCACAGTCTTTGGTTTCTCAATTGGATTCATCGAAGGAATCA
GACTATGTCACCAAGCAAAATGCAGAAAAGTTCATTGAGAAGAAGGTTTCACAAAGGCTA
TCTAACCTAGAAGTTGAAACGTTAAAGAAGTTTGAAGATACTTTGAACAATTCACTATTA
TCAGACGACGACAAGGATGCCGTTGATGGAATATCATCAAGTTCATTGAATAATCAAATC
GAGTCGTTGAACAAGAAACTAACATTATTTGATCAATTAGAGTTACAAAAGTTGGAGAAA
TATGGGGGTGCCAAAGGTAAATCTGATAAAAAAACCGACAACGGCAGCATTTCTATAAAG
GCAAAATTGACTGAGTGTCTTTTGGCCAATAAGGGCAAGCCATTGAATTGTTACGAAGAG
ATGGAAGAATTCAAGAAGCTCGTTATGGGTTGA

The end result is a URL that looks like this: [http://tools.neb.com/NEBcutter2/cutshow.php?name=28fbd353-YFR011C__Chr_6](http://tools.neb.com/NEBcutter2/cutshow.php?name=28fbd353-YFR011C__Chr_6)

The list of 0 Cutters and 1 Cutters is on the right hand side, and looks doable via REGEX.  The URL changes when you click on those pages to [http://tools.neb.com/NEBcutter2/listbycuts.php?name=28fbd353-YFR011C__Chr_6&numcuts=0](http://tools.neb.com/NEBcutter2/listbycuts.php?name=28fbd353-YFR011C__Chr_6&numcuts=0)

All of this seems like it could be done relatively easily with PERL adding "numcuts=0" or 1 depending on which list I want.  Also, it seems like I could pull the information with REGEX doing a split after #8B008B>" and then the ending with "</a>"

The problem is actually submitting the FASTA information to generate this information.  I tried to change the URL to something that I haven't submitted before IE YHR100C  Chr 8 so the URL looked like:  [http://tools.neb.com/NEBcutter2/listbycuts.php?name=28fbd353-YHR100__Chr_8](http://tools.neb.com/NEBcutter2/listbycuts.php?name=28fbd353-YHR100__Chr_8)
However, this did not work.  It looks like you have to submit the job in order to generate the information.  Any ideas?

Thanks,
Hans

---

### Post by siouzi on 2008-08-08
This is a bit offtopic, but should you not already know, check out [http://www.bioperl.org/](http://www.bioperl.org/) - "BioPerl is a toolkit of perl modules useful in building bioinformatics solutions in Perl". For future reference, anyway ;)

---

### Post by unutbu on 2008-08-08
This program uses the HTML::TableExtract perl module. It was not absolutely necessary -- I could alter the program below to grab the same info without using this module. However, if you can install this module, it will allow you to say "The enzyme is in the second column of the table" instead of "The enzyme is whatever follows color: #8B008B". 

To install HTML::TableExtract on an Ubuntu system:
```
sudo apt-get install libhtml-tableextract-perl
```

If you are on a non-Ubuntu machine but can become root, then to install HTML::TableExtract, as root type
```
perl -MCPAN -e shell
install HTML::TableExtract
```

If you are not the administrator on the machine on which you are running perl, I think there is a way to install modules in your home directory.
Try as a normal user:
```
perl -MCPAN -e shell
install HTML::TableExtract
```

```
#!/usr/bin/perl
use strict;
use warnings;
use LWP 5.64;
use HTML::TableExtract;

open GI, "<data.csv" or die $!;
my @gi = <GI>;
close(GI);

my $gi=join("",@gi);
my @seqs=split(/(?=\>)/,$gi);


my $browser = LWP::UserAgent->new;
my $url='http://tools.neb.com/NEBcutter2/enzcut.php';

my @cutshow_names=();
foreach my $seq (@seqs) {
    next if ($seq=~m/^Protein/);
    # This is how to submit the FASTA information
    my $response = $browser->post( $url, [
				       sequence => $seq
				   ]);
    my $content=$response->content;
    my ($cutshow_name)=($content=~m/cutshow.php\?name=([^']+)/);
    if ($cutshow_name) {
	push(@cutshow_names,$cutshow_name);
    } else {
	die "Failed to retrieve cutters for sequence $seq"
    }
}

$url='http://tools.neb.com/NEBcutter2/listbycuts.php';
foreach my $cutshow_name (@cutshow_names) {
    my @zero_cut=get_cutters($cutshow_name,0);
    print "$cutshow_name: 0 cutters:\n";
    print join(", ",@zero_cut);
    print "\n\n";

    print "$cutshow_name: 1 cutters:\n";
    my @single_cut=get_cutters($cutshow_name,1);
    print join(", ",@single_cut);
    print "\n\n";
}


sub get_cutters {
    my $name = shift;
    my $numcuts = shift;
    my $response = $browser->post( $url, [
				       name => $name,
				       numcuts => $numcuts
				   ]); 
    my $content=$response->content;
    my $te = HTML::TableExtract->new();

    # $te can parse the HTML page for tables.
    $te->parse($content);

    # Warning: I'm extracting table data from with depth 0 and count 2. 
    # If tools.neb.com were to change the location of the data on the listbycuts.php page,
    # then this will break -- you'll have to change the numbers in "table(0,2)" to
    # something else.
    my $ts=$te->table(0,2);

    my @enzymes=();
    foreach my $row ($ts->rows) {
	next if ($row->[1]=~m/Enzyme/i);
	my ($datum)=($row->[1]=~m/([a-zA-Z0-9]+)/);
	if ($datum) {
	    push(@enzymes,$datum);
	} else {
	    die "died in get_cutters: Couldn't find datum in $row->[1]";
	}
    }
    return @enzymes;
}

```

---

### Post by sharma2008 on 2008-08-08
quite interesting...

---

