---
title: "regex/apache experts please help"
date: 2009-01-18
forum: Programming Talk
---

### Post by belfasttim on 2009-01-18
Hi all-- 

I have done some messing with htaccess files and url rewriting-- but this one is beyond me at this point.

I'd like to take a subdomain request (like sports.mysite.com) and using htaccess, rewrite that to mysite.com/page.php?id=sports (or something similar).

I know that basic task is no problem with apache. My questions are:

1) Does each subdomain have to have an entry in DNS? Or will any subdomain request go to the mysite.com domain by default where it can be handled via htaccess?

2) Is it possible, after doing this rewrite, to still show the user the sports.mysite.com domain, rather than mysite.com/page.php?id=sports?

If this can be done without modifying DNS, any tips on the actual rewrite conditions/rules hugely appreciated.

Thanks

---

