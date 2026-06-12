---
title: "gpapers installation in ubuntu"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by jlawrence on 2008-04-22
Hi,

Recently I have been very jealous with Mac users because they have decent softwares to manage their pdf files (Papers and yep).

I found a similar software for Linux, named gPapers. 
[http://gpapers.org/](http://gpapers.org/)

However the installation is very complex and I got several problems in the installation of pysqlite and poppler. I am not an experienced user and tried to follow the instruction but still I am confused.

Can someone post solutions for this problem ? Thank you.

JL

---

### Post by Het Irv on 2008-04-22
Copy & Paste the first command
```
sudo apt-get install python python-glade2 python-gnome2 python-sqlite3 graphviz
```

```
svn checkout [http://gpapers.googlecode.com/svn/trunk/](http://gpapers.googlecode.com/svn/trunk/) gpapers
```
```
svn co [http://code.djangoproject.com/svn/django/trunk/django](http://code.djangoproject.com/svn/django/trunk/django)gpapers/django
```
```
svn checkout [http://deseb.googlecode.com/svn/trunk/src/deseb](http://deseb.googlecode.com/svn/trunk/src/deseb) gpapers/deseb

```
```
sudo apt-get install build-essential libpoppler2 libpoppler-dev libpoppler-glib2 libpoppler-glib-dev python-cairo-dev bzr gnome-common python-dev python-gnome2-dev python-gtk2-dev python-gobject-dev python-pyorbit-dev
```

```
bzr branch [http://bazaar.launchpad.net/~poppler-python/poppler-python/poppler-0.6-experimental](http://bazaar.launchpad.net/~poppler-python/poppler-python/poppler-0.6-experimental)
```
```
cd poppler-0.6-experimental
```
 ```
./autogen.sh
```
 ```
./configure
```
 ```
make
```
 ```
sudo make install 
```

Copy and Paste these one at a time, If you come to an error post it and I will try to help you with it.

---

### Post by rax_m on 2008-04-22
Hi jlawrence, 

if you can give some details of what errors you have then we may be able to point where you're going wrong. 

In the mean time, if you don't want to go through the hassle, there are a couple of other reference management tools I've used that are ok:
bibus
jabref
zotero (firefox extension)
connotea (open source web based application)

I hope that helps
Cheers
Rax

---

### Post by rax_m on 2008-04-22
or you can try what Het Irv posted ... guess I was a bit slow ;)

---

### Post by jlawrence on 2008-04-23
Hi,

Thanks for the replies. I tried the first command set, but I got this message:

python is already the newest version.
python-glade2 is already the newest version.
python-gnome2 is already the newest version.
E: Couldn't find package python-sqlite3

How do I install python-sqlite3 ? I tried installing python-sqlite2 as well but couldn't find it.

If it is relatively bug free, I think gpapers is the best for now. Zotero is not that straight forward, and I think the ability to add annotation or note to the pdf will be great for Linux community.

---

### Post by Het Irv on 2008-04-23
Try searching in Synaptic Package Manger for python-pysqlite2

It looks like that package should work. Disclaimer: note the SHOULD is the previous sentence.

---

### Post by jlawrence on 2008-04-30
gpapers rocks!

thank you Het Irv. pysqlite2 works well.

Step 3 and 6 needs to be modified, probably better for newbie, because I could not make it work unless I changed them as below:
(change "hxxp to http")

Step 3:
svn co hxxp://code.djangoproject.com/svn/django/trunk/django

Step 6:
bzr branch hxxp://bazaar.launchpad.net/~poppler-python/poppler-python/poppler-0.6-experimental

Anyway, gpapers needs to be improved more, if possible better than Papers or Yep.

Regards,

---

### Post by chechojp on 2008-05-02
I am also a newbie but somehow I managed to install gpapers (I believe) flawlessly...I mean I had no errors no weird messages and so on.

The problem is that i cant find how to run it. It doesnt appear under the applications directory and i dont know if it can be "executed" from the terminal...please help!!!!

---

