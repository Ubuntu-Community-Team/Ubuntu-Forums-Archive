---
title: "Gnucash - newbie frustration - rant"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Loki*PI on 2008-04-29
As a newbie I'm getting very frustrated.  There are times when I actually want to use the applications I install rather than chasing around for this library and dependency and reading forums! I want to learn Ubuntu but I also need to actually use my computer to do work.

I'm trying transition from Windows but I'm spending all my time in Ubuntu reading forums.  I have to go back to XP to actually do anything.

Gnucash - I installed it ok, that worked, well it opened.  Nothing in it seemed to function.  Tried to use help, another mess.  No help files.  I checked the forums. Ok,I had to installed the gnucash help file package, I did as instructed but Gnucash couldn't find them.  Spent hours reading the forums on how to get the help to work, never did. Why aren't the help files installed with the original package, seems obvious?  If they are separate they should at least install where the application is going to look for them.

I imported Quicken data, big feature in Gnucash, and it made a total mess of it.  What is the point of importing data if it is all going to be corrupted?     

Tried to update stock quotes another major feature - didn't work.   Read the forums - needed more libraries, needed Perl, installed it all, ran the tests, everything worked and was configured per the forums but Gnucash could not update stock prices. This is one of the main features of the application yet as installed it doesn't work.

It is not just gnucash it seem ubiquitous. Every time I launch ktorrent I have to go in and edit a file to get the GUI to come up.  Then the value is reset either at closing or at launching and I have to edit again. 

Does there come a time when things actually work or is always tweaking this and that, and reading forums? I could have easily purchased the latest Quicken, upgraded, done all I need to do, and be done with the project just in the time I was trying to get the help to work.  Sure Ubuntu and Gnucash are free but my time isn't.

---

### Post by Ek0nomik on 2008-04-29
> **Loki*PI said:**
> As a newbie I'm getting very frustrated.  There are times when I actually want to use the applications I install rather than chasing around for this library and dependency and reading forums! I want to learn Ubuntu but I also need to actually use my computer to do work.

I'm trying transition from Windows but I'm spending all my time in Ubuntu reading forums.  I have to go back to XP to actually do anything.

Gnucash - I installed it ok, that worked, well it opened.  Nothing in it seemed to function.  Tried to use help, another mess.  No help files.  I checked the forums. Ok,I had to installed the gnucash help file package, I did as instructed but Gnucash couldn't find them.  Spent hours reading the forums on how to get the help to work, never did. Why aren't the help files installed with the original package, seems obvious?  If they are separate they should at least install where the application is going to look for them.

I imported Quicken data, big feature in Gnucash, and it made a total mess of it.  What is the point of importing data if it is all going to be corrupted?     

Tried to update stock quotes another major feature - didn't work.   Read the forums - needed more libraries, needed Perl, installed it all, ran the tests, everything worked and was configured per the forums but Gnucash could not update stock prices. This is one of the main features of the application yet as installed it doesn't work.

It is not just gnucash it seem ubiquitous. Every time I launch ktorrent I have to go in and edit a file to get the GUI to come up.  Then the value is reset either at closing or at launching and I have to edit again. 

Does there come a time when things actually work or is always tweaking this and that, and reading forums? I could have easily purchased the latest Quicken, upgraded, done all I need to do, and be done with the project just in the time I was trying to get the help to work.  Sure Ubuntu and Gnucash are free but my time isn't.

I have never used GNUCash, but I have seen other people rant about it.  You have to understand that there are certain areas in which Linux excels, and other areas where Windows excels.  That's why many people chose to run both Windows and Linux.  So, regarding your GNUCash problem, I can't really help you.  However, I will say there should be *plenty* of support for GNUCash out there.

KTorrent on the other hand is an issue that shouldn't be happening.  Would you mind sharing what you have to change for the GUI to appear?  I'll try to find some info for you.  Otherwise you can always try a different torrent application.  My personal favorite is Deluge or rTorrent.  But, if you can expand on your kTorrent issue a bit more I'll try to help.

---

### Post by lazyart on 2008-04-29
Gnucash is a great program, but getting it up and running was tough, especially if you want the online banking features which require a bit of compiling.  I got it finally working, then decided I wasnt going to use it after all.  It hurts too much to remove it, so it sits there.

How to do it is here: [http://wiki.gnucash.org/wiki/Debian](http://wiki.gnucash.org/wiki/Debian)

On top of that, making the account actually work is a bit trying.

---

### Post by Loki*PI on 2008-04-29
To launch ktorrent GUI I have to go to: /home/ric/.kde/share/config/ktorrentrc.  

The line: hidden_on_exit=false has to be set to false for the GUI to launch, it defaults to true.

I posted this on the ktorrent forum but last I checked no solution.

Oddly this happens about 80% of the time, not 100%.

Thanks for the reply.

---

### Post by Ek0nomik on 2008-04-29
> **Loki*PI said:**
> To launch ktorrent GUI I have to go to: /home/ric/.kde/share/config/ktorrentrc.  

The line: hidden_on_exit=false has to be set to false for the GUI to launch, it defaults to true.

I posted this on the ktorrent forum but last I checked no solution.

Oddly this happens about 80% of the time, not 100%.

Thanks for the reply.

Perhaps this is something that will help?

[http://ktorrent.org/forum/viewtopic.php?t=2158&sid=99042582530f25677fe82058283af92e](http://ktorrent.org/forum/viewtopic.php?t=2158&sid=99042582530f25677fe82058283af92e)

---

### Post by Loki*PI on 2008-04-29
Thanks Ek0nomik, I've read that one.  There are several threads that say to change the value but no one mentions it resetting itself to the default 'true'.  Another odd thing when I save the file it creates another file ktorrentrc~, if I save again it creates ktorrentrc~~, etc. 

Thanks again

---

### Post by Ek0nomik on 2008-04-30
> **Loki*PI said:**
> Thanks Ek0nomik, I've read that one.  There are several threads that say to change the value but no one mentions it resetting itself to the default 'true'.  Another odd thing when I save the file it creates another file ktorrentrc~, if I save again it creates ktorrentrc~~, etc. 

Thanks again

Well, the creation of the file with the ~ at the end of it I believe is a feature of the text editor.  It creates a file with the ~ at the end of it without asking you as safety method (it's just a backup file of the original when you opened it)

Have you posted a bug report with kTorrent?  I think Launchpad is a place where you can post bugs related to kTorrent.

I wasn't able to find much beyond that really.  Perhaps a different torrent client would serve you better?  (I assume you have completely removed kTorrent and tried reinstalling?)

---

