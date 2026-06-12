---
title: "[SOLVED] Problem with first perl attempts"
date: 2008-06-29
forum: Programming Talk
---

### Post by jraab22 on 2008-06-29
I've been trying to learn perl and the first thing I've tried to do is the following: I have a tab separated file such as this :

location (tab) value

I've been able to read that file in and grab all the locations which have above a certain value.  I eventually want to end up with a file that shows a location as a range and the total value associated with that range:

start (tab) end (tab) value ( example below)
12345    12360    10 
12363    12734    12
12800    12483    10 
15000    15500    9
I'm stuck trying to compare multiple rows of my file at once and combining rows which have are withina  certain distance (i.e. in my example say within 400 the rows should be combined and start in row 1 should be start end in row 2 should be end and the values should be added. THen row 3 should be added to that, but 4 should be excluded. 

This is probably some really trivial problem, but I'm stuck as to what I should be trying to learn.  I've been working through tutorials and reading the perldocs, but nothing has jumped out at me about how to handle this.  Is this something that can be solved with simple arrays or hashes, or is this a situation a need more complex data structures (arrays of arrays/hashes of arrays etc. )

If someone could give me a hint as to what I need to learn to accomplish this it'd be very much appreciated.  Thanks

---

### Post by myrtle1908 on 2008-06-29
I don't totally understand your problem but if you want to post some example input/output files I'd be happy to help.

---

### Post by jraab22 on 2008-06-29
That'd be a huge help, I'll attach two files, the first, input.txt I'm looking through this file for places were the location in the first column has above a certain value.  The second file is output.txt. I want to display ranges where what I found in the first file were all above a certain value ( I've been using value >= 3, and distance between locations of 5000). You'll see in the second file how I'm stuck, I can make the output in the form of 
start    end

but I can't have it continue consolidating.  The example file should eventually boil down to two large ranges.  
Thanks, I appreciate the help.

---

### Post by ghostdog74 on 2008-06-29
so where is your Perl code?

---

### Post by jraab22 on 2008-06-30
The first file I posted is the file I've started with, I'm able to get a list of "locations" with above a certain threshold value attached. 

I've been trying to use something like this code :

```
#!/usr/bin/perl
use strict;
use warnings;
my $in2="tmp.txt";
my $out2="out.txt";
open(my $in, "<",$in2)||die "cannot open $in2 $!\n";
open(my $out,">",$out2)||die "cannot open $out2 $!\n";
#this block evaluates each coordinate to the coordinate in the row below
#and returns a range if they are within 5000 of each other
#this code is working

my $line1;
my $line2;
while (defined <$in>) {
     chomp ($line1=<$in>);
     my ($chr1,$bin1,$tag1)=split(/\t/,$line1);
     chomp ($line2=<$in>);
     my ($chr2,$bin2,$tag2)=split(/\t/,$line2);
     if (abs($bin1-$bin2<=5000&&$chr1 eq $chr2)){
	  print "$chr1\t$bin1\t$bin2\n";
          }
     }
```

I attached the file tmp.txt to see what I'm running this script on.  The main problem I get from this output is it misses values that are more than 5000 (or whatever distance I define) away from the start value, even if it is within 5000 of a value later on in the list.  Hopefully thats somewhat understandable.  

This is probably something simple, and I'm looking for a point in the right direction.  I'm sure theres a better way of doing this, which I'm happy to read up on.  

Thanks for taking a look.

---

### Post by ghostdog74 on 2008-06-30
check your split statement. Tab is not "t" but \t. if in doubt, always do things one step at a time
```

while (defined <$in>) {
     chomp ($line1=<$in>);
     my ($chr1,$bin1,$tag1)=split(/t/,$line1); <<--- erroneous
     print $bin . "\n";
}
  

```

---

### Post by jraab22 on 2008-06-30
sorry, I had read one of the FAQs suggested putting PHP tags around code for better readability, when I did that it changed my \t to just t.  I went back to edit and it was still like that. I changed to code tags so it shows up correctly, in my script it was fine.

---

### Post by ghostdog74 on 2008-06-30
well, i don't understand what's wrong
```

#!/usr/bin/perl

# use strict;
use warnings;
my $in2="tmp.txt";
my $out2="out.txt";
open(IN, "<",$in2)||die "cannot open $in2 $!\n";
# open(my $out,">",$out2)||die "cannot open $out2 $!\n";
#this block evaluates each coordinate to the coordinate in the row below
#and returns a range if they are within 5000 of each other
#this code is working

my $line1;
my $line2;


while (defined( my $line1 = <IN> )) {
     chomp ($line1);
     
     my ($chr1,$bin1,$tag1)=split(/\t/,$line1);
#      print "$bin1" . "\n";
     my $line2=<IN>;
     chomp($line2);
     my ($chr2,$bin2,$tag2)=split(/\t/,$line2);
#        print "$bin2" . "\n";
     
#      print "$bin1 $bin2" . "\n";
#      if (abs($bin1-$bin2<=5000&&$chr1 eq $chr2)){
       print "Before: " .abs($bin1 - $bin2) . "\n";
      if ( abs($bin1-$bin2) <= 5000 and ( $chr1 eq $chr2) ){
      print "$chr1\t$bin1\t$bin2\t\t: " . abs($bin1-$bin2). "\n";
#           }
     }
}  

```

---

### Post by jraab22 on 2008-06-30
THe input file looks like this:

chr1	807432	4
chr1	810832	3
chr1	811232	3
chr1	811632	3
chr1	812032	4
chr1	814232	5
chr1	814832	3
chr1	815632	6
chr1	816032	4
chr1	822632	5
chr2	999632	3
chr2	1000032	4
chr2	1004832	3
chr2	1005632	3
chr2	1021032	3
chr2	1093632	5
chr2	1093832	4
chr2	1097632	4
chr2	1098832	5
chr2	1106432	3

