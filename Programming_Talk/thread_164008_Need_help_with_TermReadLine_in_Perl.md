---
title: "Need help with Term::ReadLine in Perl"
date: 2006-04-22
forum: Programming Talk
---

### Post by pianoboy3333 on 2006-04-22
I realized while using a program that I was creating, that in order to scroll back in history, I had to press the up arrow key twice, as oposed to how it should be (once) how can I fix this? Here is a sample program in which I would have to press up twice on my machine:
```

#!/usr/bin/perl

$ENV{PERL_RL}='Gnu o=0';
use Term::ReadLine;
$term = new Term::ReadLine 'Test';
$prompt = "-> ";

while( defined ($_ = $term->readline($prompt)) && $_ ne 'exit') {

$term->addhistory($_);
}

```

---

### Post by pianoboy3333 on 2006-04-22
No one knows how to only have it so that I only have to press up once?

---

