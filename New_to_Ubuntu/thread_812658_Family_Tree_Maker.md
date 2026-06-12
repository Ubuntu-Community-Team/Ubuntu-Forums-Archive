---
title: "Family Tree Maker"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by BornCynic on 2008-05-30
Is FTM v16 compatible with Ubuntu?  Anyone using this program in Ubuntu?

---

### Post by PmDematagoda on 2008-05-30
I am not very familiar with genealogy software, so I am just giving you some applications you can try out:-

1) GRAMPS:-
```
sudo apt-get install gramps
```

2) Lifelines:-
```
sudo apt-get install lifelines
```

3) Geneweb:-
```
sudo apt-get install geneweb
```

---

### Post by Buster95 on 2008-09-30
I have used FTM for many years and couldn't get any of the versions to work in Dapper, Fiesty or Hardy. I've had to retain a Windows dual boot capability just to run it (and my old Canon N640P scanner which I've never been able to get working in any Ubuntu release).

I have now migrated my master file to GRAMPS (3.0.1)and have been testing it for about two months in parallel.

So far, it has performed well with the following comments:
* It's not quite as intuitive as FTM but as I get used to it, it's becoming easier.
* The GEDCOM import resulted in some relatively minor issues with sources and source notes, but they were easy to recognise and correct. In any case, I suspect the problem may have been more to do with translating the FTM format to GEDCOM than with the GRAMPS XML format.
* I'm still evaluating the reliability and accuracy of archive and backup. The GRAMPS "package" format is supposed to backup any linked JPEGs along with the data files. Currently, I lose the links to any JPEG files when I backup the file then restore it using.

Cheers

---

### Post by malleus74 on 2008-11-04
A Family Tree Maker equivalent is one of two programs that I need to switch totally to Ubuntu. Besides games, I'm trying not to use Wine. :)

Is there a way to import / convert (*.ftw, *.ftm ? maybe?) files into Gramps? Long story, but at the second it wouldn't be real easy to install Family Tree Maker on my laptop... and I have a direct lineage and some offshoots going back 400 years. 

Also, having limited experience with Gramps, does it have the main features / as easy to use as FTM? I really liked the tabbed / tree view FTM used.

---

### Post by bayvista on 2009-03-12
I have switched from FTM to Gramps and find it quite OK. Of course there are differences, but if you are a confirmed Ubuntu user, make the switch. It saves a lot of time in rebooting.

---

### Post by anewguy on 2009-03-12
I also have been a dedicated FTM fan for years, and also would like a replacement in Linux.  I've tried Gramps and a couple of others and really didn't like them - they aren't as intuitive and the "view" is different right from the start.  I have found no way to directly import a FTM file - only from gedcom.  This has also turned me away from migrating, as I have many photos, etc., that aren't handled by the export to gedcom, so I would have to do them manually.  Part of the reason for this is that FTM has their own database I just haven't been able to hack apart yet, so there are no external tools that I am aware of for migrating a complete FTM file to another product.  There is a browser based tool called The Next Generation (link is [http://lythgoes.net/genealogy/software.php]("http://lythgoes.net/genealogy/software.php")).  It uses MySql and PHP, but I haven't looked at it enough yet to see if it will work in Linux.  It's like $30, and what I saw on the demo pages wasn't bad.  I think if I can get it to run natively in Linux that it would be the tool I would chose and then bite the bullet to migrate all my photos, etc..

Dave :)

---

### Post by malleus74 on 2009-03-12
You hit exactly on my problem! I have a lot of interconnected data in FTM, and I don't even want to **imagine **how long it would take to convert to another format by hand. I've yet to find a tool that will convert it for me correctly.

---

### Post by anewguy on 2009-03-12
I would love to decode FTM's internal database structure so we could all do this.  Maybe I'll give it another crack or 2.  It may take me quite a while, so don't expect an answer right away.  I know FTM does it to lock people in to their product, but it sure would be nice if one could export EVERYTHING.

I'll let you know how my adventure goes.

Dave :)

---

### Post by click4851 on 2009-03-12
I also made the switch to Gramps from FTM, luckily I had procrastinated about adding photos. Since the migration I've been adding photos like a drunken sailor....Yes its not FTM, but its free, and no more proprietary formats.

---

### Post by malleus74 on 2009-03-13
If you can crack the format, I'm all for it! You'll have at least one fan!

I'm all for free and non-proprietary, but it'd be nice to have another ui for Gramps. I really like Family Tree Maker... but I'm not trying to restart the argument with user-friendly vs. familiar here :)

I just want to eventually eliminate Vista, but not at my own expense. It's kinda like music for me.... I use the mp3 format mostly because it works on any platform I use... plus I'd probably lose a lot of quality converting to ogg.

---

### Post by bayvista on 2009-12-27
Anyone got FTM 2009 working under Wine. I've tried but get a string of error messages. What about 'VirtualBox'?

Just to let everyone know that I got FTM 2009 working OK using VirtualBox. However, I agree with other contributors and suggest that you have a good look at  Gramps. It may not have all the features of FTM, but it will improve.

---

### Post by Mark Phelps on 2009-12-29
> **BornCynic said:**
> Is FTM v16 compatible with Ubuntu?  Anyone using this program in Ubuntu?

The following page is from the WinHQ site, clearly indicating that newer versions of FTM will not work with Wine:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=494]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=494")

And yes, they don't have an entry for "v16" (the 2010 version), but given that the more recent versions are rated Garbage, there's no reason to suspect this new version will be rated any different.

---

