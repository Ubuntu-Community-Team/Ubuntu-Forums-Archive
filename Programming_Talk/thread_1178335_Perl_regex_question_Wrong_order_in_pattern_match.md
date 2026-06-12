---
title: "Perl regex question: Wrong order in pattern match"
date: 2009-06-04
forum: Programming Talk
---

### Post by Luke has no name on 2009-06-04
$logline = "14:40:23 Oct: Stuff happened: More stuff happened.";

I want to return the message about what happened, and truncate the date. So, I try to use the following pattern:
```

$pattern =~ /(\d\d):(\d\d):(\d\d.+):(.*)/;

if ($logline =~ $pattern)
{
$returnline = $4;
}

```

But that only returns the "More stuff happened" part. I want it to return everything after the third colon, not everything after the LAST colon.

What's the issue?

---

### Post by Luke has no name on 2009-06-04
Fixed. I learned abotu greedy and lazy matching. 

```

/(\d\d):(\d\d):(\d\d.+?):(.*)

```

---

