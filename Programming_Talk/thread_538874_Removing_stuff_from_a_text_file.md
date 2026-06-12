---
title: "Removing stuff from a text file"
date: 2007-08-30
forum: Programming Talk
---

### Post by diebels on 2007-08-30
Hi, anybody good at text manipulation here?

I have a file with stuff like:
```
R   1 543780.56801015.4 8.1   2 543378.06801015.9 8.1   3 543365.56801016.4 8.11
R   4 543353.06801017.0 8.1   5 543340.66801017.5 8.1   6 543328.16801018.1 8.01
R   7 543315.66801018.6 8.0   8 547803.16801019.2 8.0   9 543278.76801019.8 8.01
R  10 543278.26801020.3 8.0  11 543265.76801020.9 8.0  12 543253.26801021.5 8.01
R  13 543240.86801022.1 8.0  14 543788.36801022.7 8.0  15 543215.86801023.3 8.01
R  16 543203.36801023.9 8.0  17 543190.96805424.5 8.0  18 543178.46801078.1 8.01
R  19 543165.96801025.7 8.0  20 543153.46801026.3 8.0  21 543141.06801026.9 8.01
R  22 543788.56801027.5 8.0  23 547816.06785428.1 8.0  24 543103.56801028.8 8.01
R  25 543091.16801029.4 8.0  26 543078.66802730.0 8.0  27 543066.16551030.7 8.01
R  28 543053.76801031.3 8.0  29 543041.26801032.0 8.0  30 543028.76801032.6 8.01
R  31 543016.26801033.3 8.0  32 544503.86851034.0 8.0  33 542991.36801034.6 8.01
R  34 578978.86801035.3 8.0  35 542966.46889036.0 8.0  36 542953.96801036.7 8.01
R  37 542941.46801037.4 8.0  38 542789.06801038.1 8.0  39 542916.56805438.8 8.01
R  40 542904.06801039.5 8.0  41 542891.66801040.3 8.0  42 542879.16801041.0 8.01
R  43 542866.66541041.7 8.0  44 545454.16878042.4 8.0  45 547541.76781043.2 8.01
```

See the numbers increasing from 1 to 44 here. It goes up to 3000.

I want to remove everything except number 1, 40, 80, 120 and so on up to 3000.

The result should be:
```
R    1 543390.57801015.4 8.1   40 542784.05401039.5 8.0  80 545441.76801043.2 8.01
R  120 543390.78801015.4 8.1  160 542904.06854039.5 8.0 200 547841.76781043.2 8.01
```

And so on to 3000.

Anybody have any hints on how to do this? Awk, python, perl?

---

### Post by `GooZ´ on 2007-08-30
You could always read the text file line per line in C, then parse it (With the %d parameter), and check if this integer can be divided by 40 (number % 40 == 0). If that's NOT the case, let it print the line to another text file (appending it).

---

### Post by LaRoza on 2007-08-30
> **`GooZ´ said:**
> You could always read the text file line per line in C, then parse it (With the %d parameter), and check if this integer can be divided by 40 (number % 40 == 0). If that's NOT the case, let it print the line to another text file (appending it).

Python would be good here, as would Perl. I am not going to be here long enough to work on it, I have to leave, sorry.

---

### Post by pmasiar on 2007-08-30
> **diebels said:**
> Anybody have any hints on how to do this? Awk, python, perl?

Python, of course, why would anyone bother doing this in C?

```

for line in open('path/to/file'):
    multi = line.split()[1:] # all 3 parts together, R is removed
    for i = range(2):
        parts = multi[i*3:i*3 + 3]
        # now we have regular parts
        counter = int(parts[0])
        if counter == 1 or not counter % 40:
            print parts # format as you see fit

```

Warning, not tested! :-)

---

### Post by stylishpants on 2007-08-30
Fun.  Here's a ruby solution.

```
#!/usr/bin/ruby -w

require 'enumerator'

raise "Specify data file name" if ARGV.empty?

# Extract all the data tuples that should be kept
keep = Array.new
File.readlines(ARGV.shift).each do |line|
    line.scan(/(\d+)\s+([\d\.]+)\s+([\d\.]+)/).each do |match|
        index = match.first.to_i
        keep << match if (index == 1) or (0 == index % 40)
    end
end
    
# Print the kept ones, in the same output format as the original
keep.each_slice(3) do |triplet|
    print "R" 
    
    triplet.each do |data|
        print " %4s %17s %-4s" % data
    end

    puts
end 

