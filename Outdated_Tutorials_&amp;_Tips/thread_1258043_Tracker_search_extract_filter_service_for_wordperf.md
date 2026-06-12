---
title: "Tracker search extract filter service for wordperfect"
date: 2009-09-04
forum: Outdated Tutorials &amp; Tips
---

### Post by lizardsigh on 2009-09-04
Here are the steps I took to get default install of Jaunty's tracker index search tool/daemon to handle the extraction and indexing of the contents of various versions of old wordperfect files.  Wordperfect files usually have the *.wpd extension.  I have hundreds of wordperfect files where the secretary had used her own filenaming convention; she changed the DOS filename extension from the default wp* to whatever type document she was typing.  My collection thus has *.ltr files etc.  

I could not easily discover from the documentation how new filters were added, but I figured out eventually and here's what you do:


[LIST=1]
[*]Install libwpd-tools
[*]Edit /usr/share/tracker/services/default.service
This is the file that needs to know the mime type of wordperfect files.
Go down to the [Documents] section and add "[FONT=Courier New]**application/vnd.wordperfect;**"[/FONT] to the end of the line. Shown below:

```
[Documents]
DisplayName=Documents
Description=Office and PDF based files
PropertyPrefix=Doc
Parent=Files
UIVisible=true
Icon=x-office-document
KeyMetadata1=Doc:Title
KeyMetadata2=Doc:Author
KeyMetadata3=Doc:Created
TabularMetadata=File:Name;File:Mime;Doc:Title;Doc:Author;File:Size;File:Modified;Doc:Created;
TileMetadata=Doc:Title;Doc:Subject;Doc:Author;Doc:Created;DocageCount;File:Size;
ContentMetadata=File:Contents
Mimes=application/rtf;text/richtext;application/msword;application/pdf;application/postscript;application/x-dvi;application/vnd.ms-excel;vnd.ms-powerpoint;application/x-abiword;text/html;text/sgml;text/x-tex;application/x-mswrite;application/x-applix-word;application/docbook+xml;application/x-kword;application/x-kword-crypt;application/x-lyx;application/vnd.lotus-1-2-3;application/x-applix-spreadsheet;application/x-gnumeric;application/x-kspread;application/x-kspread-crypt;application/x-quattropro;application/x-sc;application/x-siag;application/x-magicpoint;application/x-kpresenter;application/illustrator;application/vnd.corel-draw;application/vnd.stardivision.draw;application/vnd.oasis.opendocument.graphics;application/x-dia-diagram;application/x-karbon;application/x-killustrator;application/x-kivio;application/x-kontour;application/x-wpg;application/vnd.wordperfect;
MimePrefixes=application/vnd.oasis.opendocument;application/vnd.sun.xml;application/vnd.stardivision;
ShowServiceFiles=true
ShowServiceDirectories=true
HasMetadata=true
HasFullText=true
HasThumbs=true
```
[*][FONT=Courier New]**"application/vnd.wordperfect" **[/FONT]is the mime type.  Now you create a filter so that Tracker can extract the contents and index it.  The easiest way is to simply start with a copy of an existing filter and modify it.  cd to the following directory:
/usr/lib/tracker/filters/application/
[*]copy the pdf_filter like so:
[FONT=Courier New]"cp pdf_filter vnd.worperfect_filter"

[/FONT]
[*]Now edit [FONT=Courier New]vnd.worperfect_filter,[/FONT] delete the line that was in pdf_filter ("nice -n19 pdftotext -enc UTF-8 -q -nopgbrk  "$1" -")   and the script should simply be the following:

```
#!/bin/sh
nice -n19 wpd2text "$1" -
```[B][FONT=Courier New]

[/FONT][/B]
[*]Now you have to completely re-index everything.  Simply choosing re-index from the Tracker applet won't be enough.  You must delete the existing index database.  From your home directory: "[FONT=Courier New]rm .local/share/tracker/data/common.db[/FONT]"
[*]NOW, right-click on the Tracker magnifying glass applet and after you make sure to add the directories where your wordperfect files are, then choose to re-index.  After it's done, you should be able to search contents of all your wordperfect files.
[/LIST]

---

### Post by kowy on 2011-01-07
Thank you. It helps me much. 

It's a pity this very useful hint is missing in Tracker documentation wiki.

---

### Post by forliberty on 2011-02-21
Thank you, lizardsigh; this is a life-saver!! I had been trying to get recoll to index WordPerfect files, but even with compiling the libwpd helper app from source, could not get it to work. 

I would add a very simple correction to your HOWTO: you said to add the following line to vnd.worperfect_filter:

nice -n19 wpd2text "$1" -

But the hyphen at the end of the line must be deleted, or it won't work. In other words, the line should be:

nice -n19 wpd2text "$1"

---

### Post by medoc92 on 2011-03-12
[QUOTE=forliberty;10482046]Thank you, lizardsigh; this is a life-saver!! I had been trying to get recoll to index WordPerfect files, but even with compiling the libwpd helper app from source, could not get it to work. 
/QUOTE]

Just for the record and the benefit of future search engine travellers, on Ubuntu, you need to install the libwpd-tools to get the wpd2html command (used by Recoll to extract text from wordperfect files). This works for me with recoll 1.15.5 on Lucid.

---

### Post by forliberty on 2011-03-12
I'm glad recoll works for you, medoc92, but even with libwpd-tools installed from the libraries, it would not work for me. That's why I tried compiling the latest version of the libwpd helper app from source, to see if maybe it would work then. It did not.

---

