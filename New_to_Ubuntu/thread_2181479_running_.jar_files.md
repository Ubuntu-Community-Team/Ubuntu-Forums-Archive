---
title: "running .jar files"
date: 2013-10-18
forum: New to Ubuntu
---

### Post by quarkhirad on 2013-10-18
Hi i am running ubuntu 13.04.

I have downloaded a .jar file called RSCAD-3.003-Linux-x86-Setup.jar Now when i right click on the file and click open with openJDK java 7 runtime a dialogue box pops up saying 

```
The file '/media/khirad/Data_D/Shell Folders/Downloads/RSCAD-3.003-Linux-x86-Setup.jar' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit. 
```

How do i make the file a executable??

Some notes:

```

khirad@gini:/media/khirad/Data_D/Shell Folders/Downloads$ ls -l
total 528101
-rw------- 1 khirad khirad    544632 Jun 25 00:03 00801880.pdf
-rw------- 2 khirad khirad     15502 Aug 26 18:30 556883_10151998229500107_437294627_n.jpg
-rw------- 2 khirad khirad     16263 Aug 26 18:26 564493_4355208128418_333983194_n.jpg
-rw------- 2 khirad khirad     11387 Mar 10  2013 AlbumArt_{A2D553D2-1BDF-47EF-939E-58470ED61691}_Large.jpg
-rw------- 2 khirad khirad      2773 Mar 10  2013 AlbumArt_{A2D553D2-1BDF-47EF-939E-58470ED61691}_Small.jpg
-rw------- 2 khirad khirad      2773 Mar 10  2013 AlbumArtSmall.jpg
-rw------- 2 khirad khirad    913832 Oct  4 16:38 chromeinstall-7u40.exe
-rw------- 1 khirad khirad   4300104 Oct  2 10:30 CW1394A0.exe
-rw------- 2 khirad khirad     10595 Oct  2 10:57 dellsystemdetect.application
-rw------- 2 khirad khirad     10699 Aug 11 13:48 dellsystemdetect.bootstrapper.application
-rw------- 1 khirad khirad      1034 Sep 25 20:02 desktop.ini
-rw------- 1 khirad khirad     11387 Mar 10  2013 Folder.jpg
-rw------- 2 khirad khirad    784856 Aug 11 10:57 GoogleVoiceAndVideoSetup.exe
-rw------- 2 khirad khirad   9880374 Aug 11 13:02 iTunes64Setup.exe.part
-rw------- 2 khirad khirad     92671 Oct  4 17:44 [kickass.to]1920.bitwa.warszawska.2011.720p.bluray.x264.dts.b89.film.polski.torrent
-rw------- 2 khirad khirad     14816 Oct  4 17:19 [kickass.to]500.days.of.summer.2009.dvd.rip.nlx.torrent
-rw------- 2 khirad khirad     14772 Oct  4 17:09 [kickass.to]a.walk.to.remember.2002.dvdrip.xvid.torrent
-rw------- 2 khirad khirad     16979 Oct  4 17:11 [kickass.to]dexter.s08e04.season.8.480p.mkv.minirlss.mrlss.torrentino.torrent
-rw------- 2 khirad khirad     16963 Oct  4 17:08 [kickass.to]dexter.s08e06.season.8.480p.mkv.minirlss.mrlss.torrentino.torrent
-rw------- 2 khirad khirad     25003 Oct  4 17:20 [kickass.to]dexter.season.8.complete.480p.hdtv.x264.multi.sub.dexzaery.torrent
-rw------- 2 khirad khirad     14088 Oct  4 17:05 [kickass.to]homeland.s02.season.2.hdtv.x264.evolve.asap.torrent
-rw------- 2 khirad khirad     14796 Oct  4 17:51 [kickass.to]jackie.chan.city.hunter.dvdivx.torrent
-rw------- 2 khirad khirad     14780 Oct  4 17:20 [kickass.to]man.on.a.ledge.2012.proper.dvdrip.xvid.sparks.torrent
-rw------- 2 khirad khirad     14537 Oct  4 18:01 [kickass.to]new.police.story.2004.dual.audio.chi.eng.720p.x264.tynyfy.torrent
-rw------- 2 khirad khirad     14867 Oct  4 17:28 [kickass.to]the.princess.diaries.2001.dvdrip.xvid.torrent
drwx------ 1 khirad khirad         0 Aug 18 14:15 MTECH ENGR OFFER DOC2
-rw------- 2 khirad khirad   1374583 Aug 18 13:06 MTECH ENGR OFFER DOC2.zip
-rw------- 1 khirad khirad  10797616 Oct  2 10:54 R296901.exe
**_[COLOR="#FF0000"]-rw------- 2 khirad khirad 481236942 Oct 17 11:28 RSCAD-3.003-Linux-x86-Setup.jar[/COLOR]_**
-rw------- 2 khirad khirad       286 Oct 14 16:59 rscad_KhiradLT.key
-rw------- 2 khirad khirad  27723672 Aug  9 22:48 Sony PC Companion_2.10.165_Web.exe
-rw------- 2 khirad khirad    375124 Aug 27 20:38 super-solvers-outnumbered.zip
-rw------- 2 khirad khirad   2448565 Aug  9 23:04 userguide_EN_C5503-C5502_2_Android4.2.pdf
khirad@gini:/media/khirad/Data_D/Shell Folders/Downloads$
```

---

### Post by kJkc8Hy on 2013-10-18
To make a file executable from the command line use, chmod +x <filename>

---

### Post by Habitual on 2013-10-18
/path/to/java/bin/java -jar "/media/khirad/Data_D/Shell Folders/Downloads/RSCAD-3.003-Linux-x86-Setup.jar"

---

### Post by quarkhirad on 2013-10-22
Hey guys thanks

---

### Post by Habitual on 2013-10-22
You're very welcome.

---

