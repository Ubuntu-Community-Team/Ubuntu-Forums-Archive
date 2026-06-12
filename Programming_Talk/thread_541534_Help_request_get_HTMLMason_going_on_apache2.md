---
title: "Help request: get HTML::Mason going on apache2"
date: 2007-09-02
forum: Programming Talk
---

### Post by davious on 2007-09-02
I'll trying to get HTML::Mason going on apache2.

I've installed the apache2, apache2-mod-perl2, and lib-html-mason packages.

Apache is telling me that it is running mod-perl

I've also added, per [mason's installation notes]("http://www.masonhq.com/docs/manual/Mason.html#installation")

```

    PerlModule HTML::Mason::ApacheHandler

    <Location />
        SetHandler perl-script
        PerlHandler HTML::Mason::ApacheHandler
    </Location>

```

in a conf file.

Something's happening with this, since I start getting 404's when I restart apache.

Any pointer on how I should proceed from here?

---

