---
title: "Python format reporting module"
date: 2008-07-07
forum: Programming Talk
---

### Post by unutbu on 2008-07-07
Suppose lst is a list of tuples. Each tuple has the same number of elements, and each element is either a number or a string.

Is there an easy way, (such as a module?), which can print lst as a table with a dynamically determined number of characters per column?

For example, if given an appropriate lst, the module function could print

```
+----------+--------+-----------------------------+-----------------------+---------+------------+
| symbolid | symbol | stockname                   | type                  | current | analyzable |
+----------+--------+-----------------------------+-----------------------+---------+------------+
|       27 | MSFT   | Microsoft                   | software              |       1 |          1 | 
|       63 | ANF    | Abercrombie & Fitch         | clothing              |       1 |          1 | 
|      163 | MCHP   | Microchip Technology        | semiconductors        |       1 |          1 | 
|      306 | NOIZ   | Micronetics                 | electronic components |       1 |          1 | 
|     1121 | AMD    | Advanced Micro Devices Inc. | semiconductors        |       1 |          1 | 
+----------+--------+-----------------------------+-----------------------+---------+------------+

```
or

```
+----------+--------+----------------------+--------------+---------+------------+
| symbolid | symbol | stockname            | type         | current | analyzable |
+----------+--------+----------------------+--------------+---------+------------+
|        2 | GE     | General Electric     | conglomerate |       1 |          1 | 
|       15 | MMM    | 3M                   | conglomerate |       1 |          1 | 
|       43 | BRK-A  | Berkshire Hathaway A | conglomerate |       1 |          1 | 
|       58 | LTR    | Loews                | conglomerate |       1 |          1 | 
|       93 | DHR    | Danaher              | conglomerate |       1 |          1 | 
+----------+--------+----------------------+--------------+---------+------------+

```
without me having to calculate the width of each column?

---

### Post by nanotube on 2008-07-07
well, i don't know of something like that off hand, but it should be easy enough to calc the appropriate width of each column, and then use print with printf-style formatting to generate the output.

---

### Post by unutbu on 2008-07-07
I'm just learning python. Is this how you would implement the function? It looks atrocious to me, but I don't know what to do to make it better.

File: test.py
```
#!/usr/bin/python
def report_table(alist,corner='+',hdivider='-',vdivider='|'):
    num_col=len(alist[0])
    max_len=[]
    for atuple in alist:
        idx=0
        for aitem in atuple:
            try:
                max_len[idx]
            except:
                max_len.append(0)
            alen=len("%s" % aitem)
            if max_len[idx]<alen:
                max_len[idx]=alen
            idx+=1
    hline=corner+corner.join([hdivider.center(max_len[idx]+2,hdivider) for idx in range(0,num_col)])+corner+"\n"
    result=hline
    first_tuple=alist[0]
    result+=("%s "%vdivider)+(" %s "%vdivider).join([("%s"%first_tuple[idx]).ljust(max_len[idx]) for idx in range(0,num_col)])+(" %s\n"%vdivider)
    result+=hline
    for atuple in alist[1:]:
        result+=("%s "%vdivider)+(" %s "%vdivider).join([("%s"%atuple[idx]).ljust(max_len[idx]) for idx in range(0,num_col)])+(" %s\n"%vdivider)
    result+=hline
    return result

alist=[(1,2,3),
       ('how','nice','to'),
       ('see','you','mommy')]

print report_table(alist)
```

```


% test.py
+-----+------+-------+
| 1   | 2    | 3     |
+-----+------+-------+
| how | nice | to    |
| see | you  | mommy |
+-----+------+-------+

```

---

### Post by WW on 2008-07-07
Cool.

While I don't think brevity is, by itself, an important design goal, I was curious to see if some of your loops could be condensed a bit.  You can replace this
```

    max_len=[]
    for atuple in alist:
        idx=0
        for aitem in atuple:
            try:
                max_len[idx]
            except:
                max_len.append(0)
            alen=len("%s" % aitem)
            if max_len[idx]<alen:
                max_len[idx]=alen
            idx+=1

```
with this
```

    max_len = [max([len(str(x[i])) for x in alist]) for i in range(len(alist[0]))]

```
I suspect there may be an even more compact way to do it that might at the same time be more comprehensible.

