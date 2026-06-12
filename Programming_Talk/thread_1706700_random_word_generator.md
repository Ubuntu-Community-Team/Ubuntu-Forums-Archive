---
title: "random word generator"
date: 2011-03-14
forum: Programming Talk
---

### Post by sn0m on 2011-03-14
Hi guys
Can someone help me write a script.
I need to generate randomly a word from a list.
So lets say I have 4 entries on my list, ie
list.txt= 1)AR 2)RRR 3)ARR 4)NNT
I need to have a script which each time it is executed, it generates randmly AR or NNT etc.
I tried to use $RANDOM function but struggling to get output to produce words rather then numbers
Thanks
Sokol

---

### Post by cipherboy_loc on 2011-03-14
A couple of questions:

1) What language(s)?
2) Will you supply a word list, or should it use a default word list (/usr/share/dict/*)?
3) One word or multiple?

Personally, I could write it in Perl fairly quickly...

Thanks,
Cipherboy

---

### Post by sn0m on 2011-03-14
Thanks cipherboy
I will supply a list, it is a text file which is kept in my home directory.
Lines usually contains one word but occasionally can contain group of words.
But it would be fine if the script printed out one line at time generated randomly through lines in the text file.
Many thanks
Sokol

---

### Post by Joeb454 on 2011-03-14
*Thread moved to **Programming Talk**.*

---

### Post by sisco311 on 2011-03-14
```
shuf -n1 file
```
or
```
rl -c1 file
```

---

### Post by cipherboy_loc on 2011-03-14
sn0m: Sisco's command is better than mine, but here is my Perl script: 

```

#!/usr/bin/perl                                                                                                                   

use strict;
use warnings;

sub main {
    my $file_path = init();
    open(FILE, "<", $file_path);
    my @file_array = <FILE>;
    close(FILE);

    my $line_max = $#file_array+1;
    my $line = (rand()*100) % $line_max;
    print $file_array[$line];
}

sub init {
    my $file = "";

    if ($#ARGV == -1) {
        print STDERR "Usage: random_line.pl [file]\n\n";
        exit 1;
    } elsif ($ARGV[0] eq '--help') {
        print STDERR "Usage: random_line.pl [file]\n\n";
        exit 0;
    } else {
        $file = $ARGV[0];
        return $file;
    }
}

main();


```

---

### Post by sn0m on 2011-03-14
Thnaks guys for all you answers.
Cipherboy, is there a way of telling script not to repeat the same word and where the file is?
I'm planning to alias to a letter and would like the script to print on screen words rather then executing with the file all the time?
Thanks Sokol

---

### Post by kaibob on 2011-03-14
Deleted by kaibob.

---

