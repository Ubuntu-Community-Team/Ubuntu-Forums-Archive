---
title: "Right tool and method to strip off html files (python or sed?)"
date: 2007-07-13
forum: Programming Talk
---

### Post by sebast on 2007-07-13
Hi,

I'm in the process of refactoring a lot of HTML documents and I'm
using html tidy to do a part of this
work. (clean up, change to xhtml and remove font and center tags)

Now, Tidy will just do a part of the work I need to
do, I have to remove all the presentational tags and attributes from
the pages (in other words rip off the pages) including the tables that
are used for disposition of content (how to differentiate?).

I thought about doing that with python (for which I'm in process of
learning), but maybe an other tool (like sed?) would be better suited
for this job.

I kind of know generally what I need to do:

1- Find all html files in the folders (sub-folders ...)
2- Do some file I/O and feed Sed or Python or what else with the file.
3- Apply recursively some regular expression on the file to do the
things a want. (delete when it encounters certain tags, certain
attributes)
4- Write the changed file, and go through all the files like that.

But I don't know how to do it for real, the syntax and everything. I
also want to pick-up the tool that's the easiest for this job. I heard
about BeautifulSoup and lxml for Python, but I don't know if those
modules would help.

Any help would be really appreciated.

---

### Post by duff on 2007-07-13
If you go the python route:

Use os.walk to traverse your directory structure.  It's pretty easy to use, run ```
# python -c 'import os; print os.walk.__doc__'
``` from the terminal to get the hang of it.

To parse HTML, you could use the "htmllib" module and subclass the "HTMLParser" object. The object provides methods for most HTML tag.  run ```
# python -c 'import htmllib; print dir(htmllib.HTMLParser)'
``` for a list of the overrideable methods.  From here, you can override the tags you want to keep to print them out .. you could even output them in valid XHTML.  And do nothing for the tags you don't want.

---

