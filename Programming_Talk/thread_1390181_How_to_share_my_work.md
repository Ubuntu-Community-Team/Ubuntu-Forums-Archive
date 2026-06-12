---
title: "How to share my work"
date: 2010-01-25
forum: Programming Talk
---

### Post by zyberwoof on 2010-01-25
I got tired of not being able to move my 1-5 star rated music from Windows Media Player to any Linux apps, so I am writing my own code to do it.

I wrote a small C++ utility that is able to get/set ratings that are stored in the ID3 tag of an MP3 file.  I also wrote a script that lets you specify a directory, and it recursively finds all MP3 files and runs the C++ utility.  Right now it just makes it so that the ratings from WMP show up in Songbird.

I got it to work on my system (Ubuntu Karmic x64).  Now I'd like to share what I've done so that it may help others.

How should I go about doing this?
- Will my compiled code work on other systems, including 32 bit OS's?  
- Should I even bother distributing the binary, or just ask others to compile it?
- Do I need to license what I have done, or just post it?
- My project uses [libid3]("http://id3lib.sourceforge.net/").  It is listed on SourcForge as "GNU Library or Lesser General Public License (LGPL)".  Does that complicate things any?

**My environment**
Ubuntu 9.10 (Karmic) amd64
gcc version 4.2.4

**Dependencies for compiling**  *Both installed from apt.*
libid3-3.8.3c2a
libid3-3.8.3-dev

---

### Post by MaindotC on 2010-01-25
You should open up a project on [Sourceforge](http://www.sourceforge.net).  You get a free project page, chat room, servers to upload your code, svn, all that stuff.

---

### Post by matmatmat on 2010-01-25
LGPL isn't an issue with launchpad, and most projects release code that needs to be compiled or you could make an autopackage or deb (for Linux users)?

[Launchpad]("https://launchpad.net/")

---

