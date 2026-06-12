---
title: "Oneiric - I know its Alpha 2, unstable ... but I would like to ask :)"
date: 2011-07-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by An Sanct on 2011-07-12
I'm just downloading Oneiric RC2 and would like to actually test it (thus - no Virtual Machine stuff)

I already have Natty installed on one partition, making it a triple boot (Maverick/Natty/Win7) and I would like to swap Natty with Oneiric, just to see what kernel 3.0rc5 has to offer to me :)

So, my actual questions are: 
-Is it safe? 
-Can I make a Live USB (because images are over the CD size) and install without the fear of loosing any other information on my disk (Other OSes...)?
-Will the partitioning/HDD space assigned be respected by the installer or will it FUp my disk?

-Other known issues?
-any other suggestions or helping hints I should see/know, before doing so?

---

### Post by Quackers on 2011-07-12
You should take a look at the OO forum below and maybe ask a moderator to move your thread there.
[http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=403](http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=403)

---

### Post by An Sanct on 2011-07-12
[Quackers]("http://ubuntuforums.org/member.php?u=369240") asked me to move [my question]("http://ubuntuforums.org/showthread.php?t=1802603") to this part of the forum ... 

So, would an administrator please do so :)

I would have done this before ... but my Firefox add-on named 'Ubuntu Forums Menu 0.59' doesn't want to work on FF 8.0a1 - I had to hack the RDF to make it install ... sorry, it is outdated ...

edit: forgot to tell you, the menu is outdated, and brought me to the location, my post is in after choosing "install and upgrade"....

---

### Post by An Sanct on 2011-07-12
done so ... now waiting for it to happen :) ... grrr... misspelled the topic there ...

---

### Post by Quackers on 2011-07-12
In answer to your questions
you can make a usb, yes.
You can choose manual partitioning and over-write your Natty installation with Oneiric.
Yes, it is safe, but you must bear in mind that it is in alpha and is likely to break with updates from time to time.
Read this forum and see what problems others have had then make your judgment.

You should also bear in mind that any partitioning or installing of operating systems carries a risk. Things can go very wrong sometimes.
It is wise to backup any data which you would not like to lose.
It is also wise to make sure that you can recover your Windows system without using the recovery partition (which can get damaged). You should also make a Windows repair disc if you don't already have one. (Control Panel > Backup & Restore Centre > make recovery cd). 
NOTE this is not a recovery dvd, but a repair cd, which MS calls a recovery cd.

---

### Post by philinux on 2011-07-12
Threads Merged. Please use the Report/Abuse button at any time to get the attention of staff to move threads etc.

---

### Post by An Sanct on 2011-07-12
> **Quackers said:**
> In answer to your questions
you can make a usb, yes.
You can choose manual partitioning and over-write your Natty installation with Oneiric.
Yes, it is safe, but you must bear in mind that it is in alpha and is likely to break with updates from time to time.
Read this forum and see what problems others have had then make your judgment.

You should also bear in mind that any partitioning or installing of operating systems carries a risk. Things can go very wrong sometimes.
It is wise to backup any data which you would not like to lose.
It is also wise to make sure that you can recover your Windows system without using the recovery partition (which can get damaged). You should also make a Windows repair disc if you don't already have one. (Control Panel > Backup & Restore Centre > make recovery cd). 
NOTE this is not a recovery dvd, but a repair cd, which MS calls a recovery cd.

Thank you :) ...


PS. I could not care less about my Win7 partitions (I'm thinking of wiping it), it's ALL the stuff on my Maverick partition, that I'm worried about ....

---

### Post by An Sanct on 2011-07-12
> **philinux said:**
> Threads Merged. Please use the Report/Abuse button at any time to get the attention of staff to move threads etc.

Thanks :) I'm kinda not into pushing the "report abuse" button on myself :) ... at least never thought about it ...

---

### Post by Quackers on 2011-07-12
You're welcome :-)
Just backup your needed data from Maverick first then.

---

### Post by jbicha on 2011-07-12
It depends on what you mean by "safe". Yesterday there was a critical bug which prevented the mouse and keyboard from working so please don't depend on a development build as your only way to use the computer because things break.

---

### Post by VinDSL on 2011-07-12
> **An Sanct said:**
> So, my actual questions are: 
[LIST]
[*]Is it safe? 
[*]Can I make a Live USB (because images are over the CD size) and install without the fear of loosing any other information on my disk (Other OSes...)?
[*]Will the partitioning/HDD space assigned be respected by the installer or will it FUp my disk?
[/LIST]I only have a minute, then I need to run...

Yes, it is "safe" but you need to be uber careful.  Click the wrong button, during the install process, and you can easily wipe your existing installs.

I do fresh installs all the time, (now) using the Hybrid CD/USB image.

Here is a quick HOWTO:  [http://ubuntuforums.org/showpost.php?p=10945413&postcount=1](http://ubuntuforums.org/showpost.php?p=10945413&postcount=1)

Lastly, life will be much easier, if you maintain a separate /home partition, and NEVER format it.  You can format / (e.g. root) and the swap partition(s), but during the installation process, leave your /home partition alone.

Hope that makes since.  BBL

---

### Post by An Sanct on 2011-07-12
Things break and I am happy, they do, IT is a part of development and people need to see it break, to report issues and make the final product near perfect!

... I want to see that :) 

... I just don't want my little experiment (Oneiric in a eprouvette) to 'kill' my work machine (Maverick since the release) ... but I'll make sure it doesn't ... (64GB OS disk-SSD, 1TB backup disk HDD, I'll make an 100% image of the OS disk before proceeding .... ;))

My main boot is still Maverick and I keep a Maverick Live USB in my pocket to go for sure ...

I'm marking this thread as solved, Thank you (in chronological order ...): 
jbicha, 
Quackers - for bringing me to the right place and for the answer!
philinux - for merging the two threads
**edit: VinDSL ... tnx!**

I will follow this part of the forum for a few days and then (after the backup and all...) try to make it work like magic :) as it is supposed to be ...

edit: WOW :) When answering and closing this thread, VinDSL showed up! ... thank you too ;) I'll be reading the link you posted tomorrow, its late here ...

---

### Post by An Sanct on 2011-07-12
Ow ... tried to run it in VirtualBox ... the screenshot is what happened

... it threw me into a terminal ... huh?

(enough resources ... i5, three cores assigned, 3072Mb ram, 640Gb disk ... what else does an OS want?)

---

### Post by An Sanct on 2011-07-12
I browsed the net for a few minutes then ... then ... kapow !!!! GUI appeared :) Install is willing and able :) so, discard my last rant about it not working! ;)

---

### Post by Quackers on 2011-07-12
That's good news :-)
I know little of VB.

---

