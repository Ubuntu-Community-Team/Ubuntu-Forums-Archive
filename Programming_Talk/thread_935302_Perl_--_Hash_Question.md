---
title: "Perl -- Hash Question"
date: 2008-10-01
forum: Programming Talk
---

### Post by hansoffate on 2008-10-01
Hello all,

    I am having a few issues with my script.  I started out writing this script without "use strict", however, everyone suggested that I should, so I started converting everything over.  Now that I added use strict and the my in their respective places, my script won't run.  Here is my error.


```

hansoffate@grunt:~/Documents/Steve/Project/SGD_datapull$ perl projectV3.pl 
syntax error at projectV3.pl line 32, near "$feat_type{"
syntax error at projectV3.pl line 33, near "$feat_qual{"
Execution of projectV3.pl aborted due to compilation errors.

```

I have a feeling this is an easy problem that I am just overlooking. 

Alright, now down to the real problem.  So far in the script, there has only been one entry per SGDID.  However, in the go_slim_mapping.tab file ([located here]("ftp://genome-ftp.stanford.edu/pub/yeast/data_download/literature_curation/go_slim_mapping.tab")), the Molecular Function, Biological Process, and Cellular Component are stored as multiple line entries.  The 4th field contains a 1 letter code F, P, or C, which represents the titles respectively.  The 5th field actually contains the description that I want to put in my CSV file I am trying to create.  

Example SGDID: S000004664
There are 4 "C" descriptions, 1 "F", and 3 "P"s.  I was thinking of trying to join the descriptions together with a pipe and then putting those respective values in the CSV file.  I'll readup on how to do this, but if anyone have any comments or suggestions, please post!

Thank you for the help,
Hans


```
#!/usr/bin/perl
use strict;
use warnings;
use LWP::Simple;

open IDS, "<fullsgdids.txt";
chomp (my @ids = <IDS> );
close(IDS);

##Tilda Delimitted File
open (MYFILE, '>data.csv');
print MYFILE "SGDID~ORF~Standard_Name~Alias~Description~Name_Description~Molecular_Function~Biological_Process~Cellular_Component~Define~Mutant_Phenotype\n";

open (SGDFEAT, "SGD_features.tab") || die "File not found\n";
chomp (my @sgdfeats=<SGDFEAT>);
close (SGDFEAT);

#open (GENEASSOC, "gene_association.sgd") || die "File not found\n";
#chomp (my @gene=<GENEASSOC>);
#close (GENEASSOC);

open (SLIMMAP, "go_slim_mapping.tab") || die "File not found\n";
chomp (my @slim=<SLIMMAP>);
close (SLIMMAP);


##List of columns $sgdid, $feat_type, $feat_qual, $feat_name, $stnd_name, $alias, 
##$parent, $sec_sgdid, $chrom, $start_coord, $stop_coord, $strand, $genetic_pos, 
##$coord_ver, $seq_vers, $desc

foreach my $i (@sgdfeats) {
	my ($sgdid, $feat_type, $feat_qual, $feat_name, $stnd_name, $alias, $parent, $sec_sgdid, $chrom, $start_coord, $stop_coord, $strand, $genetic_pos, $coord_ver, $seq_vers, $desc) = split(/\t/, $i);
	my $feat_type{$sgdid} = $feat_type;
	my $feat_qual{$sgdid} = $feat_qual;
	my $feat_name{$sgdid} = $feat_name;
	my $stnd_name{$sgdid} = $stnd_name;
	my $desc{$sgdid} = $desc;
	my $alias{$sgdid} = $alias;
	my $parent{$sgdid} = $parent;
	my $sec_sgdid{$sgdid} = $sec_sgdid;
	my $chrom{$sgdid} = $chrom;
	my $start_coord{$sgdid} = $start_coord;
	my $stop_coord{$sgdid} = $stop_coord;
	my $strand{$sgdid} = $strand;
	my $genetic_pos{$sgdid} = $genetic_pos;
	my $coord_ver{$sgdid} = $coord_ver;
	my $seq_vers{$sgdid} = $seq_vers;
}

##List of Columns for gene_associations: $db, $db_obj_id, $db_obj_symb, $not
##$goid, $db_ref, $evid, $with, $aspect, $db_obj_name, $db_obj_synonym, 
##$db_obj_type, $taxon, $date, $assgn_by

#foreach my $o (@gene) {
#	my ($db, $sgdid, $db_obj_symb, $not, $goid, $db_ref, $evid, $with, $aspect, $db_obj_name, $db_obj_synonym, $db_obj_type, $taxon, $date, #     $assgn_by) = split(/\t/, $o);
#   	my $db{$sgdid} = $db;
#	my $db_obj_symb{$sgdid} = $db_obj_symb;
#	my $not{$sgdid} = $not;
#	my $goid{$sgdid} = $goid;
#	my $db_ref{$sgdid} = $db_ref;
#	my $evid{$sgdid} = $evid;
#	my $with{$sgdid} = $with;
#	my $aspect{$sgdid} = $aspect;
#	my $db_obj_name{$sgdid} = $db_obj_name;
#	my $db_obj_synonym{$sgdid} = $db_obj_synonym;
#	my $db_obj_type{$sgdid} = $db_obj_type;
#	my $taxon{$sgdid} = $taxon;
#	my $date{$sgdid} = $date;
#	my $assgn_by{$sgdid} = $assgn_by;
#}

##List of Columns for go_slim: $orf, $gene, $sgdid, $go_aspect, $go_slim, $goid, $feature_type

foreach my $p (@slim) {
	my ($orf, $gene, $sgdid, $go_aspect, $go_slim, $goid, $feature_type) = split(/\t/, $p);
      my $orf{$sgdid} = $orf;
	my $gene{$sgdid} = $gene;
	my $go_aspect{$sgdid} = $go_aspect;
	my $go_slim{$sgdid} = $go_slim;
	my $goid{$sgdid} = $goid;
	my $feature_type{$sgdid} = $feature_type;
}

foreach my $ids (@ids) {
    print MYFILE "$ids~$feat_name{$ids}~$stnd_name{$ids}~$alias{$ids}~$desc{$ids}~$go_aspect{$ids}~$go_slim{$ids}\n"
}


```

