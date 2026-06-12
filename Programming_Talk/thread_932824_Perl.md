---
title: "Perl"
date: 2008-09-28
forum: Programming Talk
---

### Post by hansoffate on 2008-09-28
::EDIT:: Sorry I didn't put a more descriptive title.  I started to and then I forgot and moved on.

I have a few tab deliminated files from a genome database that I need to work with to look up info and create an easy to read excel file for my proff. 

When I try to run this script, I get this error
```
perl projectV2.pl 
Use of uninitialized value in concatenation (.) or string at projectV2.pl line 44.
YFR011C
Use of uninitialized value in concatenation (.) or string at projectV2.pl line 44.
 YHR100C
```

Any ideas?

Thanks,
Hans

```
#!/usr/bin/perl
#use strict;
use warnings;
use LWP::Simple;

open IDS, "<fullids.txt";
@orfs = <IDS>;
close(IDS);

open (MYFILE, '>data.csv');
print MYFILE "ORF,SGDID\n";

open (SGDFEAT, "SGD_features.tab") || die "File not found\n";
@lines=<SGDFEAT>;
close (SGDFEAT);
chomp @lines;

##List of columns $sgdid, $feat_type, $feat_qual, $feat_name, $stnd_genename, $alias, 
##$parent, $sec_sgdid, $chrom, $start_coord, $stop_coord, $strand, $genetic_pos, 
##$coord_ver, $seq_vers, $desc

foreach $i (@lines) {
	($sgdid, $feat_type, $feat_qual, $feat_name, $stnd_genename, $alias, $parent, $sec_sgdid, $chrom, $start_coord, $stop_coord, $strand, $genetic_pos, $coord_ver, $seq_vers, $desc) = split(/\t/, $i);
    $feat_type{$feat_name} = $feat_type;
	$feat_qual{$feat_name} = $feat_qual;
	$sgdid{$feat_name} = $sgdid;
	$stnd_genename{$feat_name} = $stnd_genename;
	$desc{$feat_name} = $desc;
	$alias{$feat_name} = $alias;
	$parent{$feat_name} = $parent;
	$sec_sgdid{$feat_name} = $sec_sgdid;
	$chrom{$feat_name} = $chrom;
	$start_coord{$feat_name} = $start_coord;
	$stop_coord{$feat_name} = $stop_coord;
	$strand{$feat_name} = $strand;
	$genetic_pos{$feat_name} = $genetic_pos;
	$coord_ver{$feat_name} = $coord_ver;
	$seq_vers{$feat_name} = $seq_vers;
}


foreach my $orfs (@orfs) {
    ##print "$orfs is $feat_qual{$orfs} and id $sgdid{$orfs} and desc $desc{$orfs}\n";
	print "$orfs $sgdid{$orfs}"
}

```

---

### Post by forger on 2008-09-28
I'm still a beginner in perl, but I'm not sure whether you're able to use $orfs to enumerate @orfs with foreach

This should clear things up:
```
foreach my $x (@orfs) {
    ##print "$x is $feat_qual{$x} and id $sgdid{$x} and desc $desc{$x}\n";
    print "Is this the bad one: $x"
    print "Or this one: $sgdid{$orfs}"
}
```

---

### Post by hansoffate on 2008-09-28
> **forger said:**
> I'm still a beginner in perl, but I'm not sure whether you're able to use $orfs to enumerate @orfs with foreach

This should clear things up:
```
foreach my $x (@orfs) {
    ##print "$x is $feat_qual{$x} and id $sgdid{$x} and desc $desc{$x}\n";
    print "Is this the bad one: $x"
    print "Or this one: $sgdid{$orfs}"
}
```

I should be able to use $orfs.  Anyways, It's a problem from the second print line.  idk what will fix this.

Thanks for trying.  Anyone else have some ideas?

---

### Post by loell on 2008-09-28
its probably your text file that you are reading which has  blank lines in it.

---

