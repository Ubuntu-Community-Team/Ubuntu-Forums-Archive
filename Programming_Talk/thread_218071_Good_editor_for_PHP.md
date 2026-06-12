---
title: "Good editor for PHP"
date: 2006-07-18
forum: Programming Talk
---

### Post by mssever on 2006-07-18
Since I'm trying to fully abandon Windows, I'm looking for a good editor for web development--particularly PHP. One feature that I'm looking for in particular is PHP function tooltips (or equivalent) that give quick reminders of the perameters the function expects.

In Windows, I used scite (aka Scintilla Text Editor). However, the tooltip ability seems to be missing from the Linux version (strange, since it started as a Linux program).

Screem has the tooltip feature, but it has many other drawbacks: When using word wrap--as I usually do--the tooltips frequently cover up there I'm trying to type, and they can't be closed without moving the cursor out to the function or editing the preferences. Plus, its syntax highlighting mode is horribly broken. I won't take the time to list my other objections to screem. Unfortunately, it's the only editor I've found that has function tooltips.

JEdit looks like it would be a great editor if I could find a plugin to implement function reference tooltips (and to use a tabbed interface--listing open files in a drop-down window is just lame.

I've also tried Bluefish and gPHPedit, and found both to be missing what I consider to be an essential feature.

Does anyone know of an editor that does what I want?

---

### Post by kpolice on 2006-07-18
I use eclipse + phpeclipse plugin, also I have exadel studio for jsp, jsf. Pretty good and I recommend it to anyone.

---

### Post by mssever on 2006-07-18
> **kpolice said:**
> I use eclipse + phpeclipse plugin, also I have exadel studio for jsp, jsf. Pretty good and I recommend it to anyone.

Does it do some sort of instant PHP function paremeter reference? It has so many dependencies that I don't want download it and have to try to remember everything I need to remove in case I don't like the program.

---

### Post by xtine on 2006-07-18
Although more for web design, Quanta is pretty nice for PHP work.

---

### Post by ifokkema on 2006-07-18
> **mssever said:**
> I've also tried Bluefish and gPHPedit, and found both to be missing what I consider to be an essential feature.
gPHPEdit definately has the tooltip function, but it pops up when you WRITE the function (i.e. opening the parenthesis at the right of a known function name). Furthermore, when you select a function and press F1, it opens the PHP manual reference for that function in a new tab (requires manual installation of the PHP manual, though).

---

### Post by kpolice on 2006-07-18
Don't download eclipse from the repositories, download it from eclipse.org, it's faster and easier to install, you just need j2sdk installed.

---

### Post by mssever on 2006-07-18
> **ifokkema said:**
> gPHPEdit definately has the tooltip function, but it pops up when you WRITE the function (i.e. opening the parenthesis at the right of a known function name). Furthermore, when you select a function and press F1, it opens the PHP manual reference for that function in a new tab (requires manual installation of the PHP manual, though).

Thanks. Somehow I missed the tooltip function when I first tried gPHPEdit. Where do you install the PHP manual for F1 to work? I've got the manual installed locally, but gPHPEdit doesn't know about it and I can't find an option to tell it where the manual is.

---

### Post by ifokkema on 2006-07-19
> **mssever said:**
> Thanks. Somehow I missed the tooltip function when I first tried gPHPEdit. Where do you install the PHP manual for F1 to work? I've got the manual installed locally, but gPHPEdit doesn't know about it and I can't find an option to tell it where the manual is.
I had to mess around with that for a while, but I found this works:
```
sudo mkdir /usr/share/doc/phpdoc
sudo ln -s /path/to/the/docs /usr/share/doc/phpdoc/html

```
:)

Edit: Oh yeah, if you run into trouble with the current dapper version of gPHPEdit, you can download an update from [here]("http://www.ifokkema.nl/gphpedit-0.9.91_0.9.91-1_i386.deb").
(See [this thread]("http://www.ubuntuforums.org/showpost.php?p=1236293&postcount=15") for more info.

---

### Post by mssever on 2006-07-19
Thanks a bunch!

---

### Post by egon spengler on 2006-07-20
> **mssever said:**
> Does it do some sort of instant PHP function paremeter reference? It has so many dependencies that I don't want download it and have to try to remember everything I need to remove in case I don't like the program.

I you install programs with aptitude it will remember any dependecies and so when you uninstall a program it will also remove any dependencies that were pulled in with it so long as no other program needs them

---

### Post by simms on 2006-07-29
here's my 2 cents: gPHPedit has crashed every time i've tried to use it (whether on breezy or dapper).  gedit is still far from the perfect solution.  i used to have scite set up, but it's actually pretty slow, and since dapper it doesn't work on my machine anymore.

:KS on the bright side though, **eclipse for PHP** is quite nice.  

on dapper, the easiest way to install this environment is as follows:

- enable the *multiverse* repository, and issue ```
sudo apt-get install j2sdk1.4
```

- once Java is installed, just point your browser to the Eclipse PHP IDE sub-project page at [http://download.eclipse.org/tools/php/downloads/index.php]("http://download.eclipse.org/tools/php/downloads/index.php") and follow the latest 'stable build' link; the .tar.gz package on the next page (~90MB) is an all-in-one Eclipse build with the PHP-specific modules already included

- just decompress the package once it comes down the wire, and save the contents wherever in their own 'eclipse' directory; clicking on the 'eclipse' executable there should be enough to get it started.. :cool:

---

### Post by ifokkema on 2006-07-29
> **simms said:**
> here's my 2 cents: gPHPedit has crashed every time i've tried to use it (whether on breezy or dapper).
Mine has only had this behaviour in Dapper. That's why I added the link in my post to the earlier thread about this, that also offers a download for a more stable .deb file.

---

### Post by andyjeffries on 2006-09-07
ifokkema, I'm going to need to make you a badge/certificate soon for being Number 1 gPHPEdit Evangelist :-)

---

### Post by andyjeffries on 2006-09-07
> **simms said:**
> here's my 2 cents: gPHPedit has crashed every time i've tried to use it (whether on breezy or dapper). 

As ifokkema said, the latest version is defintely stable and fine.  I'm now an Ubuntu user (for about 4 months I guess) so I literally use gPHPEdit on Dapper for about 12 hours per day, it hasn't crashed on me since the last version release :-)

---

### Post by joflow on 2006-09-28
Anyone know of an editor with good support for php5 classes (code completion of methods).  I know about Zend Studio..but I want something free and open source.

---

### Post by Colonel Kilkenny on 2006-09-28
Eclipse + Zend PHP Ide is the best alternative I guess.
[http://www.zend.com/phpide](http://www.zend.com/phpide)

---

### Post by Desi-Tek.com on 2006-09-28
well my favourite is dreamweaver.

---

