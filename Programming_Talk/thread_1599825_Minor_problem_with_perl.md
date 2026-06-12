---
title: "Minor problem with perl"
date: 2010-10-18
forum: Programming Talk
---

### Post by nebu on 2010-10-18
Hi,
I have an hash in perl of the form
```

%hash = {
  val1 => ["string",1],
  val2 => ["string",10],
  val3 => ["string",100],
  val4 => ["string",1000],
  val5 => ["string",10000],
  val6 => ["string",100000],
};

```

How do I change the integral values to zero in each line using a map statement.
Right now I am naively looping through the keys of the hash.
I guess there must be a smaller way to do this.

Thx for the help!!:P

---

### Post by shawnhcorey on 2010-10-18
Do you mean this:
```
%hash = (
  val1 => ["string",1],
  val2 => ["string",10],
  val3 => ["string",100],
  val4 => ["string",1000],
  val5 => ["string",10000],
  val6 => ["string",100000],
);
```

Or this?
```
$hash = {
  val1 => ["string",1],
  val2 => ["string",10],
  val3 => ["string",100],
  val4 => ["string",1000],
  val5 => ["string",10000],
  val6 => ["string",100000],
};
```

---

### Post by nebu on 2010-10-18
the one with %

---

### Post by gmargo on 2010-10-18
"map" returns a list that will go unused, so it's not the right tool here. "foreach" can do it in a one-liner:
```

$hash{$_}->[1] = 0 foreach keys %hash;

```Here's another way, just using the values since they are references:
```

$_->[1] = 0 foreach values %hash;

```

---

