---
title: "stackless python - how to install?"
date: 2006-07-08
forum: Programming Talk
---

### Post by Van_Gogh on 2006-07-08
Hi all,

After reading [this tutorial]("http://members.verizon.net/olsongt/stackless/why_stackless.html"), I've become really interested in trying out [Stackless Python]("http://www.stackless.com/download"). However, it is not in any repository and only exists in source form for Linux, and basically I got no clue how to install it. Google is no help, so anyone here knows how to do it?

I don't mind it overwriting the stock version of python as non-stackless code should runs fine on stackless.

---

### Post by Somenoob on 2006-07-08
search for repositories who contain it.

Or just get the required dependencies for the program, and then compile/build it.

---

### Post by Van_Gogh on 2006-07-08
Hi somenoob,

Stackless is not in any repository as I already said. I don't know why it isn't, but I think it's because it needs to overwrite some part of standard Python installation.

About building it myself: I got no idea how and just sounds like a really complicated thing to do. I'd rather spend my time programming IN stackless than installing it, I suppose ;)

BTW, I got it working on Windows(very simple to do), so maybe I'll just have to run it there. It's not in the spirit of open source though.

---

### Post by Somenoob on 2006-07-08
> **Van_Gogh said:**
> Hi somenoob,

Stackless is not in any repository as I already said. I don't know why it isn't, but I think it's because it needs to overwrite some part of standard Python installation.

About building it myself: I got no idea how and just sounds like a really complicated thing to do. I'd rather spend my time programming IN stackless than installing it, I suppose ;)

BTW, I got it working on Windows(very simple to do), so maybe I'll just have to run it there. It's not in the spirit of open source though.

Well, if you can find a ".deb" ".rpm" ".gz" ".bz2" archive for stackless python, then it should be simple to install it.

[Read this]("http://ubuntuforums.org/showpost.php?p=878846&postcount=1") for installing/building instructions, it's not as difficult to install them as most users think.

And Stackless python is avalible for Linux.

---

### Post by tistje on 2007-09-23
Hi,

I did install stackless (2.5.1) on ubuntu feisty (./configure; make; sudo make install). Everything works well. :)

But since  I didn't use the package manager,  I guess a newer version of the python2.5 package in the repositories will overwrite it? :confused: 
Anyone experience with that?

greetz,
Tistje

---

### Post by sr12zar on 2008-03-18
Hi,

I am new Ubuntu (7.04) user, and still exploring around.
However I installed stackless python (latest maint from stackless.com) using the usual (tar -xvf ...; cd ...; ./configure; make; sudo make install). All went well and I could start python and got stackless python.

I went on to do 'apt-get install python-visual' and that went well.

However, when inside stackless, I tried 'from visual import *', stackless said it knew nothing about visual!

A day later, I found:
1) stackless python was installed into /usr/local/lib/... (ubuntu python2.5 is in /usr/lib/...
2) visual went into /usr/lib/python2.5/site-packages/
3) my PATH now /usr/loca/sbin:/usr/local/bin:/usrsbin:/usr/bin:/usr/games

I tried 'sudo make clean' and 'sudo make distclean' to remove stackless from /usr/local/lib/... Not successful!

I made 'sudo ln -s /usr/lib/python2.5/sitepackges/ usr/local/lib/python2.5/site-packages/'. When I tried import visual in stackless, that worked.

I tried installing stackless into /usr/lib/python2.5 by setting --prefix=/usr and --exec-prefix=/usr. The installation went well.
I have stackless+visual python on ubuntu 7.04 ..... yipeeee.

But then I found that alacarte, sudoku and update manager did not work as expected. I re-installed ubuntu python2.5.1 into /usr/lib. Now alacarte works but sudoku doesn't and I don't know how to test update manager.

Has anyone gone into putting stackless+visual python on ubuntu 7.04? Can anyone suggest a lower risk path of doing this?

---

### Post by pmasiar on 2008-03-18
I don't have ubuntu around ATM, but can you find stackless in standard repositories (universe I guess) instead of installing from the source? If not, experts will advise you how to create package installable by apt. It is always preferable over manual install from sources.

---

### Post by LaRoza on 2008-03-18
The source tarball has a script to install it for you.

---

### Post by sr12zar on 2008-03-18
Thanks guys.

I should explain my problems better.

1) I couldn't find a ubuntu-ready-to-install package for stackless. (I used 'stackless/ python-stackless / stackless-python/ ...' in my search. So if someone could point to a repo, please?)

