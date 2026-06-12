---
title: "[C++] How to check drive free space?"
date: 2008-01-01
forum: Programming Talk
---

### Post by EXCiD3 on 2008-01-01
I am writing an application in C++ using QT. Basically everything uses QT so that it is cross-platform compatible. What I need now is to check the drive space on ANY platform. Is there something built into QT that can do this or do i need to have OS specific sections that are used when the app is compiled on the other OSes? I need to be able to check the drive space on Linux, Windows, and Mac OS. Thanks for any help!

---

### Post by geirha on 2008-01-03
I think you need OS-specific sections. In unix you would use statfs() while in windows you would use GetDiskFreeSpace(). I doubt QT has anything that can do this, and I don't know of any other library that will abstract it for you.

---

### Post by EXCiD3 on 2008-01-03
Hey thanks. Thats what I figured i would end up using. I was hoping there would be a library that would be able to abstract it for me so that all that i would need to do was compile it on the other os other than using a language like java.

---

### Post by GeneralZod on 2008-01-04
Qt doesn't have this, to my knowledge, but I'm fairly sure kdelibs does.

> I doubt QT has anything that can do this

Actually, this is *precisely* the kind of thing I would expect to find in Qt, and I'm rather surprised that it isn't there.

Edit: Well, what do you know - looks like I'm wrong, and kdelibs *doesn't* have this functionality.  I wonder what Dolphin looks like under Windows, then?

Edit2: Lol - I was right all along:

[http://api.kde.org/4.0-api/kdelibs-apidocs/kio/html/kdiskfreespace_8cpp-source.html](http://api.kde.org/4.0-api/kdelibs-apidocs/kio/html/kdiskfreespace_8cpp-source.html)

---

### Post by xen on 2008-01-04
If you can't find anything within QT, have you tried looking at [Boost]("http://www.boost.org/") libraries? They are also cross-platform and I'm sure one of them could do what you are looking for.

I found [this]("http://lists.trolltech.com/qt-interest/2004-08/msg01173.html") on a mailing-list, which may also help.

Sorry if this doesn't help!

---

### Post by Cesa on 2008-09-23
So, did you ever find anything? I am in a similar situation right now (though I'm not using QT), and it would be very nice if I didn't have to implement this function for each OS.

I looked at Boost, but I couldn't find anything that returns the free space for a drive.

---

