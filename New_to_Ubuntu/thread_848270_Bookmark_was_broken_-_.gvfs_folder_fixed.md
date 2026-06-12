---
title: "Bookmark was broken - .gvfs folder fixed"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by Chris_Sugden on 2008-07-03
Although my first root login was 1988 (i386 Xenix), I have been so long in Winworld that I really am a newbie.

I have a bookmark to a subdirectory on a Win box that could no longer be reached using Kompozer (a HTML WYSIWYG editor) to open or save files.  Browsing through Nautilus still worked, just not the File Open nor Save dialogs.

Research showed that the dialogs relied on a file in the /home/chris/.gvfs subdirectory.

I found that this subdirectory was left in an unusable condition after the last Samba update.  Issuing the command "ls -al /home/chris" showed the .gvfs subdirectory had all "?" for its permissions, users, etc.

Logging in as root did not give me the ability to fix this, as far as I could tell from playing around.

Here is my workaround:
[LIST=1]
[*]Boot from the Live CD (Take the time to make one if you haven't yet)
[*]Use System->Administration->Users and Groups to add a password for root
[*]Stay in users admin and add chris as a user under the Live CD login
[*]Open Terminal
[*]su
[*]cd /media/disk/home/chris
[*]chown chris:chris .gvfs
[*]Restart the computer
[*]Boot normally - no Live CD
[*]Open Terminal
[*]chown chris:chris /home/chris/.gvfs (This is not a mistake, I had to do it again under the normal boot)
[/LIST]

Even logging in as root, I could not fix this problem without booting from Live CD.  It seemed that the .gvfs subdirectory was left "open".

The Live CD work gets the subdirectory to be recognized, but with the wrong owner (Here I wish I knew more than a newbie).  The second chown fixes all.

Remember to insert YOUR username where I have "chris".

Hope that helps.

---

### Post by Anzan on 2008-07-03
Interesting. Thanks.

---

