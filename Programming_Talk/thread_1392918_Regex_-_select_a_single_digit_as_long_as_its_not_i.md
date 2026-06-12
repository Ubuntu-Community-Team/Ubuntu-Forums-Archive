---
title: "Regex - select a single digit as long as its not in a pair"
date: 2010-01-28
forum: Programming Talk
---

### Post by pmorton on 2010-01-28
I'm scratching my head over this, with my meagre regex skills. Can anyone help?

Embedded somewhere in a line of text is either a single digit, or a pair of digits. I want to match only the single digit. I'm probably over-complicating it when I say that I could do it with a lookforward and a lookbehind to negate a digit in either location, and I don't even think you can do both in one expression (can you?)

Please, some regex wizard, put me out of my misery with the trivial solution I'm missing!

Thanks

---

### Post by myrtle1908 on 2010-01-28
You could use word boundary for that eg.

```

use strict;
use warnings;

my @s;
while (<DATA>) {
  @s = ($_ =~ /\b\d\b/g);
}
print join(':', @s);

__DATA__
3 4 hello 55 6 7 999999 there
```

Yields ...

```
3:4:6:7
```

---

### Post by pmorton on 2010-01-29
> **myrtle1908 said:**
> You could use word boundary for that eg.

```

use strict;
use warnings;

my @s;
while (<DATA>) {
  @s = ($_ =~ /\b\d\b/g);
}
print join(':', @s);

__DATA__
3 4 hello 55 6 7 999999 there
```

Yields ...

```
3:4:6:7
```


Thanks for that. It's a little more complicated though. How would it match the 3's in the following:

__DATA__
7 4 h3ll0 55 6 7 999999 th3r3[/CODE]

---

### Post by cdiem on 2010-01-29
I have been trying to learn python in the last 2-3 days; except for the problems in the 'Project Euler' website, I thought this would be an interesting challenge to solve with the language. You could try with the following:

[PHP]
import re

DATA = "7 4 h3ll0 55 6 7 999999 th3r3[/CODE]"
print(re.findall(r"(?<![0-9])\d(?![0-9])", DATA))
[/PHP]

On my machine:
[PHP]
python test.py
['7', '4', '3', '0', '6', '7', '3', '3']
[/PHP]

The groups starting with "?<!" and "?!" are negative searches (as described here: [http://docs.python.org/library/re.html](http://docs.python.org/library/re.html)).

---

### Post by myrtle1908 on 2010-01-29
```
use strict;
use warnings;

my $s = '7 4 h3ll0 55 6 7 999999 th3r3';
my @ss = ($s =~ m/(?<!\d)\d(?!\d)/g);
print join ':', @ss;
```

```
7:4:3:0:6:7:3:3
```

Is that what you want?

---

### Post by pmorton on 2010-01-29
Yes, each is precisely what I want. Many thanks, both of you.

---

