---
title: "Sync wiki between computers using google drive"
date: 2016-06-22
forum: New to Ubuntu
---

### Post by Andrea_Re on 2016-06-22
I don't know if this is the correct section, so (obviously) feel free to move in the right one.
I'd like to know if it is possible to sync a wiki (in my case dokuwiki) between multiple computers using google drive.
I try to elaborate: I have a local folder synced with google drive with Insync (btw, great software). I have installed dokuwiki bitnami stack in another folder in /home.
Can i copy (and if so, how) the dokuwiki folder inside the other folder synced with google drive ?
The goal is to sync the wiki with my home PC, provided that also in this one I have previously installed dokuwiki stack.
Is there someone who has already tried this or that can point me in the right direction ?
Cheers.
Andrea

---

### Post by TheFu on 2016-06-22
Welcome to the forums.

I've never used douwiki or google-drive, but if the files are just simple text then that should be fine.  If the files have a DBMS, then you should shutdown the DBMS, perform the synce, then bring up the DBMS to avoid corruption.  A quick read of the docuwiki install instructions says it is a simple file-based wiki that needs a web server.  Sorta wonder why you don't just access the wiki from the other machine directly? Why make a copy at all?  To me, that's the reason we use Linux - to be able to trivially run servers that we can make accessible however we like.

But ... but ... why go through google at all?  Why not just rsync them directly?

---

### Post by Andrea_Re on 2016-06-23
Thank you for taking time to answer. I really appreciate.
Maybe you are right but I haven't so deep technical skills to follow your solution (a brief tutorial, if you have time, would really be appreciated :) ).
What I would like to achieve is to find a method to obtain a sort of "portable wiki" that automatically syncs between computers (home, office, ...)
Something like what is described [here]("https://primalcortex.wordpress.com/2011/01/07/private-dokuwiki-on-multiple-computers-using-dropbox/") What kept me from trying is the fear of messing with files permissions, ownership and so on.

---

### Post by TheFu on 2016-06-23
Don't know anything about "automatic" synching.  But I have been synching files daily between systems for decades.  For example, I push my password manager DB to about 6 different systems daily, so it is almost always up-to-date everywhere I need it.  I use cron and rsync for this. Cron controls WHEN and rsync controls WHAT and WHERE.  Of course, the systems have to be connected together in a way that allows it.

A solution that hides the details of the required connectivity is beyond my skills. Sorry.  I only know how to do it the old-school, manual, ways.  I do have an idea for how tools like owncloud and seafile work, but cannot recommend those to anyone without a full VPN setup.

OTOH, if you setup ssh access to your home from anywhere in the world, then almost anything you've asked for is possible without trusting the largest advertising company in the world with your data. That's a personal choice, of course.

Maybe someone else can help?

---

