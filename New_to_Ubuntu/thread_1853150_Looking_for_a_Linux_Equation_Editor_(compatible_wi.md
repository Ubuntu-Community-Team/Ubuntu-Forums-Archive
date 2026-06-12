---
title: "Looking for a Linux Equation Editor (compatible with powerpoint)?"
date: 2011-10-01
forum: New to Ubuntu
---

### Post by honeybear on 2011-10-01
Hello,

I have to type lot of equations for collegue, and I would like to do it under Linux (without using wine), and then make it available to Word later (Microsoft).

I am looking then a Linux Equation Editor (compatible with powerpoint)? 

I googled but nothing found. I would like a frontend (not latex), that looks like MS equation.

Have you eventually any ideas what I could use?

```
$ apt-cache search equation editor
abiword-plugin-mathview - equation editor plugin for AbiWord
texlive-latex-extra - TeX Live: LaTeX supplementary packages
openoffice.org-math - office productivity suite -- equation editor
openoffice.org - office productivity suite
```
abi-word is too basic
openoffice is very heavy to install. 

I just would like sthg like MS equation editor for linux only, and nothing else... 


Thank you very much !!

---

### Post by angryfirelord on 2011-10-01
Well, you're probably going to have to use something like LaTeX. But as far as I know, the AbiWord plugin is LaTeX-compatible, so that should work. Here's the example I took from Wikipedia:

```
m = \frac{m_0}{\sqrt{1-\frac{v^2}{c^2}}}
```

You can save it as a .doc in Abiword and see if it open in Word.

---

### Post by Isaacgallegos on 2011-10-01
http://www.wolframalpha.com/input/?i=z+%3D+sqrt%28x^2%2By^2%29

?

---

### Post by anewguy on 2011-10-01
I'm not sure, just because I've never tried to do it, but I thought libreoffice math could do that, and you should be able use the resulting docs in presentation.

Dave ;)

---

### Post by dniMretsaM on 2011-10-01
LibreOffice Math should work just fine:
```
sudo apt-get install libreoffice-math
```This installs just the math program, not the whole thing. OpenOffice.org has a math program also (pretty much the same). Use whichever you choose.

Also, I would recommend using LibreOffice Impress to do your presentation instead of PP (free software and open formats).

```
sudo apt-get install libreoffice-impress
```

---

### Post by entropy1 on 2011-10-01
With OpenOffice Impress, I like to add the extension OOoLatex

[http://extensions.services.openoffice.org/en/project/ooolatex]("http://extensions.services.openoffice.org/en/project/ooolatex")

Then you can type LaTeX commands into a dialog box in Impress, and you get the equation latexed and put into the slide.  After installing the extension, you have to tell it where to find latex and ghostscript.  On my system, they were both in /usr/bin.  Also, if you can't find the toolbar with "Equation" "Expand" "Config", go to View --> Toolbars --> Add-On 1 (or other number).  This extension works great on Linux, though I've never been able to use it successfully on Windows.

---

### Post by jacksaff on 2011-10-01
The latex plugins for open/libre office are your best bet. They replace your latex equation wtih a png image so the file should save and open in MS Office  just fine.

If you are going to be doing a lot of equation writing learning latex is a must. Other equation editors seem easier to use at first, but latex is just a lot more powerful. As soon as you need to do anythiing more complicated than adding in one-line equations you'll be glad you made the  effort to learn it.

---

### Post by Abhinav Kumar on 2011-10-02
I think the best way of typing any equation would be to use computer typesetting LATEX.  A good software Kile is available. May be you have to learn some of d basics of LATEX. Enjoy :D

---

### Post by honeybear on 2011-10-02
> **dniMretsaM said:**
> LibreOffice Math should work just fine:
```
sudo apt-get install libreoffice-math
```This installs just the math program, not the whole thing. OpenOffice.org has a math program also (pretty much the same). Use whichever you choose.

Also, I would recommend using LibreOffice Impress to do your presentation instead of PP (free software and open formats).

```
sudo apt-get install libreoffice-impress
```

```
~# apt-get install openoffice.org-math
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libgraphite3 libhyphen0 libmythes-1.2-0 libraptor1 librasqal2 librdf0 libstlport4.6ldbl libtextcat-data-utf8 openoffice.org-common openoffice.org-core
  openoffice.org-style-galaxy ttf-opensymbol uno-libs3 ure xfonts-mathml
Suggested packages:
  raptor-utils rasqal-utils librdf-storage-postgresql librdf-storage-mysql librdf-storage-sqlite redland-utils openoffice.org-style-industrial
  openoffice.org-style-hicontrast openoffice.org-style-tango openoffice.org-style-crystal openoffice.org-style-oxygen cli-uno-bridge otf-stix
The following NEW packages will be installed:
  libgraphite3 libhyphen0 libmythes-1.2-0 libraptor1 librasqal2 librdf0 libstlport4.6ldbl libtextcat-data-utf8 openoffice.org-common openoffice.org-core
  openoffice.org-math openoffice.org-style-galaxy ttf-opensymbol uno-libs3 ure xfonts-mathml
0 upgraded, 16 newly installed, 0 to remove and 11 not upgraded.
Need to get 76.9 MB of archives.
After this operation, 200 MB of additional disk space will be used.
Do you want to continue [Y/n]? 


```

200MB for a simple equation editor ... pfff 

it is kind of exaggerated for a simple app 

ok. I am making testing... I will post first impressions ;)



> **Abhinav Kumar said:**
> I think the best way of typing any equation would be to use computer typesetting LATEX.  A good software Kile is available. May be you have to learn some of d basics of LATEX. Enjoy :D

