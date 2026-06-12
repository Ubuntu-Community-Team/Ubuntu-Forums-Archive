---
title: "Representing home directory in Perl (~)"
date: 2009-07-15
forum: Programming Talk
---

### Post by c0mput3r_n3rD on 2009-07-15
Ok, so I'm learning Perl, and I'm writing a program (just practice some stuff I've learned) that's asks you where you want to write a file to (which directory), and then what text you want to add to it (1 line).  Here's what I got:
```

#!/usr/bin/perl

print "Put file in home directory? (y/n) ";
$where = <STDIN>;
chop $where;
if ($where eq "y")
{
    print "Name of file? ";
    $where = <STDIN>;
    $dir = <~/$where>;
}
elsif ($where eq "n")
{
    print "Write full path!!!\n Dir:";
    $loc = <STDIN>;
    $str1 = $loc;
}
else
{
    print "wrong answer.\n";
    while ($where ne 'y' || $where ne 'n')
    {
        print "Try again (y/n): ";
        $where = <STDIN>;
        chop $where;
    }
}
    
open(OUT, ">$str1") || die "Cannot open $out for write :$!"; # Open file for writing
print "Enter text to write: \n";                 
$text = <STDIN>;                         # Read string to write
print OUT "$text";                         # Write string to file
close(OUT);                                 # Close file    

# # # # # # # # # # # # # # #
# # Open files for reading
# # # # # # # # # # # # # # #
open(INFO, "$str1");
@lines = <INFO>;
foreach $line (@lines)                         # Print contents of file
{
    print $line, "\n";
}


```Now I'm sure it's not the best it could be and could be written better and all that but I'm not worried about it.  The problem I'm having is right here:
```

 $dir = <~/$where>;

```it's telling me that the directory doesn't exist, yet it should be the home directory + what ever $where contains.  What am I missing here

---

### Post by c0mput3r_n3rD on 2009-07-15
Never mind, it was that I wasn't assigning the value file name to $str1 so be used as the path.      ](*,)
I thought I had it ride.

---