### Post by Het Irv on 2008-05-05
try opening the terminal and typing: gpapers

It may be hidden in the menus, try going to System-> Prefrences -> Main Menu
from here you may be able to find it unchecked, or hidden, and check it to show up in the menu.

---

### Post by AmericanAqualung on 2008-05-11
So, there are once again issues with the install of gPapers.  Well, in particular the prerequisite of poppler-python.  This has now been updated to version 0.8 in order to make use of poppler version 0.8.  Unfortunately all of the versions in Ubuntu are the 0.6.x.  I have been trying to figure out how to update this manually without screwing up things that depend on poppler that are already installed (pretty much a lot of things requiring pdf rendering).  Furthermore, I'd like to keep xpdf after the update.  Does anybody have any idea?
(Oh and unfortunately the 0.6-experimental version is not available either).

-Andy O'Hara

---

### Post by gtzam on 2008-07-10
I am facing a problem with the installation of gpapers. When I type
```
bzr branch http://bazaar.launchpad.net/~poppler...6-experimental
```

I am getting this error message:
*bzr: ERROR: Not a branch: "https://code.launchpad.net/".*

Therefore I cannot proceed with the installation. Any suggestions?
Many thanks

---

### Post by stumbleUpon on 2008-07-11
> **gtzam said:**
> I am facing a problem with the installation of gpapers. When I type
```
bzr branch http://bazaar.launchpad.net/~poppler...6-experimental
```

I am getting this error message:
*bzr: ERROR: Not a branch: "https://code.launchpad.net/".*

Therefore I cannot proceed with the installation. Any suggestions?
Many thanks

Same problem with me.

When i try

```
bzr branch http://bazaar.launchpad.net/~poppler-python/poppler-python/poppler-0.6-experimental
```

i get

```
bzr: ERROR: Not a branch: "https://code.launchpad.net/".
```

Everything else upto this point is fine.

Any help is greatly appreciated.

---

### Post by sybille on 2008-07-11
> **jlawrence said:**
> Zotero is not that straight forward, and I think the ability to add annotation or note to the pdf will be great for Linux community.

