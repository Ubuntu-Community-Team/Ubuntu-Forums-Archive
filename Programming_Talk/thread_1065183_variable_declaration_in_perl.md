---
title: "variable declaration in perl"
date: 2009-02-09
forum: Programming Talk
---

### Post by qmqmqm on 2009-02-09
Hi

If I have a perl program like this:

```
my $count = 0;

sub mySubroutine
{
    $count = 0;
    ... ...
}

... ...
```

Will the 2 variables interfere with each other?

Thanks,

Tom

---

### Post by johnl on 2009-02-09
Check out [this link](http://www.perlmonks.org/?node_id=66677) about scoping in perl.

Hope this helps.

---

