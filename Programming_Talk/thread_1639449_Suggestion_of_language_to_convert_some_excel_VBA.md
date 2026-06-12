---
title: "Suggestion of language to convert some excel VBA"
date: 2010-12-06
forum: Programming Talk
---

### Post by HereSomeHow on 2010-12-06
Hi, I'm researching what would be the best path to convert some excel vba macros I've created to run as console apps in a linux environment, 'cause windows is too unstable and I need to depend on them running daily without me having to reset the machine every other day.

I'm relatively fluent in vba, have a little pascal, xbase, and some reminiscence of C. I need to cover 3 aspects:

1. I need to take my input from mysql (from a remote server)
2. I need to generate .xls files as output
3. I need to send those .xls files via smtp

So far, 1 and 3 I think are the easy ones, but the .xls part is the one that is making my hair to fall off. Can somebody suggest what would be the easier option to program with?

Thanks...

---

### Post by oldfred on 2010-12-06
I have been trying to teach myself python and it has libraries for just about anything.

[http://bytes.com/topic/python/answers/717804-writing-blank-excel-file-using-python](http://bytes.com/topic/python/answers/717804-writing-blank-excel-file-using-python)

I have been able to create & display sql queries but I am using SQLite.

[http://stackoverflow.com/questions/2482024/convert-the-mysql-table-details-to-an-excel-xls-or-comma-separated-file-csv](http://stackoverflow.com/questions/2482024/convert-the-mysql-table-details-to-an-excel-xls-or-comma-separated-file-csv)

---

### Post by HereSomeHow on 2010-12-06
> **oldfred said:**
> I have been trying to teach myself python and it has libraries for just about anything.

[http://bytes.com/topic/python/answers/717804-writing-blank-excel-file-using-python](http://bytes.com/topic/python/answers/717804-writing-blank-excel-file-using-python)

I have been able to create & display sql queries but I am using SQLite.

[http://stackoverflow.com/questions/2482024/convert-the-mysql-table-details-to-an-excel-xls-or-comma-separated-file-csv](http://stackoverflow.com/questions/2482024/convert-the-mysql-table-details-to-an-excel-xls-or-comma-separated-file-csv)
Thanks for the reply... I'll search more about python, but the example you referr first seems that is done in windows, and it requires excel installed (it's using COM or something to talk to an instance of excel).

I need a linux environment, and to write "natively" to .xls files, simple writes but native nonetheless.

---

### Post by oldfred on 2010-12-06
Open office supports .xls, so there must be a way.

I did find this:
[http://pypi.python.org/pypi/xlwt/](http://pypi.python.org/pypi/xlwt/)

---

### Post by SaintDanBert on 2010-12-06
> **HereSomeHow said:**
> 
...
I need a linux environment, and to write "natively" to .xls files, simple writes but native nonetheless.

There are several libraries for reading and writing XLS and CSV files from both python and perl. Since you are working in an Ubuntu environment, I'd encourage you to learn and use python to build quick-and-dirty desktop applications and utilities.

Also, I encourage you to learn perl for applications and utilities that are "smarter" than makes sense for a pure shell (bash) script but not "smart enough" to require a full GUI. Perl apps are easy to run from a browser as cgi-code.

Bonne chance,
~~~ 0;-Dan

---

### Post by HereSomeHow on 2010-12-06
I'm sold on python already, I found a library for direct excel reading/writing [http://www.python-excel.org/]("http://www.python-excel.org/")

and also a smtp one [http://docs.python.org/library/smtplib.html]("http://docs.python.org/library/smtplib.html")

and last, MySQL supports python directly, so python it is.

Now, as I'm coming from windows world, I need an IDE with debugging capabilities, I'll make only console apps for the time being, but as python is ident sensitive (so I've read), would you recommend one that covers that and maybe has a windows port?

thx a lot for your time.

---

### Post by oldfred on 2010-12-07
Geany does not have much in the way of debugging like VB did. I just add print statements if I need to track a variable. 

Geany is in the repositories. I like it because with some setup to convert tabs to 4 spaces in a couple of places, and once you save as a .py; you can run the program and it does give you the errors or run. I often copy a small program I find on the net, save and run it to understand what it does. I can do that with a copy, paste, save & click to run.

Supposedly Eclipse is more full featured but it is large and a lot more to learn. 

Others:
Editors:
Too many choices but many are free so you can try them
[http://wiki.python.org/moin/PythonEditors](http://wiki.python.org/moin/PythonEditors)

---