this is something for geeks.
[http://kile.sourceforge.net/images/screenshots/snap_refinsert.png](http://kile.sourceforge.net/images/screenshots/snap_refinsert.png)

Latex has nothing to do with the regular word. And it is not used in any large companies. World is simpler than that :) 

If you tell for most windows users to use latex instead of word, it would not work. 

Luckily openoffice is there. Opensource and Linux are so cool

---

### Post by Zill on 2011-10-02
> **honeybear said:**
> ...200MB for a simple equation editor ... pfff...
I am slightly puzzled.  OpenOffice, including the math equation editor, is installed by default in Ubuntu 10.04.  Presumably, LibreOffice has the same functionality in later versions of Ubuntu.

So, you are not talking about 200MB for a "simple equation editor", but for a complete office suite!

---

### Post by angryfirelord on 2011-10-02
> **honeybear said:**
> 200MB for a simple equation editor ... pfff 

it is kind of exaggerated for a simple app 

ok. I am making testing... I will post first impressions ;)
Keep in mind that it's pulling in all of the core OpenOffice libraries, so if you were to install writer and calc, it wouldn't add that much to it. I agree with the above, if LaTeX is too much, use OpenOffice/LibreOffice.
> Latex has nothing to do with the regular word. And it is not used in any large companies. World is simpler than that

If you tell for most windows users to use latex instead of word, it would not work.

Luckily openoffice is there. Opensource and Linux are so cool 
Well, there are probably easier tools to use, but they probably aren't going to be free and they're not going to run on Linux.

---

### Post by dniMretsaM on 2011-10-02
> **Zill said:**
> I am slightly puzzled.  OpenOffice, including the math equation editor, is installed by default in Ubuntu 10.04.  Presumably, LibreOffice has the same functionality in later versions of Ubuntu.

So, you are not talking about 200MB for a "simple equation editor", but for a complete office suite!

No he's not. The largest part of the 200MiB is from the [FONT=Courier New]libreoffice-core[/FONT] package which is (obviously) the core of the program. Writer, Math, Impress, etc. are actually fairly small, but he's only installing Math, not Writer or anything else (although adding them wouldn't add a huge amount of data), so he isn't getting the entire suite.

---

### Post by Claus7 on 2011-10-02
Hello,

even doing so the above, you end up using equations as images, as a result I do not know whether you will be able to modify them afterwards. Not bad, yet not the best. I do not know whether there is 100% compatibility.

+1 for kile. Very nice interface, very nice latex editor.

Regards!

---

### Post by angryfirelord on 2011-10-02
Hmm, I just did some searching and it looks like there's an equation editor built into PowerPoint: [http://www.dummies.com/how-to/content/write-equations-in-powerpoint-2007.html]("http://www.dummies.com/how-to/content/write-equations-in-powerpoint-2007.html")

I have no idea if it's any good.

---

### Post by Zill on 2011-10-02
> **dniMretsaM said:**
> No he's not. The largest part of the 200MiB is from the [FONT=Courier New]libreoffice-core[/FONT] package which is (obviously) the core of the program. Writer, Math, Impress, etc. are actually fairly small, but he's only installing Math, not Writer or anything else (although adding them wouldn't add a huge amount of data), so he isn't getting the entire suite.
Sorry, my apologies...
I should have said "...but for *almost* a complete office suite!". ;-)

---

### Post by dniMretsaM on 2011-10-02
> **Zill said:**
> Sorry, my apologies...
I should have said "...but for *almost* a complete office suite!". ;-)

No need for apologies. You were mostly correct, as he was installing pretty much everything he would need to run the entire suite. I just figured it would be best to clarify. Nice avatar by the way.

---

### Post by gatorbrit on 2011-10-02
I battled this issue for the longest time.  The bottom line is that you can get powerpoint to run in wine - at least I could get ppt 2002 working OK.  THe equation editor would work fine - it would also work for word.  But later versions of ms office programs really never worked that well in either wine or cross over office.

The solution, at least for presentations, was to use Latex - but I use Lyx [www.lyx.org](www.lyx.org) as the front end.  It is super easy and using the "beamer" class, you can make really slick presentations that look much better IMHO than powerpoint.   

I actually now use Mac OS lion as my main OS, but I still us Lyx for presentations.  

As for equations in documents - if you are not sharing with other people, then libreoffice is great, but once you start sharing docs and folks are using different versions of word, things start to fall apart.

Best of luck

---

### Post by beew on 2011-10-02
There is an equation plugin called dmaths which works with OpenOffice and LibreOffice 3.4.x.
[http://www.dmaths.org/](http://www.dmaths.org/)

If you are on Maverick the dmaths package for OOO is in the repository.

Unfortunately Ubuntu11.04 comes with LibreOfice 3.3.x and there is no dmaths package for it in the repository,  the dmaths package for it from dmaths.org apparently doesn't work, so you would need to remove the LO3.3 packages first and install the .debs for LibreOffice 3.4.3 manually and then install the dmaths package (34) from dmaths.org. You can find the debs in the LO website.

---

### Post by honeybear on 2011-10-03
The solution from openoffice is a kind of coding thing again, sort of pseudo frontend of latex equation.

I would be looking for a real equation editor like normal mathematic programs.
[http://media.wiley.com/Lux/49/75449.image4.jpg?h=400&w=535](http://media.wiley.com/Lux/49/75449.image4.jpg?h=400&w=535)

Visibly Linux likes latex... :( 

maybe good programs are not opensource... I do not know..

---

