---
title: "CUPS pdf printer - change output file name"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by corkscrew on 2008-05-18
I'm sure there's an easy answer to this but i cant find it, i'm another guy trying to migrate from windows. In windows when i wanted to print somthing to pdf i would either use acrobat or cute pdf (ghostscript writer) to print to pdf in both cases you will get a box with option to change the name and the location to save the file. Is there anyway to do this in ubuntu? I can print to pdf using cups ok but it by default it goes in my pdf folder with no option to change that that i can see?

---

### Post by HotShotDJ on 2008-05-18
> **corkscrew said:**
> in both cases you will get a box with option to change the name and the location to save the file. Is there anyway to do this in ubuntu?If you use the export to PDF option in OpenOffice, you'll be able to do that.  However, I've found no way to specify a path and filename using the CUPS driver.  After the file is created, you can change the name and move it like you would any other file.  I've just learned to live with it (and lets face it, the things people just learn to live with in Windows are considerably more, shall we say, inconvenient).

---

### Post by noynac on 2008-05-18
> **corkscrew said:**
> I'm sure there's an easy answer to this but i cant find it, i'm another guy trying to migrate from windows. In windows when i wanted to print somthing to pdf i would either use acrobat or cute pdf (ghostscript writer) to print to pdf in both cases you will get a box with option to change the name and the location to save the file. Is there anyway to do this in ubuntu? I can print to pdf using cups ok but it by default it goes in my pdf folder with no option to change that that i can see?

There is no easy way to do this. You can have cups-pdf give the file a job ID so that one PDF does not overwrite another. And, from within Firefox, you can use the print to file option in which case you can give the PDF a file name.

---

### Post by corkscrew on 2008-05-19
yes i know what you mean about learning to live with stuff in windows!!
so this minor in comparison, just thought i'd ask though

---

### Post by HotShotDJ on 2008-05-19
> **corkscrew said:**
> yes i know what you mean about learning to live with stuff in windows!!
so this minor in comparison, just thought i'd ask thoughYes indeed. :)  And, of course it never hurts to ask.  Who knows, maybe somebody may have a solution!

---

### Post by SupraGuy on 2009-08-05
In the file /etc/cups-pdf.conf there is a key for PostProcessing which is supposed to specify a script which can be run after the PDF is created.  I'm trying to use this myself, since what I want to do is set up an automated archiving system.

I want to use the PDF printer from remote systems, and when the PDF is created, I want it renamed, emailed and then removed from disk.

The script named in the PostProcessing key is supposed to be called with the PDF filename as the first argument, but I'm having difficulty getting it to work.  (Runing Jaunty Jackelope)

I've simplified my test script to the following:

```
#!/bin/bash
logfile=/tmp/logfile.$$
echo /usr/local/bin/foo called at `date` >> ${logfile}
echo Arguments=$* >> ${logfile}
chmod a+rw ${logfile}
```

When run from the command line:
```
$ foo this and that
```

I get a file in /tmp with the contents:

```
/usr/local/bin/foo called at Wed Aug 5 09:45:27 MDT 2009
Arguments=this and that
```

However, at present, when I print to the PDF printer, I see no evidence that this script has run.

Other people seem to be having this work for them, so I'm not sure what I'm doing wrong, as yet.

Edit:

Okay, now it works, after running the command line:

```
$ sudo aa-complain cupsd
```

---

### Post by SaintDanBert on 2010-01-28
Do you REALLY want to launch a script with every print request?
You might use the script to create a "work order" but it might be better to separate that from doing the work.

Why not have a daemon of some sort?
Use a daemon process to watch for new files or to read and chew on the list of "work orders". Daemon config explains what to do with what it finds in the target folder.
** rename
** rename and email
** rename and move
** rename and copy
** keep name and email
** keep name and move
** keep name and copy
** slice and dice some how
... and so on

Cheers,
~~~ 0;-Dan

---

