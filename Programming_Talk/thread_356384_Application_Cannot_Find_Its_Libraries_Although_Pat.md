---
title: "Application Cannot Find Its Libraries Although Path Searches Set Properly"
date: 2007-02-08
forum: Programming Talk
---

### Post by mavigozler on 2007-02-08
I have looked at a number of posts that report problems with executables finding their (shared) libraries, and I too am having a problem with this.

I have this open source scientific (bioinformatics) package that I downloaded and have been trying to build.  The developer has also included a 'contrib' package which he assembled because it depends on a number of other libraries (BOOST, CGAL, XERCES, NETCDF, etc.), and the developer thought to make them all buildable in one go from a single configure/Makefile.

After building the contrib package, and installing QT3 through Synaptics, I then built the main package:  autoconf, configure with some exceptional options passed to it, make, and then make install.

These processes run with being stopped by errors.

The final step is to do 'make test' to test the build.   But when done, it stops with errors that It cannot find the dynamic link libraries (*.so) built in the contrib package and in the main package, which are kept in lib directories off the $HOME directory.  

LD_LIBRARY_PATH is set, upon the instructions of the package developer, so that the linker can find these libraries, but it doesn't.  The report is "no such file or directory" when looking for the *.so.

Now when I create a symbolic link (ln -s) to the missing libraries (determined by using 'ldd' on the executable to look for dependencies), and I put the link in /usr/lib, it finds the library but cannot open it, reporting "Error 40".  More detail and the output of commands is given in the link below.

This detail includes:[LIST=1]
[*]the setting of the LD_LIBRARY_PATH (done in .bash_profile and then a re-login done) with a report of 'echo $LD_LIBRARY_PATH
[*]the listing ('ls -alF') of the directories containing the libraries reported as 'not found' by 'ldd' on the executables
[*]the output of 'ldd' on the executables in question[/LIST]Before coming here, I had already gone to the developer---who ran out of ideas after 5-6 cycles of email, and then to a couple of Usenet groups.  I have posted this explanation with relevant output to comp.os.linux.development.apps, so if you would be willing to go [_**[COLOR=Blue]here[/COLOR]**_,]("http://groups.google.com.tr/group/comp.os.linux.development.apps/msg/4fd4e12a18f82f4b?&hl=en") you can get more information.

I am stumped.

I returned to using a *nix-based system after a decade (in mid 1990s, I did a lot of C programming on a AT&T SVR4) and in mid 1980s played around with Bourne shell (sh) scripts on a Ultrix system.  So it could be I have forgotten how the build process works.

---

### Post by jblebrun on 2007-02-08
Looking at the exhaustive output you provide in the Usenet posting, this does seem like an evil problem. Have you looked into the Makefile to see exactly what "make test" is doing? The only thing that I can think of is that LD_LIBRARY_PATH is being over-written somehow in the test process, although that seems unlikely. 

Is this package freely available, so that we might try compiling it ourselves? If so, can you provide a link?

---

### Post by mavigozler on 2007-02-08
> **jblebrun said:**
> Looking at the exhaustive output you provide in the Usenet posting, this does seem like an evil problem. Have you looked into the Makefile to see exactly what "make test" is doing? 

**make test** calls a number of executables such as **ClassTest_test** and others.  I am not intimately familiar with details of the developer's code and style, and don't plan to hack it in the early stage of using it.

> **jblebrun said:**
> The only thing that I can think of is that LD_LIBRARY_PATH is being over-written somehow in the test process, although that seems unlikely.

The developer/maintainer probably considered that possibility, although he did not say so in the several email cycles we had in trying to get the build to this point.

> **jblebrun said:**
> Is this package freely available, so that we might try compiling it ourselves? If so, can you provide a link?

Absolutely!  If you took the time to try to build it on your system, that would be cool.

There are two packages to download from the Sourceforge site.  The download section is on this **[page]("http://sourceforge.net/project/showfiles.php?group_id=90558")**  The individual components are:[LIST=1]
[*] OpenMS:  [COLOR=Blue]**[home page]("http://open-ms.sourceforge.net/index.php")**[/COLOR]     [[COLOR=Blue]**download**[/COLOR]]("http://sourceforge.net/project/showfiles.php?group_id=90558&package_id=95251&release_id=480156")
[*][COLOR=Blue][COLOR=Black]Contrib package:  [COLOR=Blue]**[download]("http://sourceforge.net/project/showfiles.php?group_id=90558&package_id=151210&release_id=480158")**[/COLOR][/COLOR]
[/COLOR][/LIST]Although the home page link explains how to do the install (recommended reading), my short form instruction to you or anyone is:
[LIST=1]
[*]unzip/untar the OpenMS
[*]'mv' the OpenMS directory name to 'OpenMS';  it untars as 0penMS-0.95 or something like that, and I usually don't like entering long path names
[*]unzip/untar the contrib package under the OpenMS directory as 'contrib'
[*]build the contrib package first and do any tests it requires
[*]make sure that Qt3 headers and lib are installed:  use whatever you like (apt-get, aptitude, Synaptics)
[*]then build the OpenMS:[LIST]
[*]configure will need the location of includes and libs and will report what's missing.  Usually you will want to specify boost (--with-boost-incl=$HOME/OpenMS/contrib/inclue --with-boost-lib=$HOME/OpenMS/contrib/lib) and the Qt3 locations (probably --with-qt-incl=/usr/include/qt3 --with-qt-lib=/usr/lib) and that it is multi-threaded (--with-qt-mt).   Usually configure wants to see those.
[*]after configure, then make creates the dependencies, goes to the compiling, and builds the shared object library
[*]make install is next
[*]then 'make test':  which is where I was halted[/LIST] [/LIST]A GUI is then built (TOPP) and also tested (TOPPtest).

Good luck.

Once built, I think you run TOPP and then you manipulate mass spectra.  I can send you some spectra and tell you how to manipulate once I learn more about it myself.  One of the features I am interested in is the so-called "Peak Picking" function:  many mass spectra are complicated by the presence of a low signal-to-noise ratio, and it is difficult to pull signal out of that noise.  If this application can "clean up" spectra and help me use it for my purposes (yet to be ascertained), then I can clear out a logjam of data I have and publish this with high confidence.

Right now I am using an apparently "popular" commercial package of bioinformatics software that is a [SIZE=3][COLOR=Red]**NIGHTMARE**[SIZE=2][COLOR=Black] which should never be used or purchased by anyone.  For anyone interested in knowing the name of this software in order to avoid it, [/COLOR][/SIZE][/COLOR][/SIZE][EMAIL="garyconditswellhungrelative@yahoo.com"]email me[/EMAIL][SIZE=3][COLOR=Red][SIZE=2][COLOR=Black].[/COLOR][/SIZE][/COLOR][/SIZE]

---

### Post by mavigozler on 2007-02-10
[SIZE="5"]**WORKAROUND FOUND**[/SIZE]


The workaround, but not the solution, was to cp (copy) the libraries determined to be [COLOR="Red"][SIZE="3"]"not found"[/SIZE][/COLOR] to the **[SIZE="3"]/usr/lib[/SIZE]** directory, rather than struggling to make the link editor find them in the paths defined in LD_LIBRARY_PATH.

The application now works, and it even generated its first unhandled exception (app crash).

For any of you still wishing to find the real solution to the problem and not cotent with seeing this messy workaround, be my guest, and I would appreciate an email from you in case this thread starts to get very dated.


I posted this note on comp.os.linux.development.apps too.

---

