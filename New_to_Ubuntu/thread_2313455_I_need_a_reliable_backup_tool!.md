---
title: "I need a reliable backup tool!"
date: 2016-02-12
forum: New to Ubuntu
---

### Post by JorgeO on 2016-02-12
Hello, my first post.

A short time ago I gave up on Windows and started using Ubuntu. So far, so good. I configured a second notebook to my liking, but then I found in the WEB a suggestion to try KDE.
I did it, did not like (the need to re configure all again), and decided to remove it. Big mistake, the nice Ubuntu install became shaky.

No problem, I have a very recent Deja Dup backup. Restore it and presto.

Not so fast. Restoring the backup crashed, both using the Linux in the HD and the Live CD. So, I`m typing in a PC after hours of reconfiguring it.

Is there a reliable backup (preferably GUI) I can use, that won`t let one down when need arises?

Thanks,

Jorge

---

### Post by HermanAB on 2016-02-12
All good backup tools use rsync underneath.  Backintime is one of them.  It is in the repos.

---

### Post by grahammechanical on 2016-02-12
Excuse me, but are you saying that you used Deja Dup to backup and restore a computer operating system?  I see one problem with doing that. 

> Some versions of Déjà Dup will not correctly restore files stored in **a  folder that you did not have write access to when you backed them up**.   After the restore completes, you will get an error screen listing each  file that was not restored.  You can still manually copy the files to  where you&#8217;d like them to be by going to the temporary folder named in  the error dialog and moving the files.

We do not normally have write access to system folders.

> The primary use case for Déjà Dup is backing up user data

[https://wiki.gnome.org/DejaDup/Help/Restore/Full](https://wiki.gnome.org/DejaDup/Help/Restore/Full)

Regards.

---

### Post by Habitual on 2016-02-12
> **JorgeO said:**
> after hours of reconfiguring it.
You may wish to consider a separate /home directory.

With one of those, you can re-install in 30 minutes, depending on processor and memory.
I've had the same /home for 8 years and the same desktop for all 8.

---

### Post by JorgeO on 2016-02-12
[URL="http://ubuntuforums.org/member.php?u=44990"][B][COLOR=#000000]@ HermanAB - Thanks!

  [/COLOR][/B]**[COLOR=#000000] [/COLOR]**[/URL][B][COLOR=#000000][@ ]("http://ubuntuforums.org/member.php?u=1087323")[URL="http://ubuntuforums.org/member.php?u=1087323"][B][COLOR=#000000]grahammechanical - Yes, that`s what I`ve done for years and it always worked.

[/COLOR][/B][/URL][URL="http://ubuntuforums.org/member.php?u=504341"][B][COLOR=#000000]@ Habitual - Have you tried to get an answer from Google when what used to work on say, Ubuntu 12 doesn`t works anymore on 14? I tried before asking.

And BTW Deja Dup CRASHED in the middle of the restore, not a single error message. [/COLOR][/B][/URL]
[/COLOR][/B]

---

### Post by buzzingrobot on 2016-02-12
> **JorgeO said:**
> 

...a suggestion to try KDE.
I did it, did not like (the need to re configure all again), and decided to remove it. Big mistake, the nice Ubuntu install became shaky.



As a side note, installing a large and complex suite of packages like KDE and then trying to remove everything cleanly is very often asking for trouble.  A full install of KDE from the kde-full metapackage adds about a gig's worth of packages.  (Many, many packages.)  The safest way to sample a different desktop environment is booting an install image of the appropriate Ubuntu spin and running it live in "Try" mode.

I don't use DejaDup so I can't add anything there.  I only backup portions of my home directory.  It's so quick and easy to do a reinstall that I don't find it necessary to worry about system backups and recoveries.

---

### Post by Habitual on 2016-02-12
> **JorgeO said:**
> @ Habitual - Have you tried to get an answer from Google when what used to work on say, Ubuntu 12 doesn`t works anymore on 14? I tried before asking.
Sure have. Been doing so since google was in Beta. <search_term> +"ubuntu 14"
My signature is not directed at you personally, or this subject. It's just a signature. ):P

---

### Post by Mark Phelps on 2016-02-13
Personally, I use Clonezilla but have also used RedoBackup.  The first provides more features but is more difficult to use; the second is simpler and uses a GUI.

---

### Post by HermanAB on 2016-02-13
BTW, making a backup of the system itself is a total waste of time and resources.  There are hundreds of Linux mirrors out there, you don't need to make a backup of Linux.  

Just save your data and install a fresh system when the inevitable happens.

---

### Post by yogich246 on 2016-02-19
Thank you, Mark Phelps...I discovered that Ubuntu's 14.04 Backups app leaves a bit to be, desired.

---

### Post by trag on 2016-02-20
Try TimeShift or SystemBack

---

### Post by leunam12 on 2016-02-20
I use clonezilla to backup the system partition and rsync to backup /home and my storage drive.
Another option is tar.

---

