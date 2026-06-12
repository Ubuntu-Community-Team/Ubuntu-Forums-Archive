---
title: "Windows has &quot;program Files&quot;;  Ubuntu has &quot;?&quot;"
date: 2011-12-16
forum: New to Ubuntu
---

### Post by c28mac on 2011-12-16
** This is day one of my Ubuntu usage, I apologize for my very basic question** 

When I install a program on windows (lets say Firefox) I know a folder will be created under "program files," and this file will give me access to history, cookies, and so on.

When I installed Ubuntu 11.10 today (came with Firefox) I have been looking through "file systems" looking for something similar, and I cannot find an individual file for the programs I install.

Thank you

C

---

### Post by RomeReactor on 2011-12-16
Hi. Open Nautilus (the file manager) and press CTRL+H to show hidden files and folders in your home directory (names of hidden files and folders are prefaced by a dot), then look for **.mozilla**. Most other programs will have their configuration folders similarly hidden in your home folder.

---

### Post by ve4cib on 2011-12-16
Linux, unlike Windows, tends to put application-specific files in different folders; configuration files for all programs will be together, icons together, and executables together.

When you install Firefox the actual executable program will be in /usr/bin (normally -- more on this in a bit).  The Firefox icon will usually be in somewhere like /usr/share/pixmaps or /usr/share/icons/<whatever icon theme you're using>/apps.

Things like history and configuration (user-specific settings) are stored in a hidden "dot-folder" in your home directory.  It's called a dot-folder because it starts with a period.  Firefox's settings are stored in /home/<username>/.mozilla.  You can view hidden folders by hitting "ctrl-h" in Nautilus (the standard Gnome file browser -- this shortcut may also work in other file browsers, I'm not sure), or by using the "-a" flag when using the "ls" command in a terminal.  You'll see that there are LOTS of dot-folders created in your home directory.  This is pretty standard for Linux programs.  Windows has the "%appdata" directory, Linux uses hidden folders in your home directory.  Same effect, just a different way of doing it.

Now, as for the non-user filesystem stuff, executables are pretty much always installed to one of three places:

- /usr/bin (normal executables the user would want to use: firefox, nautilus, banshee, etc...)
- /bin (generally used for system-level executables; shells, standard POSIX command-line tools like ls)
- /usr/local/bin (normally used for non-standard programs you've installed and/or compiled yourself)

Application settings (not user settings, but global settings) are normally in /usr/share or /usr/local/share (again, that "local" bit is normally for things you've installed manually).  Lower-level system settings (for services your computer is running: FTP and SSH are good examples) are typically in /etc.

Now, I'm sure this idea of scattering the different parts of a program all over seems a little weird, since you were obviously expecting everything to be in one place.  Don't worry too much about it; it's a different way of organizing the system, but it's no better or worse than how Windows does it.  Just different.

Hopefully that answers your question somewhat?

---

### Post by papibe on 2011-12-16
Hi c28mac. Welcome to the forums.

Take a look at [this]("https://help.ubuntu.com/community/LinuxFilesystemTreeOverview") overview of the typical Linux file system.

I hope it helps.
Regards.

---

### Post by 3Miro on 2011-12-16
Because programs under Ubuntu share components, thus they are not divided into one folder each, but rather split into logical components.

For example, the executable for firefox is in /usr/bin/firefox, while the icons are in /usr/share/icons. For many of its functions, Firefox uses libraries in /lib or /usr/lib (those are like the .dll files of Windows).

The Firefox Cache and personal settings are located in /home/<your_user_name>/.mozilla

When you go into the file manager, hit Ctr + H to see the "hidden" folders.

---

### Post by matt_symes on 2011-12-16
> It's called a dot-folder because it starts with a [COLOR=Blue]period[/COLOR].A 'full stop' in Britain :)

Nice write up though.

---

### Post by oldos2er on 2011-12-16
Firefox cookies and personal preferences, etc. Are stored in your user's home folder, in a hidden folder .mozilla/firefox.

Linux file system structure is very different from Windows. See [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) and [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/)

You can see where each file in a given package is installed by running ```
dpkg -L firefox
``` for example, in a terminal. Most user-installed executables wind up in /usr/bin

---

### Post by c28mac on 2011-12-16
Thank you everyone for such quick and detailed responses.  I found the files I was seeking, and yes the file system (being scattered) is a lot to get used to.  I obviously have a lot of reading to do on my part.

Thanks again

c

---

### Post by PhilGil on 2011-12-16
As a Windows administrator, it troubled me at first to have less control over where my program files were installed (although having all the user settings in the home folder is brilliant).

As I got used to using Ubuntu, I found that the package (application) management system worked so well that I rarely had to think about program files and where they were installed.

---

### Post by mikewhatever on 2011-12-16
> **c28mac said:**
> ** This is day one of my Ubuntu usage, I apologize for my very basic question** 

When I install a program on windows (lets say Firefox) I know a folder will be created under "program files," and this file will give me access to history, cookies, and so on.

When I installed Ubuntu 11.10 today (came with Firefox) I have been looking through "file systems" looking for something similar, and I cannot find an individual file for the programs I install.

Thank you

C

History and cookies for Firefox in Windows are not stored in Program Files, they should be 'Documents and Settings\Application Data' or similar.

---

### Post by audiomick on 2011-12-16
> **matt_symes said:**
> A 'full stop' in Britain :)

As in Australia, because we speak proper English too. ;)

---

### Post by ve4cib on 2011-12-16
> **audiomick said:**
> As in Australia, because we speak proper English too. ;)

