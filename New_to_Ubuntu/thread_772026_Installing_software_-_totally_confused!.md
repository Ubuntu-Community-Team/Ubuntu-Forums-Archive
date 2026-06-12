---
title: "Installing software - totally confused!"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by chrisp9au on 2008-04-28
Hi, brand new to Linux and Ubuntu, managed to sort out the Grub boot sequence issue last night. Tonight I thought I would install a game.

So I downloaded a game called Tux Racer, 2 files required, stored them on the desktop and extracted them to folders on the desktop. Next I read the INSTALL file, and get the biggest load of gobbledegook I've ever seen!

Now in windows, I unzip a file, click on the setup.exe file, and follow the prompts, if any. Then fire up the program. That does not appear to be the case with Linux! 

The following instructions describe the "Basic Installation" for a simple game...

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Basic Installation
==================

   These are generic installation instructions.

   The `configure' shell script attempts to guess correct values for
various system-dependent variables used during compilation.  It uses
those values to create a `Makefile' in each directory of the package.
It may also create one or more `.h' files containing system-dependent
definitions.  Finally, it creates a shell script `config.status' that
you can run in the future to recreate the current configuration, a file
`config.cache' that saves the results of its tests to speed up
reconfiguring, and a file `config.log' containing compiler output
(useful mainly for debugging `configure').

   If you need to do unusual things to compile the package, please try
to figure out how `configure' could check whether to do them, and mail
diffs or instructions to the address given in the `README' so they can
be considered for the next release.  If at some point `config.cache'
contains results you don't want to keep, you may remove or edit it.

   The file `configure.in' is used to create `configure' by a program
called `autoconf'.  You only need `configure.in' if you want to change
it or regenerate `configure' using a newer version of `autoconf'.

The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation.

  5. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  To also remove the
     files that `configure' created (so you can compile the package for
     a different kind of computer), type `make distclean'.  There is
     also a `make maintainer-clean' target, but that is intended mainly
     for the package's developers.  If you use it, you may have to get
     all sorts of other programs in order to regenerate files that came
     with the distribution.

Compilers and Options
=====================

   Some systems require unusual options for compilation or linking that
the `configure' script does not know about.  You can give `configure'
initial values for variables by setting them in the environment.  Using
a Bourne-compatible shell, you can do that on the command line like
this:
     CC=c89 CFLAGS=-O2 LIBS=-lposix ./configure

Or on systems that have the `env' program, you can do it like this:
     env CPPFLAGS=-I/usr/local/include LDFLAGS=-s ./configure

Compiling For Multiple Architectures
====================================

   You can compile the package for more than one kind of computer at the
same time, by placing the object files for each architecture in their
own directory.  To do this, you must use a version of `make' that
supports the `VPATH' variable, such as GNU `make'.  `cd' to the
directory where you want the object files and executables to go and run
the `configure' script.  `configure' automatically checks for the
source code in the directory that `configure' is in and in `..'.

   If you have to use a `make' that does not supports the `VPATH'
variable, you have to compile the package for one architecture at a time
in the source code directory.  After you have installed the package for
one architecture, use `make distclean' before reconfiguring for another
architecture.

Installation Names
==================

   By default, `make install' will install the package's files in
`/usr/local/bin', `/usr/local/man', etc.  You can specify an
installation prefix other than `/usr/local' by giving `configure' the
option `--prefix=PATH'.

   You can specify separate installation prefixes for
architecture-specific files and architecture-independent files.  If you
give `configure' the option `--exec-prefix=PATH', the package will use
PATH as the prefix for installing programs and libraries.
Documentation and other data files will still use the regular prefix.

   In addition, if you use an unusual directory layout you can give
options like `--bindir=PATH' to specify different values for particular
kinds of files.  Run `configure --help' for a list of the directories
you can set and what kinds of files go in them.

   If the package supports it, you can cause programs to be installed
with an extra prefix or suffix on their names by giving `configure' the
option `--program-prefix=PREFIX' or `--program-suffix=SUFFIX'.

Optional Features
=================

   Some packages pay attention to `--enable-FEATURE' options to
`configure', where FEATURE indicates an optional part of the package.
They may also pay attention to `--with-PACKAGE' options, where PACKAGE
is something like `gnu-as' or `x' (for the X Window System).  The
`README' should mention any `--enable-' and `--with-' options that the
package recognizes.

   For packages that use the X Window System, `configure' can usually
find the X include and library files automatically, but if it doesn't,
you can use the `configure' options `--x-includes=DIR' and
`--x-libraries=DIR' to specify their locations.

Specifying the System Type
==========================

   There may be some features `configure' can not figure out
automatically, but needs to determine by the type of host the package
will run on.  Usually `configure' can figure that out, but if it prints
a message saying it can not guess the host type, give it the
`--host=TYPE' option.  TYPE can either be a short name for the system
type, such as `sun4', or a canonical name with three fields:
     CPU-COMPANY-SYSTEM

See the file `config.sub' for the possible values of each field.  If
`config.sub' isn't included in this package, then this package doesn't
need to know the host type.

   If you are building compiler tools for cross-compiling, you can also
use the `--target=TYPE' option to select the type of system they will
produce code for and the `--build=TYPE' option to select the type of
system on which you are compiling the package.

Sharing Defaults
================

   If you want to set default values for `configure' scripts to share,
you can create a site shell script called `config.site' that gives
default values for variables like `CC', `cache_file', and `prefix'.
`configure' looks for `PREFIX/share/config.site' if it exists, then
`PREFIX/etc/config.site' if it exists.  Or, you can set the
`CONFIG_SITE' environment variable to the location of the site script.
A warning: not all `configure' scripts look for a site script.

Operation Controls
==================

   `configure' recognizes the following options to control how it
operates.

`--cache-file=FILE'
     Use and save the results of the tests in FILE instead of
     `./config.cache'.  Set FILE to `/dev/null' to disable caching, for
     debugging `configure'.

`--help'
     Print a summary of the options to `configure', and exit.

`--quiet'
`--silent'
`-q'
     Do not print messages saying which checks are being made.  To
     suppress all normal output, redirect it to `/dev/null' (any error
     messages will still be shown).

`--srcdir=DIR'
     Look for the package's source code in directory DIR.  Usually
     `configure' can determine that directory automatically.

`--version'
     Print the version of Autoconf used to generate the `configure'
     script, and exit.

`configure' also accepts some other, not widely useful, options.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

How is a newcomer to make sense of this sort of stuff? Life wasn't meant to be this hard surely?
:(
I don't want to do 'unusual things', I don't want to compile or configure anything, I want to install the b****y game so I can play!

Please tell me there is a simple straight forward way of doing this?

Thanks

Chris

---

### Post by encompass on 2008-04-28
nope, your doing it the "old" windows way...
in linux... 99 percent of what you need is located in applications add remove... you can search for the application there.
Other places you can go to do the same exact install are synaptic package manager, found in settings... administration... 
Did you find those programs?  If so, just click search and type in part of what your searching for... like racer.  It shoudl popup... from there you click apply and it downlaods, sets up, and installs it all for you... you don't even have to go to the programs website.  cool huh?

---

### Post by vishzilla on 2008-04-28
Fire up the terminal and enter this command ```
sudo apt-get install extremetuxracer
``` and after installation go to Appications>Games
Its a game based on Tux Racer
Enjoy

---

### Post by Google Spider on 2008-04-28
System>Administrator>Synaptic

I searched for 'tux' and found lots of things. I think what you want is called 'extremetuxracer' (or something on similar lines) in synaptic. Mark it for installation and click apply.

EDIT: Beaten

---

### Post by Michael.Godawski on 2008-04-28
Also check my small installation guide. I will update it soon and add more ways to install stuff, but for now it should suffice for your needs:

[http://godawski.piranho.de/installingapps.html](http://godawski.piranho.de/installingapps.html)

---

### Post by chrisp9au on 2008-04-28
Hi encompass,
Thanks, I found the Synaptic Package Manager but it's not really intuitive is it! Seems to be working, re-downloading files that I've already downloaded! I guess this is ok, but when I'm browsing the internet and see something interesting, files to download etc. do I download the file? or do I have to go to the Synaptic Package Manager? That takes all the fun out of browsing!
Chris

---

### Post by 3rdalbum on 2008-04-28
If you must search the web for software, try to find a .deb (Debian) package, or at least a pre-compiled binary. At your stage of Linux use, you should avoid compiling from source code.

Synaptic is not re-downloading files that you've already downloaded. You've downloaded the source code for the program. This is what developers use to modify the program, but it requires compiling in order to actually run. Synaptic is downloading a pre-compiled version of the program, which cannot be modified, but is ready to use.

BTW, I find it perfectly intuitive that you add new applications to your system by going to "Add/Remove Applications" in the Applications menu :-)

---

### Post by ByteJuggler on 2008-04-28
> **chrisp9au said:**
> Hi encompass,
Thanks, I found the Synaptic Package Manager but it's not really intuitive is it! Seems to be working, re-downloading files that I've already downloaded! I guess this is ok, but when I'm browsing the internet and see something interesting, files to download etc. do I download the file? or do I have to go to the Synaptic Package Manager? That takes all the fun out of browsing!
Chris

Once you've become a little familiarised with it you'll probably find it suddenly is intuitive... :)

Linux is not Windows, it's packages are not managed/distributed like Windows applications.  This has upsides as well as downsides, but IMHO the upsides far outweigh the downsides.  For most people, having a strong package management system that can automatically deal with dependencies and that they can query and ask to automatically install software specifically for their system by far outweighs the alledged benefits of a "piecemeal" style system where you manually install packages ala Windows.   

Anyway, there's basically 3 ways of installing software on Ubuntu:
1.) Using the package management system (Synaptic etc.) By far the best option if possible.
2.) Download a .deb Debian package and install with GDebi (right click, "open" will offer to open with GDebi, or indeed double click.)  This usually works (but rarely not.) 
3.) Download the source code for the application and compile/build from scratch.  Not normally something end user would be interested in, you need to have some technical/programmer knowledge/understanding to use this installation method.

