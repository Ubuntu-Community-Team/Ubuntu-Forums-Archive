---
title: "Simple mp3splt-gtk / Mp3spl with graphical front end. Split mp3 / ogg"
date: 2008-01-18
forum: Outdated Tutorials &amp; Tips
---

### Post by Omnios on 2008-01-18
I like playing around with audio files so I installed [FONT=Arial][SIZE=2][B]mp3splt-gtk
[/B][/SIZE][/FONT] From what I have read so far it is based on the command like program  mp3splt with a graphical front end, 

 Now this little how to is based on the fact that the downloaded program has a dependies problem and also requires that you install another deb package named libmp3splt_0.3.1. The links to the files are below. Other than downloading the two files its a simple install except there is no menu for it installed. A menu how to is at the bottom of this post.

This is a link to Gnome-files that has a lot of info on this package.
[http://www.gnomefiles.org/app.php/mp3splt-gtk](http://www.gnomefiles.org/app.php/mp3splt-gtk)


```

mp3splt :
 
Mp3splt is the command line program from the mp3splt-project.
    
  libmp3splt :
 
Libmp3splt is a library created from mp3splt version 2.1c.
  
   mp3splt-gtk :
 
 Mp3splt-gtk is a GTK2 gui that uses libmp3splt. 

``````

 mp3splt-project common features :[LIST]
[*]split mp3 and ogg files from a begin time to an end time *without decoding*
[*]split an album with splitpoints from the freedb.org server
[*]split an album with local .XMCD, .CDDB or .CUE file
[*]split files automatically with silence detection
[*]split files by a fixed time length
[*]split files created with Mp3Wrap or AlbumWrap
[*]split concatenated mp3 files
[*]support for mp3 VBR (variable bit rate)
[*]specify output directory for split files[/LIST]
``````

 "Synaptic local install description"

GTK2 gui that uses libmp3splt to split mp3 and ogg files
without deconding
 .
 Homepage: http://mp3splt.sourceforge.net/

``` 

[COLOR="Blue"]Download the Deb package links from SourceForge :[/COLOR]

= download the mp3splt-gtk package

 link = : [COLOR=Blue][sourceforge=mp3splt-gtk_0.3.1_i386.deb]("http://sourceforge.net/project/downloading.php?groupname=mp3splt&filename=mp3splt-gtk_0.3.1_i386.deb&use_mirror=easynews")[/COLOR]
 
= download the   libmp3splt_0.3.1 package

link = :[COLOR=Blue][sourceforge=libmp3splt_0.3.1_i386.deb]("http://sourceforge.net/project/downloading.php?group_id=55130&use_mirror=easynews&filename=libmp3splt_0.3.1_i386.deb&13462726")[/COLOR]

 This package does not install a menu item. The program can be launched with the terminal with the following command.

```

 mp3splt-gtk

```

 To make a menu item from menu choose 

 Menu
            Preferences
                                   Main Menu
   
 In the menu program  click on the sound or an other main area you want the menu item for the program in.

 Now click add item "not New Menu" 

 In the pop up menu Give the menu a name such as  "splt-gtk" for example   
  this is the name that you will see in the menu. For the command
 use mp3splt-gtk which is the launcher for the program. You can also give it a icon by clicking the square thing on the top left.

---

### Post by Vinger on 2008-02-06
Hello,

I installad mp3splt-gtk succesfully. I can split files without problems except for this one:

The splitted files haven't good mp3!
The problem is that the players (snackamp or beep media player) don't play my music well. so the converting is also not good!

What can be the problem?

grz

---

### Post by LeDechaine on 2008-05-13
Installed this program...
...Uninstalled it less than 5 minutes after.

The program was giving me an "inexistent file" error, even if the mp3 file was right in front of my eyes. Now i'm searching for a working alternative.

---

### Post by moa3333 on 2008-06-03
Ok, the ast version is not yet stable.

The new version will come in a few days!

You can use the new version, supposed to be much more stable.

If you find any bugs in the new version, submit them to the tracker, the project is NOT abandoneware!

---

### Post by rykel on 2008-06-05
Hi,

I cannot install mp3splt-gtk on Ubuntu Hardy Heron, because it says that it needs to have beep-media-player installed. However, Hardy only has bmpx (Beep Media Player Experimental) and so mp3splt-gtk thinks that Beep is unavailable. (see screenshot)

Please help?

---

### Post by devehf on 2008-06-14
The deb package doesn't work for me either due to the same BMP dependency error. Tried to make the binary with make and got the following error.

```
In file included from /usr/include/libmp3splt/mp3splt.h:34,
                 from tree_tab.c:41:
/usr/include/libmp3splt/mp3splt_types.h:34:17: error: mad.h: No such file or directory
In file included from /usr/include/libmp3splt/mp3splt.h:34,
                 from tree_tab.c:41:
/usr/include/libmp3splt/mp3splt_types.h:296: error: field ‘stream’ has incomplete type
/usr/include/libmp3splt/mp3splt_types.h:297: error: field ‘frame’ has incomplete type
/usr/include/libmp3splt/mp3splt_types.h:298: error: field ‘synth’ has incomplete type
/usr/include/libmp3splt/mp3splt_types.h:300: error: expected specifier-qualifier-list before ‘mad_fixed_t’
make[2]: *** [tree_tab.o] Error 1
make[2]: Leaving directory `/home/davef/mp3splt-gtk/mp3splt-gtk-0.3.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/davef/mp3splt-gtk/mp3splt-gtk-0.3.1'
make: *** [all] Error 2
```

i don't understand the error msg because the directory "/usr/include/libmp3splt" certainly exists as does the mp3splt_types.h file. is there an error in this file?

---

### Post by optimix on 2008-09-05
The new mp3splt-gtk version 0.5 now supports Audacious instead of Beep Media Player. It should work on Hardy.

---

### Post by nemodx on 2008-11-06
Under 8.10 it is impossible to get it to compile.

---

### Post by optimix on 2008-12-03
Here is a temporary fix for the compilation issue :

[https://sourceforge.net/tracker2/?func=detail&aid=2144760&group_id=55130&atid=476061](https://sourceforge.net/tracker2/?func=detail&aid=2144760&group_id=55130&atid=476061)

---

### Post by bogyit on 2008-12-19
under ubuntu 7.04 it's impossible, I can't find libtool and autotools-dev :(

---

### Post by Hated On Mostly on 2008-12-19
getdeb has the latest version of Mp3splt available as a deb package:

[http://www.getdeb.net/app/Mp3splt](http://www.getdeb.net/app/Mp3splt)

---

### Post by IB1Dance on 2009-01-03
> **Hated On Mostly said:**
> getdeb has the latest version of Mp3splt available as a deb package:

[http://www.getdeb.net/app/Mp3splt](http://www.getdeb.net/app/Mp3splt)

Has anyone got the mp3splt-gtk GUI working with 8.10 (intrepid)?.

As 2 others have reported on getdeb.when I click and open a mp3 file to load it up, no mp3 is loaded.

---

### Post by zekopeko on 2009-01-06
same here. 8.10.

---

### Post by Hated On Mostly on 2009-01-12
If you can't get mp3splt to work use mp3directcut in WINE.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=6785](http://appdb.winehq.org/objectManager.php?sClass=application&iId=6785)
[http://mpesch3.de1.cc/mp3dc.html](http://mpesch3.de1.cc/mp3dc.html)

mp3directcut works perfectly for me in WINE.

---

### Post by optimix on 2009-01-18
You can try installing the latest intrepid packages from the mp3splt project web site :
[http://mp3splt.sourceforge.net/mp3splt_page/downloads.php](http://mp3splt.sourceforge.net/mp3splt_page/downloads.php)

---