We Canadians generally use proper English (e.g. colo*u*r, and neighbo*u*r), but we live rather close to a very malign influence on our language that occasionally works its way into our vocabulary.

---

### Post by matt_symes on 2011-12-17
Hi

If you install a .deb package you can see where all the files are stored by opening a terminal and typing
 	```

dpkg -L <name of package>
```

Edit: I just noticed that i gave the same advice as oldos2er. This post is pretty redundant. That will teach me to read all the posts in a thread thoroughly in future.

Kind regards

---

### Post by jerome1232 on 2011-12-17
> **audiomick said:**
> As in Australia, because we speak proper English too. ;)

> **matt_symes said:**
> A 'full stop' in Britain :)

Nice write up though.

Are you guys telling me you call a period a full stop?

I think my mind just blew, I live in California, we definitely don't speak proper English, our Spanish is even worse.

---

### Post by matt_symes on 2011-12-17
> **jerome1232 said:**
> Are you guys telling me you call a period a full stop?

I think my mind just blew, I live in California, we definitely don't speak proper English, our Spanish is even worse.

Yes. In parts of the world a period is called a full stop. That's why i mentioned it; just in case others did not know what a period was.

---

### Post by sunfromhere on 2011-12-17
> **matt_symes said:**
> Hi

If you install a .deb package you can see where all the files are stored by opening a terminal and typing

```
dpkg -L <name of package>
```

Kind regards

About this... 
How do I find out the name of the package? F.e. Google Chrome, I tried dpkg -L Chrome, chrome, googlechrome, google_chrome,google-chrome, google-chrome-stable_current_i386 (basically, I took a look at the folders and tried with the names found there), etc and all reported: Package is not installed.

---

### Post by nothingspecial on 2011-12-17
It's chromium-browser

Tip, if you type dpkg -L chr

then press the Tab key a couple of times it will list all the installed packages that start with chr

```
$ dpkg -L chromium-
chromium-browser              chromium-codecs-ffmpeg-extra
chromium-browser-l10n  
```

---

### Post by sunfromhere on 2011-12-17
> **nothingspecial said:**
> It's chromium-browser

Tip, if you type dpkg -L chr

then press the Tab key a couple of times it will list all the installed packages that start with chr

```
$ dpkg -L chromium-
chromium-browser              chromium-codecs-ffmpeg-extra
chromium-browser-l10n  
```

Aha! Thank you.
Basically I just try tab with first three letters I suspect may be in the name and it lists me the options.
Every day I learn something new :D

---

### Post by corncob on 2011-12-17
> **jerome1232 said:**
> Are you guys telling me you call a period a full stop?

I think my mind just blew, I live in California, we definitely don't speak proper English, our Spanish is even worse.

No callo 'period'.  Callo 'dot':P

---

### Post by ve4cib on 2011-12-17
> **sunfromhere said:**
> About this... 
How do I find out the name of the package? F.e. Google Chrome, I tried dpkg -L Chrome, chrome, googlechrome, google_chrome,google-chrome, google-chrome-stable_current_i386 (basically, I took a look at the folders and tried with the names found there), etc and all reported: Package is not installed.

Another option is to use "apt-cache search" to look for packages:

