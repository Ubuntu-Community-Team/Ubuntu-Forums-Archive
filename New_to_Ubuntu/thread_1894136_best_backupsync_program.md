---
title: "best backup/sync program?"
date: 2011-12-11
forum: New to Ubuntu
---

### Post by JohnDillinger43 on 2011-12-11
I'm trying to find a suitable backup program for Ubuntu.  I use SyncToy on Windows and have been pleased with it.  What I'm looking for is I guess more of a sync program: I don't really have a need for multiple complete backups, I just want current copies of all my files on a backup drive that I can restore in the event of a HDD failure or something similar.  I want something that will sync only modified files, rather than doing a complete backup each time; I do a lot of photography and music creation (as well as music listening), so I'm looking at backing up 1TB+ of files.  Most of the programs I've looked at either only do full backups, or don't do unidirectional syncs, etc., so I'm open to suggestions.

---

### Post by jonnyboysmithy on 2011-12-11
Dejadup will do all this: [http://live.gnome.org/DejaDup](http://live.gnome.org/DejaDup) its what I use and it works fine.
Maybe someone could write up a script (or find a way) to copy files that skips the ones that haven't been edited since the last backup..

---

### Post by JohnDillinger43 on 2011-12-11
Yeah I was looking at that one, but I can't find a way to pair individual folders, which is one of the features I like about SyncToy.  Probably it would be mostly a non-issue except that my backup drive currently has all my backup stuff stored in specific folders, and I'd like to continue to be able to let SyncToy back up when I'm running Windows.  Don't know if that would be possible with Dejadup?

---

### Post by llamabr on 2011-12-11
[https://help.ubuntu.com/community/Unison](https://help.ubuntu.com/community/Unison)

---

### Post by JohnDillinger43 on 2011-12-11
Unison looks to be exactly what I was looking for.  Installing it as I type.  Thanks!

---

### Post by jonnyboysmithy on 2011-12-11
I think I'll use unison instead of dejadup. What bothers me about dejadup is that I can't view the files because their in some other format. Unison=Lovely!

---

### Post by cbanakis on 2011-12-11
I have not tried it out yet, but I had a similar question recently, and someone recommended rsync.

---

### Post by kurt18947 on 2011-12-12
> **cbanakis said:**
> I have not tried it out yet, but I had a similar question recently, and someone recommended rsync.

I've played with Grsync, rsync with a graphical frontend.  I tried Unison and found it not all that intuitive when backing up to a local drive, it looked easier to configure to backup over a network.  I may not have understood how to use Unison properly but found Grsync  pretty straight forward when backing up to an external USB drive.

---

### Post by intruderukr on 2011-12-13
I wish the developers who did Backintime would fix it. That was my favorite backup.

---

### Post by JohnDillinger43 on 2011-12-14
I think my optimistic note about Unison was premature -- like kurt18947 I found it unintuitive when actually trying to use it.  Grsync looks more like what I was looking for.  For those of you who use it, I have two newbie questions: (1) can I set up multiple pairs of folders under a single session profile, so that I don't have to manually select pairs of folders each time, and (2) can I schedule rsync to run at a certain time every day?

---

### Post by ElSlunko on 2011-12-14
I've trusted back in time for the last 4 years for my photography and it worked out just fine.

---

### Post by Akhnatoun on 2012-05-07
[SIZE="3"]You may need to try FreeFileSync. [http://sourceforge.net/projects/freefilesync](http://sourceforge.net/projects/freefilesync)

it is the best sync application ever, it's even better than the most of backup/sync MST Windows applications. Whatever your need from a sync software, u will find FreeFileSync useful as it's easy, flexible, fast and full of essential syncronization options. Before I use it, I was switching to Windows in a dualboot PC, just to do sync jobs to my external USB HD, but now, I don't know how my Windows looks like ;)[/SIZE]

---

### Post by forrestcupp on 2012-05-07
This is an old thread, but if anyone is interested, Luckybackup is pretty good. It's a nice graphical front end to rsync, and it sounds like it would be perfect for the OP.

---

### Post by cmcanulty on 2012-05-07
I love grsync, fast and only the files are  copied that changed. Also every file can be accessed in it's normal path. No need to restore everything to just get a few files or folders.Just read a bit about the options before using be careful of the delete on destination box as if you make a mistake files are gone. I backup all of /Home which is 160GB 2x a week and it takes a very few minutes.

---