---

### Post by nanotube on 2008-07-07
i can't think of a more compact approach than what WW has posted.

if you are looking for a generic solution to working with multidimensional arrays, i might suggest looking at the numpy package for python, or even looking into R instead of python.

---

### Post by unutbu on 2008-07-07
So much to learn, so few brain cells... :lolflag:

Do you know of any good resources to learn R?

---

### Post by ghostdog74 on 2008-07-08
you might also want to take a look at pretty print, string templates, simple string formats like rjust, ljust, etc or even [search Cheeseshop](http://pypi.python.org/pypi?%3Aaction=search&term=Pythonreports&submit=search) for modules like that.

---

### Post by pmasiar on 2008-07-08
> **unutbu said:**
> Do you know of any good resources to learn R?

As always, start at wikipedia: [http://en.wikipedia.org/wiki/R_programming_language](http://en.wikipedia.org/wiki/R_programming_language) and check homepage: [http://www.r-project.org/](http://www.r-project.org/)

You might be interested in RPy - Python bindings for R: [http://rpy.sourceforge.net/](http://rpy.sourceforge.net/)

---

### Post by nanotube on 2008-07-08
> **unutbu said:**
> So much to learn, so few brain cells... :lolflag:

Do you know of any good resources to learn R?

there's a /lot/ of documentation on the R website (r-project.org).
the "manuals" section, particularly the "introduction to R", is a good start: [http://cran.r-project.org/manuals.html](http://cran.r-project.org/manuals.html)

after that, there's a good selection of docs in contributed documentation (choose ones that fit your purpose):
[http://cran.r-project.org/other-docs.html](http://cran.r-project.org/other-docs.html)

and if you run into any problems as you go along, the answers are always a websearch (or a forum post here, or a post to the r-help mailing list) away.

out of curiosity, and so that we may better help you - what is your longer term goal for this? or are you just exploring stuff "for fun" ? :)

---

### Post by unutbu on 2008-07-08
I've written a suite of perl programs whose logic could be streamlined and improved. The perl programs are my attempt at testing the Efficient Market Hypothesis. I can no longer wrap my mind around the logic of the system, even though I wrote it.

So while I am having fun learning python, I have in mind a complete rewrite of the perl programs.
R and numpy both look like they could be useful, though the math I'm using is not very high-powered.

Two pieces of perl that I'll need to replace with python modules are Math::Brent ([http://search.cpan.org/dist/Math-Brent/Brent.pm](http://search.cpan.org/dist/Math-Brent/Brent.pm))
for nonlinear function minimization (for the calculation of rates of return, solving of high-order polynomial equations) and a statistical linear fit package 
([http://search.cpan.org/~randerson/Statistics-LineFit-0.07/lib/Statistics/LineFit.pm](http://search.cpan.org/~randerson/Statistics-LineFit-0.07/lib/Statistics/LineFit.pm))

A python package (or R?) than can do multivariable statistical regression would be of great interest to me too.

---

### Post by nanotube on 2008-07-08
> **unutbu said:**
> I've written a suite of perl programs whose logic could be streamlined and improved. The perl programs are my attempt at testing the Efficient Market Hypothesis. I can no longer wrap my mind around the logic of the system, even though I wrote it.

So while I am having fun learning python, I have in mind a complete rewrite of the perl programs.
R and numpy both look like they could be useful, though the math I'm using is not very high-powered.

Two pieces of perl that I'll need to replace with python modules are Math::Brent ([http://search.cpan.org/dist/Math-Brent/Brent.pm](http://search.cpan.org/dist/Math-Brent/Brent.pm))
for nonlinear function minimization (for the calculation of rates of return, solving of high-order polynomial equations) and a statistical linear fit package 
([http://search.cpan.org/~randerson/Statistics-LineFit-0.07/lib/Statistics/LineFit.pm](http://search.cpan.org/~randerson/Statistics-LineFit-0.07/lib/Statistics/LineFit.pm))

A python package (or R?) than can do multivariable statistical regression would be of great interest to me too.

well, in that case, definitely go with R, because R is built for statistics - it's simply the right tool for the job you have in mind. specifically you might look at function lm() for linear fits and multivariate statistical analysis, and function optimize() for brent's optimization algorithm (both part of the core R install).

---

