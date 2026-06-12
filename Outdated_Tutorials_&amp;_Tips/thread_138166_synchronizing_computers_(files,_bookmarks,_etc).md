---
title: "synchronizing computers (files, bookmarks, etc)"
date: 2006-03-01
forum: Outdated Tutorials &amp; Tips
---

### Post by svref on 2006-03-01
Everyone here uses more than one computer regularly.    Everyone here gets annoyed by having files, bookmarks, etc not be accessible on all their computers all the time.  

In the good old days before laptops and wifi, this was not so much a problem, since centralized fileservers could store all your files.  But with laptops and the advent of mobile computing, one has to be able to work even without a network connection.  Each laptop should be able to cache all the files you need and be able to go offline.  Then, when network connectivity is restored, the changes should magically propagate to all the other computers you might want to use.

The ideal solution to this problem is called a "distributed file system", and the good news is that people are working on it.  The bad news is, its still not ready, and since they've been working on it since the 80s, I wouldn't hold your breath waiting.  The three I found were "OpenAFS", "Intermezzo", and "Coda".  For various reasons none of them are worth installing, mainly because they're just not ready for prime time.

So introducing the practical solution.  With a careful definition of what files need to be synchronized, you can make changes on any computer at any time, then reconcile the changes with a synchronization command.  Unless you've been careless and modified the same file on two computers since the last sync, this will be automatic.  (if you HAVE been careless, then you can dig out with some minor hacking, or just choose the version you like better and overwrite the other file).  

**Unison** is a program for synchronizing similar trees of files on different machines.  Unlike rsync, Unison can sync in both directions.  Unison is available in universe, and runs on All Platforms.  It has a nice gtk gui or works from the command line.  The underlying network transfer protocol is ssh, so all your keys and encryption will work perfectly with it.

Using Unison will require you carefully write a configuration file that describes a translation between remote and local files, e.g. in my firefox bookmark-and-password sync file I have:

root = /roam/dave/.mozilla/firefox/oygxf25u.browser
root = ssh://svref@mydomain.com//home/svref/.mozilla/firefox/oygxf25u.browser

This says that I'll be syncing files between firefox profiles locally (on the laptop I'm writing this from) and on my server.  I then go on to tell it to sync bookmarks.html,  key3.db, cert8.db, and signons.txt.  As a result I have firefox's PasswordManager feature remembering passwords I type into any computer, remembered permanently on all my computers.

Okay, in the interestests of full disclosure, I just got this working this morning, I haven't really banged on it hard to see what bad things happen when bookmarks.html gets written while firefox is running and thinks it owns the file.  Your Milage May Explode In Your Face.  However, that's just one application, the file syncing possibilities are good, for, e.g. papers you're working on, source code, artwork, .bashrc, etc.

This article has been a sorta-HOWTO, and has an ulterior motive: can someone come up with a better system?  Writing Unison configuration files is, well, tricky.  It requires careful thought about what should and should not be sync'ed, and when the sync should be done.  Has anyone thought of a better solution?

---

### Post by majikstreet on 2006-03-02
neat... but don't assume that everyone uses more than one computer and gets annoyed at them not being synced... assuming makes an a$$ out of you and me.

---

### Post by 1oki on 2006-03-07
Way to read howtoforge!

[http://www.howtoforge.com/comment/reply/43](http://www.howtoforge.com/comment/reply/43)

---

### Post by Leppiz on 2006-03-09
I got unison working, but I'm having difficulties putting a cron job to do it automatically. I just doesn't do anything, no errors in syslog. I managed to get it working running it in a gnome-terminal by putting this in crontab:
```
10 * * * * DISPLAY=:0 gnome-terminal --execute /usr/bin/unison kissalle
```

I hate the popup because of gnome-terminal. I tried creating a bash script but it didn't work. I even tried to run it in cron as from command line with all the absolute-paths:
```
10 * * * * /usr/bin/unison /home/leppis/koulu ssh://leppis@kissa//home/leppis/koulu -batch
```

I've got ssh authetication made with keys, so it doesn't ask for password and everything works fine from command line. I even ended the last line of crontab, which emacs doesn't do automatically.

SSH authentication seems to be working in cron, i tried it with scp. Also local copying with unison works in cron.

Could someone give me some suggestions how to get this working, please.

---

### Post by svref on 2006-03-11
I'm 99.% sure that just setting DISPLAY=:0 won't work the way you want it to, and in any case I suspect your'e forgetting a ';' after setting DISPLAY.

I'd try figuring out the flag to unison that makes it use the text interface, and passing that in just to be sure.  Yeah, I know, you're passing -batch, so it should have no UI whatsoever, but it can't hurt.

I'd make sure you have the same version of unison on both client and server.

---

### Post by Leppiz on 2006-03-12
> 
I'd try figuring out the flag to unison that makes it use the text interface, and passing that in just to be sure.  Yeah, I know, you're passing -batch, so it should have no UI whatsoever, but it can't hurt.


-ui text or -ui graphic had no effect in cron nor command line, but i played with the thought and added -silent at the command line, and now it works \\:D/ 

It must be a bug of some kind, it seems to do nothing, if it can't print anything...

Thanks for the inspiration!

---

