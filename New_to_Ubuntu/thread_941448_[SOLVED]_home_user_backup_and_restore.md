---
title: "[SOLVED] home user backup and restore"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by telltommy on 2008-10-08
i downloaded this program yesterday. incase someone doesn't know, it backups the home folder and restore. i opened the program thru system, admin, and it took along time to open. i reinstalled the program and it opened after about three minutes. i ran it and saved to cd. fine. i deleted a photo to test it's restore, but it doesn't open. system, admin, home restore and it won't open.

---

### Post by talsemgeest on 2008-10-08
What format does the program save it's backups as?

---

### Post by telltommy on 2008-10-09
It's saving to cd. If i open the cd it reads:
dar archive
/media/cdrom 0
mine type application/x-dar

---

### Post by talsemgeest on 2008-10-09
OK, so what is the file extension of the backup file/s?

---

### Post by germanix on 2008-10-09
The file ext. is ".dar". I did not see this post, I just posted a similar problem.

---

### Post by germanix on 2008-10-09
I found the following in Internet. At least it helps somewhat. I t still however does not explain why HUBackup is not functioning properly.

Restoring file using HUBackup

After receiving quite some emails about folks bewildered by the crashing hurestore I think it's only fair to create a post about how to restore files from archives created using hubackup using the underlying archiver , DAR.

Usually after a typical run of hubackup you will have two resulting files:

.hubackup-data/paepp-master-archive.1.dar
.hubackup-data/paepp-master-catalog.1.dar

(Thanks goes to Peter Päppinghaus for sending me an email about this)

To restore , which actually usually means extract in DAR's language you need to do something like:

dar -x .hubackup-data/paepp-master-archive -R TARGET_DIR

If there is more then one slice DAR knows how to switch between them properly.

That should be enough for most of operations, for more detailed explanation of what dar can do in restoration (or backup for that matter) DAR's manual pages are quite good. 
Posted by Sivan Greenberg at 9:31 PM

and here another .

Restore Files

Restoring files from System&#8212;>Administration&#8212;>Home User Restore is not working for me i.e it is crashing for me in ubuntu gutsy so we need to use command line restore.

Home user backup application hubackup using the underlying archiver , DAR.

Usually after a typical run of hubackup you will have two resulting files

/home/backup/ruchi-master-archive.1.dar
/home/backup/ruchi-master-catalog.1.dar

To restore , which actually usually means extract in DAR&#8217;s language you need to do something like:

dar -x /home/backup/ruchi-master-archive -R TARGET_DIR

If there is more then one slice DAR knows how to switch between them properly.

---

### Post by Therion on 2008-10-09
You might find [QuickStart](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11) easier to use.

---

### Post by telltommy on 2008-10-09
too complicated. i switched to using sbackup. thanks for trying to help me, i'm just not very skilled when it comes to terminal stuff.

---

### Post by talsemgeest on 2008-10-09
Quickstart is about the easiest backup solution there is. Just tell it what to back up, where to back it up and it does it all for you. No command line involved!

---

### Post by DGortze380 on 2008-10-09
I would look at using rsync, or ask nicely and maybe someone here will right you a script, or even a program for that matter.

---

### Post by crjackson on 2008-10-09
> **Therion said:**
> You might find [QuickStart](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11) easier to use.

At work right now so I can't test this out yet.  Will QuickStart let me back up an individule folder and preserve the permissions?

---

### Post by talsemgeest on 2008-10-09
If it is in your home folder, you can exclude everything else, and that should do it.

---

### Post by crjackson on 2008-10-09
> **talsemgeest said:**
> If it is in your home folder, you can exclude everything else, and that should do it.

It is.  I just want to backup my .mozilla.thunderbird emails and my .tomboy notes.

---

### Post by talsemgeest on 2008-10-09
That should work well enough then.

---

### Post by telltommy on 2008-10-10
went with Quickstart. It works great and so easy to use, thanks.

---

### Post by talsemgeest on 2008-10-10
Cool, glad you like it. Oh, and don't forget to mark the thread as solved.

---