```
$ apt-cache search chrome
libslang2-dev - The S-Lang programming library, development version
libxpm-dev - X11 pixmap library (development headers)
libxpm4 - X11 pixmap library
libxpm4-dbg - X11 pixmap library (debug package)
splix - Driver for Samsung's SPL2 (bw) and SPLc (color) laser printers
xserver-xorg-video-openchrome - X.Org X server -- VIA display driver
dicomscope - The OFFIS DICOM Viewer
epiphany-browser - Intuitive GNOME web browser
libjs-excanvas - HTML5 Canvas for Internet Explorer
libv8-2.5.9.9 - V8 JavaScript Engine
libv8-dbg - Debugging symbols for the V8 JavaScript Engine
libv8-dev - Development files for the V8 JavaScript Engine
linuxlogo - Color ANSI System Logo
minidjvu - Monochrome DjVu multipage encoder, single page encoder/decoder
murrine-themes - themes for gtk2 murrine engine
prboom - clone of the legendary first person shooter Doom
pyjamas-canvas - Pyjamas Python port of GWTCanvas SVG Library
xpat2 - Generic patience game for X11
xserver-xorg-video-via - X.Org X server -- VIA display driver (dummy transitional package)
yabasic - Yet Another BASIC interpreter
picon-domains - Picon (Personal Images) database of for Internet domain logos.
picon-misc - Picon (Personal Images) database of common accounts and misc.
picon-news - Picon (Personal Images) db of Usenet newsgroups and hierarchies
picon-unknown - Picon (Personal Images) database for very high-level domains
picon-usenix - Picon (Personal Images) db of Usenix conference attendees
picon-users - Picon (Personal Images) database of individual Internet accounts
picon-weather - Picon (Personal Images) database for displaying weather forecasts.
chromium-browser - Chromium browser
l-echo - Open source echochrome clone
```

Depending on what you search for you may get one or two packages, or a giant list to sift through.  But it will narrow down the list of options.

---

### Post by oldos2er on 2011-12-17
> **sunfromhere said:**
> About this... 
How do I find out the name of the package? F.e. Google Chrome, I tried dpkg -L Chrome, chrome, googlechrome, google_chrome,google-chrome, google-chrome-stable_current_i386 (basically, I took a look at the folders and tried with the names found there), etc and all reported: Package is not installed.

Yep, only works on installed packages.

If you prefer working with a graphical application, install Synaptic Package Manager. ```
sudo apt-get update && sudo apt-get install synaptic
``` Open Synaptic, in the lower left corner click 'Status', in the upper left corner click 'Installed', right-click on an installed package and click 'Properties', 'Installed Files'.

---

### Post by grahammechanical on 2011-12-17
Commas ( , ) semi-colons ( ; ) and colons ( : ) are also stops but not full stops. Period. :)

Regards.

---

### Post by Paddy Landau on 2011-12-17
When using Linux, unless you want to get technical and create your own programs or mess around with the system, you do not need to know where programs are stored.

To install and deinstall programs, unlike in Windows, you use a *Package Manager*. The Package Manager looks after various dependencies, and remembers where everything is stored. You don't go searching the Internet and downloading programs (well, you do when you get a bit more used to Linux, but for the newbie it's not advised).

There are several programs that interface with the Package Manager, the simplest one in Ubuntu being *Ubuntu Software Centre*.

For the OP, you are a newcomer to Linux. All you need to know about installing and deinstalling programs is this: Start Ubuntu Software Centre; install or deinstall from there.

Full stop. Or period. :)

Oh, one more thing. If you need to reset your program's settings, you do *not* deinstall and reinstall the program. That won't do a thing to your settings. Instead, you find the folder where the settings are stored (e.g. [FONT=Fixedsys]/home/c28mac/.mozilla[/FONT], commonly written as [FONT=Fixedsys]~/.mozilla[/FONT]) and delete that folder.

---

### Post by sunfromhere on 2011-12-17
> **oldos2er said:**
> 
If you prefer working with a graphical application, install Synaptic Package Manager. 

Even though I'm a novice to Ubuntu, I find CLI much more easier and efficient.* So I'm browsing these forums and making my cheat-sheet of useful commands.

*Why uninstalling a program via Software Center removes only the part of it, while purge&autoremove in Terminal uninstall it completely?

---

### Post by Paddy Landau on 2011-12-17
> **sunfromhere said:**
>  *Why uninstalling a program via Software Center removes only the part of it, while purge&autoremove in Terminal uninstall it completely?

[LIST]
[*]Deinstalling via the Software Centre does a straight remove.
[*]Deinstalling via Synaptic Package Manager gives you the option of removing or purging; the latter also removes system-level settings (not user-level settings).
[*]Auto-remove additionally removes automatically installed but redundant packages that are no longer needed by anything; this is not necessarily the case when you deinstall a program, as subsequent installations of other programs may use those packages.
[/LIST]

---

### Post by boast on 2011-12-17
> **grahammechanical said:**
> Commas ( , ) semi-colons ( ; ) and colons ( : ) are also stops but not full stops. Period. :)

Regards.

so commas are called 'slow downs,' or more of a 'rolling stop' ?

---

