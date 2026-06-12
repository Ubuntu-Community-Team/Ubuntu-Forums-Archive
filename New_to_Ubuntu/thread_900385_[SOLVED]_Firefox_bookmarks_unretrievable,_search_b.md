---
title: "[SOLVED] Firefox bookmarks unretrievable, search box broken"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-08-25
For the last few days, I cannot retrieve any bookmarks from Firefox's Google Toolbar. More, the search box to the right of the URL is dead. I can type text into it, but it isn't active. I tried aptitude to remove/install Firefox, but that didn't help.

More, I'm getting a tiny box, yellow in color, below the mouse cursor wherever it is on the screen. I think that used to be the place where words describing whatever the cursor had "rolled over" had been, but now it's gone.

I have not modified any parts of the OS or installed packages before this started.

Anybody know about this?

---

### Post by Thelasko on 2008-08-25
Likely a problem with the configuration files in your /home directory.  The quick and dirty fix is to close Firefox, rename the folder /home/username/.mozilla (it's hidden, press CTRL+H to unhide in nautilus) to something else, and reopen Firefox.

**[SIZE="3"]What this does:[/SIZE] ** 
Firefox will see none of your user settings and reset itself to its default configuration.  Unfortunately, all of your settings, bookmarks, plugins, etc. will be gone (that's why we renamed the folder instead of deleting it)

**[SIZE="3"]If it works:[/SIZE]**
Then you can either leave it alone, or pick through your old settings folder and restore various settings and bookmarks.  Beware, something in that folder is broken, so don't try to restore the whole folder.
[B][SIZE="3"]
If it doesn't work:[/SIZE][/B]
Restore the old folder so you don't lose your settings and post another message here letting us know it didn't work.

---

### Post by Mark_in_Hollywood on 2008-08-26
As I got only 1 response about this, and as it's really more a Google/Firefox/Toolbar/Bookmarks problem, I googled around the Toolbar and found the answer.

Some software in Ubuntu isn't upgrading properly, but the fix is simple enough. Below is a paste of what I found:

If you're having trouble downloading Google Bookmarks on Ubuntu,
follow these steps originally posted at [http://ubuntuforums.org/showthread.php?t=836750:](http://ubuntuforums.org/showthread.php?t=836750:)

1. In a terminal, type:

sudo apt-get install libxul-dev libstdc++5 gcc-4.1 libstdc++6

2. Uninstall the Toolbar from Firefox by going to "Tools" > "Add-ons"

> select "Google Toolbar for Firefox" and click "Remove."

3. Restart Firefox.

4. Reinstall the Toolbar from the Toolbar homepage at [http://toolbar.google.com/](http://toolbar.google.com/)

Thanks Stephan and jmasondotnet for sharing this fix with the Help
group!

Cheers,

Kiku 

----------

When I did that, I used **aptitude** and the results follow:

mark@Lexington-19:~$ sudo aptitude install libxul-dev libstdc++5 gcc-4.1 libstdc++6 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  libnspr4-dev libnss3-dev 
The following NEW packages will be automatically installed:
  cpp-4.1 gcc-4.1-base libc6-dev libmozjs-dev libmudflap0 libmudflap0-dev 
  linux-libc-dev 
The following NEW packages will be installed:
  cpp-4.1 gcc-4.1 gcc-4.1-base libc6-dev libmozjs-dev libmudflap0 
  libmudflap0-dev libxul-dev linux-libc-dev 
0 packages upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.8MB of archives. After unpacking 52.2MB will be used.
The following packages have unmet dependencies:
  libnss3-dev: Depends: libnss3-1d (< 3.12.0.3-0ubuntu0.8.04.4.1~) but 3.12.1~rc1-0ubuntu1~fta1~hardy is installed.
  libnspr4-dev: Depends: libnspr4-0d (<= 4.7.1+1.9-0ubuntu0.8.04.5.1~) but 4.7.1+1.9-0ubuntu1~fta2~hardy is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
libnspr4-0d [4.7.1+1.9-0ubuntu1~fta2~hardy (now) -> 4.7.1+1.9-0ubuntu0.8.04.5
(hardy-updates)]
libnss3-1d [3.12.1~rc1-0ubuntu1~fta1~hardy (now) -> 3.12.0.3-0ubuntu0.8.04.4
(hardy-updates)]

Score is 110

Accept this solution? [Y/n/q/?] Y
The following NEW packages will be automatically installed:
  cpp-4.1 gcc-4.1-base libc6-dev libmozjs-dev libmudflap0 libmudflap0-dev 
  libnspr4-dev libnss3-dev linux-libc-dev 
The following packages will be DOWNGRADED:
  libnspr4-0d libnss3-1d 
The following NEW packages will be installed:
  cpp-4.1 gcc-4.1 gcc-4.1-base libc6-dev libmozjs-dev libmudflap0 
  libmudflap0-dev libnspr4-dev libnss3-dev libxul-dev linux-libc-dev 
0 packages upgraded, 11 newly installed, 2 downgraded, 0 to remove and 0 not upgraded.
Need to get 11.9MB of archives. After unpacking 52.1MB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main gcc-4.1-base 4.1.2-21ubuntu1 [208kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main cpp-4.1 4.1.2-21ubuntu1 [2331kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main gcc-4.1 4.1.2-21ubuntu1 [583kB]   
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main linux-libc-dev 2.6.24-19.41 [696kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libc6-dev 2.7-10ubuntu3 [3344kB]  
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main libnspr4-0d 4.7.1+1.9-0ubuntu0.8.04.5 [122kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main libnspr4-dev 4.7.1+1.9-0ubuntu0.8.04.5 [258kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe libmozjs-dev 1.8.1.13+nobinonly-0ubuntu1 [194kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe libmudflap0 4.2.3-2ubuntu7 [75.4kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe libmudflap0-dev 4.1.2-21ubuntu1 [21.2kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main libnss3-1d 3.12.0.3-0ubuntu0.8.04.4 [1016kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main libnss3-dev 3.12.0.3-0ubuntu0.8.04.4 [253kB]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe libxul-dev 1.8.1.13+nobinonly-0ubuntu1 [2811kB]
Fetched 11.9MB in 59s (201kB/s)                                                 
Selecting previously deselected package gcc-4.1-base.
(Reading database ... 145004 files and directories currently installed.)
Unpacking gcc-4.1-base (from .../gcc-4.1-base_4.1.2-21ubuntu1_i386.deb) ...
Selecting previously deselected package cpp-4.1.
Unpacking cpp-4.1 (from .../cpp-4.1_4.1.2-21ubuntu1_i386.deb) ...
Selecting previously deselected package gcc-4.1.
Unpacking gcc-4.1 (from .../gcc-4.1_4.1.2-21ubuntu1_i386.deb) ...
Selecting previously deselected package linux-libc-dev.
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.24-19.41_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.7-10ubuntu3_i386.deb) ...
dpkg - warning: downgrading libnspr4-0d from 4.7.1+1.9-0ubuntu1~fta2~hardy to 4.7.1+1.9-0ubuntu0.8.04.5.
Preparing to replace libnspr4-0d 4.7.1+1.9-0ubuntu1~fta2~hardy (using .../libnspr4-0d_4.7.1+1.9-0ubuntu0.8.04.5_i386.deb) ...
Unpacking replacement libnspr4-0d ...
Selecting previously deselected package libnspr4-dev.
Unpacking libnspr4-dev (from .../libnspr4-dev_4.7.1+1.9-0ubuntu0.8.04.5_i386.deb) ...
Selecting previously deselected package libmozjs-dev.
Unpacking libmozjs-dev (from .../libmozjs-dev_1.8.1.13+nobinonly-0ubuntu1_all.deb) ...
Selecting previously deselected package libmudflap0.
Unpacking libmudflap0 (from .../libmudflap0_4.2.3-2ubuntu7_i386.deb) ...
Selecting previously deselected package libmudflap0-dev.
Unpacking libmudflap0-dev (from .../libmudflap0-dev_4.1.2-21ubuntu1_i386.deb) ...
dpkg - warning: downgrading libnss3-1d from 3.12.1~rc1-0ubuntu1~fta1~hardy to 3.12.0.3-0ubuntu0.8.04.4.
Preparing to replace libnss3-1d 3.12.1~rc1-0ubuntu1~fta1~hardy (using .../libnss3-1d_3.12.0.3-0ubuntu0.8.04.4_i386.deb) ...
Unpacking replacement libnss3-1d ...
Selecting previously deselected package libnss3-dev.
Unpacking libnss3-dev (from .../libnss3-dev_3.12.0.3-0ubuntu0.8.04.4_i386.deb) ...
Selecting previously deselected package libxul-dev.
Unpacking libxul-dev (from .../libxul-dev_1.8.1.13+nobinonly-0ubuntu1_all.deb) ...
Setting up gcc-4.1-base (4.1.2-21ubuntu1) ...

Setting up cpp-4.1 (4.1.2-21ubuntu1) ...
Setting up gcc-4.1 (4.1.2-21ubuntu1) ...
Setting up linux-libc-dev (2.6.24-19.41) ...
Setting up libc6-dev (2.7-10ubuntu3) ...
Setting up libnspr4-0d (4.7.1+1.9-0ubuntu0.8.04.5) ...

Setting up libnspr4-dev (4.7.1+1.9-0ubuntu0.8.04.5) ...
Setting up libmozjs-dev (1.8.1.13+nobinonly-0ubuntu1) ...
Setting up libmudflap0 (4.2.3-2ubuntu7) ...

Setting up libmudflap0-dev (4.1.2-21ubuntu1) ...
Setting up libnss3-1d (3.12.0.3-0ubuntu0.8.04.4) ...

Setting up libnss3-dev (3.12.0.3-0ubuntu0.8.04.4) ...
Setting up libxul-dev (1.8.1.13+nobinonly-0ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done 

------------------

When I restarted Firefox, the missing Bookmarks, in their proper folders where all there.

---

### Post by Thelasko on 2008-08-27
Thanks for posting the solution.

---

