---
title: "Perl multiple matches"
date: 2008-03-01
forum: Programming Talk
---

### Post by vicpascow on 2008-03-01
I have two files:

one with a list of characters, i.e.:
aaa
bbb
ccc

the second file looks like this:
aaa terre
aaa terte
aaa tere
bbb tee
ccc terrr
ccc asdf
aaa 342
bbb one

etc.

I want to try and combine these to result in:
aaa terre terte tere 342
bbb tee one
ccc terrr asdf



What I keep getting is an output that looks identical to the second file (I'm having trouble getting everything on the same line).

Any suggestions?

---

### Post by slavik on 2008-03-01
off the top of my head, all of the following code is under GPL3 :)

```

open $in_key, "file1" or die $!;
open $in_data, "file2" or die $!;

while ($key = <$in_key>) {
  while (<$in_data>) {
    push @{ $data{$key} }, $1 if (/$key\s(.*?)/);
  }
}

for (keys %data) {
  print $_." ";
  map { print $_." " } @{ $data{$_} };
  print "\n";
}

```

it is possible to get rid of the first file and do something like the following:

```

open $in_data, "file" or die $!;

while (<$in_data>) {
  push @{ $data{$1} }, $2 if (/(.*?\s(.*?)/);
}

#alternative to the loop: map { push @{ $data{$1} }, $2 if (/(.*?\s(.*?)/) } <$in_data>;

for (keys %data) {
  print $_." ";
  map { print $_." " } @{ $data{$_} };
  print "\n";
}

```

---

### Post by vicpascow on 2008-03-10
This might be beating a dead horse, but using this same example, I am trying to do the following:

the first file will still be
aaa
bbb
ccc

the second file can contain the same stuff, with a few other data points (see bottom):
aaa terre
aaa terte
aaa tere
bbb tee
ccc terrr
ccc asdf
aaa 342
bbb one
aaa bbb

now what I initially wanted to do was to yield the following (for aaa):
aaa terre terte tere 342 bbb

what i would like to  do is iterate this process in a way so that now, because bbb has it's own data, yield:
aaa terre terte tere 342 bbb **one**

'one' being the data from bbb, which is part of the data of aaa

so if there was even another data point: one asda
the result would have been aaa terre terte tere 342 bbb one asda

---

### Post by slavik on 2008-03-10
> **vicpascow said:**
> This might be beating a dead horse, but using this same example, I am trying to do the following:

the first file will still be
aaa
bbb
ccc

the second file can contain the same stuff, with a few other data points (see bottom):
aaa terre
aaa terte
aaa tere
bbb tee
ccc terrr
ccc asdf
aaa 342
bbb one
aaa bbb

now what I initially wanted to do was to yield the following (for aaa):
aaa terre terte tere 342 bbb

what i would like to  do is iterate this process in a way so that now, because bbb has it's own data, yield:
aaa terre terte tere 342 bbb **one**

'one' being the data from bbb, which is part of the data of aaa

so if there was even another data point: one asda
the result would have been aaa terre terte tere 342 bbb one asda
a directional list (a graph) ...

---

### Post by vicpascow on 2008-03-10
thanks.  i'll look into that.  

vic

---

### Post by vicpascow on 2008-03-12
just noticing that the original script is not yielding any results for me.  

i have tried playing around with the line:

    push @{ $data{$key} }, $1 if (/$key\s(.*?)/);

but to no avail...

---

