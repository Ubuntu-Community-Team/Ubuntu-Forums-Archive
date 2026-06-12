---
title: "Locating libmp3lame.so for Audacity"
date: 2006-01-24
forum: Packaging and Compiling Programs
---

### Post by treyw05 on 2006-01-24
I'm trying to export a sound clip as mp3 so I can use it as a ringtone on my phone, but I can't locate the "libmp3lame.so" to do this. I've compiled and installed the lame-3.97 package, and I was just wondering where I could find the file. Thanks!

---

### Post by gord on 2006-01-25
librarys are generally installed in /usr/lib

---

### Post by frodon on 2006-01-25
You could use these command lines to find the file : ```
sudo updatedb
locate libmp3lame.so
```

---

### Post by phanboy_iv on 2006-01-25
I had the same issue. Here's the pathname:> /usr/lib/libmp3lame.so.0 

---

### Post by inuwashi on 2006-07-10
> I had the same issue. Here's the pathname:
Quote:
/usr/lib/libmp3lame.so.0

Actually you should use 
/usr/lib/libmp3lame.so

---

### Post by tubunu on 2006-07-31
> **inuwashi said:**
> Actually you should use 
/usr/lib/libmp3lame.so

True, that's what Audacity's asking for. But in /usr/lib there's ONLY libmp3lame.so.0
How to fetch the one without 0?

---

### Post by Harleen on 2006-08-01
Just place a link to that file. A library named libxyz.so is usually only a link to the most recent version of the library libxyz. So this should solve your problem:
```
ln -s  /usr/lib/libmp3lame.so.0  /usr/lib/libmp3lame.so
```

---

### Post by mlind on 2006-08-01
That file is part of liblame-dev package, but symlink soname from liblame0 is the proper solution I guess.

Use **apt-file** to find out what package provides the files you need.

---

### Post by Kreg on 2006-10-14
hey im having the same problem and cant get it sorted. i used the sudo updatedb locate mentioned above and it showed the file path, but i still cant find it to use.

when i just type to correct file path into audacity it says it cant open the library.

Kreg

---

### Post by mrLeopold on 2006-10-18
You do need liblame0 as well as liblame-dev.
After installing both of them, I found the libmp3lame.so.0 in the /usr/lib/