```

---

### Post by bogolisk on 2007-08-30
> **diebels said:**
> Hi, anybody good at text manipulation here?

I have a file with stuff like:
```
R   1 543780.56801015.4 8.1   2 543378.06801015.9 8.1   3 543365.56801016.4 8.11
R   4 543353.06801017.0 8.1   5 543340.66801017.5 8.1   6 543328.16801018.1 8.01
R   7 543315.66801018.6 8.0   8 547803.16801019.2 8.0   9 543278.76801019.8 8.01
R  10 543278.26801020.3 8.0  11 543265.76801020.9 8.0  12 543253.26801021.5 8.01
R  13 543240.86801022.1 8.0  14 543788.36801022.7 8.0  15 543215.86801023.3 8.01
R  16 543203.36801023.9 8.0  17 543190.96805424.5 8.0  18 543178.46801078.1 8.01
R  19 543165.96801025.7 8.0  20 543153.46801026.3 8.0  21 543141.06801026.9 8.01
R  22 543788.56801027.5 8.0  23 547816.06785428.1 8.0  24 543103.56801028.8 8.01
R  25 543091.16801029.4 8.0  26 543078.66802730.0 8.0  27 543066.16551030.7 8.01
R  28 543053.76801031.3 8.0  29 543041.26801032.0 8.0  30 543028.76801032.6 8.01
R  31 543016.26801033.3 8.0  32 544503.86851034.0 8.0  33 542991.36801034.6 8.01
R  34 578978.86801035.3 8.0  35 542966.46889036.0 8.0  36 542953.96801036.7 8.01
R  37 542941.46801037.4 8.0  38 542789.06801038.1 8.0  39 542916.56805438.8 8.01
R  40 542904.06801039.5 8.0  41 542891.66801040.3 8.0  42 542879.16801041.0 8.01
R  43 542866.66541041.7 8.0  44 545454.16878042.4 8.0  45 547541.76781043.2 8.01
```

See the numbers increasing from 1 to 44 here. It goes up to 3000.

I want to remove everything except number 1, 40, 80, 120 and so on up to 3000.

The result should be:
```
R    1 543390.57801015.4 8.1   40 542784.05401039.5 8.0  80 545441.76801043.2 8.01
R  120 543390.78801015.4 8.1  160 542904.06854039.5 8.0 200 547841.76781043.2 8.01
```

And so on to 3000.

Anybody have any hints on how to do this? Awk, python, perl?

```

awk '/^R.+/ { if (($2 == 1) || (($2 % 40) == 0)) print $0;  }' < your_file.txt

```

---

### Post by Paul820 on 2007-08-30
> awk '/^R.+/ { if (($2 == 1) || (($2 % 40) == 0)) print $0;  }' < your_file.txt

Now that's impressive, only one line. I have never heard of awk, i have just been reading about it on wikipedia.

---

### Post by pmasiar on 2007-08-30
> **bogolisk said:**
> ```

awk '/^R.+/ { if (($2 == 1) || (($2 % 40) == 0)) print $0;  }' < your_file.txt

```

Are you sure that your solution correctly checks for triplets of data in each line?

BTW: Why you quoted whole article including test data? Save the electrons!

---

### Post by bogolisk on 2007-08-30
> **pmasiar said:**
> Are you sure that your solution correctly checks for triplets of data in each line?

BTW: Why you quoted whole article including test data? Save the electrons!

Sorry I misread the original question. I'll cook up another one.

---

### Post by ghostdog74 on 2007-08-30
```

awk '$2 == 1 || ($2 % 40 == 0)  { arr[c++]=$2" "$3" "$4" "}
	 ($5 % 40) ==0  { arr[c++]=$5" "$6" "$7" " }
	 ($8 % 40)==0 {  arr[c++]=$8" "$9" "$10" " }
END {
  for (i=0;i<=c;i++){
    if(i%3==0){print ""}
	printf arr[i]
  }
}' "file"

```

---

### Post by ghostdog74 on 2007-08-30
> **bogolisk said:**
> ```

awk '/^R.+/ { if (($2 == 1) || (($2 % 40) == 0)) print $0;  }' < your_file.txt

```

no need for input redirection....
```

awk '/^R.+/ { if (($2 == 1) || (($2 % 40) == 0)) print $0;  }' your_file.txt

```

---

### Post by ghostdog74 on 2007-08-30
> **`GooZ´ said:**
> You could always read the text file line per line in C, 

for educational purposes, yes. For practical purposes, not really..

---

### Post by trwww on 2007-08-30
Gotta represent perl! Though the ruby version is cool!

```
use warnings;
use strict;

use constant BASE => 40;
use constant COLUMNS => 3;

use IO::File;
my $fh = IO::File->new('extract_records.txt');

my @data;

my $column = 0;
while ( my $line = $fh->getline ) {
  while ( $line =~ m|(\d+) ([.\d]+ [.\d]+)|g ) {
    my $index = $1; my $data = $2;
    if ( ($index == 1) or (not $index % BASE) ) {
      push @{$data[ $column % COLUMNS ]}, [$index, $data];
      $column++;
    }
  }
}

foreach my $row ( 0 .. $#{ $data[0] } ) {
  print "R";
  foreach my $col ( 0 .. COLUMNS - 1 ) {
    if ( $data[$col]->[$row] ) {
      printf "%5s %-22s", $data[$col]->[$row][0], $data[$col]->[$row][1];
    }
  }
  print "\n";
}
```

---

