---
title: "Variables from a CSV file"
date: 2010-03-31
forum: Programming Talk
---

### Post by mais1976 on 2010-03-31
Hello all,

I need to read values from a csv file and I've to use Perl. Reading them and display them is quite easy. But I can't to use these variables ?

my $file = 'pcdata.csv';
my $prev = '';
my $teller = 0;

open (F, $file) || die ("Could not open $file!");

while (my $line = <F>)
{
  (my $postcode, my $plaats, my $gemeente, my $ops4, my $indicator) =
split
';',$line;

  #print "$postcode : $plaats : $gemeente : $ops4 : $indicator";

  $ops4 =~ s/^\s*(\S*(?:\s+\S+)*)\s*$/$1/;

  if ($postcode == 3336) {print "hehe Zwijndrecht\n";}
  if ($plaats != $prev)
  {
    print "dikke lul 3 bier\n";
  }
 $teller = $teller + 1;
 print "$teller\n";
}

close (F);


csv:

9469;SCHIPBORG;AA EN HUNZE;Drenthe;0
9443;SCHOONLOO;AA EN HUNZE;Drenthe;0
9656;SPIJKERBOOR DR;AA EN HUNZE;Drenthe;0
9445;VREDENHEIM;AA EN HUNZE;Drenthe;0
9400;ASSEN;ASSEN;Drenthe;2

CAn anyone help me please?

BR, Ais

---

### Post by gmargo on 2010-03-31
I'm sorry, I'd like to help but I don't understand your question.  (Oh, and if you wrap your code in CODE tags it will display in a fixed with font without stripping indentation.)

---

### Post by geirha on 2010-03-31
There's Text::CSV for parsing csv files ...

---

