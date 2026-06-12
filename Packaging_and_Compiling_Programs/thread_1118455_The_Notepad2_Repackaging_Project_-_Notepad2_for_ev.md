---
title: "The Notepad2 Repackaging Project - Notepad2 for every OS!"
date: 2009-04-07
forum: Packaging and Compiling Programs
---

### Post by Panarchy on 2009-04-07
Hello

I always find it easier to learn when there is an obtainable goal waiting for me at the end.

So for my project, I have decided to package [Notepad2]("http://www.flos-freeware.ch/notepad2.html"). 

Pretty sure it is GPL, so I shouldn't run into any licensing issues.

I will be packaging [Notepad2]("http://www.flos-freeware.ch/notepad2.html") into the following file formats;

**EXE** - _Windows_

**MSI** - _Windows_

**RPM** - _Linux_ (RedHat Package Manager)

**DEB** - _Linux_ (Debian Based)

**TGZ** - _FreeBSD_

**PKG** - _Mac OS X_

I'm open to suggestions, please just post 'em, even if you'd just like to wish me luck!

Thanks in advance,

Panarchy

PS: I will constantly update this topic after each successful packaging. 

PPS: For Linux, FreeBSD and Mac OS X, I will include WINE (as dependency needed...)

---

### Post by GTengineer on 2009-04-08
Looking forward to it. I had not heard of notepad2 but I am now very interested after reading up more on it. Good luck.

---

### Post by Panarchy on 2009-04-08
Thanks

---

### Post by Panarchy on 2009-04-13
Hello

This is a little taste of what to expect (Currently only supports XP/2003);
[http://www.mediafire.com/download.php?t2wmyjn1otj](http://www.mediafire.com/download.php?t2wmyjn1otj)

Still to add/include;

- ALL default NSIS images replaced with ones related to Notepad/Notepad2
- Information about what the setup is going to do
- Support for Vista/2008/Windows 7
- fixes for any problems reported!!!

Hope you like the installer!

Panarchy

PS: Also been working on the universal Debian/Ubuntu installer... coming shortly, have work starting tomorrow, so I may not get a chance till the weekend.

---

### Post by mc4man on 2009-04-14
For the wine version are you going to include a Notepad2 wine wrapper script? (maybe notepad2 is better name for wrapper

---

### Post by Panarchy on 2009-04-14
Hello

By wrapper do you mean dependencies needed?

As I was already planning on including that...

Panarchy

---

### Post by mc4man on 2009-04-14
> do you mean dependencies needed?

No, but it would probably be easier to do after install.

Any .exe that's a 'standalone' .exe can be installed (or in some cases moved there after install) into the windows folder.  Then by adding the wine wrapper script with the name of the .exe to a bin dir. in the path (/usr/bin, /usr/local/bin, ect.) the start command simply is the name (no wine 'path to .exe' needed

Wine does that with notepad.exe and regedit.exe, both of which have the wrapper script in /usr/bin (named notepad and regedit respectively

That's why the command to start notepad is simply <notepad>

So for instance with your notepad2.exe if it didn't install to the windows dir. I'd move it there, make a copy of the wrapper script, name it notepad2, and drop it into /usr/bin
(actually because I have a ~/bin I'd put it there, same difference. 

If you named it Notepad2.exe I'd probably change to notepad2.exe (only so I'd not have to remember the N when typing or adding to a command ect.

---

### Post by Panarchy on 2009-04-16
Hmm...

Perhaps. However, Notepad2 doesn't commit any registry changes.

How do I Package Notepad2, its license & input WINE as a dependency needed?

I've been following the Packaging Guide, but I still haven't gotten this to work.

Any advice would be appreciated.

Thanks in advance,

Panarchy

---

### Post by ikonia on 2009-04-16
packaging works the same as it did for all the packages you said you'd made for your own distro, just use the same techniques for packaging as you said you had been doing to make your own packages for your own distro.


you where given the answer on how to make packages in this thread

[http://ubuntuforums.org/showthread.php?t=1072332](http://ubuntuforums.org/showthread.php?t=1072332)

try actually reading the thread this time and the resources in it.

---