2) (As installed on my ubuntu 7.04) 
I can use either standard python by calling it '/usr/bin/python' or stackless python by calling '/usr/local/bin/python'. The symlink site-packages lets me use visual in both.

3) Here are my problems:
a) I want to be able to uninstall stackless python --cleanly # i.e. removing all generated objects and backing out edits (I should ask stackless people ;-))
b) When I launch applications/games/sudoku I get  

Traceback (most recent call last):
  File "/usr/games/gnome-sudoku", line 20, in <module>
    from gnome_sudoku.gnome_sudoku import start_game
  File "/usr/lib/python2.5/site-packages/gnome_sudoku/gnome_sudoku.py", line 7, in <module>
    import gtk, gobject, gtk.glade
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 38, in <module>
    import gobject as _gobject
  File "/var/lib/python-support/python2.5/gtk-2.0/gobject/__init__.py", line 30, in <module>
    from _gobject import *
ImportError: /var/lib/python-support/python2.5/gtk-2.0/gobject/_gobject.so: undefined symbol: PyUnicodeUCS4_FromObject

When I tried to report this, evolution mail failed!
(I ask for help here)

I am an ubuntu newbie. I am still find the places to go and get info and help. Please guys, guide me!

---

### Post by pmasiar on 2008-03-18
> **Van_Gogh said:**
> BTW, I got it working on Windows(very simple to do), so maybe I'll just have to run it there. It's not in the spirit of open source though.

If you can run same code on Windows and Linux, it pretty much **is** in the spirit of free software, IMHO. :-) Also in the spirit is that you have to learn how to install it before you can use it. Free is about the free speech, remember? You have source and you can change it, so it is Free.

---

### Post by sr12zar on 2008-03-20
I'd like to make an update on stackless python on ubuntu.

The guys from Stackless mailing list (especially Bjorn and Phoenix Sol) suggested that: it is a better idea to install stackless in /usr/local/ and leave the ubuntu's default python in /usr/; rename python in /usr/local/bin/ to stackless and symlink site-packages; this way we can call stackless or (default) python at will. (Details are at stackless.com mailing list).

I agree with them that this is a 'smooth' and 'low risk' way to install stackless python on ubuntu. (Thanks again.)

As for those who want to experiment with visual python. Just 'sudo apt-get install python-visual' to install into /usr/lib/python.../site-packages/visual. The symlink above will let stackless import visual and there we have stackless-visual python on ubuntu.

I am experinting with this setup - and will update if there are problems. Thanks for your attention.

---

### Post by young.jeezy on 2009-09-16
Hey I have been trying to install stackless as well on ibex ubuntu, and seem to be having some problems with the method mentioned above. 

I did an altinstall which put stackless /usr/local/lib and bin and symbolically linked the site packages, so I can successfully call python and stackless python seperately ... but i seem to get an issue when I try to import ctypes in stackless: "ImportError: /usr/lib/python2.5/lib-dynload/_ctypes.so: undefined symbol: PyUnicodeUCS4_FromEncodedObject " 

That path /usr/lib/python2.5 suggests to me that the ubuntu regular python and stackless are still intermingled.   Any help would be appreciated :)

With the method above of installing to usr/local/lib, the alt install doesn't place any header files in the include directory in usr/local. Do stackless.h and other header files have to be manually placed in the usr/local/include directory? Thanks for reading and any feeback would be appreciated. I don't really know what I'm doing.

---

### Post by young.jeezy on 2009-09-27
Well I made progress and solved my problem. The vyper logix blog tells a person what options to pass to configure and how to install. 

Problem: I couldn't import anything in to stackless in ubuntu after symbolically linking the site packages. An error about unicode would occur. 

Solution: use command ./configure --enable-unicode=ucs4 when creating the makefile. doing this I can import numpy from the regular ubuntu sitepackages 
when doing the installation, use the command sudo make -i altinstall if you are having errors. The -i flag makes make ignore the errors. 

Thanks.

---

### Post by psykotron on 2009-12-24
Along with the "./configure --enable-unicode=ucs4" and creating symlinks to the default python packages. You'll probably want to make the changes that match "site-packages" in /usr/lib/python2.6/site.py to /usr/local/lib/python2.6/site.py
After doing this you should be able to use most modules.

I'd recommend using matching versions of stackless and python, in this case I was using 2.6.4

---

