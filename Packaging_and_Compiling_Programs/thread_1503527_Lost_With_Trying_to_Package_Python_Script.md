---
title: "Lost With Trying to Package Python Script"
date: 2010-06-06
forum: Packaging and Compiling Programs
---

### Post by rookcifer on 2010-06-06
OK, I have read all the guides, done everything by the book and I am just not getting how to properly package a python script.  Nothing I do works.  I have tried stdeb, distutils, and followed the Ubuntu packaging guide, as well as trying a combination of all of the above.

Here is what I have:

**myscript.py**

**text_file.txt** (needs to be in the same directory since script.py reads from it)

**script.desktop** (script has a GUI)

**script.xpm** (needed for menu)

**FAQ** (for the user's questions about the script).

Can anyone please walk me through what I need to do in order to 

1) Make a proper source .deb that can be uploaded to a PPA

2) Make it so the .desktop and .xpm files install in the proper location in order to show up in the menu.

3) Make sure that text_file.txt ends up in the same directory as my script.

Thank you.

---

### Post by SevenMachines on 2010-06-08
hi, you should have a look though the [python packaging guide]("https://wiki.ubuntu.com/PackagingGuide/Python") first, its much more well informed and explained than i could manage :) You might want to pay particular attention to the 'A sophisticated rules files' section about overriding the cdbs build and install rules

---

### Post by rookcifer on 2010-06-09
I've already looked over that guide and it doesn't make sense to me.  I am lost on how to make a proper distutils package and in making a .deb.  I don't even know if I need to make a disutils package at all.  

I just need someone to provide me the template for the rules file with these specifications:

foo.py (needs to be in /usr/bin)
foo.txt (needs to be in /usr/bin/foobar)
faq (needs to be in /usr/bin/foobar)
foo.desktop (needs to be in /usr/share/applications)
foo.xpm (needs to be in /usr/share/pixmaps)

Can any experienced packager give me a rules file for the above?  Once I see it done, I should be able to catch on pretty quickly, but am a bit confused by the guides because of the naming conventions used.

---

### Post by SevenMachines on 2010-06-11
hi there, the reason i was pointing you towards the 'a sophisticated rules file' section mentioned above is that it covers exactly the thing your trying to do. what it says in essence is that you can make a rules file that runs all the debhelper scripts, but we dont want to build so we override this section.

debian/rules:
> #!/usr/bin/make -f
%:
        dh $@

override_dh_auto_build: 

then, as it goes on to explain, you can then either override override_dh_auto_install: in the rules file or better yet, you can just leave the rules file as it is and instead create a debian/<packagename>.install file and then add entries to install your files to where you want them. for example, for a package called hellome that installs the files you mention above

debian/hellome.install:
> foo.py usr/bin/
foo.txt  /usr/bin/foobar/
faq  /usr/bin/foobar/
foo.desktop  /usr/share/applications/
foo.xpm /usr/share/pixmaps/

this should now create a package using debhelper, skipping the build stage and then installing the files to the  locations you specify in the .install file.

---

### Post by Umang on 2010-06-17
Hi!
(I was the one who rewrote that guide :), I'm glad to know that people use it). 

About the package: Yes, it seems you cannot just use the tiny rules file, because you need the text_file.txt file in the same directory.

I would avoid cluttering /usr/bin with these extra files, as /usr/bin is not supposed to have data files. (Especially recommended if you plan to submit your package to Ubuntu/Debian as your sponsors will be particular about these things).

I would suggest that you overrride dh_auto_build and dh_auto_install as already suggested. You can then install both the script and the text file in /usr/share/foobar/ and then symlink /usr/bin/foobar to /usr/share/foobar/myscript.py.

This can be done by writting a debian/foobar.links file like:
```
usr/share/foobar/myscript usr/bin/foobar
``` (run `man dh_links` for more information)

(where foobar should be replaced with the name of your package or script)

I don't mean to advertise, but you can download a package of mine (my only one in Debian till now) and look at how it does something very similar. Run:
```
dget http://ftp.debian.org/debian/pool/main/p/pynagram/pynagram_1.0.0-1.dsc
``` and browse the pynagram/debian directory. 

It installs a script in /usr/share/pynagram/ and has a symlink (/usr/games/pynagram) that points to that script.

**Edit**: You can read [this]("http://www.debian.org/doc/manuals/maint-guide/ch-dother.en.html#s-docs") to decide what to do with your FAQ file. You should be installing it in /usr/share/doc/foobar, but it is better to use dh_installdocs to do that rather than dh_install.

Hope this helps

---

