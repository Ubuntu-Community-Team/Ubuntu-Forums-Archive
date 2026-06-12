---
title: "Parse websearch output with Perl (RegEx)"
date: 2008-07-07
forum: Programming Talk
---

### Post by hansoffate on 2008-07-07
I am trying to query the yeast genome database ([http://www.yeastgenome.org/](http://www.yeastgenome.org/)) to search for ORFs and get the FASTA results.  Basically, it is just a simple query, get the output from the query, then strip out what I need.


An example of an output that I would be working with is here: [http://db.yeastgenome.org/cgi-bin/getSeq?seq=YMR056C&flankl=0&flankr=0&map=p3map](http://db.yeastgenome.org/cgi-bin/getSeq?seq=YMR056C&flankl=0&flankr=0&map=p3map)
I want to take the ORF ID (YMR056C) and get the FASTA output which is:
>YMR056C  Chr 13   reverse complement
MSHTETQTQQSHFGVDFLMGGVSAAIAKTGAAPIERVKLLMQNQEEMLKQGSLDTRYKGI
LDCFKRTATHEGIVSFWRGNTANVLRYFPTQALNFAFKDKIKSLLSYDRERDGYAKWFAG
NLFSGGAAGGLSLLFVYSLDYARTRLAADARGSKSTSQRQFNGLLDVYKKTLKTDGLLGL
YRGFVPSVLGIIVYRGLYFGLYDSFKPVLLTGALEGSFVASFLLGWVITMGASTASYPLD
TVRRRMMMTSGQTIKYDGALDCLRKIVQKEGAYSLFKGCGANIFRGVAAAGVISLYDQLQ
LIMFGKKFK*


This is the code I tried to write based off another perlscript I had.  Basically, I can get the html and the results that I want to pull out are contained within the <pre>> TEXT HERE </pre>. I am close but I think my Regular Expression isn't written correctly.

Any Ideas?

Thanks,
Hans

```
#!/usr/bin/perl

use warnings;
use LWP::Simple;

while (<>) {
    chomp;
    $html = get("http://db.yeastgenome.org/cgi-bin/getSeq?seq=$_&flankl=0&flankr=0&map=p3map");
    unless (length($html)) {
	warn "Unable to load page for '$_'\n";
	next;
    }

    @found = ();
    foreach $line (split("\n", $html)) {
	next unless (($fasta) = $line =~ m#<pre>>([.<]+)</pre>#i);
	push(@found, $fasta);
    }
    print "$_: ", join(' ', @found), "\n";
}
```

---

### Post by skeeterbug on 2008-07-07
I wouldn't use regex to parse html.

[http://search.cpan.org/~petek/HTML-Tree-3.23/lib/HTML/TreeBuilder.pm](http://search.cpan.org/~petek/HTML-Tree-3.23/lib/HTML/TreeBuilder.pm)

I am sure there are others.

---

### Post by myrtle1908 on 2008-07-07
So you want to get everything in between '<pre>' and '</pre>'?

First join your html into one big string then (assuming there will only ever be one set of pre tags):-

my ($pre) = $html =~ /.*?<pre>(.*?)<\/pre>/i;

---

### Post by slavik on 2008-07-07
> **myrtle1908 said:**
> So you want to get everything in between '<pre>' and '</pre>'?

First join your html into one big string then (assuming there will only ever be one set of pre tags):-

my ($pre) = $html =~ /.*?<pre>(.*?)<\/pre>/i;
or you can do:

```

my @pre_arr = $html =~ /.*?<pre>(.*?)<\/pre>/gi;

```

---

### Post by hansoffate on 2008-07-08
I tried both regex by replacing the code below and it didn't work.  I tried to also write the join but it didn't work as well. 

Could either of you provide a bit more help?

Thanks,
Hans
 
```
    
@found = ();
    foreach $line (split("\n", $html)) {
	next unless (($fasta) = $line =~ m#<pre>>([.<]+)</pre>#i);
	push(@found, $fasta);

```

---

### Post by myrtle1908 on 2008-07-08
This works but you will need to do your own error handling etc.

```

use strict;
use warnings;
use LWP::Simple;

my $html = get("http://db.yeastgenome.org/cgi-bin/getSeq?seq=YMR056C&flankl=0&flankr=0&map=p3map");
my ($pre) = $html =~ /.*?<pre>(.*?)<\/pre>/gsi;
print $pre;
```

---

### Post by ghostdog74 on 2008-07-08
imagine you already have the page downloaded
```

#!/usr/bin/perl
$s="";
$f=0;
while (<>) {
  s/.*<pre>// and $f=1 if (/<pre>/) ; 
  $s=$s . $_ if $f;
  $f=0 if (/<\/pre>/);
}
print $s;

```
output:
```

# ./test.pl htmlfile
>YMR056C  Chr 13   reverse complement
MSHTETQTQQSHFGVDFLMGGVSAAIAKTGAAPIERVKLLMQNQEEMLKQGSLDTRYKGI
LDCFKRTATHEGIVSFWRGNTANVLRYFPTQALNFAFKDKIKSLLSYDRERDGYAKWFAG
NLFSGGAAGGLSLLFVYSLDYARTRLAADARGSKSTSQRQFNGLLDVYKKTLKTDGLLGL
YRGFVPSVLGIIVYRGLYFGLYDSFKPVLLTGALEGSFVASFLLGWVITMGASTASYPLD
TVRRRMMMTSGQTIKYDGALDCLRKIVQKEGAYSLFKGCGANIFRGVAAAGVISLYDQLQ
LIMFGKKFK*
</pre><hr size="2" width="75%">

```

---