Get used to finding stuff that seems interesting using your browser, and then switching to the package management system to see if an Ubuntu package of it is available.  If there isn't, then see if you can download .Deb, and if you're still out of luck, post here or try your luck with the source code.

---

### Post by hyper_ch on 2008-04-28
you shouldhave a read here:  [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by chrisp9au on 2008-04-28
Hi 3rdalbum,
Thanks, I get the picture. I also feel it is intuitive to go to add/remove, but only when I know what and where the file might be! In add/remove the search option only seems to search the PC, the Synaptic Package Manager seems to search the internet. So I've put the SPM icon on my desktop and will go from there.
Thanks again!
Chris

---

### Post by chrisp9au on 2008-04-28
Hi again hyper_ch, thanks for the link!

---

### Post by ByteJuggler on 2008-04-28
> **chrisp9au said:**
>  In add/remove the search option only seems to search the PC, the Synaptic Package Manager seems to search the internet. 

Correction:  Both Add/Remove and Synaptic ties into the underlying package management system, which will search all defined repositories (e.g. including the internet ones and/or CD/DVD if enabled.)

---

### Post by linuxlizard on 2008-04-28
yeah- applications- add/remove is much more organized for beginners than synaptic. Everything is in nice neat little categories- you can find lots of games there and install with 2 clicks. Much easier than surfing the web, downloading to desktop and installing.
It doesn't prevent you from browsing the web for software- but just remember that if you find something on the web, go back and check synaptic (use the search feature) and see if it's already in there.

Another good source of software is getdeb.net on the web. Lots of nice software like games. You will just click on the deb file on the page and you can install like that.

---

### Post by ryanhaigh on 2008-04-28
In add remove I think you need to change it to all available software (universe/multiverse) from all supported software (main) to search all the repos.

---

### Post by thorgal on 2008-04-28
what you put in your 1st post is the "standard" installation procedure from SOURCE, i.e. if you want to compile the program yourself.

Note that this standard installation file has been floating around for a long time in source packages. Sometimes, source package maintainers provide their own installation instructions for compiling and installing system-wide. But many software devs include the file you posted here because their compilation / installation procedure follows the automake standards :

./configure 
make
sudo make install

configrue can take some compilation options (e.g. where to install the software, what C flags should be added, etc. ./configure --help provides all compilation options)

SO unless you are interested in compiling your own software, all this is irrelevant. As mentioned by others before me, just use a package manager (synaptic for a GTK GUI, adept for KDE, aptitude for console mode or simply apt-get and relatives for one command line execution in a terminal).  

On a parallel note, you can also use these package managers to build your own software if the prebuilt version does not come with certain options builtin (e.g. for a long time, mplayer did not come compiled with jack outputs and you had to compile mplayer yourself). The sequence in that case is :

apt-get build-dep whatever-package-you-want-to-build
apt-get source whatever-package-you-want-to-build
cd /usr/src/whatever-package-you-want-to-build
./configure 
make
make install


As far as I know, it is not as straightforward to do the same in windows, if you want to compile your own software (the source should be available somewhere and you need a dev platform to compile it). In linux, you have all these possibilities and more standardized in a very neat way. One just has to get used to it, not thinking windows ;)

