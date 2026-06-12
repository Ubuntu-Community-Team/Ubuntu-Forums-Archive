---
title: "Perl to fill the lost value with previous value"
date: 2013-01-11
forum: Programming Talk
---

### Post by tzeronone on 2013-01-11
For example, I have a **text file** consist of this number
```

(#ID #number)
1 0.062
742 -1.953
744 0.176
910 -2.000
913 0.164

```
The #ID is a sequence number. Can see that ID#2 to ID#741, ID#743, ID#745 to ID#909, ID#911 to ID#912 are not recorded. My wish output is
```

(#ID #number)
1 0.062
2 0.062
3 0.062
:
740 0.062
741 0.062
742 -1.953
743 -1.953
744 0.176
745 0.176
:
909 0.176
910 -2.000
911 -2.000
912 -2.000
913 0.164

```

The **number** of the **unknown ID** will **repeat **with the **number **of the **previous recorded ID**. Any idea?

---

### Post by Vaphell on 2013-01-11
```
#! /usr/bin/perl -w
use strict;

my $prev_id = 0;
my $prev_val = 0;

while (<>)
{
  my( $id, $val ) = split;
  for( my $i=$prev_id+1; $i<$id; $i++ ) { printf( "%d %s\n", $i, $prev_val ); }
  printf( "%d %s\n", $id, $val );
  ($prev_val, $prev_id) = ($val, $id);
}
------------------------------------------------
$ ./fill.pl <<< $'1 -0.222\n4 3.33\n9 1.01'
1 -0.222
2 -0.222
3 -0.222
4 3.33
5 3.33
6 3.33
7 3.33
8 3.33
9 1.01
```

---

### Post by Tony Flury on 2013-01-11
> **tzeronone said:**
> For example, I have a **text file** consist of this number
```

(#ID #number)
1 0.062
742 -1.953
744 0.176
910 -2.000
913 0.164

```
The #ID is a sequence number. Can see that ID#2 to ID#741, ID#743, ID#745 to ID#909, ID#911 to ID#912 are not recorded. My wish output is
```

(#ID #number)
1 0.062
2 0.062
3 0.062
:
740 0.062
741 0.062
742 -1.953
743 -1.953
744 0.176
745 0.176
:
909 0.176
910 -2.000
911 -2.000
912 -2.000
913 0.164

```

The **number** of the **unknown ID** will **repeat **with the **number **of the **previous recorded ID**. Any idea?


This looks horribly like homework - I can think of no practical reason for this - unless the OP can tell me otherwise ?

---

### Post by tzeronone on 2013-01-14
> **Tony Flury said:**
> This looks horribly like homework - I can think of no practical reason for this - unless the OP can tell me otherwise ?

It practice how to bring the value of the second column to mathematical operation. Open your mind that nothing is impossible to learn.

---

