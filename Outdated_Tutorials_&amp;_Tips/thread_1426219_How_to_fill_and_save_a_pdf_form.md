---
title: "How to fill and save a pdf form"
date: 2010-03-10
forum: Outdated Tutorials &amp; Tips
---

### Post by voodew on 2010-03-10
Did a little research on how to fill and save a pdf form. Unfortunately, I don't have Ubuntu 9.10 working 100% due to some erroneous data being given by dump_data_fields from pdftk.

Alright, let's begin by installing pdftk:
```
sudo apt-get install pdftk
```

Ubuntu 9.10 has a bug with fonts, I'll get to that later.

Next, create these perl scripts:
fields2pl.pl
```
#!/usr/bin/env perl 

my ($LOOKING,$INSTATE)=(0,1);

my $state=$LOOKING;

while(<>){
  if (($state==$LOOKING) && m/---/){
    $state=$INSTATE;
  }
  if (($state==$INSTATE) && m/^FieldName:\s+(.*)$/){
    push(@names,$1);
    $state=$LOOKING;
  }
}

print '$fields={',"\n";
print join(",\n",map {sprintf("'%s'=>q{}",$_);} @names);
print "\n};\n";
```

and create genfdf.pl
```
#!/usr/bin/env perl

use strict;
use PDF::FDF::Simple;

use Getopt::Std;

our $opt_o;

getopts("o:");



my $outfile=$opt_o || "-";


my %content=();
our $fields;

foreach my $file (@ARGV){
  open(IN,"$file") || die ("could not open $file");
  undef($/);
  my $in=<IN>;
  eval($in);
  die "reading input failed: $@" if $@;

  %content=(%content, %$fields);
}


my $f=new PDF::FDF::Simple({
			    filename => $outfile,
			    content => \%content });

$f->save;
```

Now run:
```
apt-get install libpdf-fdf-simple-perl
```

Now, we can actually start manipulating our pdf's

Create a template (replace xxxx with the pdf name):
```
pdftk xxxx.pdf dump_data_fields | perl fields2pl.pl > template.pl
```

Edit template.pl with the data you want to enter.

Then
```
perl genfdf.pl template.pl > output.fdf
pdftk xxxx.pdf fill_form output.fdf output filled.pdf
```

You should be able to open filled.pdf and it should be the pdf form filled with your data.



Onto the 9.10 bugs
To fix the itext font bug:
```
sudo apt-get install dpkg-dev
sudo apt-get build-dep pdftk
sudo apt-get source pdftk
gedit pdftk-1.41+dfsg/debian/patches/set_classpath
```

change
```
+ static char my_classpath[]="CLASSPATH=/usr/share/java/bcprov.jar:/usr/share/java/bcmail.jar";
```

to
```
+ static char my_classpath[]="CLASSPATH=/usr/share/java/bcprov.jar:/usr/share/java/bcmail.jar:/usr/share/java/itext.jar";
```

then rebuild
```
sudo apt-get -b source pdftk
dpkg -i pdftk_1.41+dfsg-1_i386.deb
```

If you don't want apt to rebuild what you've done, then
```
sudo echo pdftk hold | sudo dpkg –set-selections
```

I've encountered a bug with dump_data_fields in pdftk while doing this with a couple pdf forms. Basically, some erroneous characters are added to the data fields. Not sure how to fix that one yet.

Good luck.

---

### Post by James Paige on 2010-03-29
Thanks for the instructions about fixing the pdftk font problem in 9.10. You saved me a lot of trouble with that.

I hope that fix makes it into 10.4

---

### Post by voodew on 2010-03-30
No problem. I don't know what they did with the package in 9.10, but it works great in 9.04. I'm guessing the bugs will be fixed in the next Ubuntu distribution.

---

### Post by shangxiao on 2010-08-31
Hey we're getting funny characters in our dump_data_fields as well and it's interrupting the way we fill out pdf forms.  pdftk inserts "&#0;" after each part of the qualified field name.  It works fine on an old 32-bit Debian machine but on 64-bit Ubuntu it gives us these funny characters.  They look like html entities.

Any idea on what could be causing it?

---

### Post by shangxiao on 2010-09-01
Actually the problem went away if I compiled pdftk myself.

---