---

### Post by forrestcupp on 2008-04-28
Installing software in Linux is kind of like going to [www.download.com](www.download.com) to find all of your Windows software.  Ubuntu has its own software repositories with tens of thousands of various types of apps and games that you can download all from one source.  Instead of browsing the web, downloading the files and installing them yourself, you just need to browse either Add/Remove Applications or Synaptic, then let it do all the downloading and installing for you.  

Add/Remove and Synaptic are two different kinds of programs that are GUI frontends to install things from the repositories.  They neatly categorize everything for you and give you descriptions of the apps.  You can even search for keywords to find exactly what you want quickly.  It is a *very* intuitive way of doing things, much more so than the Windows way.  If the application's descriptions aren't enough, then you can look it up on the web to find out about it and come back to Add/Remove to install it easily.

Like others said, you will find much more software if you enable the Universe and Multiverse repositories.  These just add a lot more software that isn't officially supported by Ubuntu, but they are created to work well with it.  To add these repos, go to System->Administration->Software Sources and in the 'Ubuntu Software' tab make sure all the boxes are checked.

---

### Post by Ichido on 2008-04-28
I've used Synaptic Pkg Mgr to download and install but, where are they?
Playmidi, Gutsy-wallpapers, Nautilus, et al.
They are not in any of the 'Pull-down' Menus, so where are they?

