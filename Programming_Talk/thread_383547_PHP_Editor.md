---
title: "PHP Editor?"
date: 2007-03-13
forum: Programming Talk
---

### Post by atraeyu on 2007-03-13
I'm new to Ubuntu, but not to PHP programming.  On windows, I did most of my php editing in dreamweaver (which was less than ideal).  I'm wondering if there are any great editors out there and what people would recommend?

Thanks!

---

### Post by lnostdal on 2007-03-13
I've heard PHPeclipse recommended.

---

### Post by Mirrorball on 2007-03-13
Eclipse + PDT. PHPeclipse is the old plugin, but PDT is better.

---

### Post by atraeyu on 2007-03-14
Thanks.  I'm installing eclipse now.  I did a package search for "PDT" but I didn't get any hits.  What's PDT?

---

### Post by Mirrorball on 2007-03-14
[http://www.eclipse.org/pdt/](http://www.eclipse.org/pdt/)
Here, it's an Eclipse plugin, it means PHP Development  		Tools.

---

### Post by atraeyu on 2007-03-14
Thanks!  One more question though .... I just tried to run eclipse and got the error "No Java Virtual Machine Installed." .... so I obviously need to install one.  I did a package search in synaptic for "Java Virtual Machine" and found a whole lotta packages - but none that are very obviously the one that I want to install.

So ... any suggestion for which JVM I should install to run Eclipse?  Thanks.

---

### Post by Mirrorball on 2007-03-14
Search for this package: sun-java6-jre

---

### Post by atraeyu on 2007-03-15
> **Mirrorball said:**
> Search for this package: sun-java6-jre

I found sun-java5-jre, but not sun-java6-jre.  I installed 5. :)

---

### Post by atraeyu on 2007-03-15
There are two packages to download:

> Package Types

There are two types of packages used in the PDT project:

    * All in one - includes the complete set of software to start using PDT immediately. This package already has PDT combined with the complete set of prerequisites, eclipse 3.2 sdk, emf, gef, jem and WTP. You will not need anything else
    * Runtime - only includes the PDT project builds. There are the prerequisites to install PDT. The following must be downloaded and installed before the PDT can be installed.
          o Eclipse Platform
          o GEF
          o EMF
          o JEM
          o WTP 


I downloaded the "All in one" package (I assume that was correct ... I do already have eclipse 3.2.1 installed).

There's now a zip file on my desktop - but I'm not sure how to installed the contents of the zip file correctly.  I can't seem to find instructions on the pdt site.  I imagine this is a really, really noob question - so sorry for the inconvenience ...

---

### Post by docetes on 2007-03-15
there is also gphpedit which is just an editor not an IDE but i thought it was pretty good

---

### Post by streeto on 2007-03-15
On windows, I know several people who use editplus. It is a proprietary and paid software, but it [runs fine in wine]("http://editplus.info/wiki/Running_on_Linux"). For someone who switched from MS Windows, it should give a "familiar feeling". Until, of course, you find a free software editor that you like. :)

---

### Post by Mirrorball on 2007-03-15
> **atraeyu said:**
> There's now a zip file on my desktop - but I'm not sure how to installed the contents of the zip file correctly.  I can't seem to find instructions on the pdt site.  I imagine this is a really, really noob question - so sorry for the inconvenience ...
You didn't need to download anything. Open Eclipse, go to Help Software updates and so on, add this link as a New Remote Site: [http://download.eclipse.org/tools/php/updates/](http://download.eclipse.org/tools/php/updates/)
Then select the appropriate checkboxes and Eclipse will download and install the plugin itself. I think PDT is excellent and I highly recommend it.

---

### Post by atraeyu on 2007-03-16
> **Mirrorball said:**
> You didn't need to download anything. Open Eclipse, go to Help Software updates and so on, add this link as a New Remote Site: [http://download.eclipse.org/tools/php/updates/](http://download.eclipse.org/tools/php/updates/)
Then select the appropriate checkboxes and Eclipse will download and install the plugin itself. I think PDT is excellent and I highly recommend it.

Tried this, I'm having problems though.  This gave me an error message that it required the org.eclipse.emf (2.1.0) or later version.  So ... I tried "Software Updates" -> "Find and Install" -> "Search for updates of the currently installed features" -> "Data Tools Platform" ... it goes through several processes then fails on updating "Data Access Designer" with the same error message: "requires feature org.eclipse.emf (2.1.0) or later version" ...

Any ideas?  Thanks!

---

### Post by Mirrorball on 2007-03-16
I forgot that this plugin requires other plugins.  Maybe the All in One package is easier. Just unzip it, it doesn't need to be installed, and click the eclipse executable.

---

### Post by jammodotnet on 2007-03-18
> **docetes said:**
> there is also gphpedit which is just an editor not an IDE but i thought it was pretty goodI used to code all my PHP, xhtmla, and css with pspad (on Windows), but since I came to Ubuntu, it's been tough to find a good editor.
i didnt like bluefish, nvu, nor screem.

gphpedit has been pretty decent actually.
it has a few small features i really appreciate. i am a frequent user of the famous 'Alt + Tab' combinations, both on Windows and Ubuntu. in gphpedit, it does as expected, and moves between tabs (a godsend when i have many files open) ... in the other above mentioned editors, it does not.
that was ONE BIG PLUS FOR ME!!!!

another one: upon opening the editor, it reopens all the last files i had previously opened while working.

and the biggest one, it has what i can only call 'code folding'?
another amazing feature, which i never saw in Editplus nor pspad!


if there are any comparable editors, please let me know!

---

### Post by HeavyEddie on 2007-03-18
Downloaded and installed eclipse without issue.  I'm afraid I don't see how to install or setup PDT.

---

### Post by Mirrorball on 2007-03-18
> **HeavyEddie said:**
> Downloaded and installed eclipse without issue.  I'm afraid I don't see how to install or setup PDT.
The easiest way is to download the all-in-one package from PDT's website, unpack it and click the eclipse executable inside.

---

### Post by garybrlow on 2007-03-18
Try HAPedit for windows. Scribes for Linux, it has PHP support and then some.


Cheers!!!


GaryBrlow :biggrin:

---