---

### Post by myrtle1908 on 2008-10-01
It would be best if you could provide a few sample lines of the data file(s) you have and a sample of the output you want.  Provide rules etc.

By the looks of the code you have posted it seems you may well have overcomplicated the problem. It is difficult to determine exactly what you are trying to do.

Make it as easy as possible for others to help you.

---

### Post by Martin Witte on 2008-10-02
It has to do with the redefinition of your names, change this

```
foreach my $i (@sgdfeats) {
	my ($sgdid, $feat_type, $feat_qual, $feat_name, $stnd_name, $alias, $parent, $sec_sgdid, $chrom, $start_coord, $stop_coord, $strand, $genetic_pos, $coord_ver, $seq_vers, $desc) = split(/\t/, $i);
	my $feat_type{$sgdid} = $feat_type;
	my $feat_qual{$sgdid} = $feat_qual;
	my $feat_name{$sgdid} = $feat_name;

```
to
```
my %feat_type = ();
my %feat_qual = ();
my %feat_name = ();

foreach my $i (@sgdfeats) {
	my ($sgdid, $feat_type_inp, $feat_qual_inp, $feat_name, $stnd_name, $alias, $parent, $sec_sgdid, $chrom, $start_coord, $stop_coord, $strand, $genetic_pos, $coord_ver, $seq_vers, $desc) = split(/\t/, $i);
	$feat_type{$sgdid} = $feat_type_inp;
	$feat_qual{$sgdid} = $feat_qual_inp;
	$feat_name{$sgdid} = $feat_name;

```
and so on

---

### Post by hansoffate on 2008-10-02
> **Martin Witte said:**
> It has to do with the redefinition of your names, change this

.....

and so on

Thank you very much.  I rewrote the script to create an empty hash which ran great without errors.  

Here is my updated script.