### Post by forger on 2008-09-28
+1 :)

---

### Post by hansoffate on 2008-09-28
> **loell said:**
> its probably your text file that you are reading which has  blank lines in it.

The text file has at least the SGDID per line.  Some of the feat_name (orfs) in the tab delimitted file are empty though.  I'm trying to convert my orfs (feat_name) to SGDIDs.  I'm setting up a new script that takes 3 different files that all relate information to SGDID and create a hash to lookup and pull information.  

Anyideas on how to get this working?  Once I can figure out how to do this, I can apply this to my other script.


BTW, the sgd_features.tab file is located here.
[ftp://genome-ftp.stanford.edu/pub/yeast/data_download/chromosomal_feature/](ftp://genome-ftp.stanford.edu/pub/yeast/data_download/chromosomal_feature/)

---

### Post by loell on 2008-09-28
maybe, you can just turn off uninitialization?

```
no warnings 'uninitialized';

```

or perhaps try using **map**?

so that if encounters a blank line or a blank field on those tab delimited entries, you can filter it out.

---

### Post by ghostdog74 on 2008-09-29
here's an awk implementation which only does conversion of tabs to commas
```

 awk -F"[\t]+" '{$1=$1}1' OFS="," file

```
what are the other related files??

---

### Post by hansoffate on 2008-09-29
> **ghostdog74 said:**
> here's an awk implementation which only does conversion of tabs to commas
```

 awk -F"[\t]+" '{$1=$1}1' OFS="," file

```
what are the other related files??

Thanks.  That'll be good for the future, but right now I just need to figure out a way to take a list of IDs and search a hashed table and pull information and setup a csv.  

In the posted perl code, I was able to setup the hashed table.  Now I just need to print each of the IDS from the @orfs array.

Any ideas?


@loell
no warnings 'uninitialized';
Now I get no out put.  I think its something else.

---

### Post by siouzi on 2008-09-29
```
use strict
```

Use it, unless you really know what you're doing. It saves you from a lot of errors and debugging.

Now, I really have no clue what you're trying to do (just couldn't visualize myself the data you're trying to extract...), but here's my try ;-)

I think one problem is line endings, which are not removed from the @orfs array. So each value has a line ending attached to it and the $sgdid{$orfs} lookup fails. Remove them with ```
chomp @orfs;
``` like you did with the other file.

Second, the first foreach-loop does not make any sense to me. You're reading a line and splitting it into variables, ok, but later these same variables are assigned as hashes. Upon reading the next line, these hashes get destroyed because the split function assings scalar values... so uhhh... maybe this is what you meant?

```

#!/usr/bin/perl
use strict;
use warnings;
use LWP::Simple;

my @orfs;
{
    open my $fh, '<', 'fullids.txt' or die $!;
    @orfs = <$fh>;
    chomp @orfs;
}

open my $csv_fh, '>', 'data.csv' or die $!;
print $csv_fh "ORF,SGDID\n";

open my $sgdfeat_fh, '<', 'SGD_features.tab' or die $!;

##List of columns $sgdid, $feat_type, $feat_qual, $feat_name, $stnd_genename,
##$alias, $parent, $sec_sgdid, $chrom, $start_coord, $stop_coord, $strand,
##$genetic_pos, $coord_ver, $seq_vers, $desc

my %columns_by_feat_name;

while ( my $line = <$sgdfeat_fh> ) {
    chomp $line;
    my @columns = split /\t/, $line;
    
    # remove the key 'feat_name' for cleaner code below ;)
    my $feat_name = splice @columns, 3, 1;

    next unless $feat_name;    # skip empty?

    my %data;
    @data{
        qw(sgdid feat_type feat_qual stnd_genename alias parent sec_sgdid chrom
           start_coord stop_coord strand genetic_pos coord_ver seq_vers desc)
         } = @columns;
    $columns_by_feat_name{$feat_name} = \%data;

    # Access the data like:
    #
    #   my $sgdid_of_feat_name = $columns_by_feat_name{$feat_name}->{sgdid};
    #   my $alias_of_feat_name = $columns_by_feat_name{$feat_name}->{alias};
    #
    # etc
}

foreach my $orfs (@orfs) {
    printf "%s %s\n", $orfs, $columns_by_feat_name{$orfs}->{sgdid} || 'missing';
}

```

