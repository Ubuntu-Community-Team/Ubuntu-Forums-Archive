---
title: "Help finding file that is and isn't there"
date: 2013-06-20
forum: New to Ubuntu
---

### Post by jps2012 on 2013-06-20
I invoked "curl -O "http://occri.net/wp-content/uploads/2011/03/exec_summaryOCAR.pdf" to download a PDF via the command line. Terminal reported that 100 percent of the file (1633k) downloaded. 

I used "ls" to verify that the file downloaded to my home directory, but Krusader and the Home directory do NOT list the file.

I tried opening the PDF (from the home directory) with "evince exec_summaryOCAR.pdf"

I get a "file not found" response. 

Question: Why would it show up if I use "ls" but not show up in a GUI (such as Krusader)? 

Bigger question: Is it really there? And if so, any ideas as to how to get it to show up consistently, AND open?

---

### Post by monkeybrain2012 on 2013-06-20
Don't you have to do something like "curl [http://occri.net/wp-content/uploads/2011/03/exec_summaryOCAR.pdf](http://occri.net/wp-content/uploads/2011/03/exec_summaryOCAR.pdf)  >> saved_document.pdf"  to output to a saved copy?

Why didn't you just go to the url in Firefox to download it instead of making things complicated?

---

### Post by jps2012 on 2013-06-20
Monkeybrain: In order to do the download via curl, you have to enclose the entire URL in quotes. If the argument "-O" is added, the function will track down the latest copy of the document on the server. 

In some cases, their isn't a download button on a site, and I see no options to save it as a PDF.

The question still remains (if anyone knows how to sort out the 'why' of why "ls" lists the file as resident in the home folder, and the GUI doesn't show it at all.

---

### Post by steeldriver on 2013-06-20
Well the most logical explanation is that you weren't in the directory you thought you were at the time - anyhow you can search for where it went using the 'find' command e.g. to search recursively starting from your home dir you could do

```
find ~ -name 'exec_summaryOCAR.pdf'
```

---

