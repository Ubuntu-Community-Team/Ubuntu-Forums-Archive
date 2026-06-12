---
title: "subversion, pre-commit hook to block client v &lt; 1.5?"
date: 2008-12-02
forum: Programming Talk
---

### Post by arcanus on 2008-12-02
As the topic suggests, is there a way to write a pre-commit hook (or by using a configuration option for that matter) to reject svn clients older than 1.5? I.e. clients older than 1.5 won't be allowed to commit data at all. That way we can ensure that the svn merge functionallity in subversion 1.5 is working properly. (I assume that using 1.4 clients will break that function(?)).

---

