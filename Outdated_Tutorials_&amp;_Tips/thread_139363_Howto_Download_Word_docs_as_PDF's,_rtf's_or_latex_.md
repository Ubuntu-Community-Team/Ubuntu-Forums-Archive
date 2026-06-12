---
title: "Howto: Download Word docs as PDF's, rtf's or latex from firefox"
date: 2006-03-03
forum: Outdated Tutorials &amp; Tips
---

### Post by WolfJay_83 on 2006-03-03
All my proffessors post their sylabi and documents online as word documents, I hate downloading them because I have to fire up a word processor just to read a short document.

wvware is a command line package that can convert microsoft word files to PDF, rich text or latex (among others) see: [http://wvware.sourceforge.net/#wv](http://wvware.sourceforge.net/#wv)
You can download it in synaptic - search for wv, you also need tetex-extra.
Alternatively, you can open a terminal and type:
```
sudo apt-get install wv tetex-extra
```
If it doesnt work, you may need to configure extra repositories: [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)


To get firefox to use wvware to download word documents as any of these files, here are the steps....

[SIZE="5"]Create a text file[/SIZE] with the following:
```

#!/bin/bash
wvPDF ${1:5} ${1:5}.pdf
firefox ${1:5}.pdf

```
[SIZE="5"]Save the script and make it executable:[/SIZE]
Save it as "Download_PDF" in your home directory or where ever you want.
Open a terminal, (and go to the directory if you had something other than home)
type: chmod +x Download_PDF
that will make it an executable shell script.

[SIZE="5"]Make firefox use it as a program[/SIZE]
When you click to download a text file, firefox will ask if you want to open it with your default word-processor. Click the dropdown and select "other". 
Locate your "Download_PDF" script. - firefox will remember this from now on.
Clicking "ok" will pop up a new file open or save window for a new pdf file.
[SIZE="5"]
The end result:[/SIZE]
when you click to download a word file, if you select "Download_PDF", it will pop up another window allowing you to open or save the pdf file instead of the orrigional word file.

[SIZE="5"]Modifications[/SIZE]
instead of using wvpdf in the script, you can use 
wvhtml -html output - will load right in firefox
wvlatex -latex output
wvrtf   - microsoft rich text format
wvtext   -converts to plain text - may also load in firefox

[SIZE="5"]notes[/SIZE]
If you download a filename "document.doc", this will result in a pdf file called "document.doc.pdf"  This is not a problem, however, astheticaly, someone may want to improve on this.

I am not sure how to edit the list of programs firefox uses by default.  It would be handy to be able to have all of the possible conversions listed on the dropdown of "open with". Any suggestions?

I did this because no firefox extension exists with this functionality. If someone knows of an extension, or would like to make one that does something like this, I'm sure it would be handy. -I dont know anything about programming extensions.

---

### Post by pranavdagrawal on 2010-03-17
Hi,
I tried doing this on my Ubuntu Karmic, but it did not work.
When I try to open it with Download_PDF, it just opens a new window with the address bar showing "http://<filename>.pdf"
And nothing happens, the window says:
"
 **ERROR**

 **The requested URL could not be retrieved**

 
    The following error was encountered while trying to retrieve the URL: [http://wordsample2.doc.pdf/](http://wordsample2.doc.pdf/)


"
I am behind a proxy, so if it needs any settings, please tell me...


Thanks.

[]("http://wordsample2.doc.pdf/")

---

### Post by WolfJay_83 on 2010-03-22
Firefox is probably trying to load the file through the proxy. I'm not sure how to avoid that. I actually haven't used this trick in a few years (that post was from '06).

---