[http://packages.ubuntulinux.org/dapper/libs/liblame0](http://packages.ubuntulinux.org/dapper/libs/liblame0)
[http://packages.ubuntulinux.org/dapper/libdevel/liblame-dev](http://packages.ubuntulinux.org/dapper/libdevel/liblame-dev)

---

### Post by Dicabu on 2006-12-31
I installed the Lame 3.96.1 from sourceforge(./configure, make, make install). The libmp3lame.so.0 and the link to it (libmp3lame.so) are in /usr/local/lib, not in usr/lib.
Now exporting to MP3 works fine

---

### Post by danderson3 on 2007-01-26
> **Dicabu said:**
> I installed the Lame 3.96.1 from sourceforge(./configure, make, make install). The libmp3lame.so.0 and the link to it (libmp3lame.so) are in /usr/local/lib, not in usr/lib.
Now exporting to MP3 works fine

aptitude install liblame-dev

now both the so.0 and the link are in /usr/lib

---

### Post by noalka on 2007-10-11
on Ubuntu 7.04 the file libmp3lame.so is in /usr/local/lib  :popcorn:

peace

---

### Post by hanzj on 2007-10-29
I have Ubuntu 7.10 (Gutsy) and  libmp3lame.so.0 is not in my computer, even though i have installed Audacity. Help.

---

### Post by WIREHEAD on 2007-10-30
Hanzj,

I have the same problem.

Interestingly enough navigating through the file system shows that I actually DO have the file .

Places > Computer > Filesystem > usr > lib , then scrolling down to the bottom third of the page shows libmp3lame.so is right there where it should be .

Right clicking on the file then selecting " properties " shows this file as a link to libmp3lame.so.0.0.0 ( which is also there ) , however the file permissions on these files are set to " root " .

If anybody has a quick fix for this let me know .

I am going to log in as root and see what I can do .

WIREHEAD

---

### Post by WIREHEAD on 2007-10-30
This is what I did that got Audacity working and exporting MP3's , or at least the parts of it that I remember ... 

I reinstalled liblame-dev before I realized that the file was already there .

I used gksudo nautilus to change the files  permissions .
I have no idea if this was really necessary  .
Open terminal " gksudo nautilus " without quotes > Enter
Navigate as above to find the file and right click on it , choose permissions and change to allow Read Write and Execute for your username.

If you type " locate < filename > " in a terminal you will still not be able to find the file ( What gives with that I dunno . It's there but locate can't see it ? ).

When you get to the screen in Audacity where it asks you for the file , select browse and find the file the same way you did in Nautilus , be sure to open file in Audacity window .

That allowed me to  " save project as  " , choose " apply chain " from the file menu and choose " apply MP3 conversion to current project ".

I grew up in the 70's so my explanation my be a little hard to follow .
I gotta  go record some noise now ...

Cheers !

WIREHEAD

---

### Post by WIREHEAD on 2007-10-30
Do'H !

[http://ubuntuforums.org/showthread.php?p=3670331#post3670331](http://ubuntuforums.org/showthread.php?p=3670331#post3670331)

WIREHEAD


PS
Elapsed time = 3 hours
I personally have enjoyed this little diversion and consider it a learning experience .
Not everybody will share this opinion .

---

### Post by aysiu on 2007-10-30
Here's a guide with screenshots:
[http://www.psychocats.net/ubuntu/audacity](http://www.psychocats.net/ubuntu/audacity)

---

### Post by amiga_os on 2007-10-31
This problem is only here because of patent issues surrounding distribution of a binary copy of lame.

grrrr.

Seriously, on topic, would it be ok to have liblame0 as a "suggested" dependency in the audacity package?  So Synaptic tells users it might be good to install the library?

This is one of those bits of confusion that is repeated over and over again.

---

### Post by aysiu on 2007-10-31
> **amiga_os said:**
> This problem is only here because of patent issues surrounding distribution of a binary copy of lame.

grrrr.

Seriously, on topic, would it be ok to have liblame0 as a "suggested" dependency in the audacity package?  So Synaptic tells users it might be good to install the library?

This is one of those bits of confusion that is repeated over and over again.
Actually, I think the problem is that people know what to install, but after it is installed, Audacity is looking for *libmp3lame.so.0* but the file is really called *libmp3lame.so.0.0*

---

### Post by philven on 2007-11-02
I used the instructions on making a symbolic link that were detailed earlier in this thread.  It woked.  Just remember to change your bitrate on the mp3s in the preferences in Audacity.  It defaults at 124.  I bumped it up to 192 and it sounds much better.

---

### Post by Kid Bro Sweets on 2007-12-25
> **aysiu said:**
> Here's a guide with screenshots:
[http://www.psychocats.net/ubuntu/audacity](http://www.psychocats.net/ubuntu/audacity)


i tried this method and i don't get these confirmations and it won't export still as an mp3.

---

### Post by sonrock3 on 2008-03-11
Thanks, Mr Leopold
It works for me too!
Stephen

> **mrLeopold said:**
> You do need liblame0 as well as liblame-dev.
After installing both of them, I found the libmp3lame.so.0 in the /usr/lib/

[http://packages.ubuntulinux.org/dapper/libs/liblame0](http://packages.ubuntulinux.org/dapper/libs/liblame0)
[http://packages.ubuntulinux.org/dapper/libdevel/liblame-dev](http://packages.ubuntulinux.org/dapper/libdevel/liblame-dev)

---

### Post by Squash101 on 2008-06-29
This thread can help you if you can't find your lame file:
[http://ubuntuforums.org/showthread.php?t=154583](http://ubuntuforums.org/showthread.php?t=154583)

---

### Post by lazylew on 2008-10-03
> **Squash101 said:**
> This thread can help you if you can't find your lame file:
[http://ubuntuforums.org/showthread.php?t=154583](http://ubuntuforums.org/showthread.php?t=154583)
thanks! that worked :D

---

### Post by Dan Z on 2009-01-31
> **sonrock3 said:**
> Thanks, Mr Leopold
It works for me too!
Stephen

worked like a charm!!:p

---

### Post by gregconquest on 2009-02-11
The solution to the general problem of adding the lame encoding codec is difficult to find, but it was easy to fix.

I opened a terminal and entered:
```
sudo apt-get install libmp3lame0
```
And that was it. Finished.

---

### Post by VanillaMozilla on 2009-04-12
1. Look, Audacity prompts me to find /usr/lib/libmp3lame.so.0, which is not on the computer.  There's a button that says "Download".

The button does not work.  Is this not a bug?  Is this not fixable?  I notice that this is an old thread.  Shouldn't it be taken care of by now?  Has it been reported?  Anyone?

---

### Post by unworthy on 2009-04-26
Thank you, gregconquest
It worked perfectly.
Very grateful to you.

---

### Post by BrianH_1 on 2009-06-03
> **mrLeopold said:**
> You do need liblame0 as well as liblame-dev.
After installing both of them, I found the libmp3lame.so.0 in the /usr/lib/

[http://packages.ubuntulinux.org/dapper/libs/liblame0](http://packages.ubuntulinux.org/dapper/libs/liblame0)
[http://packages.ubuntulinux.org/dapper/libdevel/liblame-dev](http://packages.ubuntulinux.org/dapper/libdevel/liblame-dev)

I am running Hardy and installing both these files worked for me.  Great Help for a newbie  like I am.  Thanks:

---

### Post by Sevenmead on 2010-05-11
I searched "libmp3" in synaptic package manager chose the two packages mentioned in this thread and then clicked ok in the audacity window and it worked.

---