I don't know if this works or if it's what you're trying to do, but HTH anyway!

---

### Post by hansoffate on 2008-09-29
> **siouzi said:**
> ```
use strict
```

Use it, unless you really know what you're doing. It saves you from a lot of errors and debugging.

Now, I really have no clue what you're trying to do (just couldn't visualize myself the data you're trying to extract...), but here's my try ;-)

I think one problem is line endings, which are not removed from the @orfs array. So each value has a line ending attached to it and the $sgdid{$orfs} lookup fails. Remove them with ```
chomp @orfs;
``` like you did with the other file.

Second, the first foreach-loop does not make any sense to me. You're reading a line and splitting it into variables, ok, but later these same variables are assigned as hashes. Upon reading the next line, these hashes get destroyed because the split function assings scalar values... so uhhh... maybe this is what you meant?

```

#!/usr/bin/perl
use strict;
use warnings;
use LWP::Simple;

my @orfs;
{
    open my $fh, '<', 'fullids.txt' or die $!;
    @orfs = <$fh>;
    chomp @orfs;
}

open my $csv_fh, '>', 'data.csv' or die $!;
print $csv_fh "ORF,SGDID\n";

open my $sgdfeat_fh, '<', 'SGD_features.tab' or die $!;

##List of columns $sgdid, $feat_type, $feat_qual, $feat_name, $stnd_genename,
##$alias, $parent, $sec_sgdid, $chrom, $start_coord, $stop_coord, $strand,
##$genetic_pos, $coord_ver, $seq_vers, $desc

my %columns_by_feat_name;

while ( my $line = <$sgdfeat_fh> ) {
    chomp $line;
    my @columns = split /\t/, $line;
    
    # remove the key 'feat_name' for cleaner code below ;)
    my $feat_name = splice @columns, 3, 1;

    next unless $feat_name;    # skip empty?

    my %data;
    @data{
        qw(sgdid feat_type feat_qual stnd_genename alias parent sec_sgdid chrom
           start_coord stop_coord strand genetic_pos coord_ver seq_vers desc)
         } = @columns;
    $columns_by_feat_name{$feat_name} = \%data;

    # Access the data like:
    #
    #   my $sgdid_of_feat_name = $columns_by_feat_name{$feat_name}->{sgdid};
    #   my $alias_of_feat_name = $columns_by_feat_name{$feat_name}->{alias};
    #
    # etc
}

foreach my $orfs (@orfs) {
    printf "%s %s\n", $orfs, $columns_by_feat_name{$orfs}->{sgdid} || 'missing';
}

```

I don't know if this works or if it's what you're trying to do, but HTH anyway!


Thanks for the help.  I'll rewrite my code to use strict but you were entirely correct.  My @orfs array had newlines at the end which was causing it to error out.  Now that I have chomp @orfs, the script is running perfectly.  Thanks for the help.

I didn't have time to really look at your code to see why you didn't build the same hash tables, but I will once I get back from work.  

Hans

---

### Post by siouzi on 2008-09-30
> **hansoffate said:**
> 
I didn't have time to really look at your code to see why you didn't build the same hash tables, but I will once I get back from work.  


Ahhh this was my "mistake" :-) Since I don't write perl without using strict mode, I thought the foreach loop did not work right, but it does... Without strict you do not have to declare variables, like this:

```

foreach... {
    ($foo, $bar) = split /\t/, $line;
    $foo{$bar}   = something
    ...
}

```

So here, we have suddenly $foo and %foo... which got me confused! ;-)

---