Hi, I made a wiki page on using Zotero with Ubuntu that I hope will make it a little more straightforward:
[https://help.ubuntu.com/community/Zotero](https://help.ubuntu.com/community/Zotero)

 You can use Zotero to associate notes with PDFs, there's more information about that in the wiki. I have more than 300 PDFs in my Zotero library and I find that it's a good solution.

Zotero probably wouldn't make sense for people who don't want to cite the PDFs in academic texts, though, since basically all the Zotero information is organized around bibliography reference data.

Anyway, I'm just mentioning it as an option for people who are having trouble installing gpapers. [Referencer]("http://icculus.org/referencer/") is another alternative.

---

### Post by adking80 on 2008-07-25
I just installed successfully under 7.10.  When I couldn't find the branch with the original bzr command I replaced it with:

bzr branch hxxp://bazaar.launchpad.net/~poppler-python/poppler-python/trunk --revision 40

and went to the "trunk" directory instead of the poppler directory to install.

---

### Post by stumbleUpon on 2008-07-29
> **adking80 said:**
> I just installed successfully under 7.10.  When I couldn't find the branch with the original bzr command I replaced it with:

bzr branch hxxp://bazaar.launchpad.net/~poppler-python/poppler-python/trunk --revision 40

and went to the "trunk" directory instead of the poppler directory to install.

Thanks a lot. I just installed successfully on Hardy 64-bit.

I had earlier tried without '--revision 40' option but i had a lot of problems about version incompatibility of installed software.

This suggestion worked perfectly.

But i think gPapers has a long way to go yet. Many a times, it mixes up the names of the authors, title, journal etc.

Perhaps it is a little too early to make such comments.

---

### Post by nmhitman on 2008-08-21
after a brief investigation within the synaptic package manager I came across a reference to python-sqlite3.  It seems it is repackaged/offered (at least to hardy users) as python-apsw.

Inserting this in place of python-sqlite3 worked for my install and I can now run the software.  However, I'm still not able to import any of my .pdf files...all of them output an error as follows:

deseb: gPapers.schema_evolution module found (24 fingerprints, 12 evolutions)
deseb: fingerprint for 'gPapers' is 'fv1:-1497796564' (unrecognized)
trying to fetch: ['/home/339.pdf']
-1265013872 importing paper = /home/339.pdf
Traceback (most recent call last):
  File "./gpapers/gPapers.py", line 332, in import_document
    paper.save_full_text_file( defaultfilters.slugify(os.path.split(filename)[1].replace('.pdf',''))+'.pdf', data )
AttributeError: 'Paper' object has no attribute 'save_full_text_file'

Any ideas?

Also, how can we go about seeing this seemingly wonderful program make its way into the repositories for easier install/use?

---

### Post by 5au1 on 2008-09-20
Hi, I have installed gpapers following all the instructions in the post, however I don't know how to execute it (just as **chechojp**).

I've noticed that gpapers and trunk's folders are in my home folder, and (from my windows experience) I think they should be somewhere else, right?

Thanks in advance

---

### Post by cosine352 on 2008-11-17
> Hi, I have installed gpapers following all the instructions in the post, however I don't know how to execute it (just as chechojp).

I've noticed that gpapers and trunk's folders are in my home folder, and (from my windows experience) I think they should be somewhere else, right?

Thanks in advance

do this
> cd gpapers
> python gPapers.py


=====================================================

> 
after a brief investigation within the synaptic package manager I came across a reference to python-sqlite3. It seems it is repackaged/offered (at least to hardy users) as python-apsw.

Inserting this in place of python-sqlite3 worked for my install and I can now run the software. However, I'm still not able to import any of my .pdf files...all of them output an error as follows:

deseb: gPapers.schema_evolution module found (24 fingerprints, 12 evolutions)
deseb: fingerprint for 'gPapers' is 'fv1:-1497796564' (unrecognized)
trying to fetch: ['/home/339.pdf']
-1265013872 importing paper = /home/339.pdf
Traceback (most recent call last):
File "./gpapers/gPapers.py", line 332, in import_document
paper.save_full_text_file( defaultfilters.slugify(os.path.split(filename)[1].replace('.pdf',''))+'.pdf', data )
AttributeError: 'Paper' object has no attribute 'save_full_text_file'

Any ideas?

Also, how can we go about seeing this seemingly wonderful program make its way into the repositories for easier install/use?

same problem here. 

This is a really great application. Hope it will work properly in future.

---

### Post by anando on 2009-04-09
Hi 

Can some kind soul please package gpapers for Ubuntu ? If there is some instructions on packaging, I can have a gander at it myself.

Regs,
Anand.

---

### Post by snova on 2009-04-09
> **anando said:**
> Can some kind soul please package gpapers for Ubuntu ? If there is some instructions on packaging, I can have a gander at it myself.

[Packaging Guide]("https://wiki.ubuntu.com/PackagingGuide") (though it's not the simplest of things)

As for getting it packaged, I asked; you could file a bug about it, but the effectiveness of that approach depends on whether somebody wants to.

---

### Post by Dionysios on 2009-06-01
I think this is one of the most useful applications ever written for Linux. It should definitely be added to the repositories.

---

### Post by iv2101 on 2009-06-15
I am running ubuntu Jaunty 32 bit and can't fetch the right packages: 

```
sudo apt-get install build-essential libpoppler-dev libpoppler-glib2 libpoppler-glib-dev python-cairo-dev bzr gnome-common python-dev python-gnome2-dev python-gtk2-dev python-gobject-dev python-pyorbit-dev
```

returns that there are no candidates to install for the *poppler* packages. Running

```
make
```

in the trunk directory [as suggested by **adking80**] returns an error. I assume these are connected...

Does anyone know how to get gpapers to work on jaunty?

Thanks!

---

### Post by snova on 2009-06-15
> **iv2101 said:**
> I am running ubuntu Jaunty 32 bit and can't fetch the right packages: 

```
sudo apt-get install build-essential libpoppler-dev libpoppler-glib2 libpoppler-glib-dev python-cairo-dev bzr gnome-common python-dev python-gnome2-dev python-gtk2-dev python-gobject-dev python-pyorbit-dev
```

returns that there are no candidates to install for the *poppler* packages. Running

```
make
```

in the trunk directory [as suggested by **adking80**] returns an error. I assume these are connected...

Does anyone know how to get gpapers to work on jaunty?

Thanks!

What is the error make returns?

---

### Post by iv2101 on 2009-06-16
this is the output of make:

```
ilya@ilya-laptop:~/trunk$ make
make  all-recursive
make[1]: Entering directory `/home/ilya/trunk'
Making all in demo
make[2]: Entering directory `/home/ilya/trunk/demo'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/ilya/trunk/demo'
make[2]: Entering directory `/home/ilya/trunk'
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I/usr/include/python2.6   -D_REENTRANT -I/usr/include/pygtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/atk-1.0 -I/usr/include/poppler/glib -I/usr/include/poppler -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/pycairo   -g -O2 -Wall -std=c9x -fno-strict-aliasing -MT poppler_la-poppler.lo -MD -MP -MF .deps/poppler_la-poppler.Tpo -c -o poppler_la-poppler.lo `test -f 'poppler.c' || echo './'`poppler.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I/usr/include/python2.6 -D_REENTRANT -I/usr/include/pygtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/atk-1.0 -I/usr/include/poppler/glib -I/usr/include/poppler -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/pycairo -g -O2 -Wall -std=c9x -fno-strict-aliasing -MT poppler_la-poppler.lo -MD -MP -MF .deps/poppler_la-poppler.Tpo -c poppler.c  -fPIC -DPIC -o .libs/poppler_la-poppler.o
poppler.c: In function '_wrap_poppler_image_mapping__get_image':
poppler.c:215: error: 'PopplerImageMapping' has no member named 'image'
poppler.c: In function '_wrap_poppler_page_get_thumbnail':
poppler.c:1410: warning: assignment from incompatible pointer type
poppler.c: In function '_wrap_poppler_page_get_selection_region':
poppler.c:1565: warning: assignment from incompatible pointer type
poppler.c: In function '_wrap_poppler_page_render_selection':
poppler.c:1610: warning: passing argument 6 of 'poppler_page_render_selection' from incompatible pointer type
poppler.c:1610: warning: passing argument 7 of 'poppler_page_render_selection' from incompatible pointer type
make[2]: *** [poppler_la-poppler.lo] Error 1
make[2]: Leaving directory `/home/ilya/trunk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ilya/trunk'
make: *** [all] Error 2

```

---

### Post by iv2101 on 2009-06-20
bump

---

### Post by iv2101 on 2009-06-25
rebump...

---

### Post by snova on 2009-06-27
> **iv2101 said:**
> I am running ubuntu Jaunty 32 bit and can't fetch the right packages: 

```
sudo apt-get install build-essential libpoppler-dev libpoppler-glib2 libpoppler-glib-dev python-cairo-dev bzr gnome-common python-dev python-gnome2-dev python-gtk2-dev python-gobject-dev python-pyorbit-dev
```

returns that there are no candidates to install for the *poppler* packages.

Ok, sorry. Lets back up a bit. What are the precise error messages for this? These packages should all be in the main repositories.

According to the installation [instructions]("http://code.google.com/p/gpapers/wiki/Installation"), you need:

```
sudo apt-get install python python-glade2 python-gnome2 python-sqlite3 graphviz
```

Later on it says to build pypoppler from source, but I think this is unnecessary, it appears to be in the repos.

```
sudo apt-get install python-poppler
```

Please try those commands, and post any errors. I think they should work (if the second doesn't, make sure the universe component is enabled in System -> Administration -> Software Sources).

---

### Post by iv2101 on 2009-06-27
aaah! Now it works. I still get the error 

E: Couldn't find package python-sqlite3

but it doesn't seems to matter. 

Thank you!

---

