---
title: "mod_rewrite and trailing backslashes?"
date: 2009-08-08
forum: Programming Talk
---

### Post by Bulletbeast on 2009-08-08
I've just learned about the wonders of mod_rewrite. However, I have encountered two problems.

1. Let's say [http://www.example.com/main](http://www.example.com/main) and [http://www.example.com/main/](http://www.example.com/main/) redirect to the same page (namely [http://www.example.com/index.php?mode=main](http://www.example.com/index.php?mode=main)). However, with the first, <a href="page"> links to [http://www.example.com/page](http://www.example.com/page) and with the second, to [http://www.example.com/main/page](http://www.example.com/main/page). How do I make such a link always point to [http://www.example.com/page?](http://www.example.com/page?) Is there a way to do this besides using absolute paths?

2. I'm running xampp 1.7.1, Apache 2.2.11 on Windows. When I have a RewriteRule without [R], it redirects me to the correct page. However, if the rule ends in [R], mod_rewrite includes the absolute path (or what it thinks to be the absolute path) in the URL. To clarify:
```
RewriteRule ^home$ home/
RewriteRule ^home/$ index.php?mode=home

```
results in [http://www.example.com/home](http://www.example.com/home) and [http://www.example.com/home/](http://www.example.com/home/) redirecting to [http://www.example.com/index.php?mode=home](http://www.example.com/index.php?mode=home).

However, 
```
RewriteRule ^home$ home/ [R]
RewriteRule ^home/$ index.php?mode=home

```
makes the former redirect to [http://localhost/H:/xampp/htdocs/example/home/](http://localhost/H:/xampp/htdocs/example/home/) (which doesn't exist).

Quite odd, I dare say. Should I file a bug?

---

