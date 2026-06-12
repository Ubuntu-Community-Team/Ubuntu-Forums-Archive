---
title: "perl - can I use a variable name inside a variable name?"
date: 2007-08-23
forum: Programming Talk
---

### Post by jimmymus on 2007-08-23
Here is the relevant code snippet

I have 3 hashes, k_1, k_2, and k_3

for($i = 1; $i < 4; $i++)
{
	while ($x, $y) = each(%k_$i)         # this is the line in question
	{
		print "k$i_x is ", $x, "\n";
		print "k$i_y is ", $y, "\n";
	}
}

This doesn't work. Is there any way that I can do what I'm trying to do? Instead of manually writing out 3 sections of code to do the same thing? Thanks!

---

### Post by pmasiar on 2007-08-23
array of hashes?

---

### Post by jimmymus on 2007-08-23
That would definitely be easier. The documentation I'm reading at the moment didn't lead me to believe that I could do anything but an array of scalars but I suppose that hardly makes sense.

Thanks :)

---

### Post by pmasiar on 2007-08-23
array of scalars, where scalar's value is reference to a hash :-)

---

### Post by slavik on 2007-08-24
> **pmasiar said:**
> array of scalars, where scalar's value is reference to a hash :-)

yeap. :)

as a note, my Perl prof on the test put a question to create "an array of hashes of arrays of hashes of arrays of hashes". nice simple brain teaser for those new to Perl. :)

---

### Post by Mr. C. on 2007-08-24
You can do what you were asking:
```

%k_1 = ( A => 1, B => 2);
%k_2 = ( C => 3, C => 4);
%k_3 = ( E => 5, F => 6);

for($i = 1; $i < 4; $i++) {
    while (($x, $y) = each (%{"k_$i"})) {
        print "k$i_x is ", $x, "\n";
        print "k$i_y is ", $y, "\n";
    }
}
```

But beware, not while 
```

use strict 'refs';
```

is in effect.

See man perlref, and search for Symbolic and symbolic reference.

MrC

---

### Post by pmasiar on 2007-08-25
> **Mr. C. said:**
> 
use strict 'refs'


"use strict;" should be third line (first after shebang :-) ) in any Perl program, if you want to have fighting **chance** to maintain it.

Of course, symbolic references like OP asked and MrC suggested are valid use of non-strict code -- as a mind teaser, not a production code of course :-)

---

### Post by weijie90 on 2007-09-21
> **slavik said:**
> yeap. :)

as a note, my Perl prof on the test put a question to create "an array of hashes of arrays of hashes of arrays of hashes". nice simple brain teaser for those new to Perl. :)

Hah- try using XML::Simple. The data structures it generates are worse: hashes of hashes of hashes with arrays mixed in, depending on how complex and nested your XML input file is.

---

### Post by slavik on 2007-09-22
I built my own xml/html parser (a very simple one) ... and yes, it can get hairy. but that's what XML is ... hash of hashes of hashes ... etc.

---

