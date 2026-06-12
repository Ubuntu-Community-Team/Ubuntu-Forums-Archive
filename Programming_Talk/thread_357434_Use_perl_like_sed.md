---
title: "Use perl like sed"
date: 2007-02-09
forum: Programming Talk
---

### Post by LotsOfPhil on 2007-02-09
I would describe what I want to do as "using perl to act like sed." I have a very simple line edit to make. I can do it with sed, but don't really know what to do in perl. The catch is I have to do it with perl.

The file to be changed has this in it:
```
# Change here
        my @round2 = (57,17,13,6,56,41,27,29,3,21,9,59,12,19,63,53,58,32,7,1,45,11,5,18,4,23,52,2,31,22,34,26);
```
The line to change is 46. I find this out by finding the #Change here line number and adding 1.

With sed I'd just type 
```
sed -i 46s/57,// $file
```

With perl, what? What I have now is:
```

open(subr, "$file");
        while(<subr>) {
                if (/Change here/) {
                        $line = <subr>;
                        $line =~ s/57,//;
                        print "$line";}
        }

```

Any help would be appreciated.

---

### Post by phossal on 2007-02-09
I think no one has helped you because no one understands what you're doing. Are you doing a simple replacement, or what?

---

### Post by LotsOfPhil on 2007-02-09
I want to take this line, which is in a file, and get rid of the "57,"
```
my @round2 = (57,17,13,6,56,41,27,29,3,21,9,59,12,19,63,53,58,32,7,1,45,11,5,18,4,23,52,2,31,22,34,26);

```

---

### Post by phossal on 2007-02-09
Here is a global substitution:

```
#!/usr/bin/perl

$x = "This is a line with 57 in two places. Here is 57 again."; #A line with 2 57's
$x =~ s/57/46/g; #Replacing both, using g for global

print $x; #Printing out the changed line.
```

---

### Post by phossal on 2007-02-09
Without trying to give it a lot of features, here is a sed-like script:
```

#Open the file
open(INF, "<$ARGV[0]") or die "Cannot open $!";
@contents = (<INF>);
close(INF);
open(OUF, ">$ARGV[0]") or die "Cannot open $!";

foreach $line (@contents) {
	$x = $line;
	$x =~ s/($ARGV[1])/$ARGV[2]/g;
	print OUF $x."\n";
}

close(OUF);
```

---------------------------------------
[EDIT]  If you call the program above (sed.pl), like so: *perl sed.pl filename search replace* , the script will try to open "filename", and recreate the file line by line, replacing whatever text you've put as argument 2 with whatever text you put as argument 3.

---

### Post by LotsOfPhil on 2007-02-10
Thanks to all for your replies. As I understand it, none of these will change the file that you read in. I am looking to take a file, find a string in it, and change that string *in the same file*.

Right now I am looking at the module Tie::File which looks promising.
[http://perldoc.perl.org/Tie/File.html](http://perldoc.perl.org/Tie/File.html)

Thanks for your help. If anyone else has advice (I hear there's more than one way to do it) please let me know.

---

### Post by phossal on 2007-02-10
I edited the script I suggested previously so that it will do what you want.

---

### Post by LotsOfPhil on 2007-02-10
Phossal, thanks for your help. Below is what I ended up doing. Like I mentioned, I used the Tie::File module.

If anyone knows a more efficient way to get the line number I want, I'm all ears. Otherwise, I'm done.

```

sub add_loser {
        my $lsr = $_[0];
                                                                                
        my $linenum;
        my @array;
        tie @array, 'Tie::File', $filetochange;
        for($i=0; $i<=$#array; $i++) {
                if($array[$i] =~ /# Change here/) {
                        $linenum = $i;
                }
        }
                                                                                
        # The [^0-9] handles single digit $lsr
        if($array[$linenum+1] =~ /[^0-9]$lsr,/) {
                $array[$linenum+1] =~ s/([^0-9])$lsr,/\1/;
        }
        elsif($array[$linenum+1] =~ /,$lsr\)/) {
                $array[$linenum+1] =~ s/,$lsr\)/\)/;
        }
        else { }
}

```

---

### Post by phossal on 2007-02-10
Phil, I'm still confused about what you're actually trying to do. You have a file full of lines, and in the middle of a line you have text that you want to replace? Why do you need the extra module?

---

### Post by stoffe on 2007-02-10
The one thing that you can't do that easily is to go to a specific line to just edit that one, that's why it isn't as easy. However, here's a quick-and-dirty for the commandline that does what you want, and as a bonus it find the correct line for itself by looking for the "Change me" line:

```
$ perl -pi.bak -e 's/57,//, undef $next if $next;$next++ if /# Change here/;' $file
```

Some things to note: 

* the order of the commands and the syntax is a bit counter-intiutive, it could be written a lot clearer but less effective ;)
* the "i.bak" part saves the original in $file.bak, you can remove it if you don't need it.
* $next tracks if the next line should be edited, could be $n instead or something to keep it shorter
* it makes sure that no other lines later are edited by "undef $next" (tested)
* it will edit more lines if you have more "# Change here" comments

---

### Post by LotsOfPhil on 2007-02-11
> **phossal said:**
> Phil, I'm still confused about what you're actually trying to do. You have a file full of lines, and in the middle of a line you have text that you want to replace? Why do you need the extra module?

I don't need the Tie module, you're right. Also, you summed up exactly what I was trying to do and your code works just as well as mine. I just didn't really want to open a file, read it in, close the file, reopen it (for writing) and then write to it. Thanks a lot, Phossal.

---

