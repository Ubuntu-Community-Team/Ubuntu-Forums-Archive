---
title: "Gscreendump version 0.1 launched."
date: 2008-12-31
forum: Programming Talk
---

### Post by moma on 2008-12-31
Hello and and happy new year to all,

**Important annoucement.**
**************************
I have now released first version (v0.1) of gscreendump.

Gscreendump is a screenshot taking application for the GNOME-desktop environment. Gscreendump can take screenshots of application windows, desktop surface, window items (such as buttons and edit fields) and selected rectangular areas of screen. It can also generate images of webpages (URIs) via the GNOME's gnome-web-photo tool.

Gscreendump can manipulate screenshot images (and other images) via add-ons/plugins. Plugins can be written in Python/Perl/Bash or any other language. Gscreendump supports drag & drop between file manager/desktop and the application.

[[img]http://bildr.no/thumb/314837.jpeg[/img]](http://bildr.no/view/314837)

**Further development:**
***********************
CAN YOU TAKE OVER FURTHER DEVELOPMENT (MAINTAINERSHIP) OF GSCREENDUMP?
This first release will not be bug-free but it shows the concept and strong potensial it has. I hope that other developers in the Linux community can now take over the further development of gscreendump because I will move to another project and will abandon gscreendump totally.

Please send me an email <osmoma@online.no> if you can take over this product. Gscreendump is released under GPL3 license.
----------------

**Current source code:**
***********************
The code is written i c with GDK/GTK+ and Xlib libraries and it is currently hosted on Google's code site at address:
[http://code.google.com/p/gscreendump]("http://code.google.com/p/gscreendump")

Google uses SVN (subversion) as a versioning system. In Ubuntu you should install "subversion" package. The access command is "svn ...". 

New maintainers can of course move the code the Launchpad.net/Bazar if they like it better.

Browse to [http://code.google.com/p/gscreendump]("http://code.google.com/p/gscreendump")
and click on the [source] tab and (svn)download the latest code as instructed.

[COLOR="Green"]mkdir $HOME/svn/[/COLOR]
[COLOR="Green"]cd $HOME/svn/[/COLOR]

# Non-members may check out a read-only working copy anonymously. 
[COLOR="Green"]svn checkout [http://gscreendump.googlecode.com/svn/trunk/](http://gscreendump.googlecode.com/svn/trunk/) gscreendump-read-only [/COLOR]

Then read the README and INSTALL files for further instructions.

[COLOR="Red"]EDIT:[/COLOR] I have updated couple of small things in the configuration + added "imagemagick" as requirement in README and INSTALL files.
Get a update by running
[COLOR="Green"]svn update [/COLOR]
----------

**Ready made Ubuntu packages:**
******************************
There is also a ready-made Ubuntu package for i386 (32bits) Ubuntu 8.10. You can grab it from
[http://code.google.com/p/gscreendump/downloads/](http://code.google.com/p/gscreendump/downloads/)

Install the .deb package by typing (as root or sudo):
[COLOR="Green"]**dpkg -i screendump-<ver>.deb**[/COLOR]

It will probably complain about missing dependencies. 
Run apt-get install -f to fix it (as root or sudo): 
[COLOR="Green"]**apt-get install -f**[/COLOR]

More information on this wiki: [http://code.google.com/p/gscreendump/w/list]("http://code.google.com/p/gscreendump/w/list")  (browse to "Installation" page).

Read also the README, INSTALL and debian/README files if you plan to generate a new debian package.

**About Plugins:**
********************
Plugins extend Gscreendump primarily by adding image manipulation functions.

Plugins are saved either in user's private folder ($HOME/.local/gscreendump/plugins) or in system global directory (/usr/[local/]share/gscreendump/plugins/).

Each plugin must have its own sub directory. And the script and directory names should be same.

I've create two Python-plugins which you can find in /usr/[local/]share/gscreendump/plugins/python/.

[COLOR="Green"]ls -l /usr/share/gscreendump/plugins/python/[/COLOR]
drwxr-xr-x 3 root root 4096 2008-12-31 12:54 sample  <-- A simple Python sample (does nothing really)
drwxr-xr-x 3 root root 4096 2008-12-31 12:54 filter  <-- Image filter and rotate/scale plugin written in PyGTK + PIL.

EDIT: Forgot to mension that GScrot's plugins are mostly compatible with Gscreesnhot. Gscrot is a very similar screenshot tool written in Perl.

**About the imagick module:**
******************************
I've tried to add [ImageMagick...]("http://www.imagemagick.org/script/command-line-options.php") support to this product. 
ImageMagick has some excellent command line tools (convert, mogrify etc.) to manipulate images. 

* The first attempt tries to access ImageMagick via its MagickWand library.
The package name is "libmagick9-dev" (or later) and the library (.so) name is "libWand".
GScreendump uses this library to rotate an image from the "Crop/scale" dialog. The actual rotation function is in sd_imagemagick.[ch] file.

* The second approach is more ambitious. 
It allows users' to create their own input-dialogs and image manipulation commands. The command files (command.lst) can reside either in user's private folder $HOME/.local/gscreendump/commands/command.lst or in the system global directory /usr/[local/]share/gscreendump/commands/command.lst. Imagick module reads both files.

Study the sd_imagick_parser.[ch] and sd_imagick_dialog.[ch] modules. 
I think these code modules may look a a bit complex and bad. They makes use of sd_mlexer.[ch] and sd_mparser.[ch] modules. 
sd_mlexer.c is a generic token parser (lexer) and sd_mparser.c is a math expression parser. 
It can also parse simple string expressions like "string1" + "string2".

All in all it allows users to create new input dialogs and image manipulation commands (everything defined in command.lst files).
For farther info, read /usr/[local/]share/gscreendump/commands/readme.txt and command.lst files.

Good luck.

New maintainers are very much welcomed !

(sorry for bad english, errors and bad code because I live in Oslo, Norway and its a damn cold day ;-)

HAPPY NEW YEAR and THANKS TO ALL,
Sincerely
  Osmo Antero (moma) Mããttã.
  Oslo, Norway.

-- end ---

See also: [http://ubuntuforums.org/showthread.php?t=1022724](http://ubuntuforums.org/showthread.php?t=1022724)

---

### Post by handband2 on 2008-12-31
moma,

Nice project.  I hope to see it compatible for 64-bit systems soon :)

---

### Post by Vadi on 2008-12-31
Only problem I see is that GScrot ([http://gscrot.ubuntu-projekte.de/](http://gscrot.ubuntu-projekte.de/)) already does this and is more mature :|

Edit: What is really needed is a good video capture program for games. [glc]("http://nullkey.ath.cx/projects/glc") is a great tool for this, but has no gui. I've been meaning to create a graphical interface to glc for a while but did not have enough manpower to start a project.

---

### Post by moma on 2009-01-01
> **handband2 said:**
> I hope to see it compatible for 64-bit systems soon :)

Hello,

You can now download a 64bits Ubuntu package from 
**[http://code.google.com/p/gscreendump/]("http://code.google.com/p/gscreendump/")**  (under Downloads page). 
 
Read also installation guide on 
**[http://code.google.com/p/gscreendump/w/list]("http://code.google.com/p/gscreendump/w/list")** (the Installation link).
Currently you must use command line to complete the installation because you need to run: 
sudo apt-get install -f 
after package installation. 
 
[There is also an important warning to developers who both compile gscreendump from source and install it from package.]

Good luck, Gscreendump is at version 0.1 but the concept should work. 
Namely that's what we are - concept programmers.

---

