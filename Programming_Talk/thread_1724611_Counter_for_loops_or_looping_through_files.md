---
title: "Counter for loops or looping through files"
date: 2011-04-08
forum: Programming Talk
---

### Post by bashologist on 2011-04-08
Looks like this.
```
for ((i = 0; i < 101; i++)); do echo 100 $i; sleep 0.05; done | counter.pl
  18% [=========                                             ]  18/100 
  41% [======================                                ]  41/100 
  69% [=====================================                 ]  69/100 
 100% [======================================================] 100/100 
```

Very simple to use just send the program standard output that looks like this.
```
100 0
100 10
100 20
100 100
```

Example 1.
```
for ((i = 0; i < 101; i++)); do echo 100 $i; sleep 0.05; done | perl counter.pl
```

Example 2.
```
counter=1
files=(*)
for file in "${files[@]}"; do
echo ${#files[@]} $((counter++))
# replace sleep command with something that uses $file
sleep 0.25
done | perl counter.pl
```

Script.
```
#!/usr/bin/env perl

$|++;

while (readline) {
	next unless /(\d+)\s+(\d+)/;
	exit if $1 eq 0;

	my $cols = qx/tput cols/;
	chomp $cols;

	my $s3s = 1 + (length $1) * 2;
	my $s2s = $cols - $s3s - 10;

	my $s1 = ($2 != 0 ? int 100 / ($1 / $2) : 0);
	my $s2 = ($2 != 0 ? $s2s / ($1 / $2) : 0);

	printf "\r % 3s%% [%-${s2s}s] % ${s3s}s ", $s1, "=" x ($s2 > $s2s ? $s2s : $s2), "$2/$1";
}

print "\n";
```

---

