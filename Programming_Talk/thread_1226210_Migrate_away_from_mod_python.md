---
title: "Migrate away from mod_python"
date: 2009-07-29
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2009-07-29
Hi Guys

I've got a site that relies on mod_python for http handling, sessions and redirects.

Does anyone have experience or and Ideas of a good route to take when migrating away to something like cherokee or nginx webservers?

Any constructive input is most welcome

Mike

---

### Post by soltanis on 2009-07-29
Well there's mod_perl, but I assume you aren't looking to move from one scripting language to another (why are you migrating, exactly? performance issues?)

---

### Post by Mickeysofine1972 on 2009-07-29
> **soltanis said:**
> Well there's mod_perl, but I assume you aren't looking to move from one scripting language to another (why are you migrating, exactly? performance issues?)

Yes, also I want to run a server with a little small footprint and a faster serving rate.

Mike

---

### Post by soltanis on 2009-07-29
Apache and Lighttpd have the highest sustained serving rates. As far as I know, mod_perl/mod_python are the fastest ways to create dynamic webpages, except for some other (more exotic?) ways.

You could consider looking into FastCGI, but that won't give you a smaller footprint. Perl is a little faster and uses a little less memory than Python, but isn't much of an improvement.

---

### Post by Mickeysofine1972 on 2009-07-29
> **soltanis said:**
> Apache and Lighttpd have the highest sustained serving rates. As far as I know, mod_perl/mod_python are the fastest ways to create dynamic webpages, except for some other (more exotic?) ways.

You could consider looking into FastCGI, but that won't give you a smaller footprint. Perl is a little faster and uses a little less memory than Python, but isn't much of an improvement.

Well I had considered lighttpd was faster than apache but how easily can I get mod_python working with that? or is that not possible?

Mike

---

### Post by soltanis on 2009-07-29
It might have its own version of mod_python; otherwise I know lighttpd uses FastCGI, which should run basically as fast.

---

