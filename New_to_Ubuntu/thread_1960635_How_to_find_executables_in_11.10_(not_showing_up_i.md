---
title: "How to find executables in 11.10 (not showing up in dash)"
date: 2012-04-17
forum: New to Ubuntu
---

### Post by jps2012 on 2012-04-17
I'd love to launch 7zip, which the Software Center says is installed, but the program doesn't show up using "file find" in dash. 

Typing 7zip at the command line doesn't launch it in Terminal. 

The questions: is the Software Center sometimes wrong about what software is installed (I'm having the same issue with other executables; I've executed "updatedb," and the update manager)? 

If it IS installed, how could I get it to show up in dash (the side panel)? 

Thanks, 
JPS

---

### Post by 3rdalbum on 2012-04-17
7zip is not a GUI program. It just provides 7z compression/decompression support to Ubuntu's default archive manager, 'File Roller'.

Therefore you can't add it to the Dash or Launcher. File Roller/Archive Manager is already in the Dash and can be dragged to the Launcher.

---

### Post by jps2012 on 2012-04-17
3rdalbum: That helps A LOT! And explains a lot. I guess dash shows plugins as well as executables (correct me if I've got that wrong). I did try to use File Roller (otherwise known as Archive Manager?) to compress a folder with jpgs in it. 

I haven't been able to figure it out. An Ubuntu FAQ says I have to context click to start a compression. The FAQ is here: [https://help.ubuntu.com/community/File%20Roller](https://help.ubuntu.com/community/File%20Roller)

Right clicking on a file (I can't seem to do a "select all") doesn't offer the options listed in the FAQ, and I see no options for compressing. If compression isn't possible with File Roller, please let me know. 

I posted a screenshot of the File Roller GUI here (which appears to be very different than the GUI described in the FAQ): 

[http://s1071.photobucket.com/albums/u503/2012jps2012/?action=view&current=ArchiveManagerCantCompress.png](http://s1071.photobucket.com/albums/u503/2012jps2012/?action=view&current=ArchiveManagerCantCompress.png)

---

### Post by jps2012 on 2012-04-17
A little more info on trying to launch zip (instead of my original launch effort, which was for "7zip," the plugin): below is my command and the shell's response: 

$ open zip
Couldn't get a file descriptor referring to the console

I went to the developer website. It doesn't appear that there are Ubuntu releases, and all the sites for binary downloads have the tagline "FROZEN," which is a little worrisome. Maybe because of how much trouble people were having with the program? 

If anyone wants to recommend a program that can zip files, I'd be grateful.

---

### Post by anejo on 2012-04-18
I like and use 7z... one of my Windoze carryovers
Ok first thing, you have to install 'p7zip-full' and I also like to add, 'p7zip-rar'
From Nautilus, whenever you select a stack of files or folders, right-click and select 'Compress',
you'll note that one of the extensions types will be '.7z'
'7z' itself can also be run from the command line

---

### Post by codemaniac on 2012-04-18
For 7-zip to be installed you need to make sure if p7zip-full package is installed .check if 7zip is installed on your system by below commnad on terminal .
```
which 7z
```

---

### Post by jps2012 on 2012-04-18
Thanks, codemaniac. I didn't know about the "which" command.

---

### Post by codemaniac on 2012-04-18
there is **whereis **command also that can be used to locate the binary, the source code and the online manual page for any specified program.
```
whereis 7z
```

---

### Post by jps2012 on 2012-04-18
Very good to know. I appreciate the help.

---

### Post by 3rdalbum on 2012-04-18
I'm unsure what I'm looking at with the screenshot you posted, but you have to click the New Archive button (the one on the extreme left) in the File Roller/Archive Manager window to create the archive first. Then you can drag files into the File Roller window to compress them and add them to the archive.

Don't worry about the difference between the current look of File Roller and the FAQ you saw. The FAQ is extremely old and the user interface has changed slightly, but the actual workings of File Roller have remained unchanged.

---

### Post by jps2012 on 2012-04-19
Just a further note about conflicting info from bash vs. Nautilus/Software Center. The Software Center says I've got 7zip installed. 

But running "$ whereis 7zip" returns no location. 

The lesson from this, for all us new users, is _don't believe what you see in Nautilus or Software Center._ Verify files (their existence, their non-existence) at the command line.

---

### Post by 3rdalbum on 2012-04-19
> **jps2012 said:**
> Just a further note about conflicting info from bash vs. Nautilus/Software Center. The Software Center says I've got 7zip installed. 

But running "$ whereis 7zip" returns no location. 

> p7zip provides:
  - /usr/bin/7zr
    a standalone minimal version of the 7-zip tool that only handles
    7z archives. 7z compression is 30-50% better than ZIP compression.
  - /usr/bin/p7zip
    a gzip-like wrapper around 7zr.

The package description of p7zip tells you. It's not "7zip", it's "7zr". And if this is too confusing, then you shouldn't be using 7zip on the command-line; instead use File Roller like the package description suggests :-)

---