### Post by SupraGuy on 2010-01-31
Actually, yes, I really do want to run a script for these print jobs. Even in heavy usage (And the cups-pdf printer shouldn't really be that heavy usage) starting a script is less overhead than a daemon process.
 
Seriously, how many times in a day would the cups-pdf printer get used? Maybe if you're converting a large number of documents (non Open-Office) to PDF format, but will you be doing that EVERY DAY? I think not.
 
Cups already runs scripts for the printer type for each and every print job, with some being simpler than others. (Use a PCL language printer, and it calls a script to change the native PostScript to PCL. Send it raw text, and it'll convert that to PostScript first. The cups-pdf printer uses scripts to convert PostScript to PDFs, even. Adding another script on the end of that train is minimal overhead, and is simple to add in. In fact the conf file is already a script, so it simply forks an instance of bash to run this.
 
If you're concerned about the efficiency of code execution, then break out gcc and write your "script" using that.

---

### Post by Morbius1 on 2010-01-31
Sorry for the interruption but if the original issue is still a problem the answer is:

Do not use **Print_To_PDF**

Use **Print to File**

Choose Output Format: PDF

It allows you to change the name of the pdf and the save location.

As a long time Windows user you probably avoided the Print to File because in windows it sent the file to binary heaven ( at least it appeared to disappear anyway ) ;)

---

### Post by tlcstat on 2010-03-03
Greetings,
Yep, the "print to file" has everything needed. Being new to Linux I didn't think to try that option. It never did much in Windows. Say! do you know what file I would need to edit to change the defaults of that "print to file" option? I would like to change the defaults to PDF instead of PS and also the save directory.
Thanks in advance.
tlcstat

---

### Post by airtonix on 2010-05-30
> **Morbius1 said:**
> Sorry for the interruption but if the original issue is still a problem the answer is:

Do not use **Print_To_PDF**

Use **Print to File**

Choose Output Format: PDF

It allows you to change the name of the pdf and the save location.

As a long time Windows user you probably avoided the Print to File because in windows it sent the file to binary heaven ( at least it appeared to disappear anyway ) ;)

Ah so begins a new hunt on how to provide a default filename in that text field : 

by default it's called : output.pdf
i'd like to have the word output replaced by the title of the page i'm printing instead.

Surely there is a config file we can change to provide a template string?

---

### Post by nardo on 2010-12-07
Somebody found an anwser to this?
I would like to send a bunch of files to cups pdf printer, and cups print them with each name .pdf 
like:
[B]File1.doc
File2.doc
File3.doc
[/B]
and get 
[B]
PDF/File1.pdf
PDF/File2.pdf
PDF/File3.pdf
[/B]

I would really apreciated any clue to solve this.

thanks

LEO

> **airtonix said:**
> Ah so begins a new hunt on how to provide a default filename in that text field : 

by default it's called : output.pdf
i'd like to have the word output replaced by the title of the page i'm printing instead.

Surely there is a config file we can change to provide a template string?

---

### Post by roymilner2001 on 2011-03-14
I would like to find out about this as well. I very seldom need a postscript file, but always need a pdf file. It would also be nice to be able to direct it to the desktop automatically instead of having to change it every time.

---

### Post by therimalaya on 2011-06-24
> **Morbius1 said:**
> Sorry for the interruption but if the original issue is still a problem the answer is:

Do not use **Print_To_PDF**

Use **Print to File**

Choose Output Format: PDF

It allows you to change the name of the pdf and the save location.

As a long time Windows user you probably avoided the Print to File because in windows it sent the file to binary heaven ( at least it appeared to disappear anyway ) ;)

Ya, Morbius is right, it is very better to use Print to File instead, but there is one problem, When you try to print something repeatedly in same format (i.e. layout, orientation, margin and more..) each time you have to set it. I cannot find anywhere to set the default setting for Print to File function of Ubuntu. If any one knows please reply ... thank you

---

### Post by jtarin on 2011-06-24
[Here to #13]("http://wiki.sabayonlinux.org/index.php?title=HOWTO:_Installing_CUPS_Print_to_PDF_driver")

---

