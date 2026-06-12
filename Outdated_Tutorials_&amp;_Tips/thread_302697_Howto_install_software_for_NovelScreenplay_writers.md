---
title: "Howto install software for Novel/Screenplay writers"
date: 2006-11-19
forum: Outdated Tutorials &amp; Tips
---

### Post by tirian on 2006-11-19
For some time, I've been looking for some novel writing software that runs on Linux. Here are two that I've found useful:

[SIZE="5"]**[yWriter](http://www.spacejock.com/yWriter.html)**[/SIZE]
*This is a freeware windows app, but works well via WINE. It is not as fully featured as some of the more mainstream software packages, but it is free and widely used.*

To install:
[LIST]
[*] Install WINE: ```
sudo apt-get install wine
```
[*] download and install yWriter: ```
cd /tmp
wget http://www.spacejock.com/files/yWriter2.exe
wine yWriter2.exe
```
[*] When installing yWriter, if you choose to make a desktop shortcut, you should see the shortcut on your Gnome desktop. If you wish to run the program manually: ```
wine ~/.wine/drive_c/Program\ Files/yWriter2/yWriter2.exe
```
[/LIST]

To uninstall:
```
wine ~/.wine/drive_c/Program\ Files/yWriter2/unins000.exe
```

[SIZE="5"]**[Writer's Cafe](http://www.writerscafe.co.uk/index.htm)**[/SIZE]
*(My personal favorite) Writer's Cafe costs $45, but it is quite fully featured and runs on Windows/Linux/Mac naively. There is a very nice demo version available for download*

To install:
[list]
[*] Download Writer's Cafe for Debian:```
cd /tmp
wget http://www.writerscafe.co.uk/WritersCafe-1.23-i386-gtk2-unicode-debian.tar.gz
```
[*] Install it:```
tar xvfz WritersCafe-1.23-i386-gtk2-unicode-debian.tar.gz
sudo ./installwc
```
[/list]

The installer will ask you a bunch of questions, here are some suggestions for the installation configuration:
[list]
[*]Install data and binaries into: /opt/WritersCafe-1.23
[*]Install launch scripts into: /usr/bin
[/list]

Here is my installer session:
```

--------------------------------------------------------------
Welcome to the Writer's Cafe 1.23 installation.
--------------------------------------------------------------

This script will install Writer's Cafe from the archive:

  WritersCafeData.tar.gz

Select the directory to install Writer's Cafe into
--------------------------------------------------------------

This is where the binaries and data will be copied to.
They can go anywhere you want, but make sure you have the
appropriate permissions if copying outside your home area.

Current value:  /home/tirian/WritersCafe-1.23

New directory: (return for existing value):
**/opt/WritersCafe-1.23**
Select the directory to install launch scripts into.
--------------------------------------------------------------

We will create scripts called writerscafe and storylines which
invoke these applications. You may wish to place these in your
local bin directory, or they can be placed in the Writer's Cafe
install directory (the default location).

Current value:  /opt/WritersCafe-1.23
**/usr/bin**
New directory: (return for existing value):


The directory to install the applications to is /opt/WritersCafe-1.23.
The directory to install the launch scripts to is /usr/bin.

Please check these settings carefully.
Are they correct? (y/n)

**y**

--------------------------------------------------------------
Writer's Cafe 1.23 Installation Menu
--------------------------------------------------------------

Ready to install applications to /opt/WritersCafe-1.23
and launch scripts to /usr/bin.

Please type a number followed by return to choose an option:

 1) Install Writer's Cafe and its launch scripts.
 2) View the readme, with a few words of introduction (install first).
 3) Launch Writer's Cafe (install first).
 4) Change the application installation directory.
 5) Change the launch script installation directory.
--------------------------------------------------------------
 0) Exit from installation.

**1**
Unarchiving /tmp/WritersCafeData.tar.gz
Wrote /usr/bin/writerscafe
Wrote /usr/bin/storylines

*** Success! Writer's Cafe was installed.

--------------------------------------------------------------
Writer's Cafe 1.23 Installation Menu
--------------------------------------------------------------

Please type a number followed by return to choose an option:

 1) Install Writer's Cafe and its launch scripts (done).
 2) View the readme, with a few words of introduction.
 3) Launch Writer's Cafe.
 4) Change the application installation directory.
 5) Change the launch script installation directory.
--------------------------------------------------------------
 0) Exit from installation.

**0**


