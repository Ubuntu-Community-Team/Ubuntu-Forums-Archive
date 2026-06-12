---
title: "[XBMCbuntu] uTorrent run program when download finish: SortTV - Problem"
date: 2013-09-12
forum: New to Ubuntu
---

### Post by amudayey on 2013-09-12
Dear Ubuntu Community,
i am running uTorrent server in a XBMCbuntu PC.
i installed [SortTV ]("http://sourceforge.net/projects/sorttv/")to organize my media.

to run SortTV I type: 
```
eyal@XBMC-PC:~$ /home/eyal/Programs/sorttv/sorttv.pl
```

and everything works great! 
see output:
```
eyal@XBMC-PC:~$ /home/eyal/Programs/sorttv/sorttv.plSortTV
~~~~~~
SortTV is copyleft free open source software.
You are free to make modifications and share, as defined by version 3 of the GNU General Public License
If you find this software helpful, $5 donations are welcomed:
[http://sourceforge.net/donate/index.php?group_id=330009](http://sourceforge.net/donate/index.php?group_id=330009)
~~~~~~
Sorting:
        From /home/eyal/DATA/Downloads/Unsorted/
        TV episodes into /home/eyal/DATA/TV Shows/
        Movies into /home/eyal/DATA/Movies/
        Music into /home/eyal/DATA/Music/
        Everything else into /home/eyal/DATA/Downloads/
22:29:57, 12-8-2013


RAR 4.00 beta 3   Copyright (c) 1993-2010 Alexander Roshal   17 Dec 2010
Shareware version         Type RAR -? for help




Extracting from /home/eyal/DATA/Downloads/Unsorted/try.rar


Extracting  //home/eyal/DATA/Downloads/Unsorted/try.rar (extracted by SortTV)/try.exe  OK 
All OK
RAR: extracting /home/eyal/DATA/Downloads/Unsorted/try.rar into //home/eyal/DATA/Downloads/Unsorted/try.rar (extracted by SortTV)


RAR 4.00 beta 3   Copyright (c) 1993-2010 Alexander Roshal   17 Dec 2010
Shareware version         Type RAR -? for help




Extracting from /home/eyal/DATA/Downloads/Unsorted/try2.rar


Extracting  //home/eyal/DATA/Downloads/Unsorted/try2.rar (extracted by SortTV)/try.exe  OK 
All OK
RAR: extracting /home/eyal/DATA/Downloads/Unsorted/try2.rar into //home/eyal/DATA/Downloads/Unsorted/try2.rar (extracted by SortTV)
SKIP: File /home/eyal/DATA/TV Shows/Breaking Bad/Season 5/Breaking Bad - S05E11 - Confessions.mp4 already exists, skipping.
SKIP: File /home/eyal/DATA/Downloads/Breaking Bad S05E11 HDTV x264-ASAP[ettv]/Torrent Downloaded From ExtraTorrent.com.txt already exists, skipping.
SKIP: already extracted: //home/eyal/DATA/Downloads/Unsorted/Californication.S06E12.HDTV.x264-2HD/californication.s06e12.hdtv.x264-2hd.rar (extracted by SortTV)
SKIP: Matches ignore list: californication.s06e12.hdtv.x264-2hd.r00
SKIP: Matches ignore list: californication.s06e12.hdtv.x264-2hd.r01
SKIP: Matches ignore list: californication.s06e12.hdtv.x264-2hd.r02
SKIP: Matches ignore list: californication.s06e12.hdtv.x264-2hd.r03
SKIP: Matches ignore list: californication.s06e12.hdtv.x264-2hd.r04
SKIP: Matches ignore list: californication.s06e12.hdtv.x264-2hd.r05
SKIP: Matches ignore list: californication.s06e12.hdtv.x264-2hd.r06
SKIP: Matches ignore list: californication.s06e12.hdtv.x264-2hd.r07
SKIP: Matches ignore list: californication.s06e12.hdtv.x264-2hd.r08
SKIP: Matches ignore list: californication.s06e12.hdtv.x264-2hd.r09
SKIP: Matches ignore list: californication.s06e12.hdtv.x264-2hd.r10
SKIP: Matches ignore list: californication.s06e12.hdtv.x264-2hd.r11
SKIP: Matches ignore list: californication.s06e12.hdtv.x264-2hd.r12
SKIP: Matches ignore list: californication.s06e12.hdtv.x264-2hd.r13
SKIP: Matches ignore list: californication.s06e12.hdtv.x264-2hd.rar
SKIP: File /home/eyal/DATA/TV Shows/Californication/Season 6/Californication - S06E12 - I'll Lay My Monsters Down.mp4 already exists, skipping.
SKIP: File /home/eyal/DATA/TV Shows/Orange is the new black/Season 1/Orange Is The New Black - S01E01 - I Wasn't Ready.srt already exists, skipping.
SKIP: File /home/eyal/DATA/TV Shows/Orange is the new black/Season 1/Orange Is The New Black - S01E02 - Tit Punch.srt already exists, skipping.
SKIP: Matches ignore list: try.rar
SKIP: File /home/eyal/DATA/Downloads/try.rar (extracted by SortTV)/try.exe already exists, skipping.
SKIP: Matches ignore list: try2.rar
SKIP: File /home/eyal/DATA/Downloads/try2.rar (extracted by SortTV)/try.exe already exists, skipping.
```

**PROBLEM IS**... when i set uTorrent to run SortTV when a download finish.
then i get:
```
Executing: /home/eyal/Programs/sorttv/sorttv.plSortTV
~~~~~~
SortTV is copyleft free open source software.
You are free to make modifications and share, as defined by version 3 of the GNU General Public License
If you find this software helpful, $5 donations are welcomed:
[http://sourceforge.net/donate/index.php?group_id=330009](http://sourceforge.net/donate/index.php?group_id=330009)
~~~~~~
DBM::Deep: Cannot sysopen file '/.tvdb.db': **[COLOR=#ff0000]Permission denied[/COLOR]**
```

why Permission is denied??
see uTorrent server permissions:
```
eyal@XBMC-PC:~$ ls -l
lrwxrwxrwx 1 root root         34 Aug 26 20:52 utserver -> /opt/utorrent-server-v3_0/utserver
```

Please Help!

---

### Post by LukeMorrison on 2013-09-12
Have you tried running the executable using sudo first?  If not, you are running it in as a non-root user, which will not have root permisions.  You will be asked to enter your password, but you will not see anything printed on the screen as you are typing it.  Hit enter when you are done and it should now allow you to run your program

---

### Post by amudayey on 2013-09-13
> **LukeMorrison said:**
> Have you tried running the executable using sudo first?  If not, you are running it in as a non-root user, which will not have root permisions.  You will be asked to enter your password, but you will not see anything printed on the screen as you are typing it.  Hit enter when you are done and it should now allow you to run your program

LukeMorrison thank you for the quick reply!
the "sudo" is not the issue.. 
When I run the command myself on terminal, i run it without sudo and it works.
the problem is when it's not me running the command, it's when uTorrent runs it,
you can tell uTorrent to run a command when a download finishes.
I defined that commend to be the same command i would run myself on terminal,
meaning:
```
/home/eyal/Programs/sorttv/sorttv.pl
```

LOOK PICTURE - uTorrent defined to run SortTV when a download finishes:
[IMG]http://s18.postimg.org/smkyo0q3d/utorrent_image.jpg[/IMG] 

please help guys!

---

### Post by shlomilanton on 2013-12-14
I have the same issue when I run the same programs (uToreent and Sorttv).
When the file is still seeding.

I know that this is an old issue but I hope that someone wiil be able to help me
Thanks

---

