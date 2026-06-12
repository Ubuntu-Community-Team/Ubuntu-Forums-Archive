---
title: "Latest DocBook GUI / Web tools?"
date: 2006-03-03
forum: Programming Talk
---

### Post by jfdill_2 on 2006-03-03
About five years ago, I wrote my thesis in DocBook SGML, but haven't done much with DocBook since then.  I'm trying to find out what is the current state of GUI tools and web engines for DocBook SGML and XML.  I'll follow up here myself as I find out stuff.

Tools that I used in the past:
* LyX
* emacs psgml mode
* jade
* some CD from the TeX Users Group (TUG)

Abiword now sounds promising.

I'm saving some links as I find info in the [DocBook Topic]("http://www.furl.net/members/jfdnerds?enc=UTF-8&search=browse&sort=&dir=&pos=&keyword=&x=25&y=11&category=675101&date=0") of my furl.net archive.
[DocBook Wiki]("http://doc-book.sourceforge.net/homepage/") looks very interesting
[SilkPage]("http://silkpage.markupware.com/") also interesting, but requires Java, and I'm not sure about the licensing
[C-Abre]("http://c-arbre.pacageek.org/espaces/portal.php?carbre_Session=bbf58f6aab352c541343da0c2e3c4b42") looks very cool

---

### Post by toojays on 2006-03-03
It's been a while since I used DocBook, but I found emacs nxml-mode to be much more useful than psgml-mode. That does of course mean that you need to use DocBook XML rather than DocBook SGML.

---

### Post by jfdill_2 on 2006-03-09
I just found this web page on using DocBook in OpenOffice, through import and export filters.  It's a bit out of date for OOo 1.X from 2005-03-25, but may still be relevant.  I'm going to give it a shot with OOo 2.0 and see what happens.

[http://wiki.docbook.org/topic/OpenOffice](http://wiki.docbook.org/topic/OpenOffice)

Link to relevant OOo XSLTs and template [http://xml.openoffice.org/xmerge/docbook/index.html](http://xml.openoffice.org/xmerge/docbook/index.html)

Hmm I'm using Dapper, and it looks like all the relevant XSLTs are already set up in OOo2 so the import filter should work, but when I open a DocBook XML document, it shows as a text file with all of the tags :/

---

### Post by jfdill_2 on 2006-03-28
Quanta seems very nice.  I found this tutorial from the KDE project on using Quanta to edit DocBook documents:

[http://quanta.kdewebdev.org/tutorials/quanta-docbook/quanta.html](http://quanta.kdewebdev.org/tutorials/quanta-docbook/quanta.html)

A couple notes for Ubuntu users:  You will also want kdelibs4-dev (on Dapper, not sure what the pkg is called on Breezy) for the checkXML script and kdelibs-bin for meinproc.  xmllint seems nicer for checking XML than checkXML, but it is nice just having to click the button to run checkXML from Quanta.

I have also been playing with jEdit and SciTE.  SciTE has a habit of crashing nastily on Dapper, but jEdit works just fine.

[http://www.jedit.org](http://www.jedit.org)
[http://www.scintilla.org/SciTE.html](http://www.scintilla.org/SciTE.html)

---

### Post by jfdill_2 on 2006-04-06
I made a Wiki page with lots more information!

[https://wiki.ubuntu.com/DocBookEditors](https://wiki.ubuntu.com/DocBookEditors)

Sincerely,
Chronic Triple Poster

---

### Post by dpm on 2006-04-07
Hi,

since I've been researching a bit about DocBook in the last few weeks, I thought I'd post my 2c on this.

I must say that I've mainly been experimenting with DocBook XML, which seems to be more "modern" than the SGML version.

About editors:

I've tried **conglomerate** and **mlview** as native XML editors under Linux. Both of them seem fine, although quite buggy at this stage. I haven't been able to finish a single document before they would crash. In this case, I prefer to use **emacs** in nxml-mode.

Last week I found this other WYSIWYG DocBook editor called **xxe** Standard Edition (or XMLMind XML Editor, at [http://www.xmlmind.com/xmleditor/)](http://www.xmlmind.com/xmleditor/)). The standard edition is free, although you will need java to get it running (it is a multiplatform editor). It looks really really good to me, and I especially like the WYSIWYG aspect of editing a DocBook document. What I also liked is that it didn't need to be compiled for installation. Simply untar the archive in a folder and run the executable. You might want to have a look into it.

I didn't have a look at commercial editors, but I must try OpenOffice for exporting into DocBook.

Regarding other tools, you will find, amongst others, these packages to be useful (all available from the repos):[LIST]
[*] *docbook* contains the DocBook SGML DTD
[*] *docbook-xml* contains the DocBook XML DTD
[*] *docbook-dssl* contains *.dsl* stylesheets for docbook SGML and XML. For XML it is recommended to use the *docbook-xsl* package, which is more actively maintained and contains *.xsl* stylesheets.
[*] *docbook-xsl* modular XSL stylesheets for processing documents composed with the DocBook XML DTD and its derivatives. The stylesheets provide XSLT transformations for HTML, XHTML, htmlhelp, javahelp, nroff, and Formatting Object output. These are the Norman Walsh.
[*]*docbook-utils* contains utilities for converting docbook files to other formats (docbook2html, docbook2pdf scripts...)[/LIST]I think that's all I can think at the moment.

Cheers.

---

### Post by jfdill_2 on 2006-04-07
[QUOTE=desp]Last week I found this other WYSIWYG DocBook editor called **xxe** Standard Edition (or XMLMind XML Editor, at [http://www.xmlmind.com/xmleditor/)](http://www.xmlmind.com/xmleditor/))[/QUOTE]
Wow, thanks for that reference, that gave me a great idea:  I put it on a USB key along with my XML project, now I can work on it on almost any computer!  I may try some of the other Java editors that way.

---