Goodbye! Your Writer's Cafe installation was successful.
If you have /usr/bin in your PATH you can simply type
'writerscafe' to get started; otherwise run /usr/bin/writerscafe.

You may now delete WritersCafe-1.23.tar.gz and WritersCafeData.tar.gz.
To uninstall Writer's Cafe in the future, remove the following files:

/usr/bin/writerscafe
/usr/bin/storylines
/opt/WritersCafe-1.23/WritersCafe-1.23

For support, please visit:

http://www.writerscafe.co.uk

From the Writer's Cafe team at Anthemion Software,
best of luck with your writing projects.

```

To launch, simply run:```
writerscafe
```

Enjoy!

PS: This is my first howto. If there is some standard format that I am violating please let me know :)
PSS: [WriteItNow](http://www.ravensheadservices.com/download.php) also looks interesting, but I haven't got it running with wine, yet.

---

### Post by bobbyshane on 2007-08-25
When you installed ywriter were you able to edit scenes? when I install ywriter2 everything seems to work fine except when i go to open a scene it brings up an error saying  the rich text file editor could not start and to reinstall ywriter which does no different. When I installed ywriter3 and tried to go into a scene it would just do nothing but then when I went to close it it would say I had to close the editor window (the one that didn't open in the first place) in order to exit the software leading me to have to kill the process. I also followed the directions on the spacejock website and installed the pendrivefiles.exe file and still no go. What version of Ubuntu were you using? In winecfg what version of windows did you have it set for?

---

### Post by cobold0815 on 2007-08-27
I have the exact same problem and this for a long time already. I cannot find the window in which I am supposed to edit the scenes and when I close ywriter, there is this error telling me that there is still something open. :(

I did my installation the same way bobbyshane did using Kubuntu feisty fawn on an acer aspire 1690.

I'd be grateful for help as well...
Micha

---

### Post by DaveDH on 2007-10-03
I want to add that I was having the same problem with yWriter3 - it all worked fabulously except for the Scene window which never appeared on the screen.  yWriter was opening the window, but not showing it (hence the close the windows before exiting message).

yWriter2 and PenDrive install just gave me the same error as BobbyShane got.

Eventually, I did an update on WINE (now runing wine-0.9.46) and then reinstalled yWriter3 (version 3.0.87) ... and it all worked!

I used it most of the day yesterday, and for about 5 hours last night creating stuff and all went diddly. 

BUT, can you believe it... I went to run it this morning and the darn thing wouldn't show the Scene window again!  

I spent all morning without success trying to make it work, and I've just spent another 3 hours this evening and totally failed.

BUT, it's now running again.  I have a dual boot win/ubuntu machine and to get on with my work I installed yWriter3 on under Windows.  After failing to get the version I installed in Wine to work, I just copied the yWriter3 folder from my Windows partition into my /home folder and used Wine to run it... bingo!  It's working again now.

Gawd knows what will happen when I try tomorrow.  Anyway, I just wanted to say that it does run under Wine if you persevere.

---

### Post by cobold0815 on 2007-10-08
I solved the problem. It was all about the wrong rich text control dll's, because wine uses its own ones instead of the ones usally used by ywriter (the original windows dll's). I attached the dll/ocx-files that need to be copied into the windows-system-folder. It's important to remove the other files first that have the same name (but maybe not case-sensitive). I didn't delete them first but since Linux decides between cases ywriter kept using the old windows dll's although the new ones were in the same folder.

```
cp riched20.dll ~/.wine/drive_c/windows/system && cp Richtx32.ocx ~/.wine/drive_c/windows/system32 && cp riched32.dll ~/.wine/drive_c/windows/system32
```

Then configure the dll's with 
```
winecfg
```
The option of chosing the version is only available in the later wine-versions.

Next step: add a new program under the winecfg-surface and the windows version (as said before).

- tab "applications"
- click "add"
- chose the ywriter.exe
- chose "windows wersion" version (I took XP for yWriter 3)

DLL-configuration
- tab "applications"
- mark the program you want to configure the dll's for (ywriter)
- tab "libraries"
- type the name of the dll and add it  at "neue Überschreibung für" (I don't know the english equivalent but it must be something with "new" and "overwrite" ;)
- standard should be "Native, Builtin"

Last but not least you close winecfg via "OK" or "Apply".
Voilà! :)

---

### Post by gimme.credit09 on 2009-11-13
Nice software. I think now i can solve the problems regarding it. :)
If you are having more information please write on this.


Visit this site : [http://www.gimmecreditcompetition.com/](http://www.gimmecreditcompetition.com/)

---

