---
title: "IPTables/Xtables/New Netfilter"
date: 2010-08-06
forum: Programming Talk
---

### Post by babzog on 2010-08-06
We have existing iptables (works on 2.6.20) code such as:
```

static int __init init(void)
{
    int ret;

    /* Register table */
    ret = ipt_register_table(&packet_manipulator, &initial_table.repl);

```

When compiled on Ubuntu LL, it complains that:

expected &#8216;struct net *&#8217; but argument is of type &#8216;struct xt_table *&#8217;

Looks like ipt_register_table was updated from two to three parameters at some point along the way.

Question... We obviously didn't need a 'struct net*' parameter before, so what do I need to pass in now?

---

### Post by babzog on 2010-08-09
Any ideas?

---

