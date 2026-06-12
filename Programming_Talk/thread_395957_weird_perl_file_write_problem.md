---
title: "weird perl file write problem"
date: 2007-03-28
forum: Programming Talk
---

### Post by monkeyking on 2007-03-28
I've made a big program in perl, and i've isolated the problem to the following procedure.


Basicly what I want is to add the array given as a parameter, as a new column in $outfile
When i do the print `cat $outfile`, it correctly displys the file before I edit it.

After I've open and closed the file I check again with the print `cat $outfile`. And I can see that the file has been updated.

Now the next time I call insert, It for some strange reason opens the oldfile since the print `cat $outfile`. Displays the values like the first time I called the print `cat $outfile.

This is indeed the weirding way of perl

```

sub insert{
  print "insert called:". $ins ."\n";
  $ins++;
  my @toBeInserted = @_;
  print `cat $outfile`;
  
  open(FILE2,$outfile)||die "you stupid ****, file doesn't exit\n";;
  open(FILE3,">"."tmp.file")||die "you stupid ****, file doesn't exit\n";;
  my $cnt=0;
  while (<FILE2>){
    chomp;
    my @fields = (split /[ \t]+/,$_);

    push(@fields,$toBeInserted[$cnt]);
    foreach(@fields){
      my $tmpString = $_ . "\t";
      print FILE3 $tmpString;
    }
    print FILE3 "\n";
    
    $cnt++;
  }
  
  close(FILE2);
  close(FILE3);
  #now swap the files
  unlink($outfile) || die "Cannont delete old file.\n";
  rename("tmp.file", $outfile) || die "Cannot rename file\n";
  print `cat $outfile`; 
}

```

---

### Post by Mr. C. on 2007-03-28
Its not the cleanest or easiest way to do this, but it works perfectly fine for me.  Your diagnosis is mistaken.  Consider the return values of your close statements.

```

$ cat outfile
line 1
line 2
line 3
$ doit.pl a b c
line    1       a
line    2       b
line    3       c
```

Anyone who says "weirding way", has no ground to provide comment on the ways of other's.

MrC

---

### Post by monkeyking on 2007-03-28
I'm having some diffuculties understanding you answer.

What is wrong with my diagnosis?
And what is your doit.pl.

Thanks for the reply

---

### Post by Mr. C. on 2007-03-29
The code has a number of problems; I indicated one of them.  It doesn't deal with more items passed to insert than lines contained in outfile.

Here's your code, plus some debug statements and calls to your insert function.

```
#!/usr/bin/perl

my $outfile=outfile;
sub insert{
  print "insert called:". $ins ."\n";
  $ins++;
  my @toBeInserted = @_;
  print `cat $outfile`;

  open(FILE2,$outfile)||die "you stupid ****, file doesn't exit\n";;
  open(FILE3,">"."tmp.file")||die "you stupid ****, file doesn't exit\n";;
  my $cnt=0;
  while (<FILE2>){
    chomp;
print "LINE:\"$_\"\n";
    my @fields = (split /[ \t]+/,$_);

    push(@fields,$toBeInserted[$cnt]);
    foreach(@fields){
      my $tmpString = $_ . "\t";
      print "STRING: \"$tmpString\"\n";
      print FILE3 $tmpString;
    }
    print FILE3 "\n";

    $cnt++;
  }

  close(FILE2);
  close(FILE3);
  #now swap the files
  unlink($outfile) || die "Cannont delete old file.\n";
  rename("tmp.file", $outfile) || die "Cannot rename file\n";
  print `cat $outfile`;
}

insert qw(a b c);
insert qw(d e f);
insert qw(g h i j);
```

```
$ cat outfile
line    1
line    2
line    3
$ doit.pl
$ cat outfile
line    1       a       d       g
line    2       b       e       h
line    3       c       f       i

```

As you can see, it does essentially what you are asking.  You claim that outfile reverts itself to the contents of the file you just unlinked.  This is not happening, so your conclusion is faulty.  There is something else wrong that you are not seeing.

MrC

---

