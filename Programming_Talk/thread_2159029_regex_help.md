---
title: "regex help?"
date: 2013-07-01
forum: Programming Talk
---

### Post by conradin on 2013-07-01
There is a webpage with links, loads of them, I want to grep out the links where the first section of the URL is constant Example:
[http://www.library.umaine.edu/auth/auth.asp?db=](http://www.library.umaine.edu/auth/auth.asp?db=)
Then there is the specific database. Web+Of+Science
then there is the end of the URL, which can be identified as " "> "
how can I grep out things between [http://www.library.umaine.edu/auth/auth.asp?db=](http://www.library.umaine.edu/auth/auth.asp?db=) * "> ?

---

### Post by trent.josephsen on 2013-07-01
If they are all of that fixed format, and there are no linebreaks in the middle of the links, I'd use grep's -o option to put each link on a separate line, then grab the db parameter with cut:

```
$ egrep -o 'http://www\.library\.umaine\.edu/auth/auth\.asp\?db=[^>]+' | cut -c 48-
```

If you need anything more sophisticated than that (e.g. the links are split across lines or you need to avoid URLs that are not part of an <a> tag), you would do well to look into sed, awk or Perl. I always use Perl for stuff like this because I learned it first and as a result never bothered with the others, but that is not a recommendation.

---

