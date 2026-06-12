---
title: "command line utility to convert csv to json"
date: 2015-05-09
forum: Programming Talk
---

### Post by IAMTubby on 2015-05-09
Is there a simple command-line utility that I can use as a one-liner to convert my csv files to json?

I haven't been able to find any.

---

### Post by Vaphell on 2015-05-09
yes, it's called a script after you write one ;-)

it should be relatively trivial in python using csv and json modules.
Provide an example.

---

### Post by tgalati4 on 2015-05-09
*xml2* will take the csv and flatten it.  That might make it easier to convert to json.

---

### Post by Vaphell on 2015-05-09
reading csv is not a problem it's 2 lines in python

that said, there are some nasty caveats.
Are rows supposed to be just thrown in as list elements or indexed by some column, ie
[ { stuff on row1}, { stuff on row2, ... }, ... ] as opposed to { id1: { ... }, id2:  { ... } } ?
Ok, that's rather easy if you decide one way or another.

But which dialect? "CSV" is so ambiguous it's painful. Is header expected or not? What about distinctions between text and numeric stuff? In theory you can demand quotes on text in LibreOffice, but then when i exported a sample file, my python prog tripped up on an unquoted date column because unquoted = non-text = number, right? Alternative is to just ignore that and read everything as text, regardless of what source is trying to say.

Disambiguation would be nice.

---

