---
title: "[HOW TO]Removing Duplicate Files(batch proccess)"
date: 2006-10-06
forum: Outdated Tutorials &amp; Tips
---

### Post by rabid9797 on 2006-10-06
**How To: Removing Duplicate Files**

This comes in handy when you download pictures en masse or have large collections of files(usually pictures or mp3's) that are not organized. Good for free'ing up space and optimizing size of collections.

There are a couple choices in programs you can go with for doing this:

[**Fdupes**]("http://netdial.caribe.net/~adrian2/fdupes.html") - Command line tool, very simple to use and will find all duplicates using an md5 hash method. Md5 hash is more accurate than checksum but takes longer. This tool is good if you just need a simple readout of duplicates(as in your going to create a script to automate deleting duplicates with the readout)
an example being: ```
$fdupes -r /folder > dupes.txt
```

this will print a readout of all duplicate files to dupes.txt with all duplicates grouped together.

Fdupes can be found in the repositories.

[**Duff**]("http://duff.sourceforge.net/") - Another command line tool, only using checksum instead of md5. 
Duff is not in the repositories.

[**FSlint**]("http://www.pixelbeat.org/fslint/") - GUI program that uses md5 hashing to find duplicate files. It also finds bad symlinks, name clashes, bad ID's duplicate packages, etc. and has advanced parameters.

Installs with a .deb package or source code repository.

[**Klean Sweep**]("http://www.kde-apps.org/content/show.php?content=28631") - KDE GUI application(should work with gnome), and also finds various other disk using waste: 
* empty files
* empty directories
* backup files
* broken symbolic links
* broken executables
* dead menu entries (.desktop files pointing to non-existing executables)
* obsolete thumbnails (thumbnails of non-existing images)
* duplicated files
* orphaned files (files not found in RPM or DEB database).

Can be installed with repositories.

Hope this How To goes to use, i know after i found FSlint it made my life easier :mrgreen: 

enjoy

---

### Post by rabid9797 on 2006-10-06
UPDATE: kleansweep has an automation option for deleting all duplicates but one

---

### Post by pixelbeat on 2006-11-24
Hi I'm the Author of FSlint.
The GUI is a wrapper around a core command line utilities.
On a standard install you can add these utils to the path with:

export PATH="$PATH":/usr/share/fslint/fslint

Then you can use the utilities like:

findup /folder     #list duplicates
findup -m /folder  #merge duplicates using hardlinks
findup -d /folder  #delete all but first duplicate
findup -dt /folder #report what would be deleted

fslint /folder #run all tools on a folder

---

### Post by Don_DiZzLe on 2006-11-24
What do u mean exactly? I just installed fslint_2.16-1_all.deb and it works just fine.

---

### Post by pixelbeat on 2006-11-24
That's good to hear :)

I'm just referring to the subject of the thread
(batch processes). I was describing the command line
interface to the FSlint package, which one can
use to automate/extend it's functionality.

Pádraig.

---

### Post by Don_DiZzLe on 2006-11-26
What does redundant whitespace mean and what will happen if i clean the selected files?

Oh and more thing what are non-stripped binaries?

---

### Post by pixelbeat on 2006-11-27
Yes that it not clear sorry.
In the latest version in svn, more explanatory
text is displayed in the status bar:
[http://code.google.com/p/fslint/source](http://code.google.com/p/fslint/source)

So the actual text displayed now for the
two functions you mentioned is:

"Redundant whitespace at the end of lines within a file"

"Executables still containing debugging information"

Pádraig.

---

### Post by Don_DiZzLe on 2006-11-27
Which package do I need to install for SVN to work?

---

### Post by pixelbeat on 2006-11-27
subversion

---

### Post by Don_DiZzLe on 2006-11-27
I just got the latest source, but how do make a deb of ur files?

---

### Post by pixelbeat on 2006-11-28
See [http://fslint.googlecode.com/svn/trunk/doc/FAQ](http://fslint.googlecode.com/svn/trunk/doc/FAQ)

---

### Post by Don_DiZzLe on 2006-11-28
Ok I did, and this is what I get:

Checked out revision 13.
rhandulle@Don-DiZzLe:~$ cp -aR fslint fslint-2.17
rhandulle@Don-DiZzLe:~$ cd fslint-2.17
rhandulle@Don-DiZzLe:~/fslint-2.17$ dpkg-buildpackage -rfakeroot -tc
dpkg-buildpackage: source package is fslint
dpkg-buildpackage: source version is 2.16-1
dpkg-buildpackage: source changed by Pádraig Brady <P@draigBrady.com>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 2.16-1
 fakeroot debian/rules clean
dh_testdir
dh_testroot
/usr/bin/make -C po clean
make[1]: Entering directory `/home/rhandulle/fslint-2.17/po'
rm -Rf locale
rm -f *.mo
make[1]: Leaving directory `/home/rhandulle/fslint-2.17/po'
dh_clean
 dpkg-source -b fslint-2.17
dpkg-source: warning: source directory `./fslint-2.17' is not <sourcepackage>-<upstreamversion> `fslint-2.16'
dpkg-source: building fslint in fslint_2.16-1.tar.gz
dpkg-source: building fslint in fslint_2.16-1.dsc
 debian/rules build
dh_testdir
# Could modify source here before install,
# but doing so would not allow one to run dpkg-buildpackage
# from a working source tree.
# Instead source edits are done in install:
 fakeroot debian/rules binary
dh_testdir
dh_testroot
dh_clean
# Note dh_installdirs will create dirs listed in fslint.dirs
# Note dh_install will install files listed in fslint.install
install -Dpm 755 fslint-gui debian/fslint/usr/bin/fslint-gui
perl -pi -e 's|^liblocation=.*|liblocation="/usr/share/fslint" #deb edit|' debian/fslint/usr/bin/fslint-gui
perl -pi -e 's|^locale_base=.*|locale_base=None #deb edit|' debian/fslint/usr/bin/fslint-gui
install -dm 755 debian/fslint/usr/share/fslint/fslint/{fstool,supprt}
install -dm 755 debian/fslint/usr/share/fslint/fslint/supprt/rmlint
install -pm 644 fslint.glade fslint_icon.png debian/fslint/usr/share/fslint
install -dm 755 debian/fslint/usr/share/pixmaps
ln -s ../fslint/fslint_icon.png debian/fslint/usr/share/pixmaps
install -pm 755 fslint/{find*,fslint,zipdir} debian/fslint/usr/share/fslint/fslint
install: cannot stat `fslint/{find*,fslint,zipdir}': No such file or directory
make: *** [install] Error 1

---

### Post by pixelbeat on 2006-11-28
I verified it works for me.
Are you sure you got all the files?
Because this works:

install -pm 644 fslint.glade fslint_icon.png debian/fslint/usr/share/fslint
install -dm 755 debian/fslint/usr/share/pixmaps
ln -s ../fslint/fslint_icon.png debian/fslint/usr/share/pixmaps

But this doesn't?

install -pm 755 fslint/{find*,fslint,zipdir} debian/fslint/usr/share/fslint/fslint
install: cannot stat `fslint/{find*,fslint,zipdir}': No such file or directory

---

### Post by pixelbeat on 2006-11-28
But this doesn't?

install -pm 755 fslint/{find*,fslint,zipdir} debian/fslint/usr/share/fslint/fslint
install: cannot stat `fslint/{find*,fslint,zipdir}': No such file or directory
Edit/Delete Message

Ah, I wonder is it something to do with your local shell globbing.
What shell are you using? Maybe I need to specify bash somewhere.

I'll look into it.

---

### Post by Don_DiZzLe on 2006-11-28
I just use the standard Ubuntu terminal and whichever shell come with it, i havnt changed nothing so

anyways thnx that u'll look in to it.

---

### Post by pixelbeat on 2006-11-29
Can you checkout and try building a deb on the latest repo.
I've removed the brace expansion from the rules file.

Pádraig.

---

### Post by Don_DiZzLe on 2006-11-29
Cool!, ill try it as soon as i get back from school.

---

### Post by Don_DiZzLe on 2006-11-29
Now I get this:

rhandulle@Don-DiZzLe:~$ cp -aR fslint fslint-2.17
rhandulle@Don-DiZzLe:~$ cd fslint-2.17
rhandulle@Don-DiZzLe:~/fslint-2.17$ dpkg-buildpackage -I.svn -rfakeroot -tc
dpkg-buildpackage: source package is fslint
dpkg-buildpackage: source version is 2.17-1
dpkg-buildpackage: source changed by Pádraig Brady <P@draigBrady.com>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 2.17-1
 fakeroot debian/rules clean
dh_testdir
dh_testroot
/usr/bin/make -C po clean
make[1]: Entering directory `/home/rhandulle/fslint-2.17/po'
rm -Rf locale
rm -f *.mo
make[1]: Leaving directory `/home/rhandulle/fslint-2.17/po'
dh_clean
 dpkg-source -I.svn -b fslint-2.17
dpkg-source: building fslint in fslint_2.17-1.tar.gz
dpkg-source: building fslint in fslint_2.17-1.dsc
 debian/rules build
dh_testdir
# Could modify source here before install,
# but doing so would not allow one to run dpkg-buildpackage
# from a working source tree.
# Instead source edits are done in install:
 fakeroot debian/rules binary
dh_testdir
dh_testroot
dh_clean
# Note dh_installdirs will create dirs listed in fslint.dirs
# Note dh_install will install files listed in fslint.install
install -Dpm 755 fslint-gui debian/fslint/usr/bin/fslint-gui
perl -pi -e 's|^liblocation=.*|liblocation="/usr/share/fslint" #deb edit|' debian/fslint/usr/bin/fslint-gui
perl -pi -e 's|^locale_base=.*|locale_base=None #deb edit|' debian/fslint/usr/bin/fslint-gui
install -dm 755 debian/fslint/usr/share/fslint/fslint/{fstool,supprt}
install -dm 755 debian/fslint/usr/share/fslint/fslint/supprt/rmlint
install -pm 644 fslint.glade fslint_icon.png debian/fslint/usr/share/fslint
install -dm 755 debian/fslint/usr/share/pixmaps
ln -s ../fslint/fslint_icon.png debian/fslint/usr/share/pixmaps
install -pm 755 fslint/find* fslint/fslint fslint/zipdir debian/fslint/usr/share/fslint/fslint
install -pm 755 fslint/fstool/* debian/fslint/usr/share/fslint/fslint/fstool
install: target `debian/fslint/usr/share/fslint/fslint/fstool' is not a directory
make: *** [install] Error 1

---

### Post by Don_DiZzLe on 2006-12-06
R u still there pixelbeat?

---

### Post by Endolith on 2007-12-15
FSlint would be great if it had a useful interface.  This free simple Windows program does it better: [http://www.geocities.com/hirak_99/goodies/finddups.html](http://www.geocities.com/hirak_99/goodies/finddups.html)

It lets you select an entire directory, and all duplicates in that directory will be removed, recursively, and any empty directories it creates will be deleted.

You can also have it "auto mark" all but one of each file.  It would be best if you could choose the criteria, though, like "all but the oldest".

It shows you the duplicate files by highlighting them with the same colors.

---

### Post by steve_waters on 2007-12-15
Hi,

I just ran fslint on my system, it used filename definitely and not md5 hash to discover duplicates, as it has selected 10 files with the same name, all of them photos which are different pictures and sizes.

Is there a way to force the use of md5? 

Thanks,
Steve

---

### Post by i M@N on 2007-12-16
Hello.

Many thnxX rabid9797 ... fdupes saved my life !

@+...

---

### Post by pixelbeat on 2007-12-16
> **Endolith said:**
> FSlint would be great if it had a useful interface.  This finddups Windows program does it better

The fslint version in ubuntu is quite old unfortunately.
I've been trying without luck to get it upgraded.
Fedora and debian always have the latest version available,
and you can download the latest ubuntu package at[www.pixelbeat.org/fslint/]("http://www.pixelbeat.org/fslint/")

> **Endolith said:**
> It lets you select an entire directory, and all duplicates in that directory will be removed, recursively, and any empty directories it creates will be deleted.

You can also have it "auto mark" all but one of each file.  It would be best if you could choose the criteria, though, like "all but the oldest".


FSlint does all of the above since version 2.18.
Well all except auto remove empty directories.
That is a separate function within FSlint, but
probably would be a good idea to incorporate
into the duplicate removal functionality. Thanks.

---

### Post by Endolith on 2007-12-16
> FSlint does all of the above since version 2.18.

Really?  I just installed 2.25 and I still don't see any way to auto-mark all files in a directory.

I just now noticed the "mark within groups" in the right-click menu, though.  That takes care of the "auto-mark" functionality, and goes a step above by letting you choose how it selects.  :-)

Where is the documentation? All I see on the website is a compilation FAQ.

Also I don't know how to find an "About.." box to be sure I'm running the current version.

> Well all except auto remove empty directories.
That is a separate function within FSlint, but
probably would be a good idea to incorporate
into the duplicate removal functionality. Thanks.

Ah.  Well sometimes you might only want to delete the empty directories it leaves behind, and not ones that were already there.

Other things the Windows program ha...



Oh wait!  You did see my previous requests, and implemented some of them!  :-D  

[http://groups.google.com/group/pixelbeat/browse_thread/thread/6e64445a01ff0452/72184b15047cc4ec](http://groups.google.com/group/pixelbeat/browse_thread/thread/6e64445a01ff0452/72184b15047cc4ec)
[http://codebrowse.launchpad.net/~vcs-imports/fslint/trunk/revision/111](http://codebrowse.launchpad.net/~vcs-imports/fslint/trunk/revision/111)

Let me try some things...

---

### Post by Endolith on 2007-12-16
Things that are done:[LIST][*]Already could select all but one in each group from the right-click menu, including the ability to select oldest or newest for keeping.
[*]Delete with *Delete* key.
[*]After you've deleted all but one instance of a particular file, it's removed from the list to let you focus on the others
[/LIST]

Maybe done:
[LIST]
[*]Apparently selecting by directory is supported by wildcards, but I can't figure out how to use wildcards.  I right-click, "Select using wildcard", type part of the path or filename, and nothing happens.  In the program I am used to, you can delete all the dupes in a certain directory at once with a directory chooser dialog, which lets you filter out files which have changed between two copies of a directory, merge directories that have a lot of the same files, but aren't the same, etc.  Wildcards would probably be better, but I can't get it to work.
[/LIST]

Things that could still be done:
[LIST]
[*]"Groups" are more obvious because they're separated by color.  Even just making the "4 x 351,863  (1,069,056)" group headers a different color or adding a dark line to separate groups would work.
[*]Progress bar as it's scanning, with results displayed as it finds them, so you can stop partially through if you've found a particular file you were looking for.  I think it scans by biggest files, first, too, so if you are just trying to clear some space you can stop after it finds two or three giant files.
[*] It warns you if you (accidentally) mark every copy of a file for deletion, which is not the same as warning before *all* deletions.  With wildcards this might be easier to do accidentally, too.  Could show this by coloring the selection red perhaps?  And popping up an "are you sure" box when you try to delete an entire group?
[*]Can delete directories that become empty during the removal process, as above.
[*]Can right-click on a directory in Windows Explorer and click "Find duplicates" and it opens with that directory as the default.  Would be great if it could be integrated into Nautilus/etc this way.
[*]Should be able to "fold up" or remove groups that you don't want to look at, like when it finds 500+ 1-byte files in my Google Earth directory, and I want to skip past them easily.

[*]Column headers stretch to fit filenames and directories, even when they're super long.  I can resize them, but after deleting one thing, they pop back to the super-wide widths.
[*]Just cuts off the ends of paths and filenames when columns are too narrow.  The best way to show a long path in a confined space is to cut out the middle: "/home/username/Pictu...ation/Filename.jpg"
[/LIST]

I was also expecting it to be able to access things from my ssh:// and smb:// bookmarks, and to move things to the trash instead of deleting them, but I guess those are really GNOME things, and this isn't a GNOME app?

Thanks for this program!

---

### Post by pixelbeat on 2007-12-17
> **Endolith said:**
> Things that are done:[LIST][*]Already could select all but one in each group from the right-click menu, including the ability to select oldest or newest for keeping.
[*]Delete with *Delete* key.
[*]After you've deleted all but one instance of a particular file, it's removed from the list to let you focus on the others
[/LIST]

Thanks for testing all this!

> **Endolith said:**
> 
Maybe done:
[LIST]
[*]Apparently selecting by directory is supported by wildcards, but I can't figure out how to use wildcards.  I right-click, "Select using wildcard", type part of the path or filename, and nothing happens.  In the program I am used to, you can delete all the dupes in a certain directory at once with a directory chooser dialog, which lets you filter out files which have changed between two copies of a directory, merge directories that have a lot of the same files, but aren't the same, etc.  Wildcards would probably be better, but I can't get it to work.
[/LIST]


To select a directory use: /full/path/*
To select a file type use: *.tmp
To select common sub dirs use: */tmp/*

> **Endolith said:**
> 
Things that could still be done:
[*]"Groups" are more obvious because they're separated by color.  Even just making the "4 x 351,863  (1,069,056)" group headers a different color or adding a dark line to separate groups would work.


The group headers should be a different colour (specifically the same
colour as the app backgound). Perhaps if you have a non standard theme
this is a problem. I'll look into making it more obvious.

> **Endolith said:**
> 
[*]Progress bar as it's scanning, with results displayed as it finds them, so you can stop partially through if you've found a particular file you were looking for.  


If you know what your looking for you should have more specific paths to scan. Adding results incrementally would require a complete rewrite of
the logic underneath.

> **Endolith said:**
> 
I think it scans by biggest files, first, too, so if you are just trying to clear some space you can stop after it finds two or three giant files.


It actually tries to scan the disk in the order files are laid out on the disk,
to minimise disk head seeking. This is a big performance win in general.

> **Endolith said:**
> 
[*] It warns you if you (accidentally) mark every copy of a file for deletion, which is not the same as warning before *all* deletions.  With wildcards this might be easier to do accidentally, too.  Could show this by coloring the selection red perhaps?  And popping up an "are you sure" box when you try to delete an entire group?


It does warn for the first deletion, or for "all in group" deletions.
I think this is OK.

> **Endolith said:**
> 
[*]Can delete directories that become empty during the removal process, as above.
[*]Can right-click on a directory in Windows Explorer and click "Find duplicates" and it opens with that directory as the default.  Would be great if it could be integrated into Nautilus/etc this way.
[*]Should be able to "fold up" or remove groups that you don't want to look at, like when it finds 500+ 1-byte files in my Google Earth directory, and I want to skip past them easily.
[*]Column headers stretch to fit filenames and directories, even when they're super long.  I can resize them, but after deleting one thing, they pop back to the super-wide widths.
[*]Just cuts off the ends of paths and filenames when columns are too narrow.  The best way to show a long path in a confined space is to cut out the middle: "/home/username/Pictu...ation/Filename.jpg"


All very good points which I will try and incorporate in the next version.

> **Endolith said:**
> 
I was also expecting it to be able to access things from my ssh:// and smb:// bookmarks, and to move things to the trash instead of deleting them, but I guess those are really GNOME things, and this isn't a GNOME app?


Yes it's not a gnome app. Also there may be logical/performance issues
for doing this over the network. I will keep this in mind though.

thank you!

---

### Post by Endolith on 2007-12-18
> **pixelbeat said:**
> To select a directory use: /full/path/*
To select a file type use: *.tmp
To select common sub dirs use: */tmp/*

OH!  That works.  I didn't know it was expecting asterisks.

To save time, if you right-click a file, and select "Select using wildcard", it should pre-fill the text entry box with the filename you clicked on, so you can delete the parts you don't want and replace them with stars.

> The group headers should be a different colour (specifically the same
colour as the app backgound). Perhaps if you have a non standard theme
this is a problem. I'll look into making it more obvious.

I just switched between all the GNOME themes and the colors didn't change.  Both the filenames and group headers are black on white.  Maybe I'm missing something.

> Adding results incrementally would require a complete rewrite of
the logic underneath.

It actually tries to scan the disk in the order files are laid out on the disk,
to minimise disk head seeking. This is a big performance win in general.

Ok.  Just comparing to the Windows program.  Neither is a big deal.

> It does warn for the first deletion, or for "all in group" deletions.
I think this is OK.

Well, the warning is really needed when the program might do something unexpected, like if you accidentally select all of one file and don't leave any copies of it on the drive, or if you mean to select three things with a wildcard and accidentally select two others as well and delete something you weren't aware of.  If you just warn before every deletion, the person is just going to click Yes mindlessly every time.

---

