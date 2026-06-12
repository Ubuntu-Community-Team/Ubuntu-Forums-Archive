---
title: "Vanishing mp3s"
date: 2013-06-11
forum: New to Ubuntu
---

### Post by mlnease on 2013-06-11
Hello!

I like to back up my music cds to my 'Music' directory for playing directly from my computer.  This has always worked fine until suddenly--all the 'folders' are empty.  As if I'd shift-deleted every song individually, leaving only the empty 'folders'.  Nothing in Trash, nothing in root Trash.

Any advice?

Thanks in advance.

mike

p.s.  I've just checked my most recent full backup and the files are missing there, too--so, apparently, this has been going on for a while.  My external hard drive seems unaffected.

---

### Post by papibe on 2013-06-11
Hi mlnease.

Have you run any terminal commands recently? Something that might have moved/deleted files around?

Try looking for any mp3 by running:
```
find ~ -iname '*.mp3'
```
Regards.

---

### Post by mlnease on 2013-06-11
> **papibe said:**
> Hi mlnease.

Have you run any terminal commands recently? Something that might have moved/deleted files around?

Try looking for any mp3 by running:
```
find ~ -iname '*.mp3'
```
Regards.

Thanks for the quick response and for the code.  I ran it but the vanished files didn't reappear--and no, though I use the terminal when I can, my command line skills are elementary at best--after all these years, I'm still pretty much a gui user.

Thanks again for your interest.

---

### Post by papibe on 2013-06-11
May be the backup process is not backing properly your files.

Do you miss any other files? If so, are they missed on the back too?

Regards.

---

### Post by mlnease on 2013-06-11
> **papibe said:**
> May be the backup process is not backing properly your files.

Do you miss any other files? If so, are they missed on the back too?

Regards.

Thanks again but no, the backup is otherwise complete, as are my other files on the original hard drive.  Just empty 'folders'--with their original filenames--empty of files.

p.s.  Empty, that is, of the--exclusively--mp3 files they originally contained.

---

### Post by gnuman on 2013-06-11
I've been using different music players lately, and, depending on their settings, they may try to help you organize your collection in one way or another.  That's my first question: which music player do you use, and have you checked the "library" settings on it?

The next thing I've come across recently were problems with filenames--especially those that have slashes in them (not a good idea).  I've been using [detox]("http://detox.sourceforge.net/") to clean up my file names, as gmusicbrowser (the player I use) was having trouble managing the library folders.  After some work getting things cleaned up a bit, a LOT of empty folders were left behind.  

Anyway, just a couple ideas that may help figure out the cause.  Good luck!

---

### Post by mlnease on 2013-06-12
> **gnuman said:**
> I've been using different music players lately, and, depending on their settings, they may try to help you organize your collection in one way or another.  That's my first question: which music player do you use, and have you checked the "library" settings on it?

The next thing I've come across recently were problems with filenames--especially those that have slashes in them (not a good idea).  I've been using [detox]("http://detox.sourceforge.net/") to clean up my file names, as gmusicbrowser (the player I use) was having trouble managing the library folders.  After some work getting things cleaned up a bit, a LOT of empty folders were left behind.  

Anyway, just a couple ideas that may help figure out the cause.  Good luck!

Hello, *Gnuman*!

Thanks for the response, my apologies for the delay.  Actually I usually just use Movie Player (Lucid's default?) for simplicity's sake.  I've dabbled a bit in Rhythmbox--didn't care much for it--and VLC.  However none of them shows any of the missing files in its 'library'.  None of the filenames included slashes but maybe I'll have a look at 'detox' just the same--thanks for the advice.

---

### Post by gordintoronto on 2013-06-13
Lucid has reached end of life, although that didn't cause your problem. However, it makes it more difficult to help you. Do you have a program called "disk utility" or something along those lines? If you point it at your hard drive, it should be able to report on the "health" of the drive, using the SMART data.

---

### Post by mlnease on 2013-06-13
> **gordintoronto said:**
> Lucid has reached end of life, although that didn't cause your problem. However, it makes it more difficult to help you. Do you have a program called "disk utility" or something along those lines? If you point it at your hard drive, it should be able to report on the "health" of the drive, using the SMART data.

Thanks for the response, GIT (no offense),

First, yeah, I understand about Lucid (*sob*).  I'll have to migrate soon.  Meanwhile, I do have gnome-disk-utility > palimpsest (from the gnome-disk-utility project) is a tool to manage disk
drives and media:

 * Format and partition drives.
 * Mount and unmount partitions.
 * Query S.M.A.R.T. attributes.

It utilizes udisks. 
I haven't yet used it but I will, as you suggest, 'point it at my hard drive', see what happens and post the results here.

Thanks again for your interest.

p.s.  I discovered another vanished file today, this one a .avi.  Curiouser and curiouser...

---

### Post by mlnease on 2013-06-13
> **gordintoronto said:**
> Lucid has reached end of life, although that didn't cause your problem. However, it makes it more difficult to help you. Do you have a program called "disk utility" or something along those lines? If you point it at your hard drive, it should be able to report on the "health" of the drive, using the SMART data.

All righty then, done.  Thanks for telling me about Palimpsest (gnome-disk-utility)--very nifty!  It seems to think my hard drive is fine.  Any other thoughts?  Anyone?

---

