---
title: "Perl TreeBuilder"
date: 2009-10-07
forum: Programming Talk
---

### Post by mastermindg on 2009-10-07
I'm running Jaunty, just want to know how to determine which version of TreeBuilder Perl is using?

---

### Post by myrtle1908 on 2009-10-07
```
perl -MHTML::TreeBuilder -e 'print "$HTML::TreeBuilder::VERSION\n"'
```

---

