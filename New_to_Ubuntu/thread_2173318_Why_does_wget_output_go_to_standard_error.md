---
title: "Why does wget output go to standard error?"
date: 2013-09-09
forum: New to Ubuntu
---

### Post by hrDGznT on 2013-09-09
I recently discovered that wget's output goes to stderr instead of stdout. I've updated my scripts to take account for this, but it feels like bad design to me *however* I'm so new to Ubuntu I'm sure I must be missing something.

Why was this design choice made?

By reading the man page at [http://www.gnu.org/software/wget/manual/wget.html](http://www.gnu.org/software/wget/manual/wget.html) it appears as though using stderr was a way to let you have document contents go to stdout if you so desired, but it just feels wrong. By design stderr should be used for error text. How many 'std*'s are there? Couldn't you just have an arbitrary number of them when designing your application, using custom file descriptor indexes for each one? So in the case of wget you could have a 'stddocument' which is actually &3 or &4 or whatever minimum unused file descriptor is available.

Any discussion that helps illuminate this for me appreciated.

---

### Post by arubislander on 2013-09-09
AFAIK there are three std*'s stdin, stdout and stderr.

I can only guess that choosing stderr for regular output was done so as not to interferen with the progress output which is directed to stdout I presume.

If you are interested in redirecting the output, you needn't be aware as to where it redirects to normally. Just use the ```
-o *logfile*
``` or ```
-a *logfile*
``` command-line argument as per the documentation link you provided.

---

### Post by IainDouglas on 2013-09-09
If you look at the man page for [stderr]("http://linux.die.net/man/3/stderr") (emphasis mine) it notes

> Under normal circumstances every UNIX program has three streams opened for it when it starts up, one for input, one for output, **and one for printing diagnostic or error messages.**


If you look at the standard output written to the terminal by wget, you can see that is is all diagnostic information 

> wget [http://serverfault.com](http://serverfault.com) >1.out
--2013-09-09 09:36:26--  [http://serverfault.com/](http://serverfault.com/)
Resolving serverfault.com... 198.252.206.16
Connecting to serverfault.com|198.252.206.16|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 51374 (50K) [text/html]
Saving to: “index.html”
100%[======================================================================================>] 51,374       228K/s   in 0.2s

2013-09-09 09:36:27 (228 KB/s) - “index.html” saved [51374/51374]


It appears that wget is using the [standard streams]("http://en.wikipedia.org/wiki/Standard_streams") as intended.

---

