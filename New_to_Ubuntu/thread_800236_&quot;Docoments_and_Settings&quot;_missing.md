---
title: "&quot;Docoments and Settings&quot; missing"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by Darvon on 2008-05-19
Hi people!

So I'm new here, and I've installed Hardy Heron with wubi on Windows XP last week. I have only one drive, with WinXP and now Ubuntu on it.
My problem is weird, I tried to get help at the germen forum (My Windows and Ubuntu are german) but they didn't find any solution.

The problem is: My Documents and settings folder (at Windows), is missing when I look for it at /host/Dokumente und Einstellungen (= Documents and Settings); 
More precisely: situation in windows: C:\Documents and Settings\ My Username\ All my stuff lke My Documents etc.

situation in Ubuntu: /host/Dokumente und Einstellungen\ WITHOUT the folder "My Username", so all my documents from Windows are missing.
Everything else is there, so anything which is not in this specific folder.

I tried something in despair:
Hence my username in Windows contains some weird characters and a space (like á á), I changed that, but I didn't change it in the registry. Nothing changed.
I created another windows user (I called it hjkl) with admin rights. Now the Folder and all files are visible in Ubuntu. I could now copy and paste all my stuff from one folder to another, but I dont have that much empty space on my disk, and I want to use my Windows further, so deleting them won't be good.
I uninstalled ubuntu and reinstalled it (yeah, I mean it) bot of course nothing happened.

enough for now

Darvon

Edit: 
Yeah I noticed the typo in the title... can I somehow change it? It would be better for those who use the search function

---

### Post by KenBW2 on 2008-05-19
Firstly: Willkommen bei Ubuntu :)

About your suggestion that the specialised characters might be causing problems - I don't think this should be the case as I have german music with umlauts and the like, and there's no problem with that. At the worst it might show a ? or something in place of the character, but not fail completely.
However, I've never tried Wubi, and that might be the source of your problem. You might want to try instaling Ubuntu the normal way (after uninstalling the wubi install to save space) to see if that works. You say you don't have much free space - you should only need about 2.5GB minimum - or if you're really desperate you could try Xubuntu, although it's not as good.

Let me know if you need help installing Ubuntu the normal way, and let me know how it goes :)

PS: about the title - I've renamed it on this post - we'll see if it changes the thread's title

---

### Post by Darvon on 2008-05-20
Okay, but installing it "the normal" way needs another partition as far as I know... and I have only one, which is C:
I'm no pro with partitioning, I always did that in the windows installation when I wanted to, but that won't work for now. So how could I install Ubuntu otherwise? Or how could I make another partition without dleting my files? Or any other suggerstion? :)
Btw, I said that with the disk space because the "My Documents" Folder ist quite big, so copying it to the other user, so having it twice, would be quite a waste, with only a few GB in Windows remaining. (And Windows is hungry:) )

Darvon

---

### Post by hyper_ch on 2008-05-20
(1) Get a partitioning tool for windows. Vista has one included, XP not (I think)
(2) If you're low on diskspace, you can Start --> Settings --> System --> System restore (or whatever it's called in english) and deactive system restore or lower the limits of it...)... that will free some diskspace / also delete the WUBI instalallation, that should also free some space...
(3) BACKUP YOUR DATA!!!!!!!
(4) Defragement your drive 2-3 times
(5) Use the partitioning tool (if you have none, have a look at PartitionMagic) and shrink the windows partition... I'd say to run confortable Ubuntu make about 7-8 GB free... that should leave you some room for swap and more programs. DO NOT PARTITION THIS SPACE. JUST LEAVE IT UNPARTITIONED!
(6) Then install ubuntu from the desktop/alternate cd and select "USE LARGEST FREE CONTINUOUS DISK SPACE". That will then use this unpartitioned space


----------------

But I have no clue why documents and settings disappeared... well, I've never used wubi...

---

### Post by KenBW2 on 2008-05-20
I see from the fact you have "Documents and Settings" that you're using XP. If you don't have/don't know of any partitioning tools for Windows (I know I don't) then you can easily partition your hard drive from the Ubuntu LiveCD from System > Administration > Partition Editor

You will see your hard drive as one big partition:
```

 ________________________________________
|////////////////////                    |
|////////////////////____________________|
    USED                    FREE

```
You need to shrink that partition to allow for the Ubuntu partition. Right-click the partition and select "Resize/Move", and drag the right-hand arrow to the left until it shows you as having about 8GB free space following resizing.
```

 ________________________________________
|////////////////////      |             |
|////////////////////______|_____________|

```
Right-click the empty space and click "New", let it fill the empty space (this should be default) and then shrink it as above, leaving about 1.5GB free following. At "Filesystem" select "ext3".
```

 ________________________________________
|////////////////////      |           | |
|////////////////////______|___________|_|

```
In the small emty space create a new partition as above and select "linux-swap" from Filesystem.

Apply all changes (make sure you've backed up!), then go through with the installation, setting the ext3 partition as "/" and the swap as "swap".
_______________________

After you've installed you should have no problems accessing your Windows My Documents. Create a shortcut on the desktop and in Nautilus' bookmarks section in the left panel to your My Documents folder and use that (at least that's what I do when I install Windows on others' PCs. I abandoned Windows months ago, so my stuff is stored with Ubuntu). You won't need to duplicate all of your documents because Ubuntu can access your Windows files - whereas Windows can't access your Ubuntu partition.

Let me know how that goes :)

---

### Post by Crossroads on 2008-05-20
Installing Ubuntu may get round the problem but I would still be interested in a solution to it. Perhaps you could post the problem in the Wubi forum here (with apologies for the double post ;)).

Before installing Ubuntu, can you try booting from a LiveCD and seeing if your files appear in the "Documents & Settings" folder?


---
I don't think it is possible to edit the thread title.

---

### Post by Crossroads on 2008-05-20
I just found this thread, with a similar problem:
[http://ubuntuforums.org/showthread.php?t=730028](http://ubuntuforums.org/showthread.php?t=730028)

---

### Post by Darvon on 2008-05-20
When I start from Live CD, I can see the folder, but not in the host folder, there is a "100 GB Medium" or somesing like that there, where the content of my HDD is completely visible, every file, also my folder in the Documents and settings.

I have a Linux expert roommate, who tried to help me: He tried to mount the drive manually (like in the thread, posted by Crossroads) but it didn't work. 
Now I'll read the two threads posted in THAT thread, and than I'll see. But still thanks for the help, at least I can read posts about people having the same problem :)

And the typo gives this thread a "unique touch" :D In future I'll look three times for mistakes :S

---

### Post by Darvon on 2008-05-20
The problem is fixed, it is a known bug in wubi, in the wubi forum they've seen it immediately ( [http://ubuntuforums.org/showthread.php?p=5003914#post5003914](http://ubuntuforums.org/showthread.php?p=5003914#post5003914) )
Thank you for the help, but this whole thing didn't really help me to find ubuntu better than windows... but I guess that will come with time. At least I hope so.
Thank you for the support,
problem solved

Darvon

---

### Post by Crossroads on 2008-05-20
I'm glad that the problem has beentracked down and a oslution is on its way. :)

---

