---
title: "Heavier-duty &quot;spreadsheet&quot;?"
date: 2007-12-10
forum: Programming Talk
---

### Post by CptPicard on 2007-12-10
I was wondering something... is there something like the old-fashioned spreadsheets we used to have before the GUI era (think Lotus 1-2-3), that would have been implemented using the modern oomph of what we have under the hood these days?

See, my client is an Excel wizard, but Excel manages to choke on the datasets he has to process -- typically something like 10 million vectors of length 6-10 and associated values that he needs to filter, sort, mess around with a bit... this is the reason why he brought me into the picture.

Now he has been migrated from Excel to all sorts of command-line tools by yours truly which are actually not all that bad, but still somewhat unsatisfactory in their rigidity. He's not a bash guru, although has managed to understand pipes and  redirection to files once I managed to demonstrate to him the benefits.

He really needs to be able to visualize (that is, see the numbers and scroll around them, find extrema...) and experiment a little -- running some algorithms with different parameters and see what comes out. Command-line tools with text files work, but are work-intensive. So something like a spreadsheet without all the extra baggage Excel/Calc come with, and with powerful facilities for extension by C and/or scripting by me would be just about perfect... he needs a sort of "workbench" if you catch my drift.

I'm not really sure if scientific packages would be too complex for him to make use of... have been looking at Octave, but am not quite sure of it yet.

Any ideas?

EDIT: Well, googling found me **sc** which just might be workable if it supports external functions...

---

### Post by meatpan on 2007-12-10
Apparently the latest version of excel can handle quite a few rows of data (beyond the old ~65k cap).  Regardless, it probably can't meet your 10 million record requirement.

I think you are going down the right path by checking out octave.   Another option is matlab, if you don't mind the license fee.  Also, R is a decent open-source statistical and visual toolkit.

I'm not totally sure of your situation, so this suggestion might be way off.  Consider providing a simple set of wrapper scripts (or even a web service) that perform  the bulk of your clients operations.  I work in a biology lab, which routinely processes data sets of 5-20 million records, and this solution has had some success.   It might be that your client is running the same command chains, and you could provide a few scripts or programs to greatly simplify the workflow.

---

### Post by pmasiar on 2007-12-10
I would recommend custom solution based on R, RPy, Python, numpy: all easy to use and quite powerfull. Of course it is not as intuitive as Excel, but close.

---

### Post by insane_alien on 2007-12-10
have you tried it in open office? i think it can handle bigger sheets.

---

### Post by hod139 on 2007-12-10
There's always [gnumeric]("http://www.gnome.org/projects/gnumeric/")

---

### Post by wolfbone on 2007-12-10
Yes. R is the obvious "heavier duty spreadsheet": it is data and stats oriented rather than scientific computing/modelling oriented like octave and scilab, and there's lots of cool stuff in CRAN you can use - including GUIs and stuff to build GUIs. I doubt you'd need any help from C or Python or whatever.

---

### Post by pmasiar on 2007-12-10
Python and RPy is for flexible parsing of files before you feed the data to R.

---

### Post by CptPicard on 2007-12-10
Thanks guys, I'll move my investigations to R... octave indeed seems too interested in solving numeric problems, while I mostly run pretty intensive combinatorial searches in the data, finding combinations that produce best values for acceptable subsets under certain conditions etc.. that kind of stuff. This is why the user needs to be able to mess around comfortably with parameters so that his seat-of-pants experience can be integrated into the end product that comes out of the pipeline :)

---

### Post by aks44 on 2007-12-10
I may be totally off the tracks with this one, but if command-line utilities can achieve what he needs, can't SQL do at least the same job?

---

### Post by pmasiar on 2007-12-10
SQL might be much slower, R keeps data in RAM (assuming they will fit - but RAM is cheap).
Workaround might be a database in RAM (keeping tables in RAM, not on disk), but R has many interesting functions missing in SQL.

---

### Post by CptPicard on 2007-12-10
> **aks44 said:**
> I may be totally off the tracks with this one, but if command-line utilities can achieve what he needs, can't SQL do at least the same job?

A worthy suggestion, but... consider that one of my tasks is, for example, going through a set of vectors of length 13 where each item is of the set {1,X,2}. So that would be in SQL terms 12 cross joins producing 3^13 lines to filter, plus in order for me to compute some goodness values I need to find vectors that are off by one... and those that are off by one... and for those that are off by one.

This stuff explodes in your face so fast you simply can't do it in a database. And this bit is relatively easy still ;) Besides, some algorithms simply are not expressible in SQL.

To the result is applied some parametrized filtering and sorting which are relatively straightforward once you've got the values (dataset is still bigger than Excel can deal with, at least in current incarnations we've tried -- I'll look into newer versions' limits). It is actually this filtering, sorting and copypaste-operations that would be cool to be more comfortable than mucking about with text files in shell. This part *could* be stuffed into database, I suppose... but teaching my client SQL is no go as he isn't doing SQL against our customer database either -- I've tried teaching some simple selects. :)

Fortunately pretty widgets are not the point here, he's a smart guy, just not wanting to spend his time "writing code" to analyse which SQL would pretty much be like... so I think I'll look into R and see if I could provide him with some interesting primitives there to use...

---

### Post by aks44 on 2007-12-10
> **CptPicard said:**
> consider that one of my tasks is, for example, going through a set of vectors of length 13 where each item is of the set {1,X,2}. So that would be in SQL terms 12 cross joins producing 3^13 lines to filter, plus in order for me to compute some goodness values I need to find vectors that are off by one... and those that are off by one... and for those that are off by one.

Whoops... I didn't realize the complexity involved. :oops: Indeed SQL seems kinda useless here.

---

### Post by CptPicard on 2007-12-10
Without going into much more detail because of business reasons, a fascinating issue about the example I gave that it appears that it is the first (smallest) instance of this class of problems that I am actually able to brute force completely through in reasonable time with tightly coded C. The problem scales with the length of the vector, and if you make it a 14-length vector, the thing again blows up in your face and is beyond your normal desktop hardware.

It is of course a really *simple* problem in algorithmic terms; you just have to crunch it. But it produces financially useful information, and is an optimization challenge. I actually suspect that if I tried doing this one in R, the mere presence of R as middleman would completely destroy running time until the interface is really lean (read non-existent) to my own native code module. Just consider that I ran an experiment where I got acceptable performance (ran overnight) and had to be really careful with for example how I compute addresses into my memory block where I just sequentially store associated data for each vector while I enumerate everything in a fairly deep recursion... if that memory access goes through some layer that makes it 1000 times slower, it's no use :) At least the only saving grace in this case is that the base dataset is actually just (3^13)*sizeof(datastruct) in size.

We do have less demanding problems too though... for those, R might just do the trick. And of course, one can always crunch the numbers externally and just do the filtering in R.

---

