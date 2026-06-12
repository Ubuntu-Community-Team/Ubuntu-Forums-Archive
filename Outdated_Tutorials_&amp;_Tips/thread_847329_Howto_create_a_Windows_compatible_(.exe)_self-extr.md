---
title: "Howto: create a Windows compatible (.exe) self-extracting ZIP file in Ubuntu"
date: 2008-07-02
forum: Outdated Tutorials &amp; Tips
---

### Post by Kajaste on 2008-07-02
**The problem**
A few days back I had to create a Win32 compatible self-extracting ZIP file for a friend. Sounds easy, right. The problem was that I didn't have a Windows machine nearby and I didn't want to install any archiving programs under Wine.

NOTE: A freeware ZIP program such as [IZArc]("http://www.izarc.org/") under [Wine]("http://www.winehq.org/") can be used to create a Win32 self-extracting ZIP file too. That will not be covered by this howto, sorry.

**The "research"**
Googling around I found this [forum post]("http://www.linuxquestions.org/questions/solaris-opensolaris-20/create-a-self-extracting-zip-file-with-zip-on-solaris-242520/") dated August 2003. Reading it I found out that self-extracting ZIP files are nothing more but a suitable unzip binary followed by a normal ZIP file. I used the unzipsfx.exe included in [Info-ZIP UnZip 5.52]("http://www.info-zip.org/UnZip.html").

The link on that post worked a few days ago so I got my hands on the unzipsfx.exe that I was looking for. Today, 2nd July 2008 I found the link dead. After some googling I didn't find a working link anywhere. I read the [licence]("ftp://ftp.info-zip.org/pub/infozip/license.html") a few times and understood that I can redistribute the original unzipsfx.exe with a license included.

Please note that the unzipsfx-552_win32.tar.gz (80 kB) is not an official [Info-ZIP]("http://www.info-zip.org/") package and it includes copyrighted software that I take no credit for. More info in the [Info-ZIP license]("ftp://ftp.info-zip.org/pub/infozip/license.html") that is also included in the tarball. The source code for the binaries included can be found [here]("http://sourceforge.net/project/showfiles.php?group_id=118012").

**The solution**

Step one, getting the unzipsfx.exe and zip package: 
* open the Terminal (in Ubuntu press alt+f2 and type gnome-terminal)
* type in the following commands
```
wget http://kolmoskone.homelinux.org/~kaja/kamaa/unzipsfx-552_win32.tar.gz
tar zxf unzipsfx-552_win32.tar.gz
sudo apt-get install zip
```

Step two, creating a ZIP file in Ubuntu:
* open the file manager (nautilus) and select the files you want to have zipped 
* right click and select Create an archive (or similar). Select a location for the ZIP file, using your home directory is the easiest. Select type .zip.
See man zip for information on how to create a ZIP file in command line.

Step three, making the ZIP file self-extracting
* type in the following commands
```
cat unzipsfx-552_win32/unzipsfx.exe MYZIPFILE.zip > mysfxfile.exe
zip -A mysfxfile.exe
```

mysfxfile.exe can now be opened in any Win32 compatible system (including for example Windows XP/2000/Vista and even Wine in Linux) or ANY ZIP COMPATIBLE archive program such as file-roller in Ubuntu.

---

### Post by fatilili on 2008-07-10
Hi Kajaste,

I have the same problem, I'm searching for the solution from 4 days ago..

before I used Zip2exe.exe to self extract from .zip to .exe, but this one is no longer supported by x64, so I'm searching for a alternative.

I'd like to know where I can find unzipsfx.exe ? and can I call it from my C++ program ?

Thanks

---

### Post by Kajaste on 2008-07-27
[ftp://ftp.info-zip.org/pub/infozip/win32/](ftp://ftp.info-zip.org/pub/infozip/win32/) seems to be up again and unzipsfx.exe can be found in [ftp://ftp.info-zip.org/pub/infozip/win32/unz552xn.exe](ftp://ftp.info-zip.org/pub/infozip/win32/unz552xn.exe) (which in fact is a self-extracting zip file).

---

### Post by Martje_001 on 2008-07-28
Thanks for this, really helpful!

---

### Post by Kromey on 2008-11-26
Hi! I have a similar need, to create a Windows self-extracting ZIP file from a Linux server. However, as these are intended to be used for an automated/unattended update process, I have two additional requirements that I'm hoping somebody can help me with:
1) I need to specify a default directory to extract to. As the server this is being built on is Linux and the target will be Windows, simply telling zip to use the full path won't work - I need to be able to prepend an arbitrary path to the relative paths stored in the archive.
2) I need to be able to set the option to extract automatically, i.e. when executed this archive must immediately extract its files instead of simply presenting the prompt asking if the default location is acceptable.

Any help on these two issues would be much appreciated!

Edit:
I've solved question 2 - using unzipsfx.exe as the stub instead of SFXwiz32.exe provides an automatically self-extracting ZIP, but now I have the problem of needing it to replace existing files without asking.

---

### Post by shane2peru on 2009-05-13
I too would be very interested in this and googling for the answer.  I often make a windows installer to install a data file in a specific directory.  I have been using IZArc under wine because I can't find any Linux native way of doing this.

Shane

Ok in a quick search I dug up this:

[http://manpages.ubuntu.com/manpages/gutsy/man1/unzipsfx.1.html](http://manpages.ubuntu.com/manpages/gutsy/man1/unzipsfx.1.html)

This package is no longer active/existent and seems to have been incorporated into: unzip or zipinfo

[http://manpages.ubuntu.com/manpages/jaunty/man1/unzip.1.html](http://manpages.ubuntu.com/manpages/jaunty/man1/unzip.1.html)

[http://manpages.ubuntu.com/manpages/jaunty/man1/zipinfo.1.html](http://manpages.ubuntu.com/manpages/jaunty/man1/zipinfo.1.html)

If someone was real good with man files they could probably figure out how to accomplish this with this info.

---

### Post by ciroberts on 2010-10-23
I too was having trouble with this trying to create a free software package. Very useful post, thanks guys!! you rock :guitar:

---

