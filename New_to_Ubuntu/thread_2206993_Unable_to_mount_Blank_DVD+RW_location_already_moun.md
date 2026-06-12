---
title: "Unable to mount Blank DVD+RW location already mounted."
date: 2014-02-21
forum: New to Ubuntu
---

### Post by wiggy252 on 2014-02-21
Hope someone can help with this.

I have now after many years removed Windows Vista completely and now running with Ubuntu 13.10 only, first time with Linux was with Maverick Meercat!
Went over to Mint for a while dual boot with Vista then used Vista on it's own but now come back to Ubuntu running just the standard install.

The problem is with the DVD drive, I have seen other posts about this but no fix.
If I put a blank DVD+RW into the drive it comes up with:-

"Unable to mount Blank DVD+RW disc
Location is already mounted"

If I create an empty file and burn it to the disc using Brasero it will detect it with no problem at all.
Only seems to be blank discs.

The DVD is working fine and it is a rewriter.
Was/is there a fix for this?

I think it has been flagged in launchpad as a bug, but looks as though it's been given a low priority, which is very odd.
I would like to be able to just put a DVD in and be able to just copy things to it when needed, at the moment I can't do that.
The only way I've found to work this is to auto open it with Brasero create an empty folder on the disc, then try and burn items to the disc and hope it works!

Thanks

Ian

---

### Post by Vladlenin5000 on 2014-02-21
The error itself doesn't impede you to use the drive for burning - Brasero, k3b, others... are usually fine - and probably that's the reason for the low priority. It's just a misplaced/unwarranted error message.

---

### Post by tinman2 on 2014-07-30
I'm having the same exact problem on Ubuntu 14.04 LTS.  If I insert a blank DVD-RW, I get the "unable to mount" error.  Then when I try to look at the disc with Krusader or any other file manager it doesn't show up.  I also have a DVD-RW with files on it that the system recognizes, but I'm still  not able to delete or move any files or folders on it.  Keep getting a pop-up saying something about not having permissions even though Krusader shows the file permissions as readable/writeable.  This has really become a huge pain in the ass with me trying to make backups on DVD-RW disc.

---

### Post by Vladlenin5000 on 2014-07-30
> **tinman2 said:**
> I'm having the same exact problem on Ubuntu 14.04 LTS.  If I insert a blank DVD-RW, I get the "unable to mount" error.  Then when I try to look at the disc with Krusader or any other file manager it doesn't show up.  I also have a DVD-RW with files on it that the system recognizes, but I'm still  not able to delete or move any files or folders on it.  Keep getting a pop-up saying something about not having permissions even though Krusader shows the file permissions as readable/writeable.  This has really become a huge pain in the ass with me trying to make backups on DVD-RW disc.

Honestly, you're assuming as a problem what is just an usage paradigm. Up to XP you couldn't do what you want - by the way, it isn't either practical or safe - unless you installed some third-party drivers (included in the Nero suite and another one I don't remember). It often caused more problems, namely making the discs unreadable in other computers, without any clear productivity gain...
Why should you be able to treat an optical disc as an hard drive? And what is so different about doing it from inside a pure file manager or from inside the file manager in, for example, K3b?

---

### Post by tinman2 on 2014-07-30
> **Vladlenin5000 said:**
> Honestly, you're assuming as a problem what is just an usage paradigm. Up to XP you couldn't do what you want - by the way, it isn't either practical or safe - unless you installed some third-party drivers (included in the Nero suite and another one I don't remember). It often caused more problems, namely making the discs unreadable in other computers, without any clear productivity gain...
Why should you be able to treat an optical disc as an hard drive? And what is so different about doing it from inside a pure file manager or from inside the file manager in, for example, K3b?

  Seriously?  Your answer is it's just a usage paradigm?  And even before XP you could use a CD/DVD re-writeable disc as a hard drive and could be formatted in several different flavors to work with other computers as well.  I have never had a problem of a CD/DVD-+RW not working on another computer as long as the other computer had the correct InCD packet drivers installed unless the drive was out-of-date or didn't have the correct/full drivers installed.

  "Why should I/we be able to use an optical disc as a hard drive?"  Really?  Perhaps to copy/move/delete files just like you would on a hard drive, the reason for having a re-writeable drive!  It would be a shame to have to run virtual Windows just to use a re-writeable drive as it was intended.  Kind of defeats the reason for having a re-writeable drive on Ubuntu/Linux.

  The difference between a pure file manager and K3b is like the difference between a text editor and an office suite.  While K3b is useful for writing .iso's or creating music disc, a file manager is used just for that, manageing files, like deleting, moving or copying.

---

