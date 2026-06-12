---
title: "Program to generate Hex"
date: 2009-10-12
forum: Programming Talk
---

### Post by Jackp90 on 2009-10-12
I was working on a program to generate every hexadecimal number between 0 and FFFFFF originally I was trying to do it in Perl since I know that language the best (I"m not really proficient in it though). and this is where I was when I gave up all hope on perl and tried Bash:

```
#!/usr/bin/perl -w
use strict;

my @array = (
0, 1, 2, 3, 4, 5, 6, 7, 8, 9, "A", "B", "C", "D", "E", "F"
);

system ({{@array}{@array}});

``` 

I was trying to figure out a way to multiply arrays together using bash brace expansion.  That I was thinking that if I could create ranged array that I might be able to do this incredibly easy like so:

> #!/usr/bin/perl -w
use strict;

my @array{1..6} = (
0, 1, 2, 3, 4, 5, 6, 7, 8, 9, "A", "B", "C", "D", "E", "F"
);

print  @array1, "\n";
print  {{@array1}{@array2}};


With the Bash you can see though it will work it is a painstakingly long process and that there is probably an easier and much shorter way to accomplish what I am trying:

```
#!/bin/bash

echo {0..9}
echo {A..F}
echo {0..9}{0..9}
echo {0..9}{A..F}
echo {A..F}{0..9}
echo {A..F}{A..F}
echo {0..9}{0..9}{0..9}
echo {0..9}{A..F}{0..9}
echo {A..F}{0..9}{0..9}
echo {A..F}{A..F}{0..9}
echo {0..9}{0..9}{A..F}
echo {0..9}{A..F}{A..F}
echo {A..F}{0..9}{A..F}
echo {A..F}{A..F}{A..F}
echo {0..9}{0..9}{0..9}{0..9}
echo {0..9}{A..F}{0..9}{0..9}
echo {A..F}{0..9}{0..9}{0..9}
echo {A..F}{A..F}{0..9}{0..9}
echo {0..9}{0..9}{A..F}{0..9}
echo {0..9}{A..F}{A..F}{0..9}
echo {A..F}{0..9}{A..F}{0..9}
echo {A..F}{A..F}{A..F}{0..9}
echo {0..9}{0..9}{0..9}{A..F}
echo {0..9}{A..F}{0..9}{A..F}
echo {A..F}{0..9}{0..9}{A..F}
echo {A..F}{A..F}{0..9}{A..F}
echo {0..9}{0..9}{A..F}{A..F}
echo {0..9}{A..F}{A..F}{A..F}


```

Thank you for your time and patience.

---

### Post by diesch on 2009-10-12
```
seq 0 0xFFFFFF | xargs printf '%06X\n'
```

---

### Post by MadCow108 on 2009-10-12
same in perl:
```

for($i = 1; $i < 0xFFFFFF; $i++) {
print sprintf("%06x",$i),"\n";
}

```

---

### Post by Jackp90 on 2009-10-12
> **MadCow108 said:**
> same in perl:
```

for($i = 1; $i < 0xFFFFFF; $i++) {
print sprintf("%06x",$i),"\n";
}

```

What if I wanted to do other characters besides hex(Like 0-9 or a-z)?

I also get the error```
Global symbol "$i" requires explicit package name at /bin/perlpasslist1 line 4.
Global symbol "$i" requires explicit package name at /bin/perlpasslist1 line 4.
Global symbol "$i" requires explicit package name at /bin/perlpasslist1 line 4.
Global symbol "$i" requires explicit package name at /bin/perlpasslist1 line 5.
Execution of /bin/perlpasslist1 aborted due to compilation errors.

```

---

### Post by diesch on 2009-10-12
Shorter Perl:

```
foreach(0..0xFFFFFF){printf("%06X\n",$_)};
```

---

### Post by eightmillion on 2009-10-12
Ruby:
```
ruby -e '(0..0xffffff).each{|x|puts "%06x"%x}'
```
Python:
```
python -c 'for i in range(0,0xffffff):print "%06x"%i'
```

---

### Post by Can+~ on 2009-10-12
C
[PHP]#include <stdio.h>

int main(int argc, char **argv)
{
	int i=0;
	
	for(; i < 0xFFFFFF; i++) printf("0x%x\n", i);
	
	return 0;
}[/PHP]

---