A different question: How do I "Thank" those who have helped me?

---

### Post by ryanhaigh on 2008-04-28
Whether man application appears in the menu or not depends on what type of application it is. For example gutsy-wallpapers won't appear in the menu but if you right click on the desktop and go to change wallpaper there will be more options. Nautilus is the file manager included by default with ubuntu, I'm guessing what you would have installed would be an extension to nautilus, depending on what that extension was it might appear in the right click menu of your files. As for playmidi considering that it has a terminal and x interface it probably should have appeared in the menu. Sometimes applications don't, I think they have to make themeselves and (I have found this more common  with older apps) some dont. If you install something like vlc you will see an entry created in the sound and video sub-menu.

EDIT: to thank people press the little medal/star with the ribbon ub the bottom left of the posts with the quote and quickreply buttons.

---

### Post by Ichido on 2008-04-29
I tried reinstalling playmidi, still no good.
I want to play my *.rmi music files, any suggestions?
My Nautilus will not Move/Copy/Delete my files that came from my old Linux (Linspire/Freespire/Kubuntu) PC.
I tried Gnome Commander and GREAT!
It looks and works just like my old Norton Commander v.4 from M$-DOS v.5 & Windo$e 3.1:)
Thank God those days are dead & Gone:KS
My Gutsy-wallpapers don't show up anywhere.
Timity, Freepats & Keyring Manager also don't show anywhere.
Any ideas for subs for the above programs?
I'm new to Ubuntu, but I like it a lot!
Again, thanks for your help.