```
#!/usr/bin/perl
use strict;
use warnings;
use LWP::Simple;

open IDS, "<fullsgdids.txt";
chomp (my @ids = <IDS> );
close(IDS);

##Tilda Delimitted File
open (MYFILE, '>data.csv');
print MYFILE "SGDID~ORF~Standard_Name~Alias~Description~Name_Description~Molecular_Function~Biological_Process~Cellular_Component~Define~Mutant_Phenotype\n";

open (SGDFEAT, "SGD_features.tab") || die "File not found\n";
chomp (my @sgdfeats=<SGDFEAT>);
close (SGDFEAT);

#open (GENEASSOC, "gene_association.sgd") || die "File not found\n";
#chomp (my @gene=<GENEASSOC>);
#close (GENEASSOC);

open (SLIMMAP, "go_slim_mapping.tab") || die "File not found\n";
chomp (my @slim=<SLIMMAP>);
close (SLIMMAP);


##List of columns $sgdid, $feat_type, $feat_qual, $feat_name, $stnd_name, $alias, 
##$parent, $sec_sgdid, $chrom, $start_coord, $stop_coord, $strand, $genetic_pos, 
##$coord_ver, $seq_vers, $desc

my %feat_type = ();
my %feat_qual = ();
my %feat_name = ();
my %stnd_name = ();
my %desc = ();
my %alias = ();
my %parent = ();
my %sec_sgdid = ();
my %chrom = ();
my %start_coord = ();
my %stop_coord = ();
my %strand = ();
my %genetic_pos = ();
my %coord_ver = ();
my %seq_vers = ();

foreach my $i (@sgdfeats) {
	my ($sgdid, $feat_type, $feat_qual, $feat_name, $stnd_name, $alias, $parent, $sec_sgdid, $chrom, $start_coord, $stop_coord, $strand, $genetic_pos, $coord_ver, $seq_vers, $desc) = split(/\t/, $i);
	$feat_type{$sgdid} = $feat_type;
	$feat_qual{$sgdid} = $feat_qual;
	$feat_name{$sgdid} = $feat_name;
	$stnd_name{$sgdid} = $stnd_name;
	$desc{$sgdid} = $desc;
	$alias{$sgdid} = $alias;
	$parent{$sgdid} = $parent;
	$sec_sgdid{$sgdid} = $sec_sgdid;
	$chrom{$sgdid} = $chrom;
	$start_coord{$sgdid} = $start_coord;
	$stop_coord{$sgdid} = $stop_coord;
	$strand{$sgdid} = $strand;
	$genetic_pos{$sgdid} = $genetic_pos;
	$coord_ver{$sgdid} = $coord_ver;
	$seq_vers{$sgdid} = $seq_vers;
}

##List of Columns for gene_associations: $db, $db_obj_id, $db_obj_symb, $not
##$goid, $db_ref, $evid, $with, $aspect, $db_obj_name, $db_obj_synonym, 
##$db_obj_type, $taxon, $date, $assgn_by

#foreach my $o (@gene) {
#	my ($db, $sgdid, $db_obj_symb, $not, $goid, $db_ref, $evid, $with, $aspect, $db_obj_name, $db_obj_synonym, $db_obj_type, $taxon, $date, #     $assgn_by) = split(/\t/, $o);
#   	my $db{$sgdid} = $db;
#	my $db_obj_symb{$sgdid} = $db_obj_symb;
#	my $not{$sgdid} = $not;
#	my $goid{$sgdid} = $goid;
#	my $db_ref{$sgdid} = $db_ref;
#	my $evid{$sgdid} = $evid;
#	my $with{$sgdid} = $with;
#	my $aspect{$sgdid} = $aspect;
#	my $db_obj_name{$sgdid} = $db_obj_name;
#	my $db_obj_synonym{$sgdid} = $db_obj_synonym;
#	my $db_obj_type{$sgdid} = $db_obj_type;
#	my $taxon{$sgdid} = $taxon;
#	my $date{$sgdid} = $date;
#	my $assgn_by{$sgdid} = $assgn_by;
#}

##List of Columns for go_slim: $orf, $gene, $sgdid, $go_aspect, $go_slim, $goid, $feature_type

my %orf = ();
my %gene = ();
#my %sgdid = ();
my %go_aspect = ();
my %go_slim = ();
my %goid = ();
my %feature_type = ();

foreach my $p (@slim) {
	my ($orf, $gene, $sgdid, $go_aspect, $go_slim, $goid, $feature_type) = split(/\t/, $p);
      $orf{$sgdid} = $orf;
	$gene{$sgdid} = $gene;
	$go_aspect{$sgdid} = $go_aspect;
	$go_slim{$sgdid} = $go_slim;
	$goid{$sgdid} = $goid;
	$feature_type{$sgdid} = $feature_type;
}

foreach my $ids (@ids) {
    print MYFILE "$ids~$feat_name{$ids}~$stnd_name{$ids}~$alias{$ids}~$desc{$ids}~$go_aspect{$ids}~$go_slim{$ids}\n"
}


```

@myrtle1908
I linked the one of the datafiles im working with (go_slim_mapping.tab) in my previous post where it says located here.  here is the actual URL - [ftp://genome-ftp.stanford.edu/pub/yeast/data_download/literature_curation/go_slim_mapping.tab](ftp://genome-ftp.stanford.edu/pub/yeast/data_download/literature_curation/go_slim_mapping.tab)

This is what is being used in the second half of the code starting with:

 foreach my $p (@slim) {
	my ($orf, $gene, $sgdid, $go_aspect, $go_slim, $goid, $feature_type) = split(/\t/, $p);

What I need to do is lookup sgdid's and reference the go_aspect term (three choices: F,C,P) and the associated description under go_slim.  If there are multiple entries of $sgdids with multiple F,C,P entries, join the specific entries (let's say C) together with a | delimmiter.

If you lookup S000004664 in the linked file, you can see about 8 rows with the same SGDID but each row has 1 associated go_aspect letter, with 1 definition for go_slim.   So for this example, lets say it takes the C values and combines them so it looks like this

cytoplasm|membrane|mitochondrial envelope|mitochondrion	

which will then be placed in the csv file for that particular SGDID under the Cellular Component column.  I would need this same process to be done for the F, and P values and their respective columns Molecular Function and Biological Process.

If you don't understand what I am talking about, please ask and I'll try to explain it again.  

Thanks for the help,
Hans

---

### Post by hansoffate on 2008-10-03
Is this even possible with perl?  I am new to PERL and programming in general.  Would I need a more complex data structure and export this to SQL and run my queries from there?

---

### Post by hansoffate on 2008-10-08
Anyone with any ideas?

Thanks,
Hans

---

