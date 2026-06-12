---
title: "ubuntu"
date: 2013-04-09
forum: New to Ubuntu
---

### Post by rtrg on 2013-04-09
I have a cd that is marked XP LIKE. The opening screen displays "UBUNTU" while the OS is loading, NO version number. I believe it is 11. When the desktop opens I see the same default desktop for XP that is called "BLISS". The START MENU is in the same place. Does this mean that downloading and installing software is done using the EXE process? If not how would I use the SOFTWARE CENTER for programs that are NOT offered, specifically OPEN OFFICE SUITE as opposed to LIBRE OFFICE which is the default program? Can I use the SEARCH bar in the CENTER to do this? Type in something like "OPEN OFFICE" or "OPEN OFFICE/INSTALL"? If not How and where do I find the TERMINAL? What is the standard script(command line) for installing OOo or ANY software NOT in the CENTER? I tried a number of DISTROS but found all of them complicated and not intuitive. XP LIKE is at least LOOKS like something I can understand. I need complete and accurate info as to how to use the OS. There are a number of programs I use that are NOT in the center. Simple language in a step format would be nice I do not mind trying something new but only if it is understandable and related to something I already use. Can I go to a publishers web site and download/install in auto mode as I do now? Using the GZ file format in the same way EXE? Solutions please.

---

### Post by snowpine on 2013-04-09
I recommend you throw the XP LIKE CD in the trash (since Ubuntu 11.04 is "end of life," obsolete, and completley unsupported) and download the official current Ubuntu release from here: [http://ubuntu.com](http://ubuntu.com)

This tutorial is a good how-to for installing software in Ubuntu (and there are lots of other good articles on the site): [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

To access the terminal press Control+Alt+T or tap the Windows/Super key and type "terminal."

If you are looking for an operating system that looks exactly like XP and acts exactly like XP and runs EXE files natively, then I recommend Microsoft Windows XP.

---

### Post by mörgæs on 2013-04-09
It's hard to answer such a salvo of questions. Please focus on one subject.

This is worth reading:
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by grahammechanical on 2013-04-09
You are not asking much are you?

As I am not familiar with the XP user interface I cannot help you. Not even to find the location of the terminal. I can tell you this, if this CD is based upon ubuntu 11.04 then the Ubuntu it is based upon has already reached end of life. If it is based upon Ubuntu 11.10, then the Ubuntu it is based upon is about to reach end of life in less than 4 weeks.

I suspect that you are running this form of Ubuntu in Live Session mode. Have you installed it on to a computer hard disk? You cannot change the programs that are on the CD without over-writing every thing that is on the CD. That is a limitation of CD/DVDs even those  that have read/write capability.

Now, if this "ubuntu" was on a large enough USB memory stick it would be something different.

Your best bet is to go to a Microsoft site to learn about the XP user interface and to go to the producers of that CD for advice on how to use the operating system.

Is that your email address in your post? Please remove it. By publishing your email address on a public forum such as this you invite spam.

Regards.

---

### Post by Sandertje on 2013-04-09
Natively, no Linux distribution will do stuff with .exe files. There are methods of using .exe files via [wine]("http://www.winehq.org/"), but this is most definitely not perfect; no one can guarantee you that the .exe file you want to use will actually run. 

A GZ file is essentially nothing more than a compression format, which you could compare to the ZIP and RAR files common on Windows. As such, a GZ file can contain literally anything - from PDFs to MP3s to indeed software. Could be anything, really. 

I guess what you mean by "install like EXE", is "I download this app from the internet, double click it, install it and run it". The closest (on Ubuntu) you'd get to that is using DEB files. Essentially, all packages in the software center are DEB files, but not all DEB files in existence are in the software center. But that is by faaar not the only way of installing software on Linux. It all depends on the format the creators of the software have provided. Some software will simply "work" (no need to install anything) by running some kind of script. For instance, the IntelliJ IDEA IDE doesn't have to be installed, you just decompress the download, and run a bootup script (which is just: double click). Somewhat rarer, there is software that will try to install itself from a binary file directly; these are mostly proprietary programs. Then.. there's also the opportunity of installing directly from source, but in your situation I would *really* discourage that (you gotta know what you're doing there). 

Do keep in mind that Linux simply is NOT Windows. One might be able to make the user interface LOOK like it, but behind the scenes Windows and Linux work *completely*[ differently. If you want to use Linux, you will eventually have to adjust to this different platform.

---

### Post by 3rdalbum on 2013-04-09
You should throw that CD in the bin and get a copy of real Ubuntu. Nobody here will be able to support a respin of Ubuntu with some unknown desktop; I can tell you how to launch programs and the Terminal on regular Ubuntu, but I've got no idea on your strange copy.

You say it's based on Ubuntu 11.04 or 11.10? Both those versions are out of support, or will be unsupported in a month. The latest version of Ubuntu is 12.10, I suggest you try that.

The only operating system that can run Windows programs is Windows. Even if somebody makes Ubuntu look identical to Windows, does not change what it is underneath.

Libreoffice is merely Openoffice.org with a couple of new features. Libreoffice has exactly the same code as Openoffice, but with extra things added.

There is no "standard script" for installing anything that's not in the repositories (Ubuntu Software Center). You can add extra repositories to an Ubuntu system to get to the software you want. That's how you install software on Ubuntu, not by downloading programs from a website.

It sounds to me like you're looking for, basically, Windows XP for free without viruses. This is not what Ubuntu is. Ubuntu is an operating system designed to be easy-to-use and powerful, not to ape Windows. If you want to use Ubuntu, you will have to learn some things that are different. Ubuntu is not difficult, it is merely different. If Ubuntu was anything like Windows XP, most people would not want to use it.

My recommendation is: If you want Windows XP, install Windows XP. If you want to try Linux, try a real Linux distribution instead of something that's pretending to be Windows. I recommend you try Ubuntu 12.10, and once you've tried it and experimented you will probably be able to answer your own questions; if you're still stuck, you can ask for help.

---

### Post by BlinkinCat on 2013-04-09
More reading -

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Cheers - :)

---

### Post by stylintile on 2013-05-05
I can't be positive, but I tried a different distro quite awhile back called YLMF OS.  It was supposed to be just like XP, and it pretty much looked like it.  That is until i clicked on the start button, then it was basically Ubuntu with an XP theme.  I had thought if it was like XP, it might be easier for me to get used to.  But it wasn't like XP in any way other than the theme, and it was a very stripped down version of ubuntu (I think).  I second what has already been said...  Throw it out, if it isn't really XP and either try one of the official Ubuntu (or other distro) new releases, or get an actual XP cd to install from.

---