The output this:
chr1	807432	810832
chr1	811632	812032
chr1	814832	815632
chr2	1004832	1005632
chr2	1093632	1093832
chr2	1098832	1106432

What I want it to do is to have that output "consilidated so that if any two rows were within 5000 of each other, they would be combined, until that no longer could occur. For the above example the correct output would have been, 
chr1 807432   816032 (this value didn't even make the output I have). 
chr2 1004832  1106432

These aren't within 5000 of each other, but there were intervening numbers on my list that were. 

My mistake is trying to compare them pairwise I think, which only goes through once and only so that 1 is compared to 2 and then 3 is compared to 4.  

I'm glad to see what I wrote isn't horribly incorrect, I'm just not sure how to write it so that it does what I want.  

If thats any clearer, and you have any advice I'd be greatful, thanks

---

### Post by ghostdog74 on 2008-06-30
well, not going to do the whole thing for you but some ideas. See if you like it.
```

use strict;
use warnings;
my $in2="file";
open(IN, "<",$in2)||die "cannot open $in2 $!\n";
my %h=();

while (defined( my $line1 = <IN> )) {
   my ($chr1,$bin1,$tag1)=split(/\s+/,$line1);  
   if ( defined($h{$chr1}) ){
        $h{$chr1} = $h{$chr1} . " " .$bin1 ;
    }else {
        $h{$chr1}="";
    }
 
}
close (IN);

  while ( my ($key, $value) = each %h) {
       print $key  ,sort($value) , "\n" ;
       # get first element and last element of $value. 
       # if they are within 5000, then print the whole $value
       # else: get second last element and compare with first element and check again and so on. you can use for loop and decrement counter.        
               
  }


```
you can store all your values into a hash. then go through the hash , sorting the values at the same time.

---

### Post by jraab22 on 2008-06-30
Thanks for taking the time, I'll spend some time trying it that way and see how it turns out, appreciate the help.

---

### Post by jraab22 on 2008-07-02
I'm still somewhat stuck on this problem. In order to simplify I just made a small array of numbers.  And took ghostdogs helpful advice on how to sort them into ranges.
```

my @list = qw/10 15 18 28 30 35 50 52 54 100 101 105 108 109 115 127 136 137 144 /;
my @sorted = sort {$a <=> $b} @list;
my $length =scalar@sorted;
my $i;
for ($i=0;$i<=$length;$i++){
    my ($start,$end)=&ranges(@sorted);
    if ($start!=0){
       print"$start\t$end\n";
}  
shift @sorted;
}

sub ranges: {
#print "sub ranges called\n";
my ($first_num,@rest)=((shift @_),@_);
#print "\t$first_num\n";
#print "@rest\n";
while ( @rest) {
    my $last=pop (@rest);
    my $diff=abs($first_num-$last);
    if ($diff<=7){
        my $start=$first_num;
        my $end = $last;
        return ($start,$end);
        }

```

This however left me with a bunch of overlappign ranges, I tried to consolidate them by reading the start and ends from a file and using this code.

```

while (<IN>){
for ($line1=<IN>;$line1;$line1=<IN>){
    my($start1,$end1)=split(/\t/,$line1);
    chomp $end1;
    my $line2=<IN>;
    my ($start2,$end2)=split(/\t/,$line2);
    chomp $end2;
    if ($end1>=$start2){
     print "$start1\t$end2\n";
     }else{ print "$start1,$end1\n$start2\t$end2\n";
        }
    $line1=$line2;
   }
}

```
This gets me one stop closer, but doesn't fully combine.  
My first question is , is there a way to continue looping this function on the output until they are combined as much as possible. For this loop I basically said if any the next start value in my list is overlapping with the previous end combine the two.  

While looking for solutions on combining ranges of integers I came across this
[http://www.wellho.net/resources/ex.php4?item=p209/coverage.pm](http://www.wellho.net/resources/ex.php4?item=p209/coverage.pm)
```

our @nreg;
 
sub addregion {
        my ($start,$end) = @_;
        if ($start > $end) {
                ($start,$end) = ($end,$start);
                }
        my $done = 0;
        my $k;
        for ($k=0;$k<@nreg;$k++) {
# new region starts after old region ends
                next if ($nreg[$k][1] < $start);
# new region ends before old region starts
                if ($end < $nreg[$k][0]) {
                        splice(@nreg,$k,0,[$start,$end]);
                        $done = 1;
                        last;
                        }
# regions overlap
                $nreg[$k][0] = $start < $nreg[$k][0] ? $start : $nreg[$k][0];
                $nreg[$k][1] = $end > $nreg[$k][1] ? $end : $nreg[$k][1];
                $done = 1;
# Combine multiple regions if the new section has brough about an overlap
                while ($k < $#nreg and $nreg[$k][1] > $nreg[$k+1][0]) {
                        $nreg[$k][1] = $nreg[$k+1][1];
                        splice(@nreg,$k+1,1);
                        }
                last;
        }
        unless ($done) {
                push @nreg,[$start,$end];
                }
}

```

It appears to do what I want, but I'm struggling to use it.  It seems to take a list of lists and split them into start and end values.  When I give it such a structure it returns 1 not a list of ranges.  If anyone has a suggestion on how to incorporate this into my problem please let me know.

Sorry for the long post

---

### Post by jraab22 on 2008-07-04
Just to update my own topic.  I ended up using the bioperl module Bio::Range to solve my problem of creating ranges.  These numbers were genome coordinates anyway, and the next step is to get the sequences associated , so it made some sense to use the bioperl modules (although Bio::Range may work for this even if they were just regular numbers).

---

