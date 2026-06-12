---
title: "Add Prefixes to All Files in a Folder"
date: 2012-09-02
forum: New to Ubuntu
---

### Post by linuxn00bface on 2012-09-02
I have a folder with the following files inside,
abc_abc.csv
abc_abc.xls
def_abc.csv
def_abc_abc.csv
def_abc_def.csv

etc.

How can I amend all the files at once so they look like this:
bla_abc_abc.csv
bla_abc_abc.xls
bla_def_abc.csv
bla_def_abc_abc.csv
bla_def_abc_def.csv

Thanks!

---

### Post by jrog on 2012-09-02
Here's how I might do it (don't type the '$' sign -- that's the sign for the prompt). Enter the directory where the files are, and then:

$ for file in * ; do mv "$file" bla_"$file" ; done

Hope that helps!

---