---

### Post by ryanhaigh on 2008-04-29
Not being able to move files from you old system is probably a permissions issue rather than a fault in nautilus. You could open nautilus using alt-f2 then gksudo nautilus to run it in root/admin mode, you can then change ownership and permissions on the files so that your normal user can access/move them. As always when doing something as root BE CAREFUL!.

If you check the available desktop backrounds by right clicking on desktop as mentioned above and see this [http://tombuntu.com/wp-content/uploads/2007/09/brownfluidwallpaper.jpg](http://tombuntu.com/wp-content/uploads/2007/09/brownfluidwallpaper.jpg) as an option then it is installed correctly. For more wallpapers you might want to check out gnome-look.org

I have never use playmidi but you may want to check the man page for it, open system>help and support and enter man playmidi. This screenshot seems to indicate it is console only [http://sourceforge.net/project/screenshots.php?group_id=8478](http://sourceforge.net/project/screenshots.php?group_id=8478)

Timidity (i think thats what you meant) according to this page [http://timidity.sourceforge.net/screenshots.html](http://timidity.sourceforge.net/screenshots.html) can be started with a gui via timidity -ia, again check the man page

This may be useful to you although it could be outdated [https://help.ubuntu.com/community/Midi/SoftwareSynthesisHowTo](https://help.ubuntu.com/community/Midi/SoftwareSynthesisHowTo)

Keyring manager I think adds a menu item under preferences called encryption preferences although I am unsure about this.

You seem to have the worst luck with these programs not creating menu entries.

Just did a quick search for rmi and midi in synaptic and the following came up:
aconnectgui
ardour
midish
playmidi
qtractor
shaketracker
timidity
You might want to look at their descriptions to see if they will be useful to you if you cant get the others going.

---

### Post by ryanhaigh on 2008-04-29
double post, this has been happening quite often, issue with the new forums or my dodgy net connection i wonder

---

### Post by forrestcupp on 2008-04-29
Well, you really should post your new questions in a new thread because they are a totally different topic.

But timidity is a command line program, which is why you can't find it in your menus.  It's made to run from the terminal where you **cd** into the directory and type
```
timidity *filename*
```You can find out what switches to use to control it by typing
```
man timidity
```
You can also find the midi file in your file browser and right click the file and choose 'Open with Other Application' and in the 'Use a custom command' spot, type **timidity**.  Then you can double click the file and hear it, but you will have absolutely no control over it, and there is nothing visible on the screen to show that the program is running.

Edit:
Thanks ryanhaigh.  I didn't know about **timidity -ia** for a GUI.  Cool.

---

### Post by ryanhaigh on 2008-04-29
Would using gnome-terminal -x timidity work for openning the midi files and terminal for control, I have never tried anything like this but I would assume the file is passed as the last arguement to the command.

---

### Post by forrestcupp on 2008-04-29
> **ryanhaigh said:**
> Would using gnome-terminal -x timidity work for openning the midi files and terminal for control, I have never tried anything like this but I would assume the file is passed as the last arguement to the command.

After what you revealed, I went into Nautilus and set the 'Open with' for midi files with the command **timidity -ta**.  Now double clicking the midi file opens the file in the GUI for timidity.

---

